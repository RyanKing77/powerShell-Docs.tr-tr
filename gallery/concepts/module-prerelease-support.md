---
ms.date: 09/26/2017
contributor: keithb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: Yayın öncesi modül sürümleri
ms.openlocfilehash: e663a42092556ef1c43a7cf236616bf420171af6
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="b11c1-103">Yayın öncesi modül sürümleri</span><span class="sxs-lookup"><span data-stu-id="b11c1-103">Prerelease Module Versions</span></span>

<span data-ttu-id="b11c1-104">1.6.0 sürümünden başlayarak, PowerShellGet ve PowerShell Galerisi sürümleri bir yayın öncesi olarak 1.0.0 büyük etiketleme için desteği.</span><span class="sxs-lookup"><span data-stu-id="b11c1-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="b11c1-105">Bu özellik önce ön öğeleri 0 ile başlayan bir sürüm olması için sınırlı.</span><span class="sxs-lookup"><span data-stu-id="b11c1-105">Prior to this feature, prerelease items were limited to having a version beginning with 0.</span></span> <span data-ttu-id="b11c1-106">Bu özellikler için daha fazla destek sağlamak için hedefidir [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) geriye doğru sürümleriyle uyumluluk PowerShell sürümleri 3 ve yukarıdaki veya varolan PowerShellGet çiğnemekten olmadan sürüm oluşturma kuralı.</span><span class="sxs-lookup"><span data-stu-id="b11c1-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="b11c1-107">Bu konu modül özgü özelliklerine odaklanır.</span><span class="sxs-lookup"><span data-stu-id="b11c1-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="b11c1-108">Komut dosyaları için eşdeğer özellikler bulunan [, yayın öncesi sürümler betikleri](script-prerelease-support.md) konu.</span><span class="sxs-lookup"><span data-stu-id="b11c1-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](script-prerelease-support.md) topic.</span></span> <span data-ttu-id="b11c1-109">Bu özellikleri kullanarak, yayımcılar bir modül veya komut dosyası sürümü 2.5.0-alpha olarak tanımlamak ve daha sonra ön sürümü yerine geçen bir üretime hazır sürüm 2.5.0 bırakın.</span><span class="sxs-lookup"><span data-stu-id="b11c1-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="b11c1-110">Yüksek düzeyde, yayın öncesi modülü özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="b11c1-110">At a high level, the prerelease module features include:</span></span>

- <span data-ttu-id="b11c1-111">Bir yayın öncesi dize modül bildirimi PSData bölümüne ekleme modülü yayın öncesi sürüm olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b11c1-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="b11c1-112">Modül PowerShell Galerisi yayımlandığında, bu veriler bildirimden ayıklanan ve yayın öncesi öğeleri tanımlamak için kullanılan.</span><span class="sxs-lookup"><span data-stu-id="b11c1-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease items.</span></span>
- <span data-ttu-id="b11c1-113">Yayın öncesi öğeleri alınırken gerektirir - AllowPrerelease bayrağı PowerShellGet komutları Bul-Module, Install-Module ekleme güncelleştirme modülü ve kaydetme modülü.</span><span class="sxs-lookup"><span data-stu-id="b11c1-113">Acquiring prerelease items requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Module, Install-Module, Update-Module, and Save-Module.</span></span> <span data-ttu-id="b11c1-114">Bayrak belirtilmezse, yayın öncesi öğeleri gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="b11c1-114">If the flag is not specified, prerelease items will not be shown.</span></span>
- <span data-ttu-id="b11c1-115">Bulma modülü, Get-InstalledModule tarafından ve PowerShell Galerisi görüntülenen modül sürümleri, 2.5.0-alpha olduğu gibi eklenmemiş ön sürüm dizesi ile tek bir dize olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b11c1-115">Module versions displayed by Find-Module, Get-InstalledModule, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="b11c1-116">Özellikler için Ayrıntılar aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b11c1-116">Details for the features are included below.</span></span>

<span data-ttu-id="b11c1-117">Bu değişiklikler, PowerShell içinde yerleşik modülü sürüm desteği etkilemez ve PowerShell 3.0 ve 4.0 5 ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="b11c1-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span>

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="b11c1-118">Bir modül sürümü yayın öncesi tanımlama</span><span class="sxs-lookup"><span data-stu-id="b11c1-118">Identifying a module version as a prerelease</span></span>

<span data-ttu-id="b11c1-119">Yayın öncesi sürümler için PowerShellGet destek modülü bildirim içinde iki alanı kullanımını gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b11c1-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

- <span data-ttu-id="b11c1-120">Bir yayın öncesi sürüm kullanılıyorsa ve varolan PowerShell sürüm oluşturma uymalıdır modül bildiriminde dahil ModuleVersion 3 parçalı sürüm olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b11c1-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="b11c1-121">Sürüm biçimi A, B ve C tüm tamsayılar nerede A.B.C olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b11c1-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span>
- <span data-ttu-id="b11c1-122">Yayın öncesi dize modül bildiriminde PrivateData PSData bölümünde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b11c1-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span>

<span data-ttu-id="b11c1-123">Aşağıda ön dizesini ayrıntılı gereksinimler verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b11c1-123">Detailed requirements on the Prerelease string are below.</span></span>

<span data-ttu-id="b11c1-124">Bir modül yayın öncesi tanımlayan bir modül bildirimi örnek bölümünde aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="b11c1-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>

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

<span data-ttu-id="b11c1-125">Yayın öncesi dize için ayrıntılı gereksinimleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b11c1-125">The detailed requirements for Prerelease string are:</span></span>

- <span data-ttu-id="b11c1-126">Yayın öncesi dize yalnızca ModuleVersion birincil.İkincil.derleme için 3 kesim olduğunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="b11c1-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="b11c1-127">SemVer v1.0.0 ile hizalar.</span><span class="sxs-lookup"><span data-stu-id="b11c1-127">This aligns with SemVer v1.0.0.</span></span>
- <span data-ttu-id="b11c1-128">Yapı numarası ve ön sürüm dizesi bölücüyü tire olur.</span><span class="sxs-lookup"><span data-stu-id="b11c1-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="b11c1-129">Bir tire ilk karakteri, yalnızca yayın öncesi dizesinde eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="b11c1-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
- <span data-ttu-id="b11c1-130">Yayın öncesi dizesi yalnızca ASCII alfasayısal içerebilir [0-9A-Za - z-].</span><span class="sxs-lookup"><span data-stu-id="b11c1-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="b11c1-131">Yayın öncesi başlamak için en iyi bir uygulamadır bu öğelerin listesini taranırken ön sürümü olduğunu belirlemek daha kolay şekilde alfasayısal bir karakterle dize.</span><span class="sxs-lookup"><span data-stu-id="b11c1-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of items.</span></span>
- <span data-ttu-id="b11c1-132">Şu anda yalnızca SemVer v1.0.0 yayın öncesi dizeler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b11c1-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="b11c1-133">Yayın öncesi dize __bulunmamalıdır__ ya da süresi içeren veya + [. +], SemVer 2. 0'verilir.</span><span class="sxs-lookup"><span data-stu-id="b11c1-133">Prerelease string __must not__ contain either period or + [.+], which are allowed in SemVer 2.0.</span></span>
- <span data-ttu-id="b11c1-134">Desteklenen yayın öncesi dizesi örnekleri:-alfasayısal, - alpha1,-BETA, - update20171020</span><span class="sxs-lookup"><span data-stu-id="b11c1-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

<span data-ttu-id="b11c1-135">__Yayın öncesi sürüm etkisini sırası ve yükleme klasörleri sıralama__</span><span class="sxs-lookup"><span data-stu-id="b11c1-135">__Prerelease versioning impact on sort order and installation folders__</span></span>

<span data-ttu-id="b11c1-136">Sıralama için PowerShell Galerisi yayımlarken önemlidir, bir yayın öncesi sürüm kullanırken ve PowerShellGet komutları kullanarak modülleri yüklerken değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b11c1-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="b11c1-137">Yayın öncesi dize için iki modülleri belirtilmediği takdirde, sıralama düzeni tire aşağıdaki dize bölümü temel alır.</span><span class="sxs-lookup"><span data-stu-id="b11c1-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="b11c1-138">Bu nedenle, sürüm 2.5.0-alpha 2.5.0-beta, hangi 2.5.0-gamma değerinden azdır.</span><span class="sxs-lookup"><span data-stu-id="b11c1-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="b11c1-139">Aynı ModuleVersion iki modülleri varsa ve tek bir ön sürüm dizesi içeriyor, yayın öncesi dize olmadan modül üretime hazır sürüm olduğu varsayılır ve (içeren yayın öncesi sürüm öncesi sürümünü daha büyük bir sürüm olarak sıralanmış dize).</span><span class="sxs-lookup"><span data-stu-id="b11c1-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="b11c1-140">Karşılaştırma bıraktığında 2.5.0 ve 2.5.0-beta, 2.5.0 örnek olarak, sürüm göz önünde bulundurulmalı iki daha büyük.</span><span class="sxs-lookup"><span data-stu-id="b11c1-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="b11c1-141">PowerShell Galerisi yayımlama sırasında varsayılan olarak PowerShell Galerisi önceden yayımlanan sürümü daha büyük bir sürüme yayımlanmakta modülü sürümü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b11c1-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a><span data-ttu-id="b11c1-142">Bulma ve PowerShellGet komutları kullanarak ön öğeleri alınıyor</span><span class="sxs-lookup"><span data-stu-id="b11c1-142">Finding and acquiring prerelease items using PowerShellGet commands</span></span>

<span data-ttu-id="b11c1-143">PowerShellGet Bul-Module, Install-modülü, Update-Module, kullanarak ön öğelerle ilgili ve kaydetme modülü komutlar gerektirir - AllowPrerelease bayrağı ekleme.</span><span class="sxs-lookup"><span data-stu-id="b11c1-143">Dealing with prerelease items using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="b11c1-144">-AllowPrerelease belirtilirse, mevcut olup olmadığını ön öğeleri dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="b11c1-144">If -AllowPrerelease is specified, prerelease items will be included if they are present.</span></span> <span data-ttu-id="b11c1-145">-AllowPrerelease bayrak belirtilmezse, yayın öncesi öğeleri gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="b11c1-145">If -AllowPrerelease flag is not specified, prerelease items will not be shown.</span></span>

<span data-ttu-id="b11c1-146">Yalnızca bu PowerShellGet modülü komutlarda Get-InstalledModule ve bazı durumlarda kaldırma modülüyle durumlardır.</span><span class="sxs-lookup"><span data-stu-id="b11c1-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span>

- <span data-ttu-id="b11c1-147">Get-InstalledModule, Modül sürümü dizesinde her zaman yayın öncesi bilgiler otomatik olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="b11c1-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span>
- <span data-ttu-id="b11c1-148">Kaldırma modül varsayılan olarak kaldırılır bir modül en son sürümünü, __hiçbir sürüm__ belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b11c1-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="b11c1-149">Bu davranışı değişmemiştir.</span><span class="sxs-lookup"><span data-stu-id="b11c1-149">That behavior has not changed.</span></span> <span data-ttu-id="b11c1-150">Ancak, bir yayın öncesi sürüm - RequiredVersion, kullanarak belirtilmişse, - AllowPrerelease gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b11c1-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="b11c1-151">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b11c1-151">Examples</span></span>

```powershell
# Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> find-module TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

# To install a prerelease, always specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

<span data-ttu-id="b11c1-152">Belirtilen yalnızca yayın öncesi nedeniyle farklı bir modül sürümlerini yan yana yüklenmesi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b11c1-152">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="b11c1-153">PowerShellGet kullanarak bir modülü yüklerken farklı aynı Modülü yüklü yan yana ModuleVersion kullanarak bir klasör adı oluşturarak sürümleridir.</span><span class="sxs-lookup"><span data-stu-id="b11c1-153">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="b11c1-154">Yayın öncesi dize olmadan ModuleVersion klasör adı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b11c1-154">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="b11c1-155">Bir kullanıcı MyModule sürüm 2.5.0-alpha yüklerse, MyModule\2.5.0 klasörüne yüklenir.</span><span class="sxs-lookup"><span data-stu-id="b11c1-155">If a user installs MyModule version 2.5.0-alpha, it will be installed to the MyModule\2.5.0 folder.</span></span> <span data-ttu-id="b11c1-156">Kullanıcı daha sonra 2.5.0-beta yüklerse, 2.5.0-beta sürüm olacak __atlayarak yazma__ MyModule\2.5.0 klasörünün içeriğini.</span><span class="sxs-lookup"><span data-stu-id="b11c1-156">If the user then installs 2.5.0-beta, the 2.5.0-beta version will __over-write__ the contents of the folder MyModule\2.5.0.</span></span> <span data-ttu-id="b11c1-157">Bu yaklaşımın bir avantajı vardır yüklemeyi gerek sürüm öncesi sürümünü üretime hazır sürümünü yükledikten sonra olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="b11c1-157">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="b11c1-158">Aşağıdaki örnek, beklenmesi gerekenler gösterir:</span><span class="sxs-lookup"><span data-stu-id="b11c1-158">The example below shows what to expect:</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-beta     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

<span data-ttu-id="b11c1-159">Kaldırma modülü bir modül en son sürümünü kaldırırsanız - RequiredVersion sağlanmadı.</span><span class="sxs-lookup"><span data-stu-id="b11c1-159">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="b11c1-160">-RequiredVersion belirtilir ve bir yayın öncesi ise, - AllowPrerelease komutu eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b11c1-160">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-Module



C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...


```

## <a name="more-details"></a><span data-ttu-id="b11c1-161">Daha fazla ayrıntı</span><span class="sxs-lookup"><span data-stu-id="b11c1-161">More details</span></span>

- [<span data-ttu-id="b11c1-162">Yayın öncesi betiği sürümleri</span><span class="sxs-lookup"><span data-stu-id="b11c1-162">Prerelease Script Versions</span></span>](script-prerelease-support.md)
- [<span data-ttu-id="b11c1-163">Bulma Modülü</span><span class="sxs-lookup"><span data-stu-id="b11c1-163">Find-Module</span></span>](/powershell/module/powershellget/find-module)
- [<span data-ttu-id="b11c1-164">Yükleme Modülü</span><span class="sxs-lookup"><span data-stu-id="b11c1-164">Install-Module</span></span>](/powershell/module/powershellget/install-module)
- [<span data-ttu-id="b11c1-165">Kaydet-Modülü</span><span class="sxs-lookup"><span data-stu-id="b11c1-165">Save-Module</span></span>](/powershell/module/powershellget/save-module)
- [<span data-ttu-id="b11c1-166">Güncelleştirme Modülü</span><span class="sxs-lookup"><span data-stu-id="b11c1-166">Update-Module</span></span>](/powershell/module/powershellget/Update-Module)
- [<span data-ttu-id="b11c1-167">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="b11c1-167">Get-InstalledModule</span></span>](/powershell/module/powershellget/get-installedmodule)
- [<span data-ttu-id="b11c1-168">Kaldırma Modülü</span><span class="sxs-lookup"><span data-stu-id="b11c1-168">UnInstall-Module</span></span>](/powershell/gallery/psget/module/psget_uninstall-module)