---
ms.date: 09/26/2017
contributor: keithb
keywords: Galeri, powershell, cmdlet, psget
title: Yayın öncesi modül sürümleri
ms.openlocfilehash: eced067dd21082de0db653daf3b838217154f1dd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056257"
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="c7e9d-103">Yayın öncesi modül sürümleri</span><span class="sxs-lookup"><span data-stu-id="c7e9d-103">Prerelease Module Versions</span></span>

<span data-ttu-id="c7e9d-104">1.6.0 sürümünden itibaren PowerShellGet ve PowerShell Galerisi olarak ön sürüm 1.0.0 büyüktür sürümleri etiketleme için desteği.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="c7e9d-105">Bu özelliği önce yayın öncesi paketleri 0 sürümü itibarıyla bulunması sınırlıydı.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="c7e9d-106">Bu özellikler için daha büyük destek sağlamak için hedefidir [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) geriye dönük uyumluluğu PowerShellGet, PowerShell sürüm 3 ve yukarıdaki veya mevcut sürümlerini bozucu olmadan sürüm oluşturma kuralı.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="c7e9d-107">Bu konu, modül özgü özellikler üzerinde odaklanır.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="c7e9d-108">Betikler için eşdeğer özellikleri [, yayın öncesi sürümler betikleri](script-prerelease-support.md) konu.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](script-prerelease-support.md) topic.</span></span> <span data-ttu-id="c7e9d-109">Bu özellikleri kullanarak yayımcılar modül veya betik sürümü 2.5.0-alpha olarak tanımlamak ve daha sonra yayım öncesi bir sürümü yerine geçen bir üretime hazır sürüm 2.5.0 bırakın.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="c7e9d-110">Yüksek düzeyde, yayın öncesi modülü özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c7e9d-110">At a high level, the prerelease module features include:</span></span>

- <span data-ttu-id="c7e9d-111">Modül bildirimini PSData bölümünü yayın öncesi bir dize ekleme modülü yayım öncesi bir sürümü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="c7e9d-112">Modülün PowerShell Galerisi'nde yayımlanmış olan, bu verileri bildiriminden ayıklanır ve yayın öncesi paketleri tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="c7e9d-113">Yayın öncesi paketleri alınıyor gerektirir ekleme `-AllowPrerelease` PowerShellGet komutlarını bayrak `Find-Module`, `Install-Module`, `Update-Module`, ve `Save-Module`.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-113">Acquiring prerelease packages requires adding `-AllowPrerelease` flag to the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span> <span data-ttu-id="c7e9d-114">Bayrak belirtilmezse, yayın öncesi paketleri gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="c7e9d-115">Modül sürümlerini tarafından görüntülenen `Find-Module`, `Get-InstalledModule`ve PowerShell galerisinde, olduğu gibi 2.5.0-alpha eklenen ön sürüm dizesi ile tek bir dize olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-115">Module versions displayed by `Find-Module`, `Get-InstalledModule`, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="c7e9d-116">Özellikler için ayrıntıları aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-116">Details for the features are included below.</span></span>

<span data-ttu-id="c7e9d-117">Bu değişiklikler, PowerShell içinde yerleşik modülü sürüm desteği etkilemez ve PowerShell 3.0 ve 4.0 5 ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span>

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="c7e9d-118">Bir modül sürümü bir yayın öncesi tanımlama</span><span class="sxs-lookup"><span data-stu-id="c7e9d-118">Identifying a module version as a prerelease</span></span>

<span data-ttu-id="c7e9d-119">Yayın öncesi sürümleri için destek PowerShellGet modülü bildirimi içinde iki alan gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c7e9d-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

- <span data-ttu-id="c7e9d-120">Yayın öncesi bir sürüm kullanılıyorsa ve mevcut PowerShell sürüm oluşturma ile uyumlu olmalıdır modül bildiriminde bulunan ModuleVersion 3 parçalı bir sürüm olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="c7e9d-121">Sürüm biçimi A.B.C, A, B ve C tüm tamsayıların nerede olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span>
- <span data-ttu-id="c7e9d-122">Modül bildirimindeki PrivateData PSData bölümünde ön sürüm dizesi belirtildi.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span>

<span data-ttu-id="c7e9d-123">Ön sürüm dizesini ayrıntılı gereksinimler aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-123">Detailed requirements on the Prerelease string are below.</span></span>

<span data-ttu-id="c7e9d-124">Bir modül ön tanımlayan bir modül bildirimi bir örnek bölümünde aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="c7e9d-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>

```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

<span data-ttu-id="c7e9d-125">Ön sürüm dizesi için ayrıntılı gereksinimler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c7e9d-125">The detailed requirements for Prerelease string are:</span></span>

- <span data-ttu-id="c7e9d-126">Yayın öncesi dize yalnızca ModuleVersion için birincil.İkincil.derleme 3 Kesimden olduğunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="c7e9d-127">Bu, SemVer v1.0.0 ile hizalar.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-127">This aligns with SemVer v1.0.0.</span></span>
- <span data-ttu-id="c7e9d-128">Derleme numarası ve ön sürüm dizesi bölücüyü tire olur.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="c7e9d-129">Bir tire ön dizedeki ilk karakter yalnızca eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
- <span data-ttu-id="c7e9d-130">Yayın öncesi dize yalnızca ASCII alfasayısal karakterler içerebilir. [0-9A-Za - z-].</span><span class="sxs-lookup"><span data-stu-id="c7e9d-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="c7e9d-131">Ön sürümün süresi başlatmak için en iyi bir yöntemdir bu paketlerin listesini taranırken yayım öncesi bir sürümü olduğunu belirlemek daha kolay olacak şekilde bir alfa karakter dize.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of packages.</span></span>
- <span data-ttu-id="c7e9d-132">Şu anda yalnızca SemVer v1.0.0 ön sürüm dizeleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="c7e9d-133">Yayın öncesi dize **gerekir** döneme içeren veya + [. +], SemVer 2. 0'verilir.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-133">Prerelease string **must not** contain either period or + [.+], which are allowed in SemVer 2.0.</span></span>
- <span data-ttu-id="c7e9d-134">Desteklenen bir ön sürüm dizesi örnekleri şunlardır:-alfa, - alpha1,-BETA, - update20171020</span><span class="sxs-lookup"><span data-stu-id="c7e9d-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="c7e9d-135">Yayın öncesi sürüm oluşturma sırası ve yükleme klasörleri sıralama etkisi</span><span class="sxs-lookup"><span data-stu-id="c7e9d-135">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="c7e9d-136">Sıralama düzeni için PowerShell Galerisi yayımlama sırasında büyük/küçük harf önemlidir, bir ön sürümünü kullanırken ve modülleri PowerShellGet komutlarını kullanarak yüklerken değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="c7e9d-137">Sıralama düzenini, yayın öncesi dize için iki modül belirtilirse, kısa çizgi aşağıdaki dize bölümü temel temel alır.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="c7e9d-138">Bu nedenle, sürüm 2.5.0-alpha 2.5.0-beta, 2.5.0-gamma değerinden küçük olan küçüktür.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="c7e9d-139">Modülü ön sürüm dizesi olmadan aynı ModuleVersion iki modül sahip ve tek bir ön sürüm dizesi varsa, üretime hazır sürüm olduğu varsayılır ve (içeren yayın öncesi sürüm öncesi sürümünü sürümünden daha yüksek bir sürüm olarak sıralanır dize).</span><span class="sxs-lookup"><span data-stu-id="c7e9d-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="c7e9d-140">Karşılaştırma bıraktığında 2.5.0 ve 2.5.0-beta, 2.5.0 örnek olarak sürüm değerlendirilir iki büyük.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="c7e9d-141">PowerShell Galerisi'nde yayımlama sırasında varsayılan olarak PowerShell Galerisi'nde olan önceden yayımlanan sürümü daha büyük bir sürümse yayımlanmakta modülü sürümüne sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="c7e9d-142">Bulma ve PowerShellGet komutlarını kullanarak yayın öncesi paketleri alınıyor</span><span class="sxs-lookup"><span data-stu-id="c7e9d-142">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="c7e9d-143">PowerShellGet bulma modülü, Install-Module güncelleştirme-Module kullanarak yayın öncesi paketleri ile ilgilenen ve Save-Module komutları gerektirir - AllowPrerelease bayrağı ekleme.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-143">Dealing with prerelease packages using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="c7e9d-144">-AllowPrerelease belirtilmediği takdirde, mevcut değilse yayın öncesi paketleri dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-144">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="c7e9d-145">-AllowPrerelease bayrak belirtilmezse, yayın öncesi paketleri gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-145">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="c7e9d-146">Yalnızca bu PowerShellGet modülü komutlarda Get-InstalledModule ve bazı durumlarda kaldırma modülü ile özel durumlardır.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span>

- <span data-ttu-id="c7e9d-147">Get-InstalledModule, modüller için sürüm dizesindeki her zaman yayın öncesi bilgiler otomatik olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span>
- <span data-ttu-id="c7e9d-148">Kaldırma-Module varsayılan olarak kaldırılır bir modülün en son sürüm ise __sürüm__ belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="c7e9d-149">Bu davranış değişmemiştir.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-149">That behavior has not changed.</span></span> <span data-ttu-id="c7e9d-150">Ancak, bir ön sürümünü kullanarak - RequiredVersion, belirtilirse - AllowPrerelease gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="c7e9d-151">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c7e9d-151">Examples</span></span>

<span data-ttu-id="c7e9d-152">PowerShell Galerisi TestPackage modül sürümlerini 1.8.0 ve 1.9.0-alpha sahip olduğunu varsayın.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-152">Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.</span></span> <span data-ttu-id="c7e9d-153">Varsa `-AllowPrerelease` olan belirtilmezse, yalnızca sürüm 1.8.0 döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-153">If `-AllowPrerelease` is not specified, only version 1.8.0 will be returned.</span></span>

```powershell
find-module TestPackage
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.8.0          TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

```powershell
find-module TestPackage -AllowPrerelease
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.9.0-alpha    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="c7e9d-154">Bir ön sürümü yüklemek için her zaman - AllowPrerelease belirtin.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-154">To install a prerelease, always specify -AllowPrerelease.</span></span> <span data-ttu-id="c7e9d-155">Yayın öncesi sürüm dizesi belirtilmesi yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-155">Specifying a prerelease version string is not sufficient.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha
```

```output
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage
```

<span data-ttu-id="c7e9d-156">-AllowPrerelease belirtilmediğinden önceki komut başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-156">The previous command failed because -AllowPrerelease was not specified.</span></span> <span data-ttu-id="c7e9d-157">Ekleme `-AllowPrerelease` başarılı şekilde neden olur.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-157">Adding `-AllowPrerelease` will result in success.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="c7e9d-158">Yalnızca ön sürümün süresi belirtilen nedeniyle farklı bir modül sürümlerini yan yana yüklenmesi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-158">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="c7e9d-159">PowerShellGet kullanarak bir modülü yüklerken farklı aynı Modülü yüklü yan yana ModuleVersion kullanarak bir klasör adı oluşturarak sürümleridir.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-159">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="c7e9d-160">Ön sürüm dizesi olmadan ModuleVersion klasör adı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-160">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="c7e9d-161">Bir kullanıcı MyModule sürüm 2.5.0-alpha yüklerse, bu şekilde yüklenecek `MyModule\2.5.0` klasör.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-161">If a user installs MyModule version 2.5.0-alpha, it will be installed to the `MyModule\2.5.0` folder.</span></span> <span data-ttu-id="c7e9d-162">Kullanıcı ardından 2.5.0-beta yüklerse, 2.5.0-beta sürümü olacak **üzerine** klasörünün içeriğini `MyModule\2.5.0`.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-162">If the user then installs 2.5.0-beta, the 2.5.0-beta version will **overwrite** the contents of the folder `MyModule\2.5.0`.</span></span> <span data-ttu-id="c7e9d-163">Bu yaklaşımın bir avantajı, yüklemeyi gerek yayım öncesi bir sürümü üretime hazır sürümünü yükledikten sonra olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-163">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="c7e9d-164">Aşağıdaki örnekte beklenmesi gerekenler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="c7e9d-164">The example below shows what to expect:</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-alpha     TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name            Repository  Description
-------        ----            ----------  -----------
1.9.0-beta     TestPackage     PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

```

<span data-ttu-id="c7e9d-165">Kaldırma modülü bir modülün en son sürümünü kaldırırsanız - RequiredVersion sağlanmadı.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-165">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="c7e9d-166">Belirtilen ve ön sürüm - RequiredVersion, - AllowPrerelease komutu eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7e9d-166">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
2.0.0-alpha1    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta

Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-Module

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
2.0.0-alpha1    TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...
```

## <a name="more-details"></a><span data-ttu-id="c7e9d-167">Daha fazla ayrıntı</span><span class="sxs-lookup"><span data-stu-id="c7e9d-167">More details</span></span>

- [<span data-ttu-id="c7e9d-168">Yayın öncesi betik sürümleri</span><span class="sxs-lookup"><span data-stu-id="c7e9d-168">Prerelease Script Versions</span></span>](script-prerelease-support.md)
- [<span data-ttu-id="c7e9d-169">Modül Bul</span><span class="sxs-lookup"><span data-stu-id="c7e9d-169">Find-Module</span></span>](/powershell/module/powershellget/find-module)
- [<span data-ttu-id="c7e9d-170">Install-Module</span><span class="sxs-lookup"><span data-stu-id="c7e9d-170">Install-Module</span></span>](/powershell/module/powershellget/install-module)
- [<span data-ttu-id="c7e9d-171">Save-Module</span><span class="sxs-lookup"><span data-stu-id="c7e9d-171">Save-Module</span></span>](/powershell/module/powershellget/save-module)
- [<span data-ttu-id="c7e9d-172">Güncelleştirme Modülü</span><span class="sxs-lookup"><span data-stu-id="c7e9d-172">Update-Module</span></span>](/powershell/module/powershellget/Update-Module)
- [<span data-ttu-id="c7e9d-173">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="c7e9d-173">Get-InstalledModule</span></span>](/powershell/module/powershellget/get-installedmodule)
- [<span data-ttu-id="c7e9d-174">Modül kaldırma</span><span class="sxs-lookup"><span data-stu-id="c7e9d-174">UnInstall-Module</span></span>](/powershell/module/powershellget/uninstall-module)
