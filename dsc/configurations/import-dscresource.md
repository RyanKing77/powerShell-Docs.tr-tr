---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kur
title: Import-DSCResource kullanma
ms.openlocfilehash: f22c741969b1429074e7307a00a5c014cf563089
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265510"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="d2934-103">Import-DSCResource kullanma</span><span class="sxs-lookup"><span data-stu-id="d2934-103">Using Import-DSCResource</span></span>

<span data-ttu-id="d2934-104">`Import-DScResource` yalnızca bir yapılandırma komut dosyası bloğunun içine kullanılabilir dinamik bir anahtar sözcüktür.</span><span class="sxs-lookup"><span data-stu-id="d2934-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="d2934-105">`Import-DSCResource` Yapılandırmanızda gereken herhangi bir kaynağa alınacak anahtar.</span><span class="sxs-lookup"><span data-stu-id="d2934-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="d2934-106">Kaynaklarınıza `$phsome` otomatik olarak alınır ancak hala açık olarak kullanılan tüm kaynakları içeri aktarmak için en iyi yöntem kabul edilir, [yapılandırma](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="d2934-106">Resources under `$phsome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="d2934-107">Sözdizimi `Import-DSCResource` aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2934-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="d2934-108">Modülleri adıyla belirtirken, her yeni bir satıra listelemek için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="d2934-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|<span data-ttu-id="d2934-109">Parametre</span><span class="sxs-lookup"><span data-stu-id="d2934-109">Parameter</span></span>  |<span data-ttu-id="d2934-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2934-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="d2934-111">İçeri aktarmanız gerekir DSC kaynak adları.</span><span class="sxs-lookup"><span data-stu-id="d2934-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="d2934-112">Modül adı belirtilmezse, komut bu DSC kaynakları bu modül içinde arar; Aksi takdirde komut tüm DSC kaynağı yollarında DSC kaynakları arar.</span><span class="sxs-lookup"><span data-stu-id="d2934-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="d2934-113">Joker karakterleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d2934-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="d2934-114">Modül adı veya modülü belirtimi.</span><span class="sxs-lookup"><span data-stu-id="d2934-114">The module name, or module specification.</span></span>  <span data-ttu-id="d2934-115">Bir modülü içeri aktarmak için kaynakları belirtirseniz, komutun yalnızca kaynakları alma dener.</span><span class="sxs-lookup"><span data-stu-id="d2934-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="d2934-116">Modül yalnızca belirtirseniz, komut modülündeki tüm DSC kaynakları alır.</span><span class="sxs-lookup"><span data-stu-id="d2934-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="d2934-117">Örnek: İçinde bir yapılandırma alma DSCResource kullanın</span><span class="sxs-lookup"><span data-stu-id="d2934-117">Example: Use Import-DSCResource within a configuration</span></span>

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
> <span data-ttu-id="d2934-118">Aynı komutta kaynak adları ve modülleri adları için birden fazla değer belirten desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d2934-118">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="d2934-119">Birden çok modüllerde aynı kaynak mevcut durumda hangi modülünden yüklemek için hangi kaynak hakkında belirleyici olmayan davranış olabilir.</span><span class="sxs-lookup"><span data-stu-id="d2934-119">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="d2934-120">Aşağıdaki komutunu derleme sırasında hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="d2934-120">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="d2934-121">Name parametresi kullanırken dikkat edilmesi gerekenler:</span><span class="sxs-lookup"><span data-stu-id="d2934-121">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="d2934-122">Bu, makinede yüklü modülleri sayısına bağlı olarak kaynak yoğunluklu bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="d2934-122">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="d2934-123">Verilen ada sahip bulunan ilk kaynak yükler.</span><span class="sxs-lookup"><span data-stu-id="d2934-123">It will load the first resource found with the given name.</span></span> <span data-ttu-id="d2934-124">Durumda yüklü aynı ada sahip birden fazla kaynak burada yanlış kaynak yüklemek.</span><span class="sxs-lookup"><span data-stu-id="d2934-124">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="d2934-125">Önerilen kullanım belirtmektir `–ModuleName` ile `-Name` aşağıda açıklandığı gibi parametre.</span><span class="sxs-lookup"><span data-stu-id="d2934-125">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="d2934-126">Bu kullanım aşağıdaki faydaları vardır:</span><span class="sxs-lookup"><span data-stu-id="d2934-126">This usage has the following benefits:</span></span>

- <span data-ttu-id="d2934-127">Performans etkisi belirtilen kaynak için arama kapsamını sınırlayarak azaltır.</span><span class="sxs-lookup"><span data-stu-id="d2934-127">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="d2934-128">Açıkça, doğru kaynak yüklenen sağlama kaynak tanımlama modülü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2934-128">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="d2934-129">PowerShell 5. 0'da, DSC kaynakları birden çok sürümü olabilir ve bir bilgisayar yan yana üzerinde sürümleri yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d2934-129">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="d2934-130">Bu, aynı modülü klasörde yer alan birden çok kaynak Modül sürümü sağlayarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d2934-130">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="d2934-131">Daha fazla bilgi için bkz: [birden çok sürümü ile kaynakları kullanarak](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="d2934-131">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="d2934-132">İçeri aktarma DSCResource IntelliSense</span><span class="sxs-lookup"><span data-stu-id="d2934-132">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="d2934-133">İşe DSC yapılandırması yazılırken PowerShell IntelliSence kaynaklar ve kaynak özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2934-133">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="d2934-134">Kaynak tanımları altında `$pshome` modül yolu otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="d2934-134">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="d2934-135">Kullanarak kaynakları aktardığınızda `Import-DSCResource` anahtar sözcüğü, belirtilen kaynak tanımları eklenir ve IntelliSense içeri aktarılan kaynağın şema içerecek şekilde genişletilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2934-135">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![Kaynak IntelliSense](/media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="d2934-137">PowerShell 5. 0'den itibaren sekme tamamlama DSC kaynakları ve bunların özelliklerini için işe eklendi.</span><span class="sxs-lookup"><span data-stu-id="d2934-137">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="d2934-138">Daha fazla bilgi için bkz: [kaynakları](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="d2934-138">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="d2934-139">Yapılandırma derlerken PowerShell alınan kaynak tanımları yapılandırmasında tüm kaynak blokları doğrulamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d2934-139">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="d2934-140">Her kaynak bloğu kaynağın şema tanımı için aşağıdaki kurallar kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="d2934-140">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="d2934-141">Şemada tanımlanan özellikler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2934-141">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="d2934-142">Veri türleri her bir özellik için doğru.</span><span class="sxs-lookup"><span data-stu-id="d2934-142">The data types for each property are correct.</span></span>
- <span data-ttu-id="d2934-143">Anahtarları özellikler belirtilir.</span><span class="sxs-lookup"><span data-stu-id="d2934-143">Keys properties are specified.</span></span>
- <span data-ttu-id="d2934-144">Salt okunur bir özellik kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2934-144">No read-only property is used.</span></span>
- <span data-ttu-id="d2934-145">Doğrulama değeri türleri eşler.</span><span class="sxs-lookup"><span data-stu-id="d2934-145">Validation on value maps types.</span></span>

<span data-ttu-id="d2934-146">Aşağıdaki yapılandırmayı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="d2934-146">Consider the following configuration:</span></span>

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

<span data-ttu-id="d2934-147">Bu yapılandırma sonuçları hata derleniyor.</span><span class="sxs-lookup"><span data-stu-id="d2934-147">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="d2934-148">IntelliSense ve şema doğrulama zorluklar çalışma zamanında önleme ayrıştırma ve derleme süre boyunca, daha fazla hatalarını yakalama olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d2934-148">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="d2934-149">Her DSC kaynağı bir ad olabilir ve bir **FriendlyName** kaynağın şema tarafından tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="d2934-149">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="d2934-150">"MSFT_ServiceResource.shema.mof" ilk iki satır aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2934-150">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="d2934-151">Bu kaynak bir yapılandırmada kullanırken belirtebilirsiniz **MSFT_ServiceResource** veya **hizmet**.</span><span class="sxs-lookup"><span data-stu-id="d2934-151">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="d2934-152">PowerShell v4 ve v5 farklılıkları</span><span class="sxs-lookup"><span data-stu-id="d2934-152">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="d2934-153">Yapılandırmalar PowerShell 4.0 vs yazarken gördüğünüz birden çok farklılıklar vardır. PowerShell 5.0 ve sonraki sürümleri.</span><span class="sxs-lookup"><span data-stu-id="d2934-153">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="d2934-154">Bu bölümde farklar vurgular ilgili bu makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="d2934-154">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="d2934-155">Birden çok kaynak sürümü</span><span class="sxs-lookup"><span data-stu-id="d2934-155">Multiple Resource Versions</span></span>

<span data-ttu-id="d2934-156">Yükleme ve kaynakları yan yana birden fazla sürümünü kullanarak PowerShell 4. 0'desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="d2934-156">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="d2934-157">Kaynakları yapılandırmanızı alma sorunları fark ederseniz, yalnızca bir sürümü yüklü kaynak olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d2934-157">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="d2934-158">Aşağıda, iki sürümü görüntüsündeki **xPSDesiredStateConfiguration** modülü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="d2934-158">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Sabit birden çok kaynak sürümü](/media/multiple-resource-versions-broken.md)

<span data-ttu-id="d2934-160">İstenen modülü sürümünüzü içeriğini modülü dizininin en üst düzeye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d2934-160">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Sabit birden çok kaynak sürümü](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a><span data-ttu-id="d2934-162">Kaynak konumu</span><span class="sxs-lookup"><span data-stu-id="d2934-162">Resource location</span></span>

<span data-ttu-id="d2934-163">Geliştirme ve yapılandırmaları derleme, kaynaklarınızın tarafından belirtilen herhangi bir dizini depolanabilir, [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="d2934-163">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="d2934-164">PowerShell 4. 0'da, tüm DSC kaynağı modülleri "Altında Program Files\WindowsPowerShell\Modules" depolanması için LCM'yi gerektirir veya `$pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="d2934-164">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="d2934-165">PowerShell 5. 0'den itibaren bu gereksinimi kaldırıldı ve kaynak modülleri tarafından belirtilen herhangi bir dizini depolanabilir `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="d2934-165">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2934-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2934-166">See also</span></span>

- [<span data-ttu-id="d2934-167">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="d2934-167">Resources</span></span>](../resources/resources.md)
