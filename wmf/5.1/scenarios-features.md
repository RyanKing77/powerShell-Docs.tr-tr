---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Yeni senaryolar ve WMF 5.1 Özellikleri
ms.openlocfilehash: b00069aad7422f86d1462a62a6c4bc8a91e46705
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687002"
---
# <a name="new-scenarios-and-features-in-wmf-51"></a><span data-ttu-id="b7b5c-103">Yeni senaryolar ve WMF 5.1 Özellikleri</span><span class="sxs-lookup"><span data-stu-id="b7b5c-103">New Scenarios and Features in WMF 5.1</span></span>

> <span data-ttu-id="b7b5c-104">Not: Bu bilgiler geçicidir ve değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-104">Note: This information is preliminary and subject to change.</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="b7b5c-105">PowerShell Sürümleri</span><span class="sxs-lookup"><span data-stu-id="b7b5c-105">PowerShell Editions</span></span>

<span data-ttu-id="b7b5c-106">Sürüm 5.1’den başlayarak, PowerShell çeşitli özellik kümelerini ve platform uyumluluğunu belirten farklı sürümler halinde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-106">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="b7b5c-107">**Masaüstü sürümü:** .NET Framework üzerine inşa edilmiş ve Windows Masaüstü ve Windows Server Core gibi tam boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="b7b5c-108">**Çekirdek sürümü:** .NET Core üzerine yapılandırılan ve Nano Server gibi Windows ve Windows IOT azaltılmış boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="b7b5c-109">**PowerShell sürümleri kullanma hakkında daha fazla bilgi edinin**</span><span class="sxs-lookup"><span data-stu-id="b7b5c-109">**Learn more about using PowerShell Editions**</span></span>

- [<span data-ttu-id="b7b5c-110">$PSVersionTable kullanarak PowerShell'in çalışan sürümü belirleme</span><span class="sxs-lookup"><span data-stu-id="b7b5c-110">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="b7b5c-111">Get-Module sonuçları PSEdition parametresini kullanarak CompatiblePSEditions göre filtrele</span><span class="sxs-lookup"><span data-stu-id="b7b5c-111">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="b7b5c-112">Betik yürütme uyumlu bir PowerShell sürümünde çalıştırmadıkça engelle</span><span class="sxs-lookup"><span data-stu-id="b7b5c-112">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="b7b5c-113">Belirli PowerShell sürümleri için bir modülün uyumluluk bildirme</span><span class="sxs-lookup"><span data-stu-id="b7b5c-113">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/gallery/concepts/module-psedition-support)

## <a name="catalog-cmdlets"></a><span data-ttu-id="b7b5c-114">Katalog cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="b7b5c-114">Catalog Cmdlets</span></span>

<span data-ttu-id="b7b5c-115">İki yeni cmdlet eklendi [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) modülü; bunlar oluşturmak ve Windows Katalog dosyaları doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-115">Two new cmdlets have been added in the [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) module; these generate and validate Windows catalog files.</span></span>

### <a name="new-filecatalog"></a><span data-ttu-id="b7b5c-116">Yeni FileCatalog</span><span class="sxs-lookup"><span data-stu-id="b7b5c-116">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="b7b5c-117">FileCatalog yeni dosya ve klasörleri kümesi için bir Windows katalog dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-117">New-FileCatalog creates a Windows catalog file for set of folders and files.</span></span>
<span data-ttu-id="b7b5c-118">Bu katalog dosyası belirtilen yolda tüm dosyaların karmalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-118">This catalog file contains hashes for all files in specified paths.</span></span>
<span data-ttu-id="b7b5c-119">Kullanıcılar, bu klasörleri temsil eden karşılık gelen katalog dosyası ile birlikte klasör kümesi dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-119">Users can distribute the set of folders along with corresponding catalog file representing those folders.</span></span>
<span data-ttu-id="b7b5c-120">Bu bilgiler, katalog oluşturma zamandan bu yana herhangi bir değişiklik klasörlere değişiklikler olup olmadığını doğrulamak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-120">This information is useful to validate whether any changes have been made to the folders since catalog creation time.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="b7b5c-121">1. ve 2 kataloğu sürümleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-121">Catalog versions 1 and 2 are supported.</span></span>
<span data-ttu-id="b7b5c-122">Sürüm 1, dosya karmaları oluşturmak için SHA1 karma algoritmasını kullanır; sürüm 2 SHA256 kullanır.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-122">Version 1 uses the SHA1 hashing algorithm to create file hashes; version 2 uses SHA256.</span></span>
<span data-ttu-id="b7b5c-123">Katalog sürümü 2 üzerinde desteklenmiyor *Windows Server 2008 R2* veya *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-123">Catalog version 2 is not supported on *Windows Server 2008 R2* or *Windows 7*.</span></span>
<span data-ttu-id="b7b5c-124">Katalog sürümü 2 kullanması gereken *Windows 8*, *Windows Server 2012*ve sonraki işletim sistemleri.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-124">You should use catalog version 2 on *Windows 8*, *Windows Server 2012*, and later operating systems.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="b7b5c-125">Bu, katalog dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-125">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="b7b5c-126">Katalog dosyası (yukarıdaki örnekte, Pester.cat) bütünlüğünü doğrulamak için onu kullanarak oturum [kümesi AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-126">To verify the integrity of catalog file (Pester.cat in above example), sign it using [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) cmdlet.</span></span>

### <a name="test-filecatalog"></a><span data-ttu-id="b7b5c-127">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="b7b5c-127">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="b7b5c-128">Test-FileCatalog klasörleri kümesini temsil eden Kataloğu doğrular.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-128">Test-FileCatalog validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="b7b5c-129">Bu cmdlet tüm dosyaların karma değerlerini karşılaştırır ve bunların göreli yollar bulunan *Kataloğu* bulunanlarla *disk*.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-129">This cmdlet compares all the files hashes and their relative paths found in *catalog* with ones on *disk*.</span></span>
<span data-ttu-id="b7b5c-130">Dosya karmalarını ve yolları arasında herhangi bir uyuşmazlık algılarsa durumu olarak döndürür. *ValidationFailed*.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-130">If it detects any mismatch between file hashes and paths it returns the status as *ValidationFailed*.</span></span>
<span data-ttu-id="b7b5c-131">Kullanıcılar, tüm bu bilgileri kullanarak alabilir *-ayrıntılı* parametresi.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-131">Users can retrieve all this information by using the *-Detailed* parameter.</span></span>
<span data-ttu-id="b7b5c-132">Ayrıca Kataloğu'nda imzalama durumu görüntüler *imza* çağırmakla eşdeğerdir özelliği [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) cmdlet'i katalog dosyası üzerinde.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-132">It also displays signing status of catalog in *Signature* property which is equivalent to calling [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) cmdlet on the catalog file.</span></span>
<span data-ttu-id="b7b5c-133">Kullanıcılar ayrıca atlayabilirsiniz herhangi bir dosya doğrulama sırasında kullanarak *- FilesToSkip* parametresi.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-133">Users can also skip any file during validation by using the *-FilesToSkip* parameter.</span></span>

## <a name="module-analysis-cache"></a><span data-ttu-id="b7b5c-134">Modül çözümleme önbellek</span><span class="sxs-lookup"><span data-stu-id="b7b5c-134">Module Analysis Cache</span></span>

<span data-ttu-id="b7b5c-135">WMF 5.1 ile başlayarak, PowerShell, bunu aktarır komutlar gibi bir modülle ilgili verileri önbelleğe almak için kullanılan dosya üzerinde denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-135">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="b7b5c-136">Varsayılan olarak, bu önbelleğin dosyasında depolanan `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-136">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="b7b5c-137">Önbellek başlatma sırasında bir komut için aranırken genellikle okuma ve bir modülü içeri aktardıktan sonra bir arka plan iş parçacığında süre yazılır.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-137">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="b7b5c-138">Önbelleğinin varsayılan konumu değiştirmek için Ayarla `$env:PSModuleAnalysisCachePath` PowerShell başlatmadan önce ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-138">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span>
<span data-ttu-id="b7b5c-139">Bu ortam değişkeni yapılan değişiklikler, yalnızca alt işlemlerin etkiler.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-139">Changes to this environment variable will only affect children processes.</span></span>
<span data-ttu-id="b7b5c-140">Değeri, PowerShell oluşturun ve dosyalarını yazma iznine sahip bir tam yol (dosya adı dahil) adlandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-140">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span>
<span data-ttu-id="b7b5c-141">Dosya önbelleği devre dışı bırakmak için geçersiz bir konum için bu değeri örneğin ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="b7b5c-141">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="b7b5c-142">Bu, geçersiz bir cihaza yolunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-142">This sets the path to an invalid device.</span></span>
<span data-ttu-id="b7b5c-143">PowerShell yolu yazılamıyor, hata döndürülür, ancak hata raporlama bir izleyici kullanarak görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b7b5c-143">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="b7b5c-144">Önbelleği dışına yazılırken, PowerShell modülleri için artık gereksiz derecede büyük bir önbellek önlemek için mevcut kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-144">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span>
<span data-ttu-id="b7b5c-145">Bazen bu denetimler, bu durumda, bunları ayarlayarak kapatabilirsiniz, istenmez:</span><span class="sxs-lookup"><span data-stu-id="b7b5c-145">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="b7b5c-146">Bu ortam değişkenini ayarlayarak hemen geçerli işlemde etkili olur.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-146">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="b7b5c-147">Modül sürümü belirtme</span><span class="sxs-lookup"><span data-stu-id="b7b5c-147">Specifying module version</span></span>

<span data-ttu-id="b7b5c-148">WMF 5.1 içinde `using module` PowerShell modülü ile ilgili diğer yapılarını aynı şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-148">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="b7b5c-149">Daha önce belirli bir modül sürümü belirtmek için imkanı yoktu; var olan birden çok sürüm varsa, bu hatayla sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-149">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="b7b5c-150">WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="b7b5c-150">In WMF 5.1:</span></span>

- <span data-ttu-id="b7b5c-151">Kullanabileceğiniz [ModuleSpecification Oluşturucusu (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="b7b5c-151">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
<span data-ttu-id="b7b5c-152">Bu karma tablosu olarak aynı biçimde `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-152">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

<span data-ttu-id="b7b5c-153">**Örnek:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="b7b5c-153">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="b7b5c-154">Birden çok modül sürümü varsa, PowerShell kullanan **aynı çözüm mantığı** olarak `Import-Module` ve bir hata--aynı davranışı döndürmüyor `Import-Module` ve `Import-DscResource`.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-154">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="b7b5c-155">Pester geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="b7b5c-155">Improvements to Pester</span></span>

<span data-ttu-id="b7b5c-156">3.4.0, ek olarak, işleme için 3.3.5 Pester PowerShell ile birlikte gelen sürümünü güncelleştirildi WMF 5.1 https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, hangi etkinleştirir daha iyi davranışı Pester Nano Sunucu'da için.</span><span class="sxs-lookup"><span data-stu-id="b7b5c-156">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0, with the addition of commit https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, which enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="b7b5c-157">ChangeLog.md dosyasını inceleyerek 3.3.5 için 3.4.0 sürümlerindeki değişikliklere göz atabilirsiniz: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span><span class="sxs-lookup"><span data-stu-id="b7b5c-157">You can review the changes in versions 3.3.5 to 3.4.0 by inspecting the ChangeLog.md file at: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span></span>
