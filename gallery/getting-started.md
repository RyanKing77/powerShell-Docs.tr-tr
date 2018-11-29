---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: PowerShell Galerisi ile çalışmaya başlama
ms.openlocfilehash: c8beba3009e462ce52cdecd34fc0313d9234f289
ms.sourcegitcommit: 1082b13115c5c5be4b76574ba55307b3e567983f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52576898"
---
# <a name="getting-started-with-the-powershell-gallery"></a><span data-ttu-id="9a781-103">PowerShell Galerisi ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="9a781-103">Getting Started with the PowerShell Gallery</span></span>

<span data-ttu-id="9a781-104">PowerShell Galerisi, betikleri ve modülleri indirin ve yararlanarak DSC kaynakları içeren bir paket depodur.</span><span class="sxs-lookup"><span data-stu-id="9a781-104">The PowerShell Gallery is a package repository containing scripts, modules, and DSC resources you can download and leverage.</span></span> <span data-ttu-id="9a781-105">Cmdlet'leri kullanmak [PowerShellGet](/powershell/module/powershellget) modülü PowerShell Galerisi'nden paketlerini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="9a781-105">You use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module to install packages from the PowerShell Gallery.</span></span> <span data-ttu-id="9a781-106">PowerShell Galerisi'nden öğeleri indirmek oturum açmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9a781-106">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="9a781-107">Bir paket doğrudan PowerShell Galerisi'nden yüklemek mümkündür, ancak bu önerilen bir yaklaşım değildir.</span><span class="sxs-lookup"><span data-stu-id="9a781-107">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span>
> <span data-ttu-id="9a781-108">Daha fazla ayrıntı için [el ile indirme paketi](/powershell/gallery/how-to/working-with-packages/manual-download).</span><span class="sxs-lookup"><span data-stu-id="9a781-108">For more details, see [Manual Package Download](/powershell/gallery/how-to/working-with-packages/manual-download).</span></span>

## <a name="discovering-packages-from-the-powershell-gallery"></a><span data-ttu-id="9a781-109">Paketler PowerShell Galerisi'ndeki keşfetme</span><span class="sxs-lookup"><span data-stu-id="9a781-109">Discovering packages from the PowerShell Gallery</span></span>

<span data-ttu-id="9a781-110">Kullanarak PowerShell Galerisi'nde paketleri bulabilirsiniz **arama** PowerShell galeri denetiminde [giriş sayfası](https://www.powershellgallery.com), betikleri ve modülleri gözatarak veya gelen [paketleri sayfası ](https://www.powershellgallery.com/packages).</span><span class="sxs-lookup"><span data-stu-id="9a781-110">You can find packages in the PowerShell Gallery by using the **Search** control on the PowerShell Gallery's [home page](https://www.powershellgallery.com), or by browsing through the Modules and Scripts from the [Packages page](https://www.powershellgallery.com/packages).</span></span> <span data-ttu-id="9a781-111">Çalıştırarak PowerShell Galerisi'ndeki paketleri bulabilirsiniz [Find-Module][], [Find-DscResource], ve [Find-Script][] cmdlet'leri, paket türüne bağlı olarak ile `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="9a781-111">You can also find packages from the PowerShell Gallery by running the [Find-Module][], [Find-DscResource], and [Find-Script][] cmdlets, depending on the package type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="9a781-112">Aşağıdaki parametreleri kullanarak Galeriden sonuçlarını filtreleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9a781-112">You can filter results from the Gallery by using the following parameters:</span></span>

- <span data-ttu-id="9a781-113">Ad</span><span class="sxs-lookup"><span data-stu-id="9a781-113">Name</span></span>
- <span data-ttu-id="9a781-114">AllVersions</span><span class="sxs-lookup"><span data-stu-id="9a781-114">AllVersions</span></span>
- <span data-ttu-id="9a781-115">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="9a781-115">MinimumVersion</span></span>
- <span data-ttu-id="9a781-116">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="9a781-116">RequiredVersion</span></span>
- <span data-ttu-id="9a781-117">Tag</span><span class="sxs-lookup"><span data-stu-id="9a781-117">Tag</span></span>
- <span data-ttu-id="9a781-118">İçerir</span><span class="sxs-lookup"><span data-stu-id="9a781-118">Includes</span></span>
- <span data-ttu-id="9a781-119">DscResource</span><span class="sxs-lookup"><span data-stu-id="9a781-119">DscResource</span></span>
- <span data-ttu-id="9a781-120">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="9a781-120">RoleCapability</span></span>
- <span data-ttu-id="9a781-121">Komut</span><span class="sxs-lookup"><span data-stu-id="9a781-121">Command</span></span>
- <span data-ttu-id="9a781-122">Filtre</span><span class="sxs-lookup"><span data-stu-id="9a781-122">Filter</span></span>

<span data-ttu-id="9a781-123">Yalnızca galerideki belirli DSC kaynakları keşfetme içinde ilginizi çeken, çalıştırabileceğiniz [Find-DscResource] cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="9a781-123">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="9a781-124">Bul-DscResource galeride bulunan DSC kaynaklardaki verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a781-124">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="9a781-125">DSC kaynakları her zaman bir modülün bir parçası olarak teslim edildiğinden, çalıştırmanız yine [Install-Module][] bu DSC kaynakları yüklenecek.</span><span class="sxs-lookup"><span data-stu-id="9a781-125">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-packages-in-the-powershell-gallery"></a><span data-ttu-id="9a781-126">PowerShell Galerisi paketleri hakkında daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="9a781-126">Learning about packages in the PowerShell Gallery</span></span>

<span data-ttu-id="9a781-127">İlginizi çeken bir paket belirledikten sonra ilgili daha fazla bilgi edinmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a781-127">Once you've identified a package that you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="9a781-128">Galeri belirli sayfasında bu paketin inceleyerek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a781-128">You can do this by examining that package's specific page on the Gallery.</span></span> <span data-ttu-id="9a781-129">Bu sayfada, paket ile karşıya meta verileri görmek mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="9a781-129">On that page, you'll be able to see all of the metadata uploaded with the package.</span></span> <span data-ttu-id="9a781-130">Bu meta veriler paketin yazarı tarafından sağlanan ve Microsoft tarafından doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="9a781-130">This metadata is provided by the package's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="9a781-131">Paketinin sahibi kesin paket yayımlamak için kullanılan galeri hesabınıza bağlanır ve yazar alanı daha güvenilirdir.</span><span class="sxs-lookup"><span data-stu-id="9a781-131">The Owner of the package is strongly tied to the Gallery account used to publish the package, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="9a781-132">Sizin de böyle bir paket iyi niyetle içinde yayımlanmamışsa keşfederseniz tıklayın **uygunsuz** sayfasında bu paketin.</span><span class="sxs-lookup"><span data-stu-id="9a781-132">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

<span data-ttu-id="9a781-133">Çalıştırıyorsanız [Find-Module][] veya [Find-Script][], döndürülen PSGetModuleInfo nesnesinde bu verileri görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a781-133">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="9a781-134">Örneğin, çalışan `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span><span class="sxs-lookup"><span data-stu-id="9a781-134">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="9a781-135">Galerideki PSReadLine modül verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a781-135">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-packages-from-the-powershell-gallery"></a><span data-ttu-id="9a781-136">PowerShell Galerisi'nden paketleri yükleniyor</span><span class="sxs-lookup"><span data-stu-id="9a781-136">Downloading packages from the PowerShell Gallery</span></span>

<span data-ttu-id="9a781-137">Aşağıdaki işlem PowerShell Galerisi'nden dosyalar indirilirken öneririz:</span><span class="sxs-lookup"><span data-stu-id="9a781-137">We encourage the following process when downloading packages from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="9a781-138">İnceleme</span><span class="sxs-lookup"><span data-stu-id="9a781-138">Inspect</span></span>

<span data-ttu-id="9a781-139">Galeri denetimi için bir paket indirmesine izin ya da çalıştırmak [Save-Module][] veya [Save-Script][] cmdlet'i, paket türüne bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="9a781-139">To download a package from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the package type.</span></span> <span data-ttu-id="9a781-140">Bu, paketi yüklemeden yerel olarak kaydetmek ve paket içeriğini İnceleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a781-140">This lets you save the package locally without installing it, and inspect the package contents.</span></span> <span data-ttu-id="9a781-141">Kaydedilen paket el ile silmeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9a781-141">Remember to delete the saved package manually.</span></span>

<span data-ttu-id="9a781-142">Bu paketler bazıları Microsoft tarafından yazılmış ve başkaları PowerShell topluluğu tarafından yazılan.</span><span class="sxs-lookup"><span data-stu-id="9a781-142">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="9a781-143">Microsoft, içeriği ve paketleri yüklemeden önce bu galeri, kod gözden geçirme önerir.</span><span class="sxs-lookup"><span data-stu-id="9a781-143">Microsoft recommends that you review the contents and code of packages on this gallery prior to installation.</span></span>

<span data-ttu-id="9a781-144">Sizin de böyle bir paket iyi niyetle içinde yayımlanmamışsa keşfederseniz tıklayın **uygunsuz** sayfasında bu paketin.</span><span class="sxs-lookup"><span data-stu-id="9a781-144">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

### <a name="install"></a><span data-ttu-id="9a781-145">Yükle</span><span class="sxs-lookup"><span data-stu-id="9a781-145">Install</span></span>

<span data-ttu-id="9a781-146">Galeri kullanmak için bir paket yüklemek için ya da çalıştırmak [Install-Module][] veya [Install-Script][] cmdlet'i, paket türüne bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="9a781-146">To install a package from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the package type.</span></span>

<span data-ttu-id="9a781-147">[Install-Module][] modülünü yükler `$env:ProgramFiles\WindowsPowerShell\Modules` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="9a781-147">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="9a781-148">Bu, bir yönetici hesabı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9a781-148">This requires an administrator account.</span></span> <span data-ttu-id="9a781-149">Eklerseniz `-Scope CurrentUser` parametresi modülünün yüklü için `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="9a781-149">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="9a781-150">[Install-Script][] betiğe yükler `$env:ProgramFiles\WindowsPowerShell\Scripts` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="9a781-150">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="9a781-151">Bu, bir yönetici hesabı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9a781-151">This requires an administrator account.</span></span> <span data-ttu-id="9a781-152">Eklerseniz `-Scope CurrentUser` parametresi, komut dosyası yüklü olduğu için `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="9a781-152">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="9a781-153">Varsayılan olarak, [Install-Module][] ve [Install-Script][] bir paketin en son sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="9a781-153">By default, [Install-Module][] and [Install-Script][] installs the most current version of a package.</span></span>
<span data-ttu-id="9a781-154">Paketin daha eski bir sürümünü yüklemek için ekleme `-RequiredVersion` parametresi.</span><span class="sxs-lookup"><span data-stu-id="9a781-154">To install an older version of the package, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="9a781-155">Dağıt</span><span class="sxs-lookup"><span data-stu-id="9a781-155">Deploy</span></span>

<span data-ttu-id="9a781-156">Azure Otomasyonu PowerShell Galerisi'ndeki bir pakete dağıtmak için **Azure Otomasyonu**, ardından **Azure Otomasyonu Dağıt** Paket Ayrıntıları sayfasında.</span><span class="sxs-lookup"><span data-stu-id="9a781-156">To deploy a package from the PowerShell Gallery to Azure Automation, click **Azure Automation**, then click **Deploy to Azure Automation** on the package details page.</span></span> <span data-ttu-id="9a781-157">Burada Azure hesabı kimlik bilgilerinizi kullanarak oturum açtığınızda Azure yönetim portalına yönlendirilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a781-157">You are redirected to the Azure Management Portal where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="9a781-158">Bağımlılıkları olan paketler dağıtılıyor tüm bağımlılıkları için Azure Otomasyonu dağıttığı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9a781-158">Note that deploying packages with dependencies deploys all the dependencies to Azure Automation.</span></span> <span data-ttu-id="9a781-159">'Azure otomasyonu için Dağıt' düğmesini ekleyerek devre dışı bırakılabilir **AzureAutomationNotSupported** paket meta verileriniz için etiket.</span><span class="sxs-lookup"><span data-stu-id="9a781-159">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your package metadata.</span></span>

<span data-ttu-id="9a781-160">Azure Otomasyonu hakkında daha fazla bilgi için bkz: [Azure Otomasyonu](/azure/automation) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="9a781-160">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-packages-from-the-powershell-gallery"></a><span data-ttu-id="9a781-161">PowerShell Galerisi'nden paketler güncelleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="9a781-161">Updating packages from the PowerShell Gallery</span></span>

<span data-ttu-id="9a781-162">PowerShell Galerisi'nden yüklü paketleri güncelleştirmek için Update-Module [] veya [Update-Script] [] cmdlet'ini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9a781-162">To update packages installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="9a781-163">Ek parametreler çalıştırdığınızda, güncelleştirme-Module [] çalıştırarak yüklü tüm modüllerin güncelleştirmek çalışır [Install-Module][].</span><span class="sxs-lookup"><span data-stu-id="9a781-163">When run without any additional parameters, [Update-Module][] attempts to update all modules installed by running [Install-Module][].</span></span> <span data-ttu-id="9a781-164">Modüller seçmeli olarak güncelleştirmek için ekleme `-Name` parametresi.</span><span class="sxs-lookup"><span data-stu-id="9a781-164">To selectively update modules, add the `-Name` parameter.</span></span> 

<span data-ttu-id="9a781-165">Benzer şekilde, hiçbir ek parametre olmadan çalıştırdığınızda, [Update-Script] [] ayrıca tüm betikleri çalıştırarak yüklü güncelleştirme girişiminde [Install-Script][].</span><span class="sxs-lookup"><span data-stu-id="9a781-165">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update all scripts installed by running [Install-Script][].</span></span> <span data-ttu-id="9a781-166">Komut dosyaları seçmeli olarak güncelleştirmek için ekleme `-Name` parametresi.</span><span class="sxs-lookup"><span data-stu-id="9a781-166">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="9a781-167">PowerShell Galerisi'nden yüklediğiniz listeyi paketleri</span><span class="sxs-lookup"><span data-stu-id="9a781-167">List packages that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="9a781-168">Hangi modülleri PowerShell Galerisi'nden yüklediğiniz öğrenmek için çalıştırma [Get-InstalledModule][] cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="9a781-168">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="9a781-169">Bu komut, sisteminizde yüklü modülleri PowerShell Galerisi'nden doğrudan yüklenen tüm listeler.</span><span class="sxs-lookup"><span data-stu-id="9a781-169">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="9a781-170">Benzer şekilde, hangi betiklerin PowerShell Galerisi'nden yüklediğiniz öğrenmek için çalıştırma [Get-InstalledScript][] cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="9a781-170">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="9a781-171">Bu komut tüm doğrudan PowerShell Galerisi'nden yüklenen, sisteminizde yüklü betikleriniz listeler.</span><span class="sxs-lookup"><span data-stu-id="9a781-171">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script
