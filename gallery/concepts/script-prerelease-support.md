---
ms.date: 10/17/2017
contributor: keithb
keywords: Galeri, powershell, cmdlet, psget
title: Betikleri uygulamasının yayım öncesi sürümleri
ms.openlocfilehash: 4e7eab682008ed57163c51fe3a61a744b347bef2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683985"
---
# <a name="prerelease-versions-of-scripts"></a><span data-ttu-id="311d0-103">Betikleri uygulamasının yayım öncesi sürümleri</span><span class="sxs-lookup"><span data-stu-id="311d0-103">Prerelease versions of scripts</span></span>

<span data-ttu-id="311d0-104">1.6.0 sürümünden itibaren PowerShellGet ve PowerShell Galerisi olarak ön sürüm 1.0.0 büyüktür sürümleri etiketleme için desteği.</span><span class="sxs-lookup"><span data-stu-id="311d0-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="311d0-105">Bu özelliği önce yayın öncesi paketleri 0 sürümü itibarıyla bulunması sınırlıydı.</span><span class="sxs-lookup"><span data-stu-id="311d0-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="311d0-106">Bu özellikler için daha büyük destek sağlamak için hedefidir [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) geriye dönük uyumluluğu PowerShellGet, PowerShell sürüm 3 ve yukarıdaki veya mevcut sürümlerini bozucu olmadan sürüm oluşturma kuralı.</span><span class="sxs-lookup"><span data-stu-id="311d0-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="311d0-107">Bu konu, betik özgü özellikler üzerinde odaklanır.</span><span class="sxs-lookup"><span data-stu-id="311d0-107">This topic focuses on the script-specific features.</span></span> <span data-ttu-id="311d0-108">Modüller için eşdeğer özellikleri [yayın öncesi modül sürümlerini](module-prerelease-support.md) konu.</span><span class="sxs-lookup"><span data-stu-id="311d0-108">The equivalent features for modules are in the [Prerelease Module Versions](module-prerelease-support.md) topic.</span></span> <span data-ttu-id="311d0-109">Bu özellikleri kullanarak yayımcılar bir betik sürümü 2.5.0-alpha olarak tanımlamak ve daha sonra yayım öncesi bir sürümü yerine geçen bir üretime hazır sürüm 2.5.0 bırakın.</span><span class="sxs-lookup"><span data-stu-id="311d0-109">Using these features, publishers can identify a script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="311d0-110">Yüksek düzeyde, yayın öncesi betik özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="311d0-110">At a high level, the prerelease script features include:</span></span>

- <span data-ttu-id="311d0-111">Sürüm dizesi betik bildiriminde PrereleaseString sonek ekleme.</span><span class="sxs-lookup"><span data-stu-id="311d0-111">Adding a PrereleaseString suffix to the version string in the script manifest.</span></span> <span data-ttu-id="311d0-112">PowerShell Galerisi'nde betikleri yayımlandığında, bu verileri bildiriminden ayıklanır ve yayın öncesi paketleri tanımlamak için kullanılan.</span><span class="sxs-lookup"><span data-stu-id="311d0-112">When the scripts is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="311d0-113">Yayın öncesi paketleri alınıyor gerektirir PowerShellGet komutlarını Find-Script, yükleme betiği, - AllowPrerelease bayrağı ekleme güncelleştirme betiğini ve Save-Script.</span><span class="sxs-lookup"><span data-stu-id="311d0-113">Acquiring prerelease packages requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Script, Install-Script, Update-Script, and Save-Script.</span></span> <span data-ttu-id="311d0-114">Bayrak belirtilmezse, yayın öncesi paketleri gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="311d0-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="311d0-115">Find-Script, Get-InstalledScript ve PowerShell Galerisi'ndeki görüntülenen betik sürümleri 2.5.0-alpha olduğu gibi PrereleaseString görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="311d0-115">Script versions displayed by Find-Script, Get-InstalledScript, and in the PowerShell Gallery will be displayed with the PrereleaseString, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="311d0-116">Özellikler için ayrıntıları aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="311d0-116">Details for the features are included below.</span></span>

## <a name="identifying-a-script-version-as-a-prerelease"></a><span data-ttu-id="311d0-117">Bir yayın öncesi bir betik sürümü tanımlama</span><span class="sxs-lookup"><span data-stu-id="311d0-117">Identifying a script version as a prerelease</span></span>

<span data-ttu-id="311d0-118">Yayın öncesi sürümler için PowerShellGet destek betikler için modülleri kolaydır.</span><span class="sxs-lookup"><span data-stu-id="311d0-118">PowerShellGet support for prerelease versions is easier for scripts than modules.</span></span> <span data-ttu-id="311d0-119">Uyumluluk sorunu yok ön dize ekleyerek neden olduğundan betik sürüm oluşturma yalnızca PowerShellGet tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="311d0-119">Script versioning is only supported by PowerShellGet, so there are no compatibility issues caused by adding the prerelease string.</span></span> <span data-ttu-id="311d0-120">Bir komut dosyası ön sürüm olarak PowerShell galerisinde tanımlamak için bir komut dosyası meta verileri doğru şekilde biçimlendirildiğini sürüm dizesi için bir ön eki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="311d0-120">To identify a script in the PowerShell Gallery as a prerelease, add a prerelease suffix to a properly-formatted version string in the script metadata.</span></span>

<span data-ttu-id="311d0-121">Bir örnek bölümü bir komut dosyası bildiriminin yayım öncesi bir sürümü ile aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="311d0-121">An example section of a script manifest with a prerelease version would look like the following:</span></span>

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

<span data-ttu-id="311d0-122">Sürüm dizesi bir ön eki kullanmak için aşağıdaki gereksinimleri karşılaması gerekir:</span><span class="sxs-lookup"><span data-stu-id="311d0-122">To use a prerelease suffix, the version string must meet the following requirements:</span></span>

- <span data-ttu-id="311d0-123">Bir ön eki yalnızca sürümü Major.Minor.Build için 3 Kesimden olduğunda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="311d0-123">A prerelease suffix may only be specified when the Version is 3 segments for Major.Minor.Build.</span></span>
  <span data-ttu-id="311d0-124">Bu SemVer v1.0.0 ile hizalar.</span><span class="sxs-lookup"><span data-stu-id="311d0-124">This aligns with SemVer v1.0.0</span></span>
- <span data-ttu-id="311d0-125">Ön eki, kısa çizgi ile başlar ve alfasayısal ASCII karakterler içerebilir bir dizedir [0-9A-Za - z-]</span><span class="sxs-lookup"><span data-stu-id="311d0-125">The prerelease suffix is a string which begins with a hyphen, and may contain ASCII alphanumerics [0-9A-Za-z-]</span></span>
- <span data-ttu-id="311d0-126">Yalnızca SemVer v1.0.0 ön sürüm dizeleri desteklenir şu anda, bu nedenle ön eki **gerekir** döneme içeren veya + [. +], SemVer 2. 0'verilir</span><span class="sxs-lookup"><span data-stu-id="311d0-126">Only SemVer v1.0.0 prerelease strings are supported at this time, so the prerelease suffix **must not** contain either period or + [.+], which are allowed in SemVer 2.0</span></span>
- <span data-ttu-id="311d0-127">Desteklenen PrereleaseString dize örnekleridir:-alfa, - alpha1,-BETA, - update20171020</span><span class="sxs-lookup"><span data-stu-id="311d0-127">Examples of supported PrereleaseString strings are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="311d0-128">Yayın öncesi sürüm oluşturma sırası ve yükleme klasörleri sıralama etkisi</span><span class="sxs-lookup"><span data-stu-id="311d0-128">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="311d0-129">Sıralama düzeni için PowerShell Galerisi yayımlama sırasında büyük/küçük harf önemlidir, bir ön sürümünü kullanırken ve betikleri PowerShellGet komutlarını kullanarak yüklerken değiştirir.</span><span class="sxs-lookup"><span data-stu-id="311d0-129">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing scripts using PowerShellGet commands.</span></span> <span data-ttu-id="311d0-130">İki sürüm numarasını sürümleriyle komutlar mevcut, kısa çizgi aşağıdaki dize bölümü temel sıralama düzenini temel alır.</span><span class="sxs-lookup"><span data-stu-id="311d0-130">If two scripts versions with the version number exist, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="311d0-131">Bu nedenle, sürüm 2.5.0-alpha 2.5.0-beta, 2.5.0-gamma değerinden küçük olan küçüktür.</span><span class="sxs-lookup"><span data-stu-id="311d0-131">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="311d0-132">İki komut aynı sürüm numarasına sahip ve tek bir PrereleaseString betik varsa **olmadan** üretime hazır sürüm olduğu varsayılır ve yayın öncesi sürümünden büyük bir sürüm olarak sıralanmış, ön eki Sürüm.</span><span class="sxs-lookup"><span data-stu-id="311d0-132">If two scripts have the same version number, and only one has a PrereleaseString, the script **without** the prerelease suffix is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version.</span></span> <span data-ttu-id="311d0-133">Karşılaştırma bıraktığında 2.5.0 ve 2.5.0-beta, 2.5.0 örnek olarak sürüm değerlendirilir iki büyük.</span><span class="sxs-lookup"><span data-stu-id="311d0-133">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="311d0-134">PowerShell Galerisi'nde yayımlama sırasında varsayılan olarak PowerShell Galerisi önceden yayımlanan sürümü daha büyük bir sürümse yayımlanmakta betik sürümüne sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="311d0-134">When publishing to the PowerShell Gallery, by default the version of the script being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span> <span data-ttu-id="311d0-135">Bir yayımcı, sürüm 2.5.0-alpha 2.5.0-beta 2.5.0 (ile ön sonek) ile veya güncelleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="311d0-135">A publisher may update version 2.5.0-alpha with 2.5.0-beta, or with 2.5.0 (with no prerelease suffix).</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="311d0-136">Bulma ve PowerShellGet komutlarını kullanarak yayın öncesi paketleri alınıyor</span><span class="sxs-lookup"><span data-stu-id="311d0-136">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="311d0-137">PowerShellGet Find-Script, yükleme betiği, Update-komut dosyası, yayın öncesi paketlerle ilgilenme ve Kaydet komut gerektirir - AllowPrerelease bayrağı ekleme.</span><span class="sxs-lookup"><span data-stu-id="311d0-137">Dealing with prerelease packages using PowerShellGet Find-Script, Install-Script, Update-Script, and Save-Script commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="311d0-138">-AllowPrerelease belirtilmediği takdirde, mevcut değilse yayın öncesi paketleri dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="311d0-138">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="311d0-139">-AllowPrerelease bayrak belirtilmezse, yayın öncesi paketleri gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="311d0-139">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="311d0-140">Bunun tek özel durum PowerShellGet betik komutlarında şunlardır: Get-InstalledScript ve kaldırma betiğini ile bazı durumlarda.</span><span class="sxs-lookup"><span data-stu-id="311d0-140">The only exceptions to this in the PowerShellGet script commands are Get-InstalledScript, and some cases with Uninstall-Script.</span></span>

- <span data-ttu-id="311d0-141">Varsa, get-InstalledScript her zaman otomatik olarak yayın öncesi bilgiler sürüm dizesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="311d0-141">Get-InstalledScript always will automatically show the prerelease information in the version string if it is present.</span></span>
- <span data-ttu-id="311d0-142">Kaldırma betiği varsayılan olarak kaldırılır en son sürümünü bir betik, **sürüm** belirtilir.</span><span class="sxs-lookup"><span data-stu-id="311d0-142">Uninstall-Script will by default uninstall the most recent version of a script, if **no version** is specified.</span></span> <span data-ttu-id="311d0-143">Bu davranış değişmemiştir.</span><span class="sxs-lookup"><span data-stu-id="311d0-143">That behavior has not changed.</span></span> <span data-ttu-id="311d0-144">Ancak, bir ön sürümünü kullanarak belirtilirse `-RequiredVersion`, `-AllowPrerelease` gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="311d0-144">However, if a prerelease version is specified using `-RequiredVersion`, `-AllowPrerelease` will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="311d0-145">Örnekler</span><span class="sxs-lookup"><span data-stu-id="311d0-145">Examples</span></span>

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
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage)[Find-Package], Exception
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

<span data-ttu-id="311d0-146">-RequiredVersion sağlanmazsa, bir komut dosyası geçerli sürümü kaldırma betiği kaldırır.</span><span class="sxs-lookup"><span data-stu-id="311d0-146">Uninstall-Script will remove the current version of a script when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="311d0-147">Belirtilen ve ön sürüm - RequiredVersion, - AllowPrerelease komutu eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="311d0-147">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

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

## <a name="more-details"></a><span data-ttu-id="311d0-148">Daha fazla ayrıntı</span><span class="sxs-lookup"><span data-stu-id="311d0-148">More details</span></span>

- [<span data-ttu-id="311d0-149">Yayın öncesi modül sürümleri</span><span class="sxs-lookup"><span data-stu-id="311d0-149">Prerelease Module Versions</span></span>](module-prerelease-support.md)
- [<span data-ttu-id="311d0-150">Bulma komut dosyası</span><span class="sxs-lookup"><span data-stu-id="311d0-150">Find-script</span></span>](/powershell/module/powershellget/find-script)
- [<span data-ttu-id="311d0-151">Yükleme betiği</span><span class="sxs-lookup"><span data-stu-id="311d0-151">Install-script</span></span>](/powershell/module/powershellget/install-script)
- [<span data-ttu-id="311d0-152">Save-script</span><span class="sxs-lookup"><span data-stu-id="311d0-152">Save-script</span></span>](/powershell/module/powershellget/save-script)
- [<span data-ttu-id="311d0-153">Güncelleştirme betiği</span><span class="sxs-lookup"><span data-stu-id="311d0-153">Update-script</span></span>](/powershell/module/powershellget/update-script)
- [<span data-ttu-id="311d0-154">Get-Installedscript</span><span class="sxs-lookup"><span data-stu-id="311d0-154">Get-Installedscript</span></span>](/powershell/module/powershellget/get-installedscript)
- [<span data-ttu-id="311d0-155">Kaldırma betiği</span><span class="sxs-lookup"><span data-stu-id="311d0-155">UnInstall-script</span></span>](/powershell/module/powershellget/uninstall-script)
