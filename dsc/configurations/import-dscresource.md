---
ms.date: 12/12/2018
keywords: DSC, PowerShell, yapılandırma, kurulum
title: Import-DSCResource kullanma
ms.openlocfilehash: e1c2c06d756a70c2de516f330e3123235ce740ba
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215412"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="90d68-103">Import-DSCResource kullanma</span><span class="sxs-lookup"><span data-stu-id="90d68-103">Using Import-DSCResource</span></span>

<span data-ttu-id="90d68-104">`Import-DScResource`yalnızca bir yapılandırma komut dosyası bloğunda kullanılabilen dinamik bir anahtar sözcüktür.</span><span class="sxs-lookup"><span data-stu-id="90d68-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="90d68-105">Yapılandırmanızda gerekli olan tüm kaynakları içeri aktarma anahtarsözcüğü.`Import-DSCResource`</span><span class="sxs-lookup"><span data-stu-id="90d68-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="90d68-106">Altındaki `$pshome` kaynaklar otomatik olarak içeri aktarılır, ancak [yapılandırmanızda](Configurations.md)kullanılan tüm kaynakları açıkça içeri aktarmak için en iyi yöntem hala kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="90d68-106">Resources under `$pshome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="90d68-107">Sözdizimi `Import-DSCResource` aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="90d68-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="90d68-108">Modülleri ada göre belirtirken, her bir yeni satıra listelemek bir gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="90d68-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|<span data-ttu-id="90d68-109">Parametre</span><span class="sxs-lookup"><span data-stu-id="90d68-109">Parameter</span></span>  |<span data-ttu-id="90d68-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90d68-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="90d68-111">İçeri aktarmanız gereken DSC kaynak adları.</span><span class="sxs-lookup"><span data-stu-id="90d68-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="90d68-112">Modül adı belirtilmişse, komut bu modül içinde bu DSC kaynaklarını arar; Aksi takdirde, komut DSC kaynaklarını tüm DSC kaynak yollarında arar.</span><span class="sxs-lookup"><span data-stu-id="90d68-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="90d68-113">Joker karakterler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="90d68-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="90d68-114">Modül adı veya modül belirtimi.</span><span class="sxs-lookup"><span data-stu-id="90d68-114">The module name, or module specification.</span></span>  <span data-ttu-id="90d68-115">Bir modülden içeri aktarılacak kaynakları belirtirseniz, komut yalnızca bu kaynakları içeri aktarmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="90d68-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="90d68-116">Yalnızca modülü belirtirseniz, komut modüldeki tüm DSC kaynaklarını içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="90d68-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="90d68-117">Örnek: Bir yapılandırma içinde Import-DSCResource kullanın</span><span class="sxs-lookup"><span data-stu-id="90d68-117">Example: Use Import-DSCResource within a configuration</span></span>

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry
    
    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> <span data-ttu-id="90d68-118">Aynı komutta kaynak adları ve modül adları için birden çok değer belirtilmesi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="90d68-118">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="90d68-119">Bu, birden çok modülde aynı kaynak olması durumunda hangi modülün yükleneceğini belirten belirleyici olmayan davranışlara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="90d68-119">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="90d68-120">Aşağıdaki komut, derleme sırasında hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="90d68-120">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="90d68-121">Yalnızca ad parametresini kullanırken göz önünde bulundurmanız gerekenler:</span><span class="sxs-lookup"><span data-stu-id="90d68-121">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="90d68-122">Makinede yüklü olan modül sayısına bağlı olarak Kaynak yoğunluklu bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="90d68-122">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="90d68-123">Verilen adla bulunan ilk kaynağı yükler.</span><span class="sxs-lookup"><span data-stu-id="90d68-123">It will load the first resource found with the given name.</span></span> <span data-ttu-id="90d68-124">Aynı ada sahip birden fazla kaynak yüklü olduğunda, yanlış kaynağı yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="90d68-124">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="90d68-125">Önerilen kullanım, aşağıda açıklandığı gibi `–ModuleName` `-Name` parametresiyle belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="90d68-125">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="90d68-126">Bu kullanım aşağıdaki avantajlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="90d68-126">This usage has the following benefits:</span></span>

- <span data-ttu-id="90d68-127">Belirtilen kaynak için arama kapsamını sınırlayarak performans etkisini azaltır.</span><span class="sxs-lookup"><span data-stu-id="90d68-127">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="90d68-128">Doğru kaynak yüklendiğinden emin olarak kaynağı tanımlayan modülü açıkça tanımlar.</span><span class="sxs-lookup"><span data-stu-id="90d68-128">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="90d68-129">PowerShell 5,0 ' de DSC kaynakları birden çok sürüme sahip olabilir ve sürümler bir bilgisayara yan yana yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="90d68-129">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="90d68-130">Bu, aynı modül klasöründe yer alan bir kaynak modülünün birden çok sürümü ile uygulanır.</span><span class="sxs-lookup"><span data-stu-id="90d68-130">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="90d68-131">Daha fazla bilgi için bkz. [birden çok sürümü olan kaynakları kullanma](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="90d68-131">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="90d68-132">Import-DSCResource ile IntelliSense</span><span class="sxs-lookup"><span data-stu-id="90d68-132">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="90d68-133">ISE 'de DSC yapılandırmasını yazarken, PowerShell kaynak ve kaynak özellikleri için Intellisence 'yi sağlar.</span><span class="sxs-lookup"><span data-stu-id="90d68-133">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="90d68-134">`$pshome` Modül yolu altındaki kaynak tanımları otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="90d68-134">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="90d68-135">`Import-DSCResource` Anahtar sözcüğünü kullanarak kaynakları içeri aktardığınızda, belirtilen kaynak tanımları eklenir ve IntelliSense, içeri aktarılan kaynağın şemasını içerecek şekilde genişletilir.</span><span class="sxs-lookup"><span data-stu-id="90d68-135">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![Kaynak IntelliSense](../media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="90d68-137">PowerShell 5,0 ' den başlayarak, DSC kaynakları ve bunların özelliklerine ilişkin sekme tamamlama, ıSE 'ye eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="90d68-137">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="90d68-138">Daha fazla bilgi için bkz. [kaynaklar](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="90d68-138">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="90d68-139">Yapılandırma derlenirken, PowerShell, yapılandırmadaki tüm kaynak bloklarını doğrulamak için içeri aktarılan kaynak tanımlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="90d68-139">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="90d68-140">Her kaynak bloğu, aşağıdaki kurallar için kaynağın şema tanımı kullanılarak onaylanır.</span><span class="sxs-lookup"><span data-stu-id="90d68-140">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="90d68-141">Yalnızca şemada tanımlanan özellikler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="90d68-141">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="90d68-142">Her bir özelliğin veri türleri doğrudur.</span><span class="sxs-lookup"><span data-stu-id="90d68-142">The data types for each property are correct.</span></span>
- <span data-ttu-id="90d68-143">Anahtarlar özellikleri belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="90d68-143">Keys properties are specified.</span></span>
- <span data-ttu-id="90d68-144">Salt okunurdur özelliği kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="90d68-144">No read-only property is used.</span></span>
- <span data-ttu-id="90d68-145">Değer eşlemeleri türlerinde doğrulama.</span><span class="sxs-lookup"><span data-stu-id="90d68-145">Validation on value maps types.</span></span>

<span data-ttu-id="90d68-146">Aşağıdaki yapılandırmayı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="90d68-146">Consider the following configuration:</span></span>

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

<span data-ttu-id="90d68-147">Bu yapılandırmanın derlenmesi bir hatayla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="90d68-147">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="90d68-148">IntelliSense ve şema doğrulama, ayrıştırma ve derleme sırasında daha fazla hata yakalamalı ve çalışma zamanında karmaşıklıkları önkullanmanıza imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="90d68-148">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="90d68-149">Her DSC kaynağı bir ada ve kaynağın şeması tarafından tanımlanan bir **FriendlyName** 'a sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="90d68-149">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="90d68-150">Aşağıda "MSFT_ServiceResource. Shema. mof" öğesinin ilk iki satırı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="90d68-150">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="90d68-151">Bu kaynağı bir yapılandırmada kullanırken, **MSFT_ServiceResource** veya **Service**belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90d68-151">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="90d68-152">PowerShell v4 ve v5 farklılıkları</span><span class="sxs-lookup"><span data-stu-id="90d68-152">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="90d68-153">PowerShell 4,0 ile yapılandırma yazma sırasında gördüğünüz birden çok fark vardır. PowerShell 5,0 ve üzeri.</span><span class="sxs-lookup"><span data-stu-id="90d68-153">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="90d68-154">Bu bölümde, bu makaleyle ilgili gördüğünüz farklar vurgulanacaktır.</span><span class="sxs-lookup"><span data-stu-id="90d68-154">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="90d68-155">Birden çok kaynak sürümü</span><span class="sxs-lookup"><span data-stu-id="90d68-155">Multiple Resource Versions</span></span>

<span data-ttu-id="90d68-156">PowerShell 4,0 ' de yan yana kaynakların birden çok sürümünün yüklenmesi ve kullanılması desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="90d68-156">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="90d68-157">Yapılandırmanızda kaynakları içeri aktarma sorunları fark ederseniz, kaynağın yalnızca bir sürümünün yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="90d68-157">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="90d68-158">Aşağıdaki görüntüde, **Xpsdesiredstateconfiguration** modülünün iki sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="90d68-158">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Birden çok kaynak sürümü düzeltildi](../media/multiple-resource-versions-broken.png)

<span data-ttu-id="90d68-160">İstediğiniz modül sürümünüzün içeriğini modül dizininin en üst düzeyine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="90d68-160">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Birden çok kaynak sürümü düzeltildi](../media/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a><span data-ttu-id="90d68-162">Kaynak konumu</span><span class="sxs-lookup"><span data-stu-id="90d68-162">Resource location</span></span>

<span data-ttu-id="90d68-163">Yapılandırma yazma ve derleme yaparken, kaynaklarınız [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path)'niz tarafından belirtilen herhangi bir dizinde depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="90d68-163">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="90d68-164">PowerShell 4,0 ' de, LCM tüm DSC kaynak modüllerinin "program Files\WindowsPowerShell\Modules" veya `$pshome\Modules`altında depolanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="90d68-164">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="90d68-165">PowerShell 5,0 ' den başlayarak bu gereksinim kaldırılmıştır ve kaynak modülleri tarafından `PSModulePath`belirtilen herhangi bir dizinde depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="90d68-165">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

## <a name="see-also"></a><span data-ttu-id="90d68-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90d68-166">See also</span></span>

- [<span data-ttu-id="90d68-167">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="90d68-167">Resources</span></span>](../resources/resources.md)
