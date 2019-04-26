---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Bileşik kaynaklar bir kaynak olarak bir DSC Yapılandırması kullanılarak--
ms.openlocfilehash: 2823d05e0c8feb2933ca691f9ab5149ace2f7ee3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076693"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="a63c0-103">Bileşik kaynaklar: DSC yapılandırma kaynağı olarak kullanma</span><span class="sxs-lookup"><span data-stu-id="a63c0-103">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="a63c0-104">Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a63c0-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="a63c0-105">Uzun ve karmaşık, birçok farklı kaynaktan çağırma ve özelliklerin geniş bir sayı ayarlandığında, gerçek durumlarda yapılandırmaları olabilir.</span><span class="sxs-lookup"><span data-stu-id="a63c0-105">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="a63c0-106">Bu karmaşıklığı çözümüne yardımcı olmak için diğer yapılandırmalar için bir kaynak olarak bir Windows PowerShell Desired State Configuration (DSC) yapılandırması kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a63c0-106">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="a63c0-107">Bu bir bileşik kaynak diyoruz.</span><span class="sxs-lookup"><span data-stu-id="a63c0-107">We call this a composite resource.</span></span> <span data-ttu-id="a63c0-108">Parametre almayan bir DSC yapılandırması bir bileşik kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="a63c0-108">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="a63c0-109">Yapılandırma parametreleri kaynak özellikleri olarak davranır.</span><span class="sxs-lookup"><span data-stu-id="a63c0-109">The parameters of the configuration act as the properties of the resource.</span></span> <span data-ttu-id="a63c0-110">Yapılandırma ile bir dosya olarak kaydedilmiş bir **. schema.psm1** uzantısı ve MOF şemayı hem kaynak yerini tipik DSC kaynak betiği alır (DSC kaynakları hakkında daha fazla bilgi için bkz. [Windows PowerShell Desired State Configuration kaynakları](resources.md).</span><span class="sxs-lookup"><span data-stu-id="a63c0-110">The configuration is saved as a file with a **.schema.psm1** extension, and takes the place of both the MOF schema and the resource script in a typical DSC resource (for more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="a63c0-111">Bileşik kaynak oluşturma</span><span class="sxs-lookup"><span data-stu-id="a63c0-111">Creating the composite resource</span></span>

<span data-ttu-id="a63c0-112">Bizim örneğimizde, çok çeşitli sanal makineleri yapılandırmak için var olan kaynaklar çağıran bir yapılandırma oluştururuz.</span><span class="sxs-lookup"><span data-stu-id="a63c0-112">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="a63c0-113">Yapılandırma bloklarında ayarlanacak değerleri belirtmek yerine, yapılandırma ardından yapılandırma bloklarında kullanılan parametreleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="a63c0-113">Instead of specifying the values to be set in configuration blocks, the configuration takes a number of parameters that are then used in the configuration blocks.</span></span>

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

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="a63c0-114">Bileşik bir kaynak olarak yapılandırması kaydediliyor</span><span class="sxs-lookup"><span data-stu-id="a63c0-114">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="a63c0-115">Parametreli yapılandırması DSC kaynağı olarak kullanmak için diğer MOF temelli kaynak gibi bir dizin yapısına kaydedin ve ile adlandırın bir **. schema.psm1** uzantısı.</span><span class="sxs-lookup"><span data-stu-id="a63c0-115">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a **.schema.psm1** extension.</span></span> <span data-ttu-id="a63c0-116">Bu örnekte, biz dosya adı **xVirtualMachine.schema.psm1**.</span><span class="sxs-lookup"><span data-stu-id="a63c0-116">For this example, we’ll name the file **xVirtualMachine.schema.psm1**.</span></span> <span data-ttu-id="a63c0-117">Ayrıca adlı bir bildirim oluşturmak gereken **xVirtualMachine.psd1** , aşağıdaki satır içerir.</span><span class="sxs-lookup"><span data-stu-id="a63c0-117">You also need to create a manifest named **xVirtualMachine.psd1** that contains the following line.</span></span> <span data-ttu-id="a63c0-118">Bu ek olarak olduğuna dikkat edin **MyDscResources.psd1**, kapsamındaki tüm kaynaklar için modül bildirimi **MyDscResources** klasör.</span><span class="sxs-lookup"><span data-stu-id="a63c0-118">Note that this is in addition to **MyDscResources.psd1**, the module manifest for all resources under the **MyDscResources** folder.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

<span data-ttu-id="a63c0-119">İşiniz bittiğinde, klasör yapısı şu şekilde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a63c0-119">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="a63c0-120">Şimdi Get-DscResource cmdlet'ini kullanarak kaynak bulunabilir ve özelliklerini ya da bu cmdlet'i veya kullanılarak bulunabilir **Ctrl + boşluk** Windows PowerShell ıse'de otomatik tamamlama.</span><span class="sxs-lookup"><span data-stu-id="a63c0-120">The resource is now discoverable by using the Get-DscResource cmdlet, and its properties are discoverable by either that cmdlet or by using **Ctrl+Space** auto-complete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="a63c0-121">Bileşik kaynak kullanarak</span><span class="sxs-lookup"><span data-stu-id="a63c0-121">Using the composite resource</span></span>

<span data-ttu-id="a63c0-122">Ardından bileşik kaynak çağıran bir yapılandırma oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a63c0-122">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="a63c0-123">Bu yapılandırma, bir sanal makine oluşturmak için xVirtualMachine bileşik kaynak çağırır ve ardından çağırır **xComputer** yeniden adlandırmak için kaynak.</span><span class="sxs-lookup"><span data-stu-id="a63c0-123">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="a63c0-124">PsDscRunAsCredential destekleme</span><span class="sxs-lookup"><span data-stu-id="a63c0-124">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="a63c0-125">**Not:** **PsDscRunAsCredential** PowerShell 5.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a63c0-125">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="a63c0-126">**PsDscRunAsCredential** özelliği kullanılabilir [DSC yapılandırmaları](../configurations/configurations.md) kaynak belirtilen kimlik bilgileri kümesi altında çalışması gerektiğini belirtmek için kaynak blok.</span><span class="sxs-lookup"><span data-stu-id="a63c0-126">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="a63c0-127">Daha fazla bilgi için [DSC çalıştıran kullanıcı kimlik bilgileriyle](../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="a63c0-127">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="a63c0-128">Özel bir kaynak içinde kullanıcı bağlamından erişmek için otomatik değişken kullanabilirsiniz `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="a63c0-128">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="a63c0-129">Örneğin aşağıdaki kod, kaynak ayrıntılı çıkış akışına çalıştırıldığı kullanıcı bağlamı yazmalısınız:</span><span class="sxs-lookup"><span data-stu-id="a63c0-129">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="a63c0-130">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a63c0-130">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="a63c0-131">Kavramlar</span><span class="sxs-lookup"><span data-stu-id="a63c0-131">Concepts</span></span>
* [<span data-ttu-id="a63c0-132">MOF ile özel bir DSC kaynağı yazma</span><span class="sxs-lookup"><span data-stu-id="a63c0-132">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="a63c0-133">Windows PowerShell Desired State Configuration ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="a63c0-133">Get Started with Windows PowerShell Desired State Configuration</span></span>](../overview/overview.md)