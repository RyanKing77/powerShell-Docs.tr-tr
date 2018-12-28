---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC kaynakları
ms.openlocfilehash: 542a210ab47c650eac625108a78e76bc2cd55572
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405726"
---
# <a name="dsc-resources"></a><span data-ttu-id="bb29e-103">DSC kaynakları</span><span class="sxs-lookup"><span data-stu-id="bb29e-103">DSC Resources</span></span>

><span data-ttu-id="bb29e-104">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bb29e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="bb29e-105">Desired State Configuration ' nı (DSC) kaynakları bir DSC yapılandırması için yapı taşlarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb29e-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="bb29e-106">Bir kaynak (şema) yapılandırılmış olabilir ve yerel Configuration Manager (LCM) ", bunu yapmak için" çağıran PowerShell Betiği işlevlerini içeren özellikleri sunar.</span><span class="sxs-lookup"><span data-stu-id="bb29e-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="bb29e-107">Bir kaynak olarak bir dosya olarak genel veya bir IIS sunucusu ayarı olarak belirli bir şey modelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb29e-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="bb29e-108">Grupları kaynaklar gibi tüm gerekli dosyaları, taşınabilir ve kaynakları nasıl kullanılması amaçlanır tanımlamak için meta veriler içeren bir yapıya düzenleyen bir DSC modülünü, birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bb29e-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="bb29e-109">Her kaynağın bir \* kaynakta kullanmak için gerekli sözdizimi belirleyen şema bir [yapılandırma](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="bb29e-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="bb29e-110">Bir kaynağın şema, aşağıdaki yollarla tanımlanabilir:</span><span class="sxs-lookup"><span data-stu-id="bb29e-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="bb29e-111">**'Schema.Mof'** dosyası: Çoğu kaynakları tanımlayan kendi *şema* 'schema.mof' nda kullanarak dosya [Yönetilen Nesne biçimi](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="bb29e-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="bb29e-112">**'\<Kaynak adı\>. schema.psm1'** dosyası: [Bileşik kaynaklar](../configurations/compositeConfigs.md) tanımlayın, *şema* içinde bir '<ResourceName>. schema.psm1' kullanarak dosya bir [parametre bloğu](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="bb29e-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="bb29e-113">**'\<Kaynak adı\>.psm1'** dosyası: Temel DSC kaynakları tanımlayan bir sınıf kendi *şema* sınıf tanımında.</span><span class="sxs-lookup"><span data-stu-id="bb29e-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="bb29e-114">Söz dizimi öğeleri sınıfı özellik olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="bb29e-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="bb29e-115">Daha fazla bilgi için [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span><span class="sxs-lookup"><span data-stu-id="bb29e-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="bb29e-116">DSC kaynak sözdizimi almak için kullanın [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet'iyle `-Syntax` parametresi.</span><span class="sxs-lookup"><span data-stu-id="bb29e-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="bb29e-117">Bu kullanım kullanmaya benzer [Get-Command](/powershell/module/microsoft.powershell.core/get-command) ile `-Syntax` cmdlet sözdizimi almak için parametre.</span><span class="sxs-lookup"><span data-stu-id="bb29e-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="bb29e-118">Bir kaynak bloğu için belirttiğiniz kaynak için kullanılan şablon, çıktıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="bb29e-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="bb29e-119">Bu kaynağın sözdizimi gelecekte değişebilir olsa, çıktıyı aşağıdaki çıktıya benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bb29e-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="bb29e-120">Cmdlet sözdizimi gibi *anahtarları* köşeli ayraçlar içinde görülen, isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="bb29e-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="bb29e-121">Her anahtar bekliyor veri türüne türlerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="bb29e-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="bb29e-122">**Olun** "Var" için varsayılanları nedeniyle anahtar isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="bb29e-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

<span data-ttu-id="bb29e-123">İçinde bir yapılandırma bir **hizmet** kaynak bloğu için şöyle görünebilir **olun** Biriktirici hizmetini çalıştıran.</span><span class="sxs-lookup"><span data-stu-id="bb29e-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="bb29e-124">Bir kaynak bir yapılandırmada kullanmadan önce kullanarak aktarmalısınız [Import-DSCResource](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="bb29e-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

<span data-ttu-id="bb29e-125">Yapılandırmalar, aynı kaynak türünün birden fazla örneğini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="bb29e-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="bb29e-126">Her örneğini benzersiz olarak adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bb29e-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="bb29e-127">Aşağıdaki örnekte, ikinci bir **hizmet** kaynak blok "DHCP" hizmetini yapılandırma eklenir.</span><span class="sxs-lookup"><span data-stu-id="bb29e-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="bb29e-128">PowerShell 5. 0'den itibaren IntelliSense için DSC eklendi.</span><span class="sxs-lookup"><span data-stu-id="bb29e-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="bb29e-129">Bu yeni özellik kullanmanıza olanak sağlar. \<sekmesini\> ve \<Ctrl + boşluk\> anahtar adları otomatik olarak tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="bb29e-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![Kaynak sekme tamamlama](/media/resource-tabcompletion.png)
