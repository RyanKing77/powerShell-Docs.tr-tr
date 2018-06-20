---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: PowerShell Galerisi ile çalışmaya başlama
ms.openlocfilehash: 83974698152e75efac66ea725a9c220486676d6f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190171"
---
# <a name="get-started-with-the-powershell-gallery"></a><span data-ttu-id="35af7-103">PowerShell Galerisi ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="35af7-103">Get Started with the PowerShell Gallery</span></span>

<span data-ttu-id="35af7-104">Sisteminize PowerShell Galerisi'nden öğe indirme gerektirir [PowerShellGet](/powershell/module/powershellget) modülü.</span><span class="sxs-lookup"><span data-stu-id="35af7-104">Downloading items from the PowerShell Gallery to your system requires the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="35af7-105">Aşağıdakilerden birini PowerShellGet modülü bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35af7-105">You can find the PowerShellGet module in any of the following.</span></span> <span data-ttu-id="35af7-106">PowerShell Galerisi'nden öğe indirme oturum açmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="35af7-106">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

## <a name="discovering-items-from-the-powershell-gallery"></a><span data-ttu-id="35af7-107">PowerShell Galerisi'nden öğeleri bulma</span><span class="sxs-lookup"><span data-stu-id="35af7-107">Discovering items from the PowerShell Gallery</span></span>

<span data-ttu-id="35af7-108">PowerShell galerisinde öğelerini kullanarak bulabilirsiniz **arama** denetim bu Web sitesinde veya modüller ve komut dosyaları sayfalarıyla giderek.</span><span class="sxs-lookup"><span data-stu-id="35af7-108">You can find items in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="35af7-109">PowerShell Galerisi'nden öğe çalıştırarak bulabileceğiniz [bulma Modülü][] ve [bulma komut dosyası][] cmdlet'leri ile öğe türüne bağlı olarak, `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="35af7-109">You can also find items from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="35af7-110">Galeri sonuçlarını filtreleme, aşağıdaki parametreleri kullanarak gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="35af7-110">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="35af7-111">Ad</span><span class="sxs-lookup"><span data-stu-id="35af7-111">Name</span></span>
- <span data-ttu-id="35af7-112">AllVersions</span><span class="sxs-lookup"><span data-stu-id="35af7-112">AllVersions</span></span>
- <span data-ttu-id="35af7-113">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="35af7-113">MinimumVersion</span></span>
- <span data-ttu-id="35af7-114">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="35af7-114">RequiredVersion</span></span>
- <span data-ttu-id="35af7-115">Tag</span><span class="sxs-lookup"><span data-stu-id="35af7-115">Tag</span></span>
- <span data-ttu-id="35af7-116">İçerir</span><span class="sxs-lookup"><span data-stu-id="35af7-116">Includes</span></span>
- <span data-ttu-id="35af7-117">DscResource</span><span class="sxs-lookup"><span data-stu-id="35af7-117">DscResource</span></span>
- <span data-ttu-id="35af7-118">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="35af7-118">RoleCapability</span></span>
- <span data-ttu-id="35af7-119">Komut</span><span class="sxs-lookup"><span data-stu-id="35af7-119">Command</span></span>
- <span data-ttu-id="35af7-120">Filtre</span><span class="sxs-lookup"><span data-stu-id="35af7-120">Filter</span></span>

<span data-ttu-id="35af7-121">Yalnızca galerisinde belirli DSC kaynakları bulmak isterseniz, çalıştırabilirsiniz [Bul DscResource] cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="35af7-121">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="35af7-122">Bul DscResource DSC kaynakları galeride yer alan verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="35af7-122">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="35af7-123">DSC kaynakları her zaman bir modül bir parçası olarak teslim edildiğinden, hala çalıştırmanız gereken [yükleme-Module][] bu DSC kaynakları yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="35af7-123">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-items-in-the-powershell-gallery"></a><span data-ttu-id="35af7-124">PowerShell galerisinde öğeleri hakkında bilgi</span><span class="sxs-lookup"><span data-stu-id="35af7-124">Learning about items in the PowerShell Gallery</span></span>

<span data-ttu-id="35af7-125">İlgilendiğiniz öğeyi tanımladıktan sonra hakkında daha fazla bilgi edinmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35af7-125">Once you've identified an item you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="35af7-126">Bu öğeye ait belirli galeri sayfasında inceleyerek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35af7-126">You can do this by examining that item's specific page on the Gallery.</span></span> <span data-ttu-id="35af7-127">Bu sayfada tüm öğe ile karşıya meta verileri görmek mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="35af7-127">On that page, you'll be able to see all of the metadata uploaded with the item.</span></span> <span data-ttu-id="35af7-128">Bir öğe için bu meta veri öğesi'nin yazarı tarafından sağlanan ve Microsoft tarafından doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="35af7-128">This metadata for an item is provided by the item's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="35af7-129">Öğenin sahibi öğesini yayımlamak için kullanılan galeri hesabı kesinlikle bağlıdır ve yazar alanı daha güvenilirdir.</span><span class="sxs-lookup"><span data-stu-id="35af7-129">The Owner of the item is strongly tied to the Gallery account used to publish the item, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="35af7-130">Düşündüğünüz bir öğe iyi niyetli içinde yayımlanmamışsa bulursanız tıklatın **rapor kötüye** bu öğeye ait sayfasında.</span><span class="sxs-lookup"><span data-stu-id="35af7-130">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

<span data-ttu-id="35af7-131">Çalıştırıyorsanız [bulma Modülü][] veya [bulma komut dosyası][], döndürülen PSGetModuleInfo nesnesinde bu verilerini görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="35af7-131">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="35af7-132">Örneğin, çalışan `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` galerisinde PSReadLine modül verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="35af7-132">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-items-from-the-powershell-gallery"></a><span data-ttu-id="35af7-133">PowerShell Galerisi'nden öğe indirme</span><span class="sxs-lookup"><span data-stu-id="35af7-133">Downloading items from the PowerShell Gallery</span></span>

<span data-ttu-id="35af7-134">PowerShell Galerisi'nden öğe indirme sırasında şu işlem öneririz:</span><span class="sxs-lookup"><span data-stu-id="35af7-134">We encourage the following process when downloading items from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="35af7-135">İnceleyin.</span><span class="sxs-lookup"><span data-stu-id="35af7-135">Inspect</span></span>

<span data-ttu-id="35af7-136">İnceleme için Galeriden bir öğe indirmek için ya da çalıştırın [Kaydet-Module][] veya [Kaydet-komut dosyası][] cmdlet öğesi türüne bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="35af7-136">To download an item from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the item type.</span></span> <span data-ttu-id="35af7-137">Bu, yüklemeden öğeyi yerel olarak kaydedin ve öğenin içeriğini incelemek sağlar.</span><span class="sxs-lookup"><span data-stu-id="35af7-137">This lets you save the item locally without installing it, and inspect the item contents.</span></span> <span data-ttu-id="35af7-138">Kaydedilen öğeyi el ile silmek unutmayın.</span><span class="sxs-lookup"><span data-stu-id="35af7-138">Remember to delete the saved item manually.</span></span>

<span data-ttu-id="35af7-139">Bu öğelerin bazıları, Microsoft tarafından yazılan ve diğerleri PowerShell topluluğu tarafından yazılan.</span><span class="sxs-lookup"><span data-stu-id="35af7-139">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="35af7-140">Microsoft, yüklemeden önce bu galeri öğeleri kodunu ve içeriğini gözden önerir.</span><span class="sxs-lookup"><span data-stu-id="35af7-140">Microsoft recommends that you review the contents and code of items on this gallery prior to installation.</span></span>

<span data-ttu-id="35af7-141">Düşündüğünüz bir öğe iyi niyetli içinde yayımlanmamışsa bulursanız tıklatın **rapor kötüye** bu öğeye ait sayfasında.</span><span class="sxs-lookup"><span data-stu-id="35af7-141">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

### <a name="install"></a><span data-ttu-id="35af7-142">Yükle</span><span class="sxs-lookup"><span data-stu-id="35af7-142">Install</span></span>

<span data-ttu-id="35af7-143">Kullanmak için Galeriden bir öğe yüklemek için ya da çalıştırın [yükleme-Module][] veya [yükleme betiği][] cmdlet öğesi türüne bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="35af7-143">To install an item from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the item type.</span></span>

<span data-ttu-id="35af7-144">[yükleme-Module][] modülünü yükler `$env:ProgramFiles\WindowsPowerShell\Modules` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="35af7-144">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="35af7-145">Bu yönetici hesabı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="35af7-145">This requires an administrator account.</span></span> <span data-ttu-id="35af7-146">Eklerseniz `-Scope CurrentUser` parametresi modülü için yüklüdür `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="35af7-146">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="35af7-147">[yükleme betiği][] komut dosyasına yükler `$env:ProgramFiles\WindowsPowerShell\Scripts` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="35af7-147">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="35af7-148">Bu yönetici hesabı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="35af7-148">This requires an administrator account.</span></span> <span data-ttu-id="35af7-149">Eklerseniz `-Scope CurrentUser` parametresi, komut dosyası için yüklendiğini `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="35af7-149">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="35af7-150">Varsayılan olarak, [yükleme-Module][] ve [yükleme betiği][] öğeyi en güncel sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="35af7-150">By default, [Install-Module][] and [Install-Script][] installs the most current version of an item.</span></span>
<span data-ttu-id="35af7-151">Öğe daha eski bir sürümü yüklemek için add `-RequiredVersion` parametresi.</span><span class="sxs-lookup"><span data-stu-id="35af7-151">To install an older version of the item, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="35af7-152">Dağıt</span><span class="sxs-lookup"><span data-stu-id="35af7-152">Deploy</span></span>

<span data-ttu-id="35af7-153">PowerShell Galerisi'nden bir öğe Azure Automation ile dağıtmak için **Azure Otomasyonu Dağıt** öğe Ayrıntıları sayfasında.</span><span class="sxs-lookup"><span data-stu-id="35af7-153">To deploy an item from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the item details page.</span></span> <span data-ttu-id="35af7-154">Burada Azure hesabı kimlik bilgilerinizi kullanarak oturum Azure yönetim portalına yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="35af7-154">You will be redirected to the Azure Management Portal, where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="35af7-155">Bağımlılıkları olan öğeleri dağıtmak için Azure Otomasyonu tüm bağımlılıkları dağıtması unutmayın.</span><span class="sxs-lookup"><span data-stu-id="35af7-155">Note that deploying items with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="35af7-156">'Azure Otomasyonu Dağıt' düğmesini ekleyerek devre dışı bırakılabilir **AzureAutomationNotSupported** öğe meta etiketi.</span><span class="sxs-lookup"><span data-stu-id="35af7-156">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your item metadata.</span></span>

<span data-ttu-id="35af7-157">Azure Otomasyonu hakkında daha fazla bilgi için bkz: [Azure Otomasyonu](/azure/automation) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="35af7-157">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-items-from-the-powershell-gallery"></a><span data-ttu-id="35af7-158">PowerShell Galerisi'nden öğeler güncelleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="35af7-158">Updating items from the PowerShell Gallery</span></span>

<span data-ttu-id="35af7-159">PowerShell Galerisi'nden yüklü öğeleri güncelleştirmek için [güncelleştirme-Module] [] veya [güncelleştirme betiğini] [] cmdlet'ini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="35af7-159">To update items installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="35af7-160">Ek parametreler çalıştırdığınızda [güncelleştirme-Module] [] çalıştırarak yüklü her modülü güncelleştirme girişiminde [yükleme-Module][].</span><span class="sxs-lookup"><span data-stu-id="35af7-160">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="35af7-161">Modülleri seçmeli olarak güncelleştirmek için ekleyin `-Name` parametresi.</span><span class="sxs-lookup"><span data-stu-id="35af7-161">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="35af7-162">Benzer şekilde, ek parametreler çalıştırdığınızda, [güncelleştirme betiğini] [] de her komut dosyası çalıştırarak yüklü güncelleştirme girişiminde [yükleme betiği][].</span><span class="sxs-lookup"><span data-stu-id="35af7-162">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="35af7-163">Komut dosyaları seçmeli olarak güncelleştirmek için ekleyin `-Name` parametresi.</span><span class="sxs-lookup"><span data-stu-id="35af7-163">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="35af7-164">PowerShell Galerisi'nden yüklediğiniz liste öğeleri</span><span class="sxs-lookup"><span data-stu-id="35af7-164">List items that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="35af7-165">PowerShell Galerisi'nden yüklü modüllerine öğrenmek için Çalıştır [Get-InstalledModule][] cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="35af7-165">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="35af7-166">Bu komut tüm doğrudan PowerShell Galerisi'nden yüklenen sisteminizde yüklü modülleri listeler.</span><span class="sxs-lookup"><span data-stu-id="35af7-166">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="35af7-167">PowerShell Galerisi'nden yüklü hangi komut dosyaları bulmak için benzer şekilde, çalıştırmak [Get-InstalledScript][] cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="35af7-167">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="35af7-168">Bu komut doğrudan PowerShell Galerisi'nden yüklenen sisteminizde yüklü komut dosyalarının tümü listeler.</span><span class="sxs-lookup"><span data-stu-id="35af7-168">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

[Bul DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[bulma Modülü]: /powershell/module/powershellget/Find-Module
[Find-Module]: /powershell/module/powershellget/Find-Module
[bulma komut dosyası]: /powershell/module/powershellget/Find-Script
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[yükleme-Module]: /powershell/module/powershellget/Install-Module
[Install-Module]: /powershell/module/powershellget/Install-Module
[yükleme betiği]: /powershell/module/powershellget/Install-Script
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Kaydet-Module]: /powershell/module/powershellget/Save-Module
[Save-Module]: /powershell/module/powershellget/Save-Module
[Kaydet-komut dosyası]: /powershell/module/powershellget/Save-Script
[Save-Script]: /powershell/module/powershellget/Save-Script