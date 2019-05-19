---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.x sürüm notları
ms.openlocfilehash: 8bdc423234cf0b104b72b1bee1de35e50783d8a4
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856402"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a><span data-ttu-id="d5a33-103">Windows Management Framework (WMF) 5.x sürüm notları</span><span class="sxs-lookup"><span data-stu-id="d5a33-103">Windows Management Framework (WMF) 5.x Release Notes</span></span>

## <a name="wmf-50-changes"></a><span data-ttu-id="d5a33-104">WMF 5.0 değiştirir</span><span class="sxs-lookup"><span data-stu-id="d5a33-104">WMF 5.0 Changes</span></span>

- <span data-ttu-id="d5a33-105">PowerShell 5.0 ekler yeni yapılandırılmış **bilgi** akış</span><span class="sxs-lookup"><span data-stu-id="d5a33-105">PowerShell 5.0 adds a new structured **Information** stream</span></span>
- <span data-ttu-id="d5a33-106">Dört yeni DSC kaynakları dahil olmak üzere DSC geliştirmeleri:</span><span class="sxs-lookup"><span data-stu-id="d5a33-106">Improvements to DSC including four new DSC resources:</span></span>
  - <span data-ttu-id="d5a33-107">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="d5a33-107">WindowsFeatureSet</span></span>
  - <span data-ttu-id="d5a33-108">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="d5a33-108">WindowsOptionalFeatureSet</span></span>
  - <span data-ttu-id="d5a33-109">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="d5a33-109">ServiceSet</span></span>
  - <span data-ttu-id="d5a33-110">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="d5a33-110">ProcessSet</span></span>
- <span data-ttu-id="d5a33-111">Eklenen yeterli rol tabanlı yönetim üzerinden PowerShell uzaktan iletişimini etkinleştirmek için Yönetim</span><span class="sxs-lookup"><span data-stu-id="d5a33-111">Added Just Enough Administration to enable role-based administration through PowerShell remoting</span></span>
- <span data-ttu-id="d5a33-112">PowerShell 5.0 kullanıcı tanımlı sınıflar ve numaralandırmalar içerecek şekilde dili genişletir.</span><span class="sxs-lookup"><span data-stu-id="d5a33-112">PowerShell 5.0 extends the language to include user-defined classes and enumerations</span></span>
- <span data-ttu-id="d5a33-113">Gelişmiş hata ayıklama PowerShell ISE ve eklenen uzaktan hata ayıklama özellikleri</span><span class="sxs-lookup"><span data-stu-id="d5a33-113">Improved debugging features in PowerShell ISE and added remote debugging</span></span>
- <span data-ttu-id="d5a33-114">PowerShellGet ve PackageManagement modülleri eklendi</span><span class="sxs-lookup"><span data-stu-id="d5a33-114">Added the PowerShellGet and PackageManagement modules</span></span>
- <span data-ttu-id="d5a33-115">PowerShell betiğini Gelişmiş günlüğe kaydetme ve dökümleri</span><span class="sxs-lookup"><span data-stu-id="d5a33-115">Enhanced PowerShell script logging and transcripts</span></span>
- <span data-ttu-id="d5a33-116">Şifreli ileti söz dizimi cmdlet'leri eklendi</span><span class="sxs-lookup"><span data-stu-id="d5a33-116">Add Cryptographic Message Syntax cmdlets</span></span>
- <span data-ttu-id="d5a33-117">WMF 5.0 NetworkSwitchManager modülü için Windows içerir.</span><span class="sxs-lookup"><span data-stu-id="d5a33-117">WMF 5.0 includes the NetworkSwitchManager module for Windows</span></span>
- <span data-ttu-id="d5a33-118">Microsoft.PowerShell.ODataUtils modülü eklendi</span><span class="sxs-lookup"><span data-stu-id="d5a33-118">Added the Microsoft.PowerShell.ODataUtils module</span></span>
- <span data-ttu-id="d5a33-119">Yazılım envanteri günlüğü (SIL) için destek eklendi</span><span class="sxs-lookup"><span data-stu-id="d5a33-119">Added support for Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="d5a33-120">Yeni Sunucu veya kullanıcı talebi ve sorununa yanıt cmdlet'leri güncelleştir</span><span class="sxs-lookup"><span data-stu-id="d5a33-120">Sever new or update cmdlets in response to user requests and issues</span></span>

## <a name="wmf-51-changes"></a><span data-ttu-id="d5a33-121">WMF 5.1 değiştirir</span><span class="sxs-lookup"><span data-stu-id="d5a33-121">WMF 5.1 Changes</span></span>

<span data-ttu-id="d5a33-122">WMF 5.1, Windows Server 2016 ile yayımlanan PowerShell, WMI, WinRM ve yazılım envanteri günlüğü (SIL) bileşenleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d5a33-122">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span> <span data-ttu-id="d5a33-123">WMF 5.1 yüklenebilmesi için Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 ve 2012 R2 ve WMF 5.0 şu gibi çeşitli iyileştirmeler sağlar:</span><span class="sxs-lookup"><span data-stu-id="d5a33-123">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides several improvements over WMF 5.0 including:</span></span>

- <span data-ttu-id="d5a33-124">Yeni cmdlet'ler</span><span class="sxs-lookup"><span data-stu-id="d5a33-124">New cmdlets</span></span>
- <span data-ttu-id="d5a33-125">PowerShellGet iyileştirmeleri arasında imzalı modülleri zorlama ve JEA modülleri yükleme bulunur</span><span class="sxs-lookup"><span data-stu-id="d5a33-125">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="d5a33-126">PackageManagement; Kapsayıcılar, CBS Kurulumu, EXE temelli kurulum ve CAD paketleri için destek ekledi</span><span class="sxs-lookup"><span data-stu-id="d5a33-126">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="d5a33-127">DSC ve PowerShell sınıfları için hata ayıklama iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="d5a33-127">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="d5a33-128">PowerShellGet cmdlet’leri kullanırken Çekme Sunucusundan gelen katalog imzalı modülleri zorlamayı da içeren güvenlik iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="d5a33-128">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="d5a33-129">Birkaç kullanıcı talebi ve sorununa yanıt</span><span class="sxs-lookup"><span data-stu-id="d5a33-129">Responses to a number of user requests and issues</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="d5a33-130">PowerShell Sürümleri</span><span class="sxs-lookup"><span data-stu-id="d5a33-130">PowerShell Editions</span></span>

<span data-ttu-id="d5a33-131">5.1 sürümünden itibaren PowerShell çeşitli özellik kümelerini ve platform uyumluluğunu belirten farklı sürümlerinde kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="d5a33-131">Starting with version 5.1, PowerShell is available in different editions that denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="d5a33-132">**Masaüstü sürümü:** .NET Framework üzerine inşa edilmiş ve Windows Masaüstü ve Windows Server Core gibi tam boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5a33-132">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="d5a33-133">**Çekirdek sürümü:** .NET Core üzerine yapılandırılan ve Nano Server gibi Windows ve Windows IOT azaltılmış boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5a33-133">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="learn-more-about-using-powershell-editions"></a><span data-ttu-id="d5a33-134">PowerShell sürümleri kullanma hakkında daha fazla bilgi edinin</span><span class="sxs-lookup"><span data-stu-id="d5a33-134">Learn more about using PowerShell Editions</span></span>

- [<span data-ttu-id="d5a33-135">$PSVersionTable kullanarak PowerShell'in çalışan sürümü belirleme</span><span class="sxs-lookup"><span data-stu-id="d5a33-135">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="d5a33-136">Get-Module sonuçları PSEdition parametresini kullanarak CompatiblePSEditions göre filtrele</span><span class="sxs-lookup"><span data-stu-id="d5a33-136">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="d5a33-137">Betik yürütme uyumlu bir PowerShell sürümünde çalıştırmadıkça engelle</span><span class="sxs-lookup"><span data-stu-id="d5a33-137">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="d5a33-138">Belirli PowerShell sürümleri için bir modülün uyumluluk bildirme</span><span class="sxs-lookup"><span data-stu-id="d5a33-138">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a><span data-ttu-id="d5a33-139">Modül çözümleme önbellek</span><span class="sxs-lookup"><span data-stu-id="d5a33-139">Module Analysis Cache</span></span>

<span data-ttu-id="d5a33-140">WMF 5.1 ile başlayarak, PowerShell, bunu aktarır komutlar gibi bir modülle ilgili verileri önbelleğe almak için kullanılan dosya üzerinde denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5a33-140">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="d5a33-141">Varsayılan olarak, bu önbelleğin dosyasında depolanan `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="d5a33-141">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="d5a33-142">Önbellek başlatma sırasında bir komut için aranırken genellikle okuma ve bir modülü içeri aktardıktan sonra bir arka plan iş parçacığında süre yazılır.</span><span class="sxs-lookup"><span data-stu-id="d5a33-142">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="d5a33-143">Önbelleğinin varsayılan konumu değiştirmek için Ayarla `$env:PSModuleAnalysisCachePath` PowerShell başlatmadan önce ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="d5a33-143">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="d5a33-144">Bu ortam değişkeni yapılan değişiklikler, yalnızca alt işlemlerin etkiler.</span><span class="sxs-lookup"><span data-stu-id="d5a33-144">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="d5a33-145">Değeri, PowerShell oluşturun ve dosyalarını yazma iznine sahip bir tam yol (dosya adı dahil) adlandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5a33-145">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="d5a33-146">Dosya önbelleği devre dışı bırakmak için geçersiz bir konum için bu değeri örneğin ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="d5a33-146">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="d5a33-147">Bu, geçersiz bir cihaza yolunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d5a33-147">This sets the path to an invalid device.</span></span> <span data-ttu-id="d5a33-148">PowerShell yolu yazılamıyor, hata döndürülür, ancak hata raporlama bir izleyici kullanarak görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d5a33-148">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="d5a33-149">Önbelleği dışına yazılırken, PowerShell modülleri için artık gereksiz derecede büyük bir önbellek önlemek için mevcut kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="d5a33-149">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="d5a33-150">Bazen bu denetimler, bu durumda, bunları ayarlayarak kapatabilirsiniz, istenmez:</span><span class="sxs-lookup"><span data-stu-id="d5a33-150">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="d5a33-151">Bu ortam değişkenini ayarlayarak hemen geçerli işlemde etkili olur.</span><span class="sxs-lookup"><span data-stu-id="d5a33-151">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="d5a33-152">Modül sürümü belirtme</span><span class="sxs-lookup"><span data-stu-id="d5a33-152">Specifying module version</span></span>

<span data-ttu-id="d5a33-153">WMF 5.1 içinde `using module` PowerShell modülü ile ilgili diğer yapılarını aynı şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="d5a33-153">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="d5a33-154">Daha önce belirli bir modül sürümü belirtmek için imkanı yoktu; var olan birden çok sürüm varsa, bu hatayla sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="d5a33-154">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="d5a33-155">WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="d5a33-155">In WMF 5.1:</span></span>

- <span data-ttu-id="d5a33-156">Kullanabileceğiniz [ModuleSpecification Oluşturucusu (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="d5a33-156">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
  <span data-ttu-id="d5a33-157">Bu karma tablosu olarak aynı biçimde `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="d5a33-157">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

  <span data-ttu-id="d5a33-158">**Örnek:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="d5a33-158">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="d5a33-159">Birden çok modül sürümü varsa, PowerShell kullanan **aynı çözüm mantığı** olarak `Import-Module` ve bir hata--aynı davranışı döndürmüyor `Import-Module` ve `Import-DscResource`.</span><span class="sxs-lookup"><span data-stu-id="d5a33-159">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="d5a33-160">Pester geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="d5a33-160">Improvements to Pester</span></span>

<span data-ttu-id="d5a33-161">WMF 5.1 Pester PowerShell ile birlikte gelen sürümünü 3.4.0 için 3.3.5 güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="d5a33-161">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0.</span></span>
<span data-ttu-id="d5a33-162">Bu güncelleştirme, Nano Sunucu'da Pester için daha iyi davranışını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="d5a33-162">This update enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="d5a33-163">İnceleyerek Pest değişiklikleri gözden geçirebilirsiniz [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) GitHub deposunda.</span><span class="sxs-lookup"><span data-stu-id="d5a33-163">You can review the changes in Pest by inspecting the [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) in the GitHub repository.</span></span>
