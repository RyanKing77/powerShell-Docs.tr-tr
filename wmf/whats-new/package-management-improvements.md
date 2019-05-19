---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1, paket yönetimi geliştirmeleri
ms.openlocfilehash: 24ff05d6bf5993826106f1a1d2cee6dad363d1e2
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856164"
---
# <a name="improvements-to-package-management-in-wmf-51"></a><span data-ttu-id="63bc4-103">WMF 5.1, paket yönetimi geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="63bc4-103">Improvements to Package Management in WMF 5.1</span></span>

<span data-ttu-id="63bc4-104">WMF 5.1 yapılan düzeltmeler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="63bc4-104">The following are the fixes made in the WMF 5.1:</span></span>

## <a name="version-alias"></a><span data-ttu-id="63bc4-105">Sürüm diğer adı</span><span class="sxs-lookup"><span data-stu-id="63bc4-105">Version Alias</span></span>

<span data-ttu-id="63bc4-106">**Senaryo**: Sürüm 1.0 ve 2.0, sisteminizde yüklü bir paketin olan, P1, sahip olduğunuz ve sürüm 1.0 kaldırmak istediğinizi, çalıştırırsınız `Uninstall-Package -Name P1 -Version 1.0` ve sürüm 1.0 cmdlet'ini çalıştırdıktan sonra kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="63bc4-106">**Scenario**: If you have version 1.0 and 2.0 of a package, P1, installed on your system, and you want to uninstall version 1.0, you would run `Uninstall-Package -Name P1 -Version 1.0` and expect version 1.0 to be uninstalled after running the cmdlet.</span></span> <span data-ttu-id="63bc4-107">Bununla birlikte, sürüm 2.0 sonucudur kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="63bc4-107">However the result is that version 2.0 gets uninstalled.</span></span>

<span data-ttu-id="63bc4-108">Bu durum oluşur `-Version` parametresi, bir diğer adını `-MinimumVersion` parametresi.</span><span class="sxs-lookup"><span data-stu-id="63bc4-108">This occurs because the `-Version` parameter is an alias of the `-MinimumVersion` parameter.</span></span> <span data-ttu-id="63bc4-109">En düşük sürümü 1.0 olan tam bir paket için PackageManagement bakıldığında, en son sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="63bc4-109">When PackageManagement is looking for a qualified package with the minimum version of 1.0, it returns the latest version.</span></span> <span data-ttu-id="63bc4-110">Bu normal durumlarda en son sürümü genellikle istenen sonucu olduğunu bulmak için beklenen bir davranıştır.</span><span class="sxs-lookup"><span data-stu-id="63bc4-110">This behavior is expected in normal cases because finding the latest version is usually the desired result.</span></span> <span data-ttu-id="63bc4-111">Bununla birlikte, uygulanması gereken değil `Uninstall-Package` çalışması.</span><span class="sxs-lookup"><span data-stu-id="63bc4-111">However, it should not apply to the `Uninstall-Package` case.</span></span>

<span data-ttu-id="63bc4-112">**Çözüm**: kaldırıldı `-Version` diğer tamamen PackageManagement (yani)</span><span class="sxs-lookup"><span data-stu-id="63bc4-112">**Solution**:removed `-Version` alias entirely in PackageManagement (a.k.a.</span></span> <span data-ttu-id="63bc4-113">OneGet) ve PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="63bc4-113">OneGet) and PowerShellGet.</span></span>

## <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a><span data-ttu-id="63bc4-114">NuGet sağlayıcısı önyükleme için birden çok istemleri</span><span class="sxs-lookup"><span data-stu-id="63bc4-114">Multiple prompts for bootstrapping the NuGet provider</span></span>

<span data-ttu-id="63bc4-115">**Senaryo**: Çalıştırdığınızda `Find-Module` veya `Install-Module` veya diğer PackageManagement cmdlet'leri bilgisayarınızda ilk kez, PackageManagement NuGet sağlayıcısı bootstrap dener.</span><span class="sxs-lookup"><span data-stu-id="63bc4-115">**Scenario**: When you run `Find-Module` or `Install-Module` or other PackageManagement cmdlets on your computer for the first time, PackageManagement tries to bootstrap the NuGet provider.</span></span> <span data-ttu-id="63bc4-116">PowerShellGet sağlayıcı NuGet sağlayıcısı ayrıca PowerShell modüllerini yüklemek için kullandığı için bunu yapar.</span><span class="sxs-lookup"><span data-stu-id="63bc4-116">It does this because the PowerShellGet provider also uses the NuGet provider to download PowerShell modules.</span></span>
<span data-ttu-id="63bc4-117">PackageManagement daha sonra kullanıcı NuGet sağlayıcısını yüklemek izin ister.</span><span class="sxs-lookup"><span data-stu-id="63bc4-117">PackageManagement then prompts the user for permission to install the NuGet provider.</span></span> <span data-ttu-id="63bc4-118">Kullanıcı önyüklemesi için "Evet" seçtikten sonra NuGet sağlayıcısı en son sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="63bc4-118">After the user selects "yes" for the bootstrapping, the latest version of the NuGet provider will be installed.</span></span>

<span data-ttu-id="63bc4-119">NuGet sağlayıcısı, bilgisayarınızda yüklü eski bir sürümü varsa, ancak bazı durumlarda, eski NuGet bazen ilk (yani PackageManagement yarış durumu) PowerShell oturumuna versiyonu.</span><span class="sxs-lookup"><span data-stu-id="63bc4-119">However, in some cases, when you have an old version of NuGet provider installed on your computer, the older version of NuGet sometimes gets loaded first into the PowerShell session (that's the race condition in PackageManagement).</span></span> <span data-ttu-id="63bc4-120">Ancak, PowerShellGet NuGet sağlayıcısı yeniden önyükleme PackageManagement bu nedenle PowerShellGet çalışmak için NuGet Sağlayıcısı'nın sonraki bir sürümünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="63bc4-120">However PowerShellGet requires the later version of the NuGet provider to work, so PowerShellGet asks PackageManagement to bootstrap the NuGet provider again.</span></span>
<span data-ttu-id="63bc4-121">NuGet sağlayıcısı önyükleme için birden çok istemleri sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="63bc4-121">This results in multiple prompts for bootstrapping the NuGet provider.</span></span>

<span data-ttu-id="63bc4-122">**Çözüm**: WMF5.1 PackageManagement NuGet sağlayıcısı önyükleme için birden çok komut istemlerini önlemek için NuGet sağlayıcısı en son sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="63bc4-122">**Solution**: In WMF5.1, PackageManagement loads the latest version of the NuGet provider to avoid multiple prompts for bootstrapping the NuGet provider.</span></span>

<span data-ttu-id="63bc4-123">Bu sorunu da çalışabilir, NuGet sağlayıcısı (NuGet Anycpu.exe) eski sürümü el ile silerek sorunu var. $env: ProgramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies</span><span class="sxs-lookup"><span data-stu-id="63bc4-123">You could also work around this issue by manually deleting the old version of the NuGet provider (NuGet-Anycpu.exe) if exists from $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies</span></span>

## <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a><span data-ttu-id="63bc4-124">PackageManagement desteği yalnızca Intranet erişimi olan bilgisayarlara</span><span class="sxs-lookup"><span data-stu-id="63bc4-124">Support for PackageManagement on computers with Intranet access only</span></span>

<span data-ttu-id="63bc4-125">**Senaryo**: Kurumsal senaryo için kişinin çalıştığı bir ortamda olduğunda hiçbir Internet erişimi ancak Intranet yalnızca.</span><span class="sxs-lookup"><span data-stu-id="63bc4-125">**Scenario**: For the enterprise scenario, people are working under an environment where there is no Internet access but Intranet only.</span></span> <span data-ttu-id="63bc4-126">PackageManagement WMF 5.0 Bu durumda desteklememektedir.</span><span class="sxs-lookup"><span data-stu-id="63bc4-126">PackageManagement did not support this case in WMF 5.0.</span></span>

<span data-ttu-id="63bc4-127">**Senaryo**: WMF 5. 0'da, yalnızca Intranet (ancak Internet değil) olan bilgisayarları PackageManagement desteklememektedir erişim.</span><span class="sxs-lookup"><span data-stu-id="63bc4-127">**Scenario**: In WMF 5.0, PackageManagement did not support computers that have only Intranet (but not Internet) access.</span></span>

<span data-ttu-id="63bc4-128">**Çözüm**: WMF 5.1, Intranet bilgisayarların, PackageManagement kullanmasına izin vermek için aşağıdaki adımları izleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="63bc4-128">**Solution**: In WMF 5.1, you can follow these steps to allow Intranet computers to use PackageManagement:</span></span>

1. <span data-ttu-id="63bc4-129">Kullanarak bir Internet bağlantısı olan başka bir bilgisayar kullanarak NuGet sağlayıcısını indir `Install-PackageProvider -Name NuGet`.</span><span class="sxs-lookup"><span data-stu-id="63bc4-129">Download the NuGet provider using another computer that has an Internet connection by using `Install-PackageProvider -Name NuGet`.</span></span>

2. <span data-ttu-id="63bc4-130">NuGet sağlayıcısı ya da altında bulma `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` veya `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.</span><span class="sxs-lookup"><span data-stu-id="63bc4-130">Find the NuGet provider under either `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` or `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.</span></span>

3. <span data-ttu-id="63bc4-131">İkili dosyaları, Intranet bilgisayar erişmek ve NuGet sağlayıcıyla yüklemeyi bir klasör veya ağ paylaşımı konumu kopyalayın `Install-PackageProvider -Name NuGet -Source <Path to folder>`.</span><span class="sxs-lookup"><span data-stu-id="63bc4-131">Copy the binaries to a folder or network share location that the Intranet computer can access, and then install the NuGet provider with `Install-PackageProvider -Name NuGet -Source <Path to folder>`.</span></span>


## <a name="event-logging-improvements"></a><span data-ttu-id="63bc4-132">Olay günlüğü geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="63bc4-132">Event logging improvements</span></span>

<span data-ttu-id="63bc4-133">Paketleri yükleme sırasında bilgisayarın durumunu değiştirmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="63bc4-133">When you install packages, you are changing the state of the computer.</span></span> <span data-ttu-id="63bc4-134">WMF 5.1, PackageManagement artık olayları için Windows olay günlüğüne kaydeder `Install-Package`, `Uninstall-Package`, ve `Save-Package` etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="63bc4-134">In WMF 5.1, PackageManagement now logs events to the Windows event log for `Install-Package`, `Uninstall-Package`, and `Save-Package` activities.</span></span> <span data-ttu-id="63bc4-135">Olay günlüğü PowerShell, diğer bir deyişle, aynıdır `Microsoft-Windows-PowerShell, Operational`.</span><span class="sxs-lookup"><span data-stu-id="63bc4-135">The Event log is the same as for PowerShell, that is, `Microsoft-Windows-PowerShell, Operational`.</span></span>

## <a name="support-for-basic-authentication"></a><span data-ttu-id="63bc4-136">Temel kimlik doğrulaması için destek</span><span class="sxs-lookup"><span data-stu-id="63bc4-136">Support for basic authentication</span></span>

<span data-ttu-id="63bc4-137">WMF 5.1, bulma ve temel kimlik doğrulaması gerektiren bir depodaki paketlerini yükleme PackageManagement destekler.</span><span class="sxs-lookup"><span data-stu-id="63bc4-137">In WMF 5.1, PackageManagement supports finding and installing packages from a repository that requires basic authentication.</span></span> <span data-ttu-id="63bc4-138">Kimlik bilgilerinizle sağladığınız `Find-Package` ve `Install-Package` cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="63bc4-138">You can supply your credentials to the `Find-Package` and `Install-Package` cmdlets.</span></span> <span data-ttu-id="63bc4-139">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="63bc4-139">For example:</span></span>

```powershell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```

## <a name="support-for-using-packagemanagement-behind-a-proxy"></a><span data-ttu-id="63bc4-140">Bir proxy'nin arkasındayken PackageManagement kullanma desteği</span><span class="sxs-lookup"><span data-stu-id="63bc4-140">Support for using PackageManagement behind a proxy</span></span>

<span data-ttu-id="63bc4-141">WMF 5.1, PackageManagement artık yeni proxy parametre almayan `-ProxyCredential` ve `-Proxy`.</span><span class="sxs-lookup"><span data-stu-id="63bc4-141">In WMF 5.1, PackageManagement now takes new proxy parameters `-ProxyCredential` and `-Proxy`.</span></span> <span data-ttu-id="63bc4-142">Bu parametreleri kullanarak, PackageManagement cmdlet'leri için kimlik bilgilerini ve proxy URL'si belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63bc4-142">Using these parameters, you can specify the proxy URL and credentials to PackageManagement cmdlets.</span></span> <span data-ttu-id="63bc4-143">Varsayılan olarak, sistem proxy ayarlarını kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63bc4-143">By default, system proxy settings are used.</span></span> <span data-ttu-id="63bc4-144">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="63bc4-144">For example:</span></span>

```powershell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```
