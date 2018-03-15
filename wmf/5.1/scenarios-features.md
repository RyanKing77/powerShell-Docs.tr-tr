---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: "Yeni senaryolar ve WMF 5.1 Özellikleri"
ms.openlocfilehash: da3dfb2243c00e3faf637d3dbcb70016cfabb011
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="new-scenarios-and-features-in-wmf-51"></a><span data-ttu-id="6968d-103">Yeni senaryolar ve WMF 5.1 Özellikleri</span><span class="sxs-lookup"><span data-stu-id="6968d-103">New Scenarios and Features in WMF 5.1</span></span> #

> <span data-ttu-id="6968d-104">Not: Bu bilgiler geçicidir ve değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6968d-104">Note: This information is preliminary and subject to change.</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="6968d-105">PowerShell Sürümleri</span><span class="sxs-lookup"><span data-stu-id="6968d-105">PowerShell Editions</span></span> ##
<span data-ttu-id="6968d-106">Sürüm 5.1’den başlayarak, PowerShell çeşitli özellik kümelerini ve platform uyumluluğunu belirten farklı sürümler halinde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6968d-106">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="6968d-107">**Masaüstü Sürümü:** .NET Framework üzerine yapılandırılmıştır ve Windows’un Sunucu Çekirdeği ve Windows Masaüstü gibi tam boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="6968d-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="6968d-108">**Çekirdek Sürümü:** .NET Core üzerine yapılandırılmıştır ve Windows’un Nano Sunucu ve Windows IoT gibi azaltılmış boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="6968d-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="6968d-109">**PowerShell sürümleri kullanma hakkında daha fazla bilgi edinin**</span><span class="sxs-lookup"><span data-stu-id="6968d-109">**Learn more about using PowerShell Editions**</span></span>
- [<span data-ttu-id="6968d-110">PowerShell çalışan sürümünü belirleme</span><span class="sxs-lookup"><span data-stu-id="6968d-110">Determine running edition of PowerShell</span></span>]()
- [<span data-ttu-id="6968d-111">Bir modülün uyumluluk belirli PowerShell sürümleri için bildirme</span><span class="sxs-lookup"><span data-stu-id="6968d-111">Declare a module's compatibility to specific PowerShell versions</span></span>]()
- [<span data-ttu-id="6968d-112">Get-Module sonuçları CompatiblePSEditions göre filtrele</span><span class="sxs-lookup"><span data-stu-id="6968d-112">Filter Get-Module results by CompatiblePSEditions</span></span>]()
- [<span data-ttu-id="6968d-113">Betik yürütme uyumlu bir PowerShell sürümünde çalıştırmadığınız sürece engelle</span><span class="sxs-lookup"><span data-stu-id="6968d-113">Prevent script execution unless run on a compatible edition of PowerShell</span></span>]()

## <a name="catalog-cmdlets"></a><span data-ttu-id="6968d-114">Katalog cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="6968d-114">Catalog Cmdlets</span></span>  

<span data-ttu-id="6968d-115">İçinde iki yeni cmdlet'ler eklenmiştir [Microsoft.PowerShell.Security](https://technet.microsoft.com/library/hh847877.aspx) modülü; bunlar oluşturmak ve Windows Katalog dosyaları doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="6968d-115">Two new cmdlets have been added in the [Microsoft.PowerShell.Security](https://technet.microsoft.com/library/hh847877.aspx) module; these generate and validate Windows catalog files.</span></span>  

###<a name="new-filecatalog"></a><span data-ttu-id="6968d-116">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="6968d-116">New-FileCatalog</span></span> 
--------------------------------

<span data-ttu-id="6968d-117">FileCatalog yeni dosya ve klasörleri kümesi için bir Windows katalog dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6968d-117">New-FileCatalog creates a Windows catalog file for set of folders and files.</span></span> <span data-ttu-id="6968d-118">Bu katalog dosyası belirtilen yolda tüm dosyalar için karmaları içerir.</span><span class="sxs-lookup"><span data-stu-id="6968d-118">This catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="6968d-119">Kullanıcılar bu klasörleri temsil eden karşılık gelen katalog dosyası ile birlikte klasörler kümesi dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6968d-119">Users can distribute the set of folders along with corresponding catalog file representing those folders.</span></span> <span data-ttu-id="6968d-120">Bu bilgiler, tüm klasörler için katalog oluşturma işleminden yapılan değişiklikler olup olmadığını doğrulamak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="6968d-120">This information is useful to validate whether any changes have been made to the folders since catalog creation time.</span></span>    

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="6968d-121">Katalog sürüm 1 ve 2 desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6968d-121">Catalog versions 1 and 2 are supported.</span></span> <span data-ttu-id="6968d-122">Sürüm 1 dosya karmaları oluşturmak için SHA1 karma algoritmasını kullanır; sürüm 2 SHA256 kullanır.</span><span class="sxs-lookup"><span data-stu-id="6968d-122">Version 1 uses the SHA1 hashing algorithm to create file hashes; version 2 uses SHA256.</span></span> <span data-ttu-id="6968d-123">Katalog sürüm 2 desteklenmiyor *Windows Server 2008 R2* veya *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="6968d-123">Catalog version 2 is not supported on *Windows Server 2008 R2* or *Windows 7*.</span></span> <span data-ttu-id="6968d-124">Katalog sürüm 2 kullanması gereken *Windows 8*, *Windows Server 2012*ve sonraki işletim sistemleri.</span><span class="sxs-lookup"><span data-stu-id="6968d-124">You should use catalog version 2 on *Windows 8*, *Windows Server 2012*, and later operating systems.</span></span>  

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="6968d-125">Bu, katalog dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6968d-125">This creates the catalog file.</span></span> 

![](../images/CatalogFile1.jpg)  

![](../images/CatalogFile2.jpg) 

<span data-ttu-id="6968d-126">Katalog dosyası (yukarıdaki örnekte, Pester.cat) bütünlüğünü doğrulamak için kullanarak oturum [kümesi AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="6968d-126">To verify the integrity of catalog file (Pester.cat in above example), sign it using [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>   


###<a name="test-filecatalog"></a><span data-ttu-id="6968d-127">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="6968d-127">Test-FileCatalog</span></span> 
--------------------------------

<span data-ttu-id="6968d-128">Test FileCatalog klasörleri kümesini temsil eden katalog doğrular.</span><span class="sxs-lookup"><span data-stu-id="6968d-128">Test-FileCatalog validates the catalog representing a set of folders.</span></span> 

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="6968d-129">Bu cmdlet tüm dosyaları karmaları karşılaştırır ve bunların göreli yollar bulunan *katalog* bulunanlarla *disk*.</span><span class="sxs-lookup"><span data-stu-id="6968d-129">This cmdlet compares all the files hashes and their relative paths found in *catalog* with ones on *disk*.</span></span> <span data-ttu-id="6968d-130">Herhangi dosya karmaları ve yolları arasında uyuşmazlık algılarsa, durum olarak döndürür *ValidationFailed*.</span><span class="sxs-lookup"><span data-stu-id="6968d-130">If it detects any mismatch between file hashes and paths it returns the status as *ValidationFailed*.</span></span> <span data-ttu-id="6968d-131">Kullanıcılar, tüm bu bilgileri kullanarak alabilir *-ayrıntılı* parametresi.</span><span class="sxs-lookup"><span data-stu-id="6968d-131">Users can retrieve all this information by using the *-Detailed* parameter.</span></span> <span data-ttu-id="6968d-132">Ayrıca Kataloğu'nda imzalama durumunu görüntüler *imza* arama için eşdeğer olan özelliği [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) katalog dosyası cmdlet'ini.</span><span class="sxs-lookup"><span data-stu-id="6968d-132">It also displays signing status of catalog in *Signature* property which is equivalent to calling [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet on the catalog file.</span></span> <span data-ttu-id="6968d-133">Kullanıcılar ayrıca atlayabilirsiniz herhangi bir dosya doğrulama sırasında kullanarak *- FilesToSkip* parametresi.</span><span class="sxs-lookup"><span data-stu-id="6968d-133">Users can also skip any file during validation by using the *-FilesToSkip* parameter.</span></span> 


## <a name="module-analysis-cache"></a><span data-ttu-id="6968d-134">Modül analiz önbelleği</span><span class="sxs-lookup"><span data-stu-id="6968d-134">Module Analysis Cache</span></span> ##
<span data-ttu-id="6968d-135">WMF 5.1 ile başlayarak, PowerShell bunu aktarır komutları gibi bir modülüyle ilgili verileri önbelleğe kullanılan dosya üzerinde denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="6968d-135">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="6968d-136">Varsayılan olarak, bu önbellek dosyasında depolanan `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="6968d-136">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="6968d-137">Önbellek başlangıçta komutu için aranırken genelde okur ve bir modülü içeri aktarıldıktan sonra arka plan iş parçacığında süre yazılır.</span><span class="sxs-lookup"><span data-stu-id="6968d-137">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="6968d-138">Önbelleğinin varsayılan konumu değiştirmek için ayarlayın `$env:PSModuleAnalysisCachePath` PowerShell başlatmadan önce ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="6968d-138">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="6968d-139">Bu ortam değişkenini yapılan değişiklikler yalnızca alt işlemleri etkiler.</span><span class="sxs-lookup"><span data-stu-id="6968d-139">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="6968d-140">Değeri PowerShell dosya oluşturma ve yazma izni olan bir tam yol (içeren dosya adı) adı.</span><span class="sxs-lookup"><span data-stu-id="6968d-140">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="6968d-141">Dosya önbelleği devre dışı bırakmak için geçersiz bir konum için bu değeri örneğin ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="6968d-141">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="6968d-142">Bu, geçersiz bir aygıta yolunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6968d-142">This sets the path to an invalid device.</span></span> <span data-ttu-id="6968d-143">PowerShell yolunu yazılamıyor, herhangi bir hata döndürdü, ancak hata bir izleyici kullanarak raporlama görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6968d-143">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="6968d-144">Önbelleği yazarken, PowerShell düşükse bir önbellek önlemek için artık mevcut modülleri için kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="6968d-144">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span>
<span data-ttu-id="6968d-145">Bazen bu denetimler, bu durumda, bunları ayarlayarak kapatabilirsiniz, istenmez:</span><span class="sxs-lookup"><span data-stu-id="6968d-145">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="6968d-146">Bu ortam değişkenini ayarı hemen geçerli işlemde etkinleşir.</span><span class="sxs-lookup"><span data-stu-id="6968d-146">Setting this environment variable will take effect immediately in the current process.</span></span>

##<a name="specifying-module-version"></a><span data-ttu-id="6968d-147">Modül sürümü belirtme</span><span class="sxs-lookup"><span data-stu-id="6968d-147">Specifying module version</span></span>

<span data-ttu-id="6968d-148">WMF 5.1 içinde `using module` diğer ilgili modülü kurulumlarını PowerShell'de aynı şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="6968d-148">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span> <span data-ttu-id="6968d-149">Daha önce belirli modülü sürüm belirtmek için hiçbir yolu yoktu; Mevcut birden çok sürüm varsa, bu hatayla sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="6968d-149">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>


<span data-ttu-id="6968d-150">WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="6968d-150">In WMF 5.1:</span></span>

* <span data-ttu-id="6968d-151">Kullanabileceğiniz [ModuleSpecification Oluşturucusu (karma)](https://msdn.microsoft.com/library/jj136290).</span><span class="sxs-lookup"><span data-stu-id="6968d-151">You can use [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290).</span></span> <span data-ttu-id="6968d-152">Bu karma tablosu ile aynı biçimi sahip `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="6968d-152">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

<span data-ttu-id="6968d-153">**Örnek:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="6968d-153">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

* <span data-ttu-id="6968d-154">Birden çok modül sürümü varsa, PowerShell kullanan **aynı çözümleme mantığı** olarak `Import-Module` ve bir hata oluştu--aynı davranışı dönmez `Import-Module` ve `Import-DscResource`.</span><span class="sxs-lookup"><span data-stu-id="6968d-154">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>


##<a name="improvements-to-pester"></a><span data-ttu-id="6968d-155">Pester geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="6968d-155">Improvements to Pester</span></span>
<span data-ttu-id="6968d-156">WMF 5.1, PowerShell ile birlikte gelen Pester sürümü 3.3.5 tamamlama eklenmesi ile 3.4.0 güncelleştirildi https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, hangi etkinleştirir daha iyi davranış Nano Server üzerinde Pester için.</span><span class="sxs-lookup"><span data-stu-id="6968d-156">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0, with the addition of commit https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, which enables better behavior for Pester on Nano Server.</span></span> 

<span data-ttu-id="6968d-157">ChangeLog.md dosyasını inceleyerek sürümleri için 3.3.5 3.4.0 değişiklikleri gözden geçirebilirsiniz: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span><span class="sxs-lookup"><span data-stu-id="6968d-157">You can review the changes in versions 3.3.5 to 3.4.0 by inspecting the ChangeLog.md file at: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span></span>

