---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC yapılandırması bir kaynak olarak kullanarak bileşik kaynakları--
ms.openlocfilehash: 246cab3b437546490d650e45be263a43fd0c84c3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="452aa-103">Bileşik kaynaklar: DSC yapılandırması bir kaynak olarak kullanma</span><span class="sxs-lookup"><span data-stu-id="452aa-103">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="452aa-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="452aa-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="452aa-105">Gerçek dünya durumlarda yapılandırmaları uzun ve karmaşık, birçok farklı kaynaklar çağırma ve özelliklerinin büyük bir sayıya ayarlanması olabilir.</span><span class="sxs-lookup"><span data-stu-id="452aa-105">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="452aa-106">Bu karmaşıklık gidermeye yardımcı olacak diğer yapılandırmaları için bir kaynak olarak bir Windows PowerShell istenen durum yapılandırması (DSC) yapılandırması kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="452aa-106">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="452aa-107">Bu birleşik kaynak diyoruz.</span><span class="sxs-lookup"><span data-stu-id="452aa-107">We call this a composite resource.</span></span> <span data-ttu-id="452aa-108">Parametreler isteyen bir DSC yapılandırması buna birleşik bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="452aa-108">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="452aa-109">Yapılandırma parametrelerinin kaynak özellikleri olarak davranır.</span><span class="sxs-lookup"><span data-stu-id="452aa-109">The parameters of the configuration act as the properties of the resource.</span></span> <span data-ttu-id="452aa-110">Yapılandırmanın bir dosya olarak kaydedilmiş bir **. schema.psm1** uzantısı ve MOF şema ve kaynağın yerini komut dosyası, tipik bir DSC kaynağı alır (DSC kaynakları hakkında daha fazla bilgi için bkz [Windows PowerShell istenen durum yapılandırması kaynakları](resources.md).</span><span class="sxs-lookup"><span data-stu-id="452aa-110">The configuration is saved as a file with a **.schema.psm1** extension, and takes the place of both the MOF schema and the resource script in a typical DSC resource (for more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="452aa-111">Bileşik kaynak oluşturma</span><span class="sxs-lookup"><span data-stu-id="452aa-111">Creating the composite resource</span></span>

<span data-ttu-id="452aa-112">Bizim örneğimizde, sanal makineleri yapılandırmak için mevcut kaynak sayısı çağıran bir yapılandırma oluşturun.</span><span class="sxs-lookup"><span data-stu-id="452aa-112">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="452aa-113">Yapılandırma bloklarında ayarlanacak değerleri belirtme yerine yapılandırmasını sonra yapılandırma bloklarında kullanılan parametreleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="452aa-113">Instead of specifying the values to be set in configuration blocks, the configuration takes a number of parameters that are then used in the configuration blocks.</span></span>

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

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="452aa-114">Bileşik bir kaynak olarak yapılandırması kaydediliyor</span><span class="sxs-lookup"><span data-stu-id="452aa-114">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="452aa-115">Parametreli yapılandırmayı DSC kaynağı olarak kullanmak için bir dizin yapısına benzer diğer MOF tabanlı kaynak kaydedin ve onunla adı bir **. schema.psm1** uzantısı.</span><span class="sxs-lookup"><span data-stu-id="452aa-115">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a **.schema.psm1** extension.</span></span> <span data-ttu-id="452aa-116">Bu örnekte, biz dosya adı **xVirtualMachine.schema.psm1**.</span><span class="sxs-lookup"><span data-stu-id="452aa-116">For this example, we’ll name the file **xVirtualMachine.schema.psm1**.</span></span> <span data-ttu-id="452aa-117">Ayrıca adlı bir bildirimi oluşturmanıza gerek **xVirtualMachine.psd1** , aşağıdaki satırı içerir.</span><span class="sxs-lookup"><span data-stu-id="452aa-117">You also need to create a manifest named **xVirtualMachine.psd1** that contains the following line.</span></span> <span data-ttu-id="452aa-118">Bu ek olarak olduğuna dikkat edin **MyDscResources.psd1**, tüm kaynaklar için modül bildirimi **MyDscResources** klasör.</span><span class="sxs-lookup"><span data-stu-id="452aa-118">Note that this is in addition to **MyDscResources.psd1**, the module manifest for all resources under the **MyDscResources** folder.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

<span data-ttu-id="452aa-119">İşiniz bittiğinde, klasör yapısı şu şekilde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="452aa-119">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="452aa-120">Şimdi Get-DscResource cmdlet'ini kullanarak kaynak bulunabilir olduğundan ve özelliklerini kullanarak veya ya da bu cmdlet'i bulunabilir **Ctrl + Ara çubuğu** Windows PowerShell ISE içinde otomatik olarak tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="452aa-120">The resource is now discoverable by using the Get-DscResource cmdlet, and its properties are discoverable by either that cmdlet or by using **Ctrl+Space** auto-complete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="452aa-121">Bileşik kaynak kullanma</span><span class="sxs-lookup"><span data-stu-id="452aa-121">Using the composite resource</span></span>

<span data-ttu-id="452aa-122">Sonraki bileşik kaynak çağıran bir yapılandırma oluşturun.</span><span class="sxs-lookup"><span data-stu-id="452aa-122">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="452aa-123">Bu yapılandırma, bir sanal makine oluşturmak için xVirtualMachine bileşik kaynak çağırır ve ardından çağırır **xComputer** yeniden adlandırmak için kaynak.</span><span class="sxs-lookup"><span data-stu-id="452aa-123">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="452aa-124">PsDscRunAsCredential destekleme</span><span class="sxs-lookup"><span data-stu-id="452aa-124">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="452aa-125">**Not:** **PsDscRunAsCredential** PowerShell 5.0 ve sonraki sürümlerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="452aa-125">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="452aa-126">**PsDscRunAsCredential** özelliği kullanılabilir [DSC yapılandırmaları](configurations.md) kaynak belirtilen kimlik bilgileri kümesi altında çalışması gerektiğini belirtmek için kaynak bloğu.</span><span class="sxs-lookup"><span data-stu-id="452aa-126">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="452aa-127">Daha fazla bilgi için bkz: [çalıştıran DSC kullanıcı kimlik bilgileriyle](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="452aa-127">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

<span data-ttu-id="452aa-128">Özel bir kaynak içinde kullanıcı bağlamından erişmek için otomatik değişkeni kullanabilirsiniz `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="452aa-128">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="452aa-129">Örneğin aşağıdaki kodu kaynak ayrıntılı çıktı akışına çalıştırıldığı kullanıcı bağlamı yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="452aa-129">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="452aa-130">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="452aa-130">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="452aa-131">Kavramlar</span><span class="sxs-lookup"><span data-stu-id="452aa-131">Concepts</span></span>
* [<span data-ttu-id="452aa-132">Özel bir DSC kaynağı MOF ile yazma</span><span class="sxs-lookup"><span data-stu-id="452aa-132">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="452aa-133">Windows PowerShell istenen durum yapılandırması ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="452aa-133">Get Started with Windows PowerShell Desired State Configuration</span></span>](overview.md)