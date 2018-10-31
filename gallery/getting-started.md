---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: PowerShell Galerisi ile çalışmaya başlama
ms.openlocfilehash: 85b0a754aba25d850dc918024419318554f92b33
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225684"
---
# <a name="getting-started-with-the-powershell-gallery"></a><span data-ttu-id="fdf0e-103">PowerShell Galerisi ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="fdf0e-103">Getting Started with the PowerShell Gallery</span></span>

<span data-ttu-id="fdf0e-104">PowerShell Galerisi'nden paketleri yüklemek için en uygun yolu cmdlet'ler kullanmaktır [PowerShellGet](/powershell/module/powershellget) modülü.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-104">The proper way to install packages from the PowerShell Gallery is to use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="fdf0e-105">PowerShell Galerisi'nden öğeleri indirmek oturum açmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-105">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="fdf0e-106">Bir paket doğrudan PowerShell Galerisi'nden yüklemek mümkündür, ancak bu önerilen bir yaklaşım değildir.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-106">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span>
> <span data-ttu-id="fdf0e-107">Daha fazla ayrıntı için [el ile indirme paketi](/powershell/gallery/how-to/working-with-packages/manual-download).</span><span class="sxs-lookup"><span data-stu-id="fdf0e-107">For more details, see [Manual Package Download](/powershell/gallery/how-to/working-with-packages/manual-download).</span></span>

## <a name="discovering-packages-from-the-powershell-gallery"></a><span data-ttu-id="fdf0e-108">Paketler PowerShell Galerisi'ndeki keşfetme</span><span class="sxs-lookup"><span data-stu-id="fdf0e-108">Discovering packages from the PowerShell Gallery</span></span>

<span data-ttu-id="fdf0e-109">Kullanarak PowerShell Galerisi'nde paketleri bulabilirsiniz **arama** bu Web sitesinde veya modülleri ve betikleri sayfalarıyla atarak denetimi.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-109">You can find packages in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="fdf0e-110">Çalıştırarak PowerShell Galerisi'ndeki paketleri bulabilirsiniz [Modül Bul][] ve [Bulma komut dosyası][] cmdlet'leri ile öğe türüne bağlı olarak, `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-110">You can also find packages from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="fdf0e-111">Galeri sonuçlarını filtreleme, aşağıdaki parametreleri kullanarak gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="fdf0e-111">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="fdf0e-112">Ad</span><span class="sxs-lookup"><span data-stu-id="fdf0e-112">Name</span></span>
- <span data-ttu-id="fdf0e-113">AllVersions</span><span class="sxs-lookup"><span data-stu-id="fdf0e-113">AllVersions</span></span>
- <span data-ttu-id="fdf0e-114">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="fdf0e-114">MinimumVersion</span></span>
- <span data-ttu-id="fdf0e-115">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="fdf0e-115">RequiredVersion</span></span>
- <span data-ttu-id="fdf0e-116">Tag</span><span class="sxs-lookup"><span data-stu-id="fdf0e-116">Tag</span></span>
- <span data-ttu-id="fdf0e-117">İçerir</span><span class="sxs-lookup"><span data-stu-id="fdf0e-117">Includes</span></span>
- <span data-ttu-id="fdf0e-118">DscResource</span><span class="sxs-lookup"><span data-stu-id="fdf0e-118">DscResource</span></span>
- <span data-ttu-id="fdf0e-119">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="fdf0e-119">RoleCapability</span></span>
- <span data-ttu-id="fdf0e-120">Komut</span><span class="sxs-lookup"><span data-stu-id="fdf0e-120">Command</span></span>
- <span data-ttu-id="fdf0e-121">Filtre</span><span class="sxs-lookup"><span data-stu-id="fdf0e-121">Filter</span></span>

<span data-ttu-id="fdf0e-122">Yalnızca galerideki belirli DSC kaynakları keşfetme içinde ilginizi çeken, çalıştırabileceğiniz [Bul-DscResource] cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-122">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="fdf0e-123">Bul-DscResource galeride bulunan DSC kaynaklardaki verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-123">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="fdf0e-124">DSC kaynakları her zaman bir modülün bir parçası olarak teslim edildiğinden, çalıştırmanız yine [Install-Module][] bu DSC kaynakları yüklenecek.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-124">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-packages-in-the-powershell-gallery"></a><span data-ttu-id="fdf0e-125">PowerShell Galerisi paketleri hakkında daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="fdf0e-125">Learning about packages in the PowerShell Gallery</span></span>

<span data-ttu-id="fdf0e-126">İlginizi çeken bir paket belirledikten sonra ilgili daha fazla bilgi edinmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-126">Once you've identified a package that you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="fdf0e-127">Galeri belirli sayfasında bu paketin inceleyerek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-127">You can do this by examining that package's specific page on the Gallery.</span></span> <span data-ttu-id="fdf0e-128">Bu sayfada, paket ile karşıya meta verileri görmek mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-128">On that page, you'll be able to see all of the metadata uploaded with the package.</span></span> <span data-ttu-id="fdf0e-129">Bu meta veriler paketin yazarı tarafından sağlanan ve Microsoft tarafından doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-129">This metadata is provided by the package's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="fdf0e-130">Paketinin sahibi kesin paket yayımlamak için kullanılan galeri hesabınıza bağlanır ve yazar alanı daha güvenilirdir.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-130">The Owner of the package is strongly tied to the Gallery account used to publish the package, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="fdf0e-131">Sizin de böyle bir paket iyi niyetle içinde yayımlanmamışsa keşfederseniz tıklayın **uygunsuz** sayfasında bu paketin.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-131">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

<span data-ttu-id="fdf0e-132">Çalıştırıyorsanız [Modül Bul][] veya [Bulma komut dosyası][], döndürülen PSGetModuleInfo nesnesinde bu verileri görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-132">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="fdf0e-133">Örneğin, çalışan `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span><span class="sxs-lookup"><span data-stu-id="fdf0e-133">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="fdf0e-134">Galerideki PSReadLine modül verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-134">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-packages-from-the-powershell-gallery"></a><span data-ttu-id="fdf0e-135">PowerShell Galerisi'nden paketleri yükleniyor</span><span class="sxs-lookup"><span data-stu-id="fdf0e-135">Downloading packages from the PowerShell Gallery</span></span>

<span data-ttu-id="fdf0e-136">Aşağıdaki işlem PowerShell Galerisi'nden dosyalar indirilirken öneririz:</span><span class="sxs-lookup"><span data-stu-id="fdf0e-136">We encourage the following process when downloading packages from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="fdf0e-137">İnceleme</span><span class="sxs-lookup"><span data-stu-id="fdf0e-137">Inspect</span></span>

<span data-ttu-id="fdf0e-138">Galeri denetimi için bir paket indirmesine izin ya da çalıştırmak [Save-Module][] veya [Save-Script][] cmdlet'i, paket türüne bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-138">To download a package from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the package type.</span></span> <span data-ttu-id="fdf0e-139">Bu, paketi yüklemeden yerel olarak kaydetmek ve paket içeriğini İnceleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-139">This lets you save the package locally without installing it, and inspect the package contents.</span></span> <span data-ttu-id="fdf0e-140">Kaydedilen paket el ile silmeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-140">Remember to delete the saved package manually.</span></span>

<span data-ttu-id="fdf0e-141">Bu paketler bazıları Microsoft tarafından yazılmış ve başkaları PowerShell topluluğu tarafından yazılan.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-141">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="fdf0e-142">Microsoft, içeriği ve paketleri yüklemeden önce bu galeri, kod gözden geçirme önerir.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-142">Microsoft recommends that you review the contents and code of packages on this gallery prior to installation.</span></span>

<span data-ttu-id="fdf0e-143">Sizin de böyle bir paket iyi niyetle içinde yayımlanmamışsa keşfederseniz tıklayın **uygunsuz** sayfasında bu paketin.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-143">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

### <a name="install"></a><span data-ttu-id="fdf0e-144">Yükle</span><span class="sxs-lookup"><span data-stu-id="fdf0e-144">Install</span></span>

<span data-ttu-id="fdf0e-145">Galeri kullanmak için bir paket yüklemek için ya da çalıştırmak [Install-Module][] veya [Yükleme betiği][] cmdlet'i, paket türüne bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-145">To install a package from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the package type.</span></span>

<span data-ttu-id="fdf0e-146">[Install-Module][] modülünü yükler `$env:ProgramFiles\WindowsPowerShell\Modules` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-146">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="fdf0e-147">Bu, bir yönetici hesabı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-147">This requires an administrator account.</span></span> <span data-ttu-id="fdf0e-148">Eklerseniz `-Scope CurrentUser` parametresi modülünün yüklü için `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="fdf0e-148">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="fdf0e-149">[Yükleme betiği][] betiğe yükler `$env:ProgramFiles\WindowsPowerShell\Scripts` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-149">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="fdf0e-150">Bu, bir yönetici hesabı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-150">This requires an administrator account.</span></span> <span data-ttu-id="fdf0e-151">Eklerseniz `-Scope CurrentUser` parametresi, komut dosyası yüklü olduğu için `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="fdf0e-151">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="fdf0e-152">Varsayılan olarak, [Install-Module][] ve [Yükleme betiği][] bir paketin en son sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-152">By default, [Install-Module][] and [Install-Script][] installs the most current version of a package.</span></span>
<span data-ttu-id="fdf0e-153">Paketin daha eski bir sürümünü yüklemek için ekleme `-RequiredVersion` parametresi.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-153">To install an older version of the package, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="fdf0e-154">Dağıt</span><span class="sxs-lookup"><span data-stu-id="fdf0e-154">Deploy</span></span>

<span data-ttu-id="fdf0e-155">Azure Otomasyonu PowerShell Galerisi'ndeki bir pakete dağıtmak için **Azure Otomasyonu Dağıt** Paket Ayrıntıları sayfasında.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-155">To deploy a package from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the package details page.</span></span> <span data-ttu-id="fdf0e-156">Burada Azure hesabı kimlik bilgilerinizi kullanarak oturum açtığınızda Azure yönetim portalına yönlendirilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-156">You will be redirected to the Azure Management Portal where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="fdf0e-157">Bağımlılıkları olan paketler dağıtılıyor tüm bağımlılıkları için Azure Otomasyonu dağıtacağınız olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-157">Note that deploying packages with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="fdf0e-158">'Azure otomasyonu için Dağıt' düğmesini ekleyerek devre dışı bırakılabilir **AzureAutomationNotSupported** paket meta verileriniz için etiket.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-158">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your package metadata.</span></span>

<span data-ttu-id="fdf0e-159">Azure Otomasyonu hakkında daha fazla bilgi için bkz: [Azure Otomasyonu](/azure/automation) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-159">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-packages-from-the-powershell-gallery"></a><span data-ttu-id="fdf0e-160">PowerShell Galerisi'nden paketler güncelleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="fdf0e-160">Updating packages from the PowerShell Gallery</span></span>

<span data-ttu-id="fdf0e-161">PowerShell Galerisi'nden yüklü paketleri güncelleştirmek için Update-Module [] veya [güncelleştirme betiğini] [] cmdlet'ini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-161">To update packages installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="fdf0e-162">Update-Module [] herhangi ek bir parametre çalıştırdığınızda çalıştırarak yüklü her modülü güncelleştirme çalışır [Install-Module][].</span><span class="sxs-lookup"><span data-stu-id="fdf0e-162">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="fdf0e-163">Modüller seçmeli olarak güncelleştirmek için ekleme `-Name` parametresi.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-163">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="fdf0e-164">Benzer şekilde, hiçbir ek parametre olmadan çalıştırdığınızda, [güncelleştirme betiğini] [] de her komut dosyası çalıştırarak yüklü güncelleştirme girişiminde [Yükleme betiği][].</span><span class="sxs-lookup"><span data-stu-id="fdf0e-164">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="fdf0e-165">Komut dosyaları seçmeli olarak güncelleştirmek için ekleme `-Name` parametresi.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-165">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="fdf0e-166">PowerShell Galerisi'nden yüklediğiniz listeyi paketleri</span><span class="sxs-lookup"><span data-stu-id="fdf0e-166">List packages that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="fdf0e-167">Hangi modülleri PowerShell Galerisi'nden yüklediğiniz öğrenmek için çalıştırma [Get-InstalledModule][] cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-167">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="fdf0e-168">Bu komut, sisteminizde yüklü modülleri PowerShell Galerisi'nden doğrudan yüklenen tüm listeler.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-168">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="fdf0e-169">Benzer şekilde, hangi betiklerin PowerShell Galerisi'nden yüklediğiniz öğrenmek için çalıştırma [Get-InstalledScript][] cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-169">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="fdf0e-170">Bu komut tüm doğrudan PowerShell Galerisi'nden yüklenen, sisteminizde yüklü betikleriniz listeler.</span><span class="sxs-lookup"><span data-stu-id="fdf0e-170">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

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
