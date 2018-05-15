---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: Komut dosyaları uygulamasının yayım öncesi sürümleri
ms.openlocfilehash: 2c7e1cbc352f8dc39fef9cd968b2f0c1964c30b3
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="prerelease-versions-of-scripts"></a><span data-ttu-id="38480-103">Komut dosyaları uygulamasının yayım öncesi sürümleri</span><span class="sxs-lookup"><span data-stu-id="38480-103">Prerelease versions of scripts</span></span>

<span data-ttu-id="38480-104">1.6.0 sürümünden başlayarak, PowerShellGet ve PowerShell Galerisi sürümleri bir yayın öncesi olarak 1.0.0 büyük etiketleme için desteği.</span><span class="sxs-lookup"><span data-stu-id="38480-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="38480-105">Bu özellik önce ön öğeleri 0 ile başlayan bir sürüm olması için sınırlı.</span><span class="sxs-lookup"><span data-stu-id="38480-105">Prior to this feature, prerelease items were limited to having a version beginning with 0.</span></span> <span data-ttu-id="38480-106">Bu özellikler için daha fazla destek sağlamak için hedefidir [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) geriye doğru sürümleriyle uyumluluk PowerShell sürümleri 3 ve yukarıdaki veya varolan PowerShellGet çiğnemekten olmadan sürüm oluşturma kuralı.</span><span class="sxs-lookup"><span data-stu-id="38480-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="38480-107">Bu konu betik özgü özelliklerine odaklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="38480-107">This topic focuses on the script-specific features.</span></span> <span data-ttu-id="38480-108">Modüller için eşdeğer özellikler bulunan [yayın öncesi modül sürümleri](module-prerelease-support.md) konu.</span><span class="sxs-lookup"><span data-stu-id="38480-108">The equivalent features for modules are in the [Prerelease Module Versions](module-prerelease-support.md) topic.</span></span> <span data-ttu-id="38480-109">Bu özellikleri kullanarak, yayımcılar bir komut dosyası sürümü 2.5.0-alpha olarak tanımlamak ve daha sonra ön sürümü yerine geçen bir üretime hazır sürüm 2.5.0 bırakın.</span><span class="sxs-lookup"><span data-stu-id="38480-109">Using these features, publishers can identify a script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="38480-110">Yüksek düzeyde, yayın öncesi betiği özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="38480-110">At a high level, the prerelease script features include:</span></span>

- <span data-ttu-id="38480-111">Komut dosyası bildiriminde sürüm dizesi PrereleaseString sonek ekleme.</span><span class="sxs-lookup"><span data-stu-id="38480-111">Adding a PrereleaseString suffix to the version string in the script manifest.</span></span> <span data-ttu-id="38480-112">PowerShell Galerisi betikleri yayımlandığında, bu veriler bildirimden ayıklanan ve yayın öncesi öğeleri tanımlamak için kullanılan.</span><span class="sxs-lookup"><span data-stu-id="38480-112">When the scripts is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease items.</span></span>
- <span data-ttu-id="38480-113">Yayın öncesi öğeleri alınırken gerektirir - AllowPrerelease bayrağı PowerShellGet komutları Bul-komut dosyası, yükleme betiği ekleme güncelleştirme betiğini ve Kaydet-komut dosyası.</span><span class="sxs-lookup"><span data-stu-id="38480-113">Acquiring prerelease items requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Script, Install-Script, Update-Script, and Save-Script.</span></span> <span data-ttu-id="38480-114">Bayrak belirtilmezse, yayın öncesi öğeleri gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="38480-114">If the flag is not specified, prerelease items will not be shown.</span></span>
- <span data-ttu-id="38480-115">Komut dosyası sürümleri Bul-komut dosyası, Get-InstalledScript tarafından ve PowerShell Galerisi görüntülenen 2.5.0-alpha olduğu gibi PrereleaseString birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="38480-115">Script versions displayed by Find-Script, Get-InstalledScript, and in the PowerShell Gallery will be displayed with the PrereleaseString, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="38480-116">Özellikler için Ayrıntılar aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="38480-116">Details for the features are included below.</span></span>

## <a name="identifying-a-script-version-as-a-prerelease"></a><span data-ttu-id="38480-117">Bir komut dosyası sürüm yayın öncesi tanımlama</span><span class="sxs-lookup"><span data-stu-id="38480-117">Identifying a script version as a prerelease</span></span>

<span data-ttu-id="38480-118">Yayın öncesi sürümler için PowerShellGet destek betikler için modülleri kolaydır.</span><span class="sxs-lookup"><span data-stu-id="38480-118">PowerShellGet support for prerelease versions is easier for scripts than modules.</span></span> <span data-ttu-id="38480-119">Yayın öncesi dize ekleyerek neden uyumluluk sorunu yok olduklarından betik sürüm yalnızca PowerShellGet tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="38480-119">Script versioning is only supported by PowerShellGet, so there are no compatibility issues caused by adding the prerelease string.</span></span> <span data-ttu-id="38480-120">Bir komut dosyasını bir yayın öncesi olarak PowerShell galerisinde tanımlamak için komut dosyası meta verilerde düzgün biçimlendirilmiş sürüm dizesi için yayın öncesi soneki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="38480-120">To identify a script in the PowerShell Gallery as a prerelease, add a prerelease suffix to a properly-formatted version string in the script metadata.</span></span>

<span data-ttu-id="38480-121">Bir komut dosyası bildirimi ön sürümü ile örnek bölümünde aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="38480-121">An example section of a script manifest with a prerelease version would look like the following:</span></span>

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>

```

<span data-ttu-id="38480-122">Bir yayın öncesi soneki kullanmak için sürüm dizesi aşağıdaki gereksinimleri karşılamalıdır:</span><span class="sxs-lookup"><span data-stu-id="38480-122">To use a prerelease suffix, the version string must meet the following requirements:</span></span>

- <span data-ttu-id="38480-123">Bir yayın öncesi soneki yalnızca sürüm 3 kesim birincil.İkincil.derleme için olduğunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="38480-123">A prerelease suffix may only be specified when the Version is 3 segments for Major.Minor.Build.</span></span>
  <span data-ttu-id="38480-124">Bu SemVer v1.0.0 ile hizalar</span><span class="sxs-lookup"><span data-stu-id="38480-124">This aligns with SemVer v1.0.0</span></span>
- <span data-ttu-id="38480-125">Yayın öncesi soneki çizgi ile başlayan ve ASCII alfasayısal içerebilir bir dizedir [0-9A-Za - z-]</span><span class="sxs-lookup"><span data-stu-id="38480-125">The prerelease suffix is a string which begins with a hyphen, and may contain ASCII alphanumerics [0-9A-Za-z-]</span></span>
- <span data-ttu-id="38480-126">Yalnızca SemVer v1.0.0 yayın öncesi dizeler desteklenir şu anda, bu nedenle ön soneki __bulunmamalıdır__ ya da süresi içeren veya + [. +], SemVer 2. 0'verilir</span><span class="sxs-lookup"><span data-stu-id="38480-126">Only SemVer v1.0.0 prerelease strings are supported at this time, so the prerelease suffix __must not__ contain either period or + [.+], which are allowed in SemVer 2.0</span></span>
- <span data-ttu-id="38480-127">Desteklenen PrereleaseString dizesi örnekleri:-alfasayısal, - alpha1,-BETA, - update20171020</span><span class="sxs-lookup"><span data-stu-id="38480-127">Examples of supported PrereleaseString strings are: -alpha, -alpha1, -BETA, -update20171020</span></span>

<span data-ttu-id="38480-128">__Yayın öncesi sürüm etkisini sırası ve yükleme klasörleri sıralama__</span><span class="sxs-lookup"><span data-stu-id="38480-128">__Prerelease versioning impact on sort order and installation folders__</span></span>

<span data-ttu-id="38480-129">Sıralama için PowerShell Galerisi yayımlarken önemlidir, bir yayın öncesi sürüm kullanırken ve PowerShellGet komutları kullanarak komut dosyalarını yüklerken değiştirir.</span><span class="sxs-lookup"><span data-stu-id="38480-129">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing scripts using PowerShellGet commands.</span></span> <span data-ttu-id="38480-130">İki sürüm numarasını sürümleriyle komut dosyaları var, sıralama düzeni tire aşağıdaki dize bölümü dayanır.</span><span class="sxs-lookup"><span data-stu-id="38480-130">If two scripts versions with the version number exist, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="38480-131">Bu nedenle, sürüm 2.5.0-alpha 2.5.0-beta, hangi 2.5.0-gamma değerinden azdır.</span><span class="sxs-lookup"><span data-stu-id="38480-131">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="38480-132">İki komut aynı sürüm numarasına sahip ve tek bir PrereleaseString komut dosyası varsa __olmadan__ yayın öncesi soneki üretime hazır sürüm olduğu varsayılır ve yayın öncesi sürümünden daha yüksek bir sürüm olarak sıralanmış Sürüm.</span><span class="sxs-lookup"><span data-stu-id="38480-132">If two scripts have the same version number, and only one has a PrereleaseString, the script __without__ the prerelease suffix is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version.</span></span> <span data-ttu-id="38480-133">Karşılaştırma bıraktığında 2.5.0 ve 2.5.0-beta, 2.5.0 örnek olarak, sürüm göz önünde bulundurulmalı iki daha büyük.</span><span class="sxs-lookup"><span data-stu-id="38480-133">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="38480-134">PowerShell Galerisi yayımlama sırasında varsayılan olarak yayımlanmakta komut dosyasının sürümünü PowerShell Galerisi önceden yayımlanan sürümü'den büyük bir sürüm olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="38480-134">When publishing to the PowerShell Gallery, by default the version of the script being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span> <span data-ttu-id="38480-135">Bir yayımcı sürüm 2.5.0-alpha 2.5.0-beta 2.5.0 (ile ön sonek) ile veya güncelleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="38480-135">A publisher may update version 2.5.0-alpha with 2.5.0-beta, or with 2.5.0 (with no prerelease suffix).</span></span>

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a><span data-ttu-id="38480-136">Bulma ve PowerShellGet komutları kullanarak ön öğeleri alınıyor</span><span class="sxs-lookup"><span data-stu-id="38480-136">Finding and acquiring prerelease items using PowerShellGet commands</span></span>

<span data-ttu-id="38480-137">PowerShellGet Bul-komut dosyası, yükleme betiğini güncelleştirmesi-komut dosyası, kullanarak ön öğelerle ilgili ve Kaydet komut gerektirir - AllowPrerelease bayrağı ekleme.</span><span class="sxs-lookup"><span data-stu-id="38480-137">Dealing with prerelease items using PowerShellGet Find-Script, Install-Script, Update-Script, and Save-Script commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="38480-138">-AllowPrerelease belirtilirse, mevcut olup olmadığını ön öğeleri dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="38480-138">If -AllowPrerelease is specified, prerelease items will be included if they are present.</span></span> <span data-ttu-id="38480-139">-AllowPrerelease bayrak belirtilmezse, yayın öncesi öğeleri gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="38480-139">If -AllowPrerelease flag is not specified, prerelease items will not be shown.</span></span>

<span data-ttu-id="38480-140">Yalnızca bu PowerShellGet betik komutlarda Get-InstalledScript ve bazı durumlarda kaldırma komut dosyası ile durumlardır.</span><span class="sxs-lookup"><span data-stu-id="38480-140">The only exceptions to this in the PowerShellGet script commands are Get-InstalledScript, and some cases with Uninstall-Script.</span></span>

- <span data-ttu-id="38480-141">Varsa, get-InstalledScript her zaman otomatik olarak yayın öncesi bilgiler sürüm dizesi içinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="38480-141">Get-InstalledScript always will automatically show the prerelease information in the version string if it is present.</span></span>
- <span data-ttu-id="38480-142">Kaldırma komut dosyası varsayılan olarak kaldırılır bir komut dosyasının en son sürümünü, __hiçbir sürüm__ belirtilir.</span><span class="sxs-lookup"><span data-stu-id="38480-142">Uninstall-Script will by default uninstall the most recent version of a script, if __no version__ is specified.</span></span> <span data-ttu-id="38480-143">Bu davranışı değişmemiştir.</span><span class="sxs-lookup"><span data-stu-id="38480-143">That behavior has not changed.</span></span> <span data-ttu-id="38480-144">Ancak, bir yayın öncesi sürüm - RequiredVersion, kullanarak belirtilmişse, - AllowPrerelease gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="38480-144">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="38480-145">Örnekler</span><span class="sxs-lookup"><span data-stu-id="38480-145">Examples</span></span>

```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> Find-Script TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Find-Script TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# To install a prerelease, you must specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and script name 'TestPackage'.
Try Get-PSRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# Note that Get-InstalledScript shows the prerelease version.
# If -RequiredVersion is not specified, all installed scripts will be displayed by Get-InstalledScript
```

<span data-ttu-id="38480-146">Kaldırma komut dosyası geçerli bir komut dosyası sürümünü kaldırırsanız - RequiredVersion sağlanmadı.</span><span class="sxs-lookup"><span data-stu-id="38480-146">Uninstall-Script will remove the current version of a script when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="38480-147">-RequiredVersion belirtilir ve bir yayın öncesi ise, - AllowPrerelease komutu eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="38480-147">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-script


C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
# Since script versions are not installed side-by-side, the above could be simply "Uninstall-Script TestPackage"

C:\windows\system32> Get-Installedscript TestPackage
PackageManagement\Get-Package : No match was found for the specified search criteria and script names 'testpackage'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.5.0.0\PSModule.psm1:4088 char:9
+         PackageManagement\Get-Package @PSBoundParameters | Microsoft. ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...lets.GetPackage:GetPackage) [Get-Package], Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.GetPackage
```

## <a name="more-details"></a><span data-ttu-id="38480-148">Daha fazla ayrıntı</span><span class="sxs-lookup"><span data-stu-id="38480-148">More details</span></span>

- [<span data-ttu-id="38480-149">Yayın öncesi modül sürümleri</span><span class="sxs-lookup"><span data-stu-id="38480-149">Prerelease Module Versions</span></span>](module-prerelease-support.md)
- [<span data-ttu-id="38480-150">Bulma komut dosyası</span><span class="sxs-lookup"><span data-stu-id="38480-150">Find-script</span></span>](/powershell/module/powershellget/find-script)
- [<span data-ttu-id="38480-151">Yükleme betiği</span><span class="sxs-lookup"><span data-stu-id="38480-151">Install-script</span></span>](/powershell/module/powershellget/install-script)
- [<span data-ttu-id="38480-152">Kaydet-komut dosyası</span><span class="sxs-lookup"><span data-stu-id="38480-152">Save-script</span></span>](/powershell/module/powershellget/save-script)
- [<span data-ttu-id="38480-153">Güncelleştirme komut dosyası</span><span class="sxs-lookup"><span data-stu-id="38480-153">Update-script</span></span>](/powershell/module/powershellget/update-script)
- [<span data-ttu-id="38480-154">Get-Installedscript</span><span class="sxs-lookup"><span data-stu-id="38480-154">Get-Installedscript</span></span>](/powershell/module/powershellget/get-installedscript)
- [<span data-ttu-id="38480-155">Kaldırma betiği</span><span class="sxs-lookup"><span data-stu-id="38480-155">UnInstall-script</span></span>](/powershell/module/powershellget/uninstall-script)