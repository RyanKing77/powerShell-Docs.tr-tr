---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Bileşik kaynaklar bir kaynak olarak bir DSC Yapılandırması kullanılarak--
ms.openlocfilehash: 2823d05e0c8feb2933ca691f9ab5149ace2f7ee3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405699"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a>Bileşik kaynaklar: DSC yapılandırma kaynağı olarak kullanma

> Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Uzun ve karmaşık, birçok farklı kaynaktan çağırma ve özelliklerin geniş bir sayı ayarlandığında, gerçek durumlarda yapılandırmaları olabilir. Bu karmaşıklığı çözümüne yardımcı olmak için diğer yapılandırmalar için bir kaynak olarak bir Windows PowerShell Desired State Configuration (DSC) yapılandırması kullanabilirsiniz. Bu bir bileşik kaynak diyoruz. Parametre almayan bir DSC yapılandırması bir bileşik kaynaktır. Yapılandırma parametreleri kaynak özellikleri olarak davranır. Yapılandırma ile bir dosya olarak kaydedilmiş bir **. schema.psm1** uzantısı ve MOF şemayı hem kaynak yerini tipik DSC kaynak betiği alır (DSC kaynakları hakkında daha fazla bilgi için bkz. [Windows PowerShell Desired State Configuration kaynakları](resources.md).

## <a name="creating-the-composite-resource"></a>Bileşik kaynak oluşturma

Bizim örneğimizde, çok çeşitli sanal makineleri yapılandırmak için var olan kaynaklar çağıran bir yapılandırma oluştururuz. Yapılandırma bloklarında ayarlanacak değerleri belirtmek yerine, yapılandırma ardından yapılandırma bloklarında kullanılan parametreleri sayısını alır.

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

Parametreli yapılandırması DSC kaynağı olarak kullanmak için diğer MOF temelli kaynak gibi bir dizin yapısına kaydedin ve ile adlandırın bir **. schema.psm1** uzantısı. Bu örnekte, biz dosya adı **xVirtualMachine.schema.psm1**. Ayrıca adlı bir bildirim oluşturmak gereken **xVirtualMachine.psd1** , aşağıdaki satır içerir. Bu ek olarak olduğuna dikkat edin **MyDscResources.psd1**, kapsamındaki tüm kaynaklar için modül bildirimi **MyDscResources** klasör.

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

İşiniz bittiğinde, klasör yapısı şu şekilde olmalıdır.

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

Şimdi Get-DscResource cmdlet'ini kullanarak kaynak bulunabilir ve özelliklerini ya da bu cmdlet'i veya kullanılarak bulunabilir **Ctrl + boşluk** Windows PowerShell ıse'de otomatik tamamlama.

## <a name="using-the-composite-resource"></a>Bileşik kaynak kullanarak

Ardından bileşik kaynak çağıran bir yapılandırma oluşturun. Bu yapılandırma, bir sanal makine oluşturmak için xVirtualMachine bileşik kaynak çağırır ve ardından çağırır **xComputer** yeniden adlandırmak için kaynak.

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

>**Not:** **PsDscRunAsCredential** PowerShell 5.0 ve sonraki sürümlerde desteklenir.

**PsDscRunAsCredential** özelliği kullanılabilir [DSC yapılandırmaları](../configurations/configurations.md) kaynak belirtilen kimlik bilgileri kümesi altında çalışması gerektiğini belirtmek için kaynak blok.
Daha fazla bilgi için [DSC çalıştıran kullanıcı kimlik bilgileriyle](../configurations/runAsUser.md).

Özel bir kaynak içinde kullanıcı bağlamından erişmek için otomatik değişken kullanabilirsiniz `$PsDscContext`.

Örneğin aşağıdaki kod, kaynak ayrıntılı çıkış akışına çalıştırıldığı kullanıcı bağlamı yazmalısınız:

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Ayrıca bkz:
### <a name="concepts"></a>Kavramlar
* [MOF ile özel bir DSC kaynağı yazma](authoringResourceMOF.md)
* [Windows PowerShell Desired State Configuration ile çalışmaya başlama](../overview/overview.md)