---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: PowerShell Galerisi ile çalışmaya başlama
ms.openlocfilehash: 39998df1a2bf9363dd008dc96a802157c8d691d7
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523068"
---
# <a name="get-started-with-the-powershell-gallery"></a><span data-ttu-id="bd8a4-103">PowerShell Galerisi ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="bd8a4-103">Get Started with the PowerShell Gallery</span></span>

<span data-ttu-id="bd8a4-104">Öğeleri PowerShell Galerisi'nden yüklemek için en uygun yolu cmdlet'ler kullanmaktır [PowerShellGet](/powershell/module/powershellget) modülü.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-104">The proper way to install items from the PowerShell Gallery is to use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="bd8a4-105">PowerShell Galerisi'nden öğeleri indirmek oturum açmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-105">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="bd8a4-106">Bir paket doğrudan PowerShell Galerisi'nden yüklemek mümkündür, ancak bu önerilen bir yaklaşım değildir.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-106">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span> <span data-ttu-id="bd8a4-107">Daha fazla ayrıntı için [el ile indirme paketi](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md).</span><span class="sxs-lookup"><span data-stu-id="bd8a4-107">For more details, see [Manual Package Download](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md).</span></span>  


## <a name="discovering-items-from-the-powershell-gallery"></a><span data-ttu-id="bd8a4-108">PowerShell Galerisi'nden öğeler bulunuyor</span><span class="sxs-lookup"><span data-stu-id="bd8a4-108">Discovering items from the PowerShell Gallery</span></span>

<span data-ttu-id="bd8a4-109">PowerShell galerisinde öğelerini kullanarak bulabilirsiniz **arama** bu Web sitesinde veya modülleri ve betikleri sayfalarıyla atarak denetimi.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-109">You can find items in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="bd8a4-110">Çalıştırarak PowerShell Galerisi'ndeki öğeleri bulabilirsiniz [Modül Bul][] ve [Bulma komut dosyası][] cmdlet'leri ile öğe türüne bağlı olarak, `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-110">You can also find items from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="bd8a4-111">Galeri sonuçlarını filtreleme, aşağıdaki parametreleri kullanarak gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="bd8a4-111">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="bd8a4-112">Ad</span><span class="sxs-lookup"><span data-stu-id="bd8a4-112">Name</span></span>
- <span data-ttu-id="bd8a4-113">AllVersions</span><span class="sxs-lookup"><span data-stu-id="bd8a4-113">AllVersions</span></span>
- <span data-ttu-id="bd8a4-114">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="bd8a4-114">MinimumVersion</span></span>
- <span data-ttu-id="bd8a4-115">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="bd8a4-115">RequiredVersion</span></span>
- <span data-ttu-id="bd8a4-116">Tag</span><span class="sxs-lookup"><span data-stu-id="bd8a4-116">Tag</span></span>
- <span data-ttu-id="bd8a4-117">İçerir</span><span class="sxs-lookup"><span data-stu-id="bd8a4-117">Includes</span></span>
- <span data-ttu-id="bd8a4-118">DscResource</span><span class="sxs-lookup"><span data-stu-id="bd8a4-118">DscResource</span></span>
- <span data-ttu-id="bd8a4-119">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="bd8a4-119">RoleCapability</span></span>
- <span data-ttu-id="bd8a4-120">Komut</span><span class="sxs-lookup"><span data-stu-id="bd8a4-120">Command</span></span>
- <span data-ttu-id="bd8a4-121">Filtre</span><span class="sxs-lookup"><span data-stu-id="bd8a4-121">Filter</span></span>

<span data-ttu-id="bd8a4-122">Yalnızca galerideki belirli DSC kaynakları keşfetme içinde ilginizi çeken, çalıştırabileceğiniz [Bul-DscResource] cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-122">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="bd8a4-123">Bul-DscResource galeride bulunan DSC kaynaklardaki verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-123">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="bd8a4-124">DSC kaynakları her zaman bir modülün bir parçası olarak teslim edildiğinden, çalıştırmanız yine [Install-Module][] bu DSC kaynakları yüklenecek.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-124">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-items-in-the-powershell-gallery"></a><span data-ttu-id="bd8a4-125">PowerShell galeride bulunan öğeler hakkında daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="bd8a4-125">Learning about items in the PowerShell Gallery</span></span>

<span data-ttu-id="bd8a4-126">İlgilendiğiniz öğeyi belirledikten sonra ilgili daha fazla bilgi edinmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-126">Once you've identified an item you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="bd8a4-127">Bu öğenin özel galeri sayfasında inceleyerek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-127">You can do this by examining that item's specific page on the Gallery.</span></span> <span data-ttu-id="bd8a4-128">Bu sayfada tüm öğeyle karşıya meta verileri görmek mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-128">On that page, you'll be able to see all of the metadata uploaded with the item.</span></span> <span data-ttu-id="bd8a4-129">Bu meta veriler için bir öğe öğenin yazarı tarafından sağlanan ve Microsoft tarafından doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-129">This metadata for an item is provided by the item's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="bd8a4-130">Öğenin sahibi kesin galeri öğesi yayımlamak için kullanılan hesaba bağlıdır ve yazar alanı daha güvenilirdir.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-130">The Owner of the item is strongly tied to the Gallery account used to publish the item, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="bd8a4-131">Sizin de böyle bir öğe inancıyla içinde yayımlanmamışsa keşfederseniz tıklayın **uygunsuz** bu öğeye ait sayfasında.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-131">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

<span data-ttu-id="bd8a4-132">Çalıştırıyorsanız [Modül Bul][] veya [Bulma komut dosyası][], döndürülen PSGetModuleInfo nesnesinde bu verileri görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-132">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="bd8a4-133">Örneğin, çalışan `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span><span class="sxs-lookup"><span data-stu-id="bd8a4-133">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="bd8a4-134">Galerideki PSReadLine modül verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-134">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-items-from-the-powershell-gallery"></a><span data-ttu-id="bd8a4-135">PowerShell Galerisi'nden öğe indirme</span><span class="sxs-lookup"><span data-stu-id="bd8a4-135">Downloading items from the PowerShell Gallery</span></span>

<span data-ttu-id="bd8a4-136">PowerShell Galerisi'nden öğe indirme işlemi gerçekleştirirken aşağıdaki işlem öneririz:</span><span class="sxs-lookup"><span data-stu-id="bd8a4-136">We encourage the following process when downloading items from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="bd8a4-137">İnceleme</span><span class="sxs-lookup"><span data-stu-id="bd8a4-137">Inspect</span></span>

<span data-ttu-id="bd8a4-138">Galeri denetimi için bir öğe indirmesine izin ya da çalıştırmak [Save-Module][] veya [Save-Script][] cmdlet'i, öğe türüne bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-138">To download an item from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the item type.</span></span> <span data-ttu-id="bd8a4-139">Bu, yüklemeden öğe yerel olarak kaydedin ve öğe içeriği İnceleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-139">This lets you save the item locally without installing it, and inspect the item contents.</span></span> <span data-ttu-id="bd8a4-140">Kaydedilen öğeyi el ile silmeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-140">Remember to delete the saved item manually.</span></span>

<span data-ttu-id="bd8a4-141">Bu öğelerin bazıları, Microsoft tarafından yazılmış ve diğer PowerShell topluluğu tarafından yazıldı.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-141">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="bd8a4-142">Microsoft, içeriği ve yüklemeden önce bu galeri öğeleri, kod gözden geçirme önerir.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-142">Microsoft recommends that you review the contents and code of items on this gallery prior to installation.</span></span>

<span data-ttu-id="bd8a4-143">Sizin de böyle bir öğe inancıyla içinde yayımlanmamışsa keşfederseniz tıklayın **uygunsuz** bu öğeye ait sayfasında.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-143">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

### <a name="install"></a><span data-ttu-id="bd8a4-144">Yükle</span><span class="sxs-lookup"><span data-stu-id="bd8a4-144">Install</span></span>

<span data-ttu-id="bd8a4-145">Galeri kullanmak için bir öğe yüklemek için ya da çalıştırmak [Install-Module][] veya [Yükleme betiği][] cmdlet'i, öğe türüne bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-145">To install an item from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the item type.</span></span>

<span data-ttu-id="bd8a4-146">[Install-Module][] modülünü yükler `$env:ProgramFiles\WindowsPowerShell\Modules` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-146">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="bd8a4-147">Bu, bir yönetici hesabı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-147">This requires an administrator account.</span></span> <span data-ttu-id="bd8a4-148">Eklerseniz `-Scope CurrentUser` parametresi modülünün yüklü için `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="bd8a4-148">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="bd8a4-149">[Yükleme betiği][] betiğe yükler `$env:ProgramFiles\WindowsPowerShell\Scripts` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-149">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="bd8a4-150">Bu, bir yönetici hesabı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-150">This requires an administrator account.</span></span> <span data-ttu-id="bd8a4-151">Eklerseniz `-Scope CurrentUser` parametresi, komut dosyası yüklü olduğu için `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="bd8a4-151">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="bd8a4-152">Varsayılan olarak, [Install-Module][] ve [Yükleme betiği][] öğenin en son sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-152">By default, [Install-Module][] and [Install-Script][] installs the most current version of an item.</span></span>
<span data-ttu-id="bd8a4-153">Öğesi daha eski bir sürümünü yüklemek için ekleme `-RequiredVersion` parametresi.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-153">To install an older version of the item, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="bd8a4-154">Dağıt</span><span class="sxs-lookup"><span data-stu-id="bd8a4-154">Deploy</span></span>

<span data-ttu-id="bd8a4-155">Azure Otomasyonu PowerShell Galerisi'ndeki bir öğeye dağıtmak için **Azure Otomasyonu Dağıt** öğe Ayrıntıları sayfasında.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-155">To deploy an item from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the item details page.</span></span> <span data-ttu-id="bd8a4-156">Burada Azure hesabı kimlik bilgilerinizi kullanarak oturum açtığınızda Azure yönetim portalına yönlendirilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-156">You will be redirected to the Azure Management Portal, where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="bd8a4-157">Bağımlılıkları olan öğeleri dağıtma tüm bağımlılıkları için Azure Otomasyonu dağıtacağınız olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-157">Note that deploying items with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="bd8a4-158">'Azure otomasyonu için Dağıt' düğmesini ekleyerek devre dışı bırakılabilir **AzureAutomationNotSupported** öğesi meta verileriniz için etiket.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-158">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your item metadata.</span></span>

<span data-ttu-id="bd8a4-159">Azure Otomasyonu hakkında daha fazla bilgi için bkz: [Azure Otomasyonu](/azure/automation) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-159">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-items-from-the-powershell-gallery"></a><span data-ttu-id="bd8a4-160">Öğeleri PowerShell Galerisi'ndeki güncelleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="bd8a4-160">Updating items from the PowerShell Gallery</span></span>

<span data-ttu-id="bd8a4-161">Yüklü PowerShell Galerisi'nden öğeleri güncelleştirmek için Update-Module [] veya [güncelleştirme betiğini] [] cmdlet'ini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-161">To update items installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="bd8a4-162">Update-Module [] herhangi ek bir parametre çalıştırdığınızda çalıştırarak yüklü her modülü güncelleştirme çalışır [Install-Module][].</span><span class="sxs-lookup"><span data-stu-id="bd8a4-162">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="bd8a4-163">Modüller seçmeli olarak güncelleştirmek için ekleme `-Name` parametresi.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-163">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="bd8a4-164">Benzer şekilde, hiçbir ek parametre olmadan çalıştırdığınızda, [güncelleştirme betiğini] [] de her komut dosyası çalıştırarak yüklü güncelleştirme girişiminde [Yükleme betiği][].</span><span class="sxs-lookup"><span data-stu-id="bd8a4-164">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="bd8a4-165">Komut dosyaları seçmeli olarak güncelleştirmek için ekleme `-Name` parametresi.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-165">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="bd8a4-166">PowerShell Galerisi'nden yüklediğiniz liste öğeleri</span><span class="sxs-lookup"><span data-stu-id="bd8a4-166">List items that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="bd8a4-167">Hangi modülleri PowerShell Galerisi'nden yüklediğiniz öğrenmek için çalıştırma [Get-InstalledModule][] cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-167">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="bd8a4-168">Bu komut, sisteminizde yüklü modülleri PowerShell Galerisi'nden doğrudan yüklenen tüm listeler.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-168">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="bd8a4-169">Benzer şekilde, hangi betiklerin PowerShell Galerisi'nden yüklediğiniz öğrenmek için çalıştırma [Get-InstalledScript][] cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-169">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="bd8a4-170">Bu komut tüm doğrudan PowerShell Galerisi'nden yüklenen, sisteminizde yüklü betikleriniz listeler.</span><span class="sxs-lookup"><span data-stu-id="bd8a4-170">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

[Bul-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Modül Bul]: /powershell/module/powershellget/Find-Module
[Find-Module]: /powershell/module/powershellget/Find-Module
[Bulma komut dosyası]: /powershell/module/powershellget/Find-Script
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Yükleme betiği]: /powershell/module/powershellget/Install-Script
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script