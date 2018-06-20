---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC yapılandırması bir kaynak olarak kullanarak bileşik kaynakları--
ms.openlocfilehash: 246cab3b437546490d650e45be263a43fd0c84c3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189372"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a>Bileşik kaynaklar: DSC yapılandırması bir kaynak olarak kullanma

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Gerçek dünya durumlarda yapılandırmaları uzun ve karmaşık, birçok farklı kaynaklar çağırma ve özelliklerinin büyük bir sayıya ayarlanması olabilir. Bu karmaşıklık gidermeye yardımcı olacak diğer yapılandırmaları için bir kaynak olarak bir Windows PowerShell istenen durum yapılandırması (DSC) yapılandırması kullanabilirsiniz. Bu birleşik kaynak diyoruz. Parametreler isteyen bir DSC yapılandırması buna birleşik bir kaynaktır. Yapılandırma parametrelerinin kaynak özellikleri olarak davranır. Yapılandırmanın bir dosya olarak kaydedilmiş bir **. schema.psm1** uzantısı ve MOF şema ve kaynağın yerini komut dosyası, tipik bir DSC kaynağı alır (DSC kaynakları hakkında daha fazla bilgi için bkz [Windows PowerShell istenen durum yapılandırması kaynakları](resources.md).

## <a name="creating-the-composite-resource"></a>Bileşik kaynak oluşturma

Bizim örneğimizde, sanal makineleri yapılandırmak için mevcut kaynak sayısı çağıran bir yapılandırma oluşturun. Yapılandırma bloklarında ayarlanacak değerleri belirtme yerine yapılandırmasını sonra yapılandırma bloklarında kullanılan parametreleri sayısını alır.

```powershell
Configuration xVirtualMachine
{
    param
    (
        # Name of VMs
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String[]] $VMName,

        # Name of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchName,

        # Type of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchType,

        # Source Path for VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDParentPath,

        # Destination path for diff VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDPath,

        # Startup Memory for VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMStartupMemory,

        # State of the VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMState
    )

    # Import the module that defines custom resources
    Import-DscResource -Module xComputerManagement,xHyper-V

    # Install the Hyper-V role
    WindowsFeature HyperV
    {
        Ensure = "Present"
        Name = "Hyper-V"
    }

    # Create the virtual switch
    xVMSwitch $SwitchName
    {
        Ensure = "Present"
        Name = $SwitchName
        Type = $SwitchType
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check for Parent VHD file
    File ParentVHDFile
    {
        Ensure = "Present"
        DestinationPath = $VHDParentPath
        Type = "File"
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check the destination VHD folder
    File VHDFolder
    {
        Ensure = "Present"
        DestinationPath = $VHDPath
        Type = "Directory"
        DependsOn = "[File]ParentVHDFile"
    }

    # Create VM specific diff VHD
    foreach ($Name in $VMName)
    {
        xVHD "VHD$Name"
        {
            Ensure = "Present"
            Name = $Name
            Path = $VHDPath
            ParentPath = $VHDParentPath
            DependsOn = @("[WindowsFeature]HyperV",
                          "[File]VHDFolder")
        }
    }

    # Create VM using the above VHD
    foreach($Name in $VMName)
    {
        xVMHyperV "VMachine$Name"
        {
            Ensure = "Present"
            Name = $Name
            VhDPath = (Join-Path -Path $VHDPath -ChildPath $Name)
            SwitchName = $SwitchName
            StartupMemory = $VMStartupMemory
            State = $VMState
            MACAddress = $MACAddress
            WaitForIP = $true
            DependsOn = @("[WindowsFeature]HyperV",
                          "[xVHD]VHD$Name")
        }
    }
}
```

### <a name="saving-the-configuration-as-a-composite-resource"></a>Bileşik bir kaynak olarak yapılandırması kaydediliyor

Parametreli yapılandırmayı DSC kaynağı olarak kullanmak için bir dizin yapısına benzer diğer MOF tabanlı kaynak kaydedin ve onunla adı bir **. schema.psm1** uzantısı. Bu örnekte, biz dosya adı **xVirtualMachine.schema.psm1**. Ayrıca adlı bir bildirimi oluşturmanıza gerek **xVirtualMachine.psd1** , aşağıdaki satırı içerir. Bu ek olarak olduğuna dikkat edin **MyDscResources.psd1**, tüm kaynaklar için modül bildirimi **MyDscResources** klasör.

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

İşiniz bittiğinde, klasör yapısı şu şekilde olması gerekir.

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

Şimdi Get-DscResource cmdlet'ini kullanarak kaynak bulunabilir olduğundan ve özelliklerini kullanarak veya ya da bu cmdlet'i bulunabilir **Ctrl + Ara çubuğu** Windows PowerShell ISE içinde otomatik olarak tamamlayın.

## <a name="using-the-composite-resource"></a>Bileşik kaynak kullanma

Sonraki bileşik kaynak çağıran bir yapılandırma oluşturun. Bu yapılandırma, bir sanal makine oluşturmak için xVirtualMachine bileşik kaynak çağırır ve ardından çağırır **xComputer** yeniden adlandırmak için kaynak.

```powershell

configuration RenameVM
{

    Import-DscResource -Module xVirtualMachine
    Node localhost
    {
        xVirtualMachine VM
        {
            VMName = "Test"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }

    Node "192.168.10.1"
    {
        xComputer Name
        {
            Name = "SQL01"
            DomainName = "fourthcoffee.com"
        }
    }
}
```

## <a name="supporting-psdscrunascredential"></a>PsDscRunAsCredential destekleme

>**Not:** **PsDscRunAsCredential** PowerShell 5.0 ve sonraki sürümlerinde desteklenir.

**PsDscRunAsCredential** özelliği kullanılabilir [DSC yapılandırmaları](configurations.md) kaynak belirtilen kimlik bilgileri kümesi altında çalışması gerektiğini belirtmek için kaynak bloğu.
Daha fazla bilgi için bkz: [çalıştıran DSC kullanıcı kimlik bilgileriyle](runAsUser.md).

Özel bir kaynak içinde kullanıcı bağlamından erişmek için otomatik değişkeni kullanabilirsiniz `$PsDscContext`.

Örneğin aşağıdaki kodu kaynak ayrıntılı çıktı akışına çalıştırıldığı kullanıcı bağlamı yazarsınız:

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Ayrıca bkz:
### <a name="concepts"></a>Kavramlar
* [Özel bir DSC kaynağı MOF ile yazma](authoringResourceMOF.md)
* [Windows PowerShell istenen durum yapılandırması ile çalışmaya başlama](overview.md)