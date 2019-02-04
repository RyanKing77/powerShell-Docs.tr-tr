---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC kaynakları
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686071"
---
# <a name="dsc-resources"></a><span data-ttu-id="5fdad-103">DSC kaynakları</span><span class="sxs-lookup"><span data-stu-id="5fdad-103">DSC Resources</span></span>

><span data-ttu-id="5fdad-104">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5fdad-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="5fdad-105">Desired State Configuration ' nı (DSC) kaynakları bir DSC yapılandırması için yapı taşlarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fdad-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="5fdad-106">Bir kaynak (şema) yapılandırılmış olabilir ve yerel Configuration Manager (LCM) ", bunu yapmak için" çağıran PowerShell Betiği işlevlerini içeren özellikleri sunar.</span><span class="sxs-lookup"><span data-stu-id="5fdad-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="5fdad-107">Bir kaynak olarak bir dosya olarak genel veya bir IIS sunucusu ayarı olarak belirli bir şey modelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fdad-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="5fdad-108">Grupları kaynaklar gibi tüm gerekli dosyaları, taşınabilir ve kaynakları nasıl kullanılması amaçlanır tanımlamak için meta veriler içeren bir yapıya düzenleyen bir DSC modülünü, birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5fdad-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="5fdad-109">Her kaynağın bir \* kaynakta kullanmak için gerekli sözdizimi belirleyen şema bir [yapılandırma](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="5fdad-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="5fdad-110">Bir kaynağın şema, aşağıdaki yollarla tanımlanabilir:</span><span class="sxs-lookup"><span data-stu-id="5fdad-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="5fdad-111">**'Schema.Mof'** dosyası: Çoğu kaynakları tanımlayan kendi *şema* 'schema.mof' nda kullanarak dosya [Yönetilen Nesne biçimi](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="5fdad-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="5fdad-112">**'\<Kaynak adı\>. schema.psm1'** dosyası: [Bileşik kaynaklar](../configurations/compositeConfigs.md) tanımlayın, *şema* içinde bir '<ResourceName>. schema.psm1' kullanarak dosya bir [parametre bloğu](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="5fdad-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="5fdad-113">**'\<Kaynak adı\>.psm1'** dosyası: Temel DSC kaynakları tanımlayan bir sınıf kendi *şema* sınıf tanımında.</span><span class="sxs-lookup"><span data-stu-id="5fdad-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="5fdad-114">Söz dizimi öğeleri sınıfı özellik olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="5fdad-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="5fdad-115">Daha fazla bilgi için [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span><span class="sxs-lookup"><span data-stu-id="5fdad-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="5fdad-116">DSC kaynak sözdizimi almak için kullanın [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet'iyle `-Syntax` parametresi.</span><span class="sxs-lookup"><span data-stu-id="5fdad-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="5fdad-117">Bu kullanım kullanmaya benzer [Get-Command](/powershell/module/microsoft.powershell.core/get-command) ile `-Syntax` cmdlet sözdizimi almak için parametre.</span><span class="sxs-lookup"><span data-stu-id="5fdad-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="5fdad-118">Bir kaynak bloğu için belirttiğiniz kaynak için kullanılan şablon, çıktıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fdad-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="5fdad-119">Bu kaynağın sözdizimi gelecekte değişebilir olsa, çıktıyı aşağıdaki çıktıya benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5fdad-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="5fdad-120">Cmdlet sözdizimi gibi *anahtarları* köşeli ayraçlar içinde görülen, isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5fdad-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="5fdad-121">Her anahtar bekliyor veri türüne türlerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="5fdad-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="5fdad-122">**Olun** "Var" için varsayılanları nedeniyle anahtar isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5fdad-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

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

<span data-ttu-id="5fdad-123">İçinde bir yapılandırma bir **hizmet** kaynak bloğu için şöyle görünebilir **olun** Biriktirici hizmetini çalıştıran.</span><span class="sxs-lookup"><span data-stu-id="5fdad-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="5fdad-124">Bir kaynak bir yapılandırmada kullanmadan önce kullanarak aktarmalısınız [Import-DSCResource](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="5fdad-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

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

<span data-ttu-id="5fdad-125">Yapılandırmalar, aynı kaynak türünün birden fazla örneğini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="5fdad-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="5fdad-126">Her örneğini benzersiz olarak adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5fdad-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="5fdad-127">Aşağıdaki örnekte, ikinci bir **hizmet** kaynak blok "DHCP" hizmetini yapılandırma eklenir.</span><span class="sxs-lookup"><span data-stu-id="5fdad-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

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
> <span data-ttu-id="5fdad-128">PowerShell 5. 0'den itibaren IntelliSense için DSC eklendi.</span><span class="sxs-lookup"><span data-stu-id="5fdad-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="5fdad-129">Bu yeni özellik kullanmanıza olanak sağlar. \<sekmesini\> ve \<Ctrl + boşluk\> anahtar adları otomatik olarak tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="5fdad-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![Kaynak sekme tamamlama](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a><span data-ttu-id="5fdad-131">Yerleşik kaynaklar</span><span class="sxs-lookup"><span data-stu-id="5fdad-131">Built-in resources</span></span>

<span data-ttu-id="5fdad-132">Topluluk kaynakları yanı sıra Windows, Linux için kaynaklar ve çapraz düğüm bağımlılığı kaynakları için yerleşik kaynaklar vardır.</span><span class="sxs-lookup"><span data-stu-id="5fdad-132">In addition to community resources, there are built-in resources for Windows, resources for Linux, and resources for cross-node dependency.</span></span> <span data-ttu-id="5fdad-133">Sözdizimi, bu kaynakları ve bunların nasıl kullanılacağını belirlemek için yukarıdaki adımları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fdad-133">You can use the steps above to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="5fdad-134">Bu kaynaklar hizmet sayfaları altında arşivlenmiştir **başvuru**.</span><span class="sxs-lookup"><span data-stu-id="5fdad-134">The pages that serve these resources have been archived under **Reference**.</span></span>

<span data-ttu-id="5fdad-135">Windows yerleşik kaynakları</span><span class="sxs-lookup"><span data-stu-id="5fdad-135">Windows built-in resources</span></span>

* [<span data-ttu-id="5fdad-136">Archive Kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-136">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
* [<span data-ttu-id="5fdad-137">Environment Kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-137">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
* [<span data-ttu-id="5fdad-138">File Kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-138">File Resource</span></span>](../reference/resources/windows/fileResource.md)
* [<span data-ttu-id="5fdad-139">Group Kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-139">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
* [<span data-ttu-id="5fdad-140">GroupSet Kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-140">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
* [<span data-ttu-id="5fdad-141">Log Kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-141">Log Resource</span></span>](../reference/resources/windows/logResource.md)
* [<span data-ttu-id="5fdad-142">Package Kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-142">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
* [<span data-ttu-id="5fdad-143">ProcessSet Kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-143">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
* [<span data-ttu-id="5fdad-144">Registry Kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-144">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
* [<span data-ttu-id="5fdad-145">Script Kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-145">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
* [<span data-ttu-id="5fdad-146">Service Kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-146">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
* [<span data-ttu-id="5fdad-147">ServiceSet Kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-147">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
* [<span data-ttu-id="5fdad-148">User Kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-148">User Resource</span></span>](../reference/resources/windows/userResource.md)
* [<span data-ttu-id="5fdad-149">WindowsFeature Kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-149">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
* [<span data-ttu-id="5fdad-150">WindowsFeatureSet Kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-150">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
* [<span data-ttu-id="5fdad-151">WindowsOptionalFeature Kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-151">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [<span data-ttu-id="5fdad-152">WindowsOptionalFeatureSet Kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-152">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [<span data-ttu-id="5fdad-153">WindowsPackageCabResource kaynak</span><span class="sxs-lookup"><span data-stu-id="5fdad-153">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
* [<span data-ttu-id="5fdad-154">WindowsProcess Kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-154">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

<span data-ttu-id="5fdad-155">[Çapraz düğüm bağımlılık](../configurations/crossNodeDependencies.md) kaynakları</span><span class="sxs-lookup"><span data-stu-id="5fdad-155">[Cross-Node dependency](../configurations/crossNodeDependencies.md) resources</span></span>

* [<span data-ttu-id="5fdad-156">WaitForAll kaynak</span><span class="sxs-lookup"><span data-stu-id="5fdad-156">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
* [<span data-ttu-id="5fdad-157">WaitForSome kaynak</span><span class="sxs-lookup"><span data-stu-id="5fdad-157">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
* [<span data-ttu-id="5fdad-158">WaitForAny kaynak</span><span class="sxs-lookup"><span data-stu-id="5fdad-158">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

<span data-ttu-id="5fdad-159">Paket Yönetimi kaynakları</span><span class="sxs-lookup"><span data-stu-id="5fdad-159">Package Management resources</span></span>

* [<span data-ttu-id="5fdad-160">PackageManagement kaynak</span><span class="sxs-lookup"><span data-stu-id="5fdad-160">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [<span data-ttu-id="5fdad-161">PackageManagementSource kaynak</span><span class="sxs-lookup"><span data-stu-id="5fdad-161">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

<span data-ttu-id="5fdad-162">Linux kaynakları</span><span class="sxs-lookup"><span data-stu-id="5fdad-162">Linux resources</span></span>

* [<span data-ttu-id="5fdad-163">Linux Archive kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-163">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
* [<span data-ttu-id="5fdad-164">Linux Environment kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-164">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
* [<span data-ttu-id="5fdad-165">Linux FileLine kaynak</span><span class="sxs-lookup"><span data-stu-id="5fdad-165">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
* [<span data-ttu-id="5fdad-166">Linux dosya kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-166">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
* [<span data-ttu-id="5fdad-167">Linux Group kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-167">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
* [<span data-ttu-id="5fdad-168">Linux paket kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-168">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
* [<span data-ttu-id="5fdad-169">Linux Script kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-169">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
* [<span data-ttu-id="5fdad-170">Linux Service kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-170">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
* [<span data-ttu-id="5fdad-171">Linux SshAuthorizedKeys kaynak</span><span class="sxs-lookup"><span data-stu-id="5fdad-171">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [<span data-ttu-id="5fdad-172">Linux kullanıcı kaynağı</span><span class="sxs-lookup"><span data-stu-id="5fdad-172">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
