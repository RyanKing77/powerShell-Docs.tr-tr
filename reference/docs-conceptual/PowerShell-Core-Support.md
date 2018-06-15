# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="01e95-101">PowerShell Core Destek Yaşam Döngüsü</span><span class="sxs-lookup"><span data-stu-id="01e95-101">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="01e95-102">PowerShell çekirdek araçları ve sevk, yüklü ve ayrı ayrı Windows Powershell'den yapılandırılmış bileşenleri ayrı bir kümesidir.</span><span class="sxs-lookup"><span data-stu-id="01e95-102">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="01e95-103">Bu nedenle, PowerShell çekirdeği Windows 7/8.1/10 veya Windows Server Lisans anlaşmalarındaki dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="01e95-103">Therefore, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="01e95-104">PowerShell çekirdek de dahil olmak üzere geleneksel Microsoft destek Anlaşmalarınızda ancak, desteklenen [Premier][], [Microsoft Kurumsal anlaşmalarındaki][enterprise-agreement]ve [Microsoft Yazılım Güvencesi][assurance].</span><span class="sxs-lookup"><span data-stu-id="01e95-104">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="01e95-105">İçin ödeme yapabildiği [Yardım desteği][] PowerShell sorununuz için bir destek isteği dosyalama tarafından çekirdek için.</span><span class="sxs-lookup"><span data-stu-id="01e95-105">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="01e95-106">Ayrıca sunuyoruz [topluluk desteği][] nerede dosyası bir sorunu, hata veya özellik isteği github'da.</span><span class="sxs-lookup"><span data-stu-id="01e95-106">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="01e95-107">Alternatif olarak, genel diğer topluluk üyelerinden Yardım bulabilirsiniz [Microsoft Topluluğu][] veya Microsoft [PowerShell Teknoloji Topluluğu][].</span><span class="sxs-lookup"><span data-stu-id="01e95-107">Alternatively, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="01e95-108">Sorunu ele veya kaldırılacak zamanında çözümlendi, hiçbir garanti var. sunuyoruz.</span><span class="sxs-lookup"><span data-stu-id="01e95-108">We offer no guarantee there that your issue will be addressed or resolved in a timely manner.</span></span>
<span data-ttu-id="01e95-109">Hemen ilgilenilmesi gereken bir sorun varsa, Geleneksel, ücretli bir destek seçenekleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="01e95-109">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="01e95-110">PowerShell çekirdek yaşam döngüsü</span><span class="sxs-lookup"><span data-stu-id="01e95-110">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="01e95-111">PowerShell çekirdek benimsenmesi [Microsoft Modern yaşam döngüsü ilkesi][modern].</span><span class="sxs-lookup"><span data-stu-id="01e95-111">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="01e95-112">Bu destek yaşam döngüsü, müşterilerin en son sürümleri ile güncel kalmasını sağlamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="01e95-112">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="01e95-113">PowerShell çekirdek sürüm 6.x dalı yaklaşık altı ayda bir güncelleştirilir (örneğin 6.0, 6.1, 6.2, vs.)</span><span class="sxs-lookup"><span data-stu-id="01e95-113">The version 6.x branch of PowerShell Core will be updated approximately once every six months (e.g. 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="01e95-114">Her yeni alt sürümü yayımlandıktan sonra destek almaya devam etmek için altı ay içinde güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="01e95-114">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="01e95-115">1 Temmuz 2018 üzerinde PowerShell çekirdek 6.1 yayımlanırsa Örneğin, 1 Ocak, destek korumak için 2019 tarafından PowerShell çekirdek 6.1 güncelleştirmek için beklediğiniz.</span><span class="sxs-lookup"><span data-stu-id="01e95-115">For example, if PowerShell Core 6.1 is released on July 1st, 2018, you would be expected to update to PowerShell Core 6.1 by January 1st, 2019 to maintain support.</span></span>

![PowerShell çekirdek şube yaşam döngüsü][lifecycle-chart]

<span data-ttu-id="01e95-117">Modern yaşam döngüsü ilkesi ayrıca Microsoft müşterileri 12 ay ürün (yani PowerShell çekirdek) için destek sona erdirme önce bildirimde olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="01e95-117">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (i.e. PowerShell Core).</span></span>

<span data-ttu-id="01e95-118">Sonuç olarak, PowerShell çekirdek benimsemeye "uzun süreli bakım" bekliyoruz yaklaşım burada biz duyar yalnızca Bakımı ve güvenlik güncelleştirmeleri destek almak için belirli bir şube/sürümünü 6.x kalmak için.</span><span class="sxs-lookup"><span data-stu-id="01e95-118">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach where we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="01e95-119">Desteklenen platformlar</span><span class="sxs-lookup"><span data-stu-id="01e95-119">Supported platforms</span></span>

<span data-ttu-id="01e95-120">PowerShell çekirdek resmi olarak aşağıdaki platformlarda desteklenir:</span><span class="sxs-lookup"><span data-stu-id="01e95-120">PowerShell Core is officially supported on the following platforms:</span></span>

* <span data-ttu-id="01e95-121">Windows 7, 8.1 ve 10</span><span class="sxs-lookup"><span data-stu-id="01e95-121">Windows 7, 8.1, and 10</span></span>
* <span data-ttu-id="01e95-122">Windows Server 2008 R2, 2012 R2'de, 2016</span><span class="sxs-lookup"><span data-stu-id="01e95-122">Windows Server 2008 R2, 2012 R2, 2016</span></span>
* <span data-ttu-id="01e95-123">[Windows Server noktalı yıllık kanalı][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="01e95-123">[Windows Server Semi-Annual Channel][semi-annual]</span></span>
* <span data-ttu-id="01e95-124">Ubuntu 14.04 ve 16.04 17.04</span><span class="sxs-lookup"><span data-stu-id="01e95-124">Ubuntu 14.04, 16.04, and 17.04</span></span>
* <span data-ttu-id="01e95-125">Debian 8.7 + ve 9</span><span class="sxs-lookup"><span data-stu-id="01e95-125">Debian 8.7+, and 9</span></span>
* <span data-ttu-id="01e95-126">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="01e95-126">CentOS 7</span></span>
* <span data-ttu-id="01e95-127">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="01e95-127">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="01e95-128">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="01e95-128">OpenSUSE 42.2</span></span>
* <span data-ttu-id="01e95-129">Fedora 27, 28</span><span class="sxs-lookup"><span data-stu-id="01e95-129">Fedora 27, 28</span></span>
* <span data-ttu-id="01e95-130">macOS 10,12 +</span><span class="sxs-lookup"><span data-stu-id="01e95-130">macOS 10.12+</span></span>

<span data-ttu-id="01e95-131">Topluluğumuz ayrıca aşağıdaki platformları için paketleri katıldığını, ancak bunlar resmi olarak suppported değildir:</span><span class="sxs-lookup"><span data-stu-id="01e95-131">Our community has also contributed packages for the following platforms, but they are not officially suppported:</span></span>

* <span data-ttu-id="01e95-132">Linux arch</span><span class="sxs-lookup"><span data-stu-id="01e95-132">Arch Linux</span></span>
* <span data-ttu-id="01e95-133">Kali Linux</span><span class="sxs-lookup"><span data-stu-id="01e95-133">Kali Linux</span></span>
* <span data-ttu-id="01e95-134">AppImage (birden çok Linux platformlar üzerinde çalışır)</span><span class="sxs-lookup"><span data-stu-id="01e95-134">AppImage (works on multiple Linux platforms)</span></span>

## <a name="notes-on-licensing"></a><span data-ttu-id="01e95-135">Lisans üzerinde notları</span><span class="sxs-lookup"><span data-stu-id="01e95-135">Notes on licensing</span></span>

<span data-ttu-id="01e95-136">PowerShell çekirdeği altında yayımlanır [MIT lisansı][].</span><span class="sxs-lookup"><span data-stu-id="01e95-136">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="01e95-137">Bu lisansı altında ve Ücretli destek sözleşmesi olmadığında kullanıcılar için sınırlı [topluluk desteği][].</span><span class="sxs-lookup"><span data-stu-id="01e95-137">Under this license, and in the absence of a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="01e95-138">Topluluk desteği, Microsoft yanıtlama hızı veya düzeltmeleri hiçbir garanti vermez.</span><span class="sxs-lookup"><span data-stu-id="01e95-138">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="01e95-139">Windows PowerShell Modülü</span><span class="sxs-lookup"><span data-stu-id="01e95-139">Windows PowerShell Module</span></span>

<span data-ttu-id="01e95-140">Desteklemek için bu modüller açıkça PowerShell çekirdek desteği sürece PowerShell çekirdek diğer ürün modüllerini erişmez.</span><span class="sxs-lookup"><span data-stu-id="01e95-140">Support for PowerShell Core does not extend to other product modules unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="01e95-141">Örneğin, kullanarak `ActiveDirectory` desteklenmeyen bir senaryodur Windows Server parçası olarak gelir modüldür.</span><span class="sxs-lookup"><span data-stu-id="01e95-141">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="01e95-142">Ancak, açıkça PowerShell çekirdek desteklemeyen modülleri bazı durumlarda uyumlu olabilir.</span><span class="sxs-lookup"><span data-stu-id="01e95-142">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="01e95-143">Yükleyerek [ `WindowsPSModulePath` ][] modülü, Windows PowerShell ekleyebilirsiniz `PSModulePath` PowerShell çekirdek için `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="01e95-143">By installing the [`WindowsPSModulePath`][] module, you can append the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="01e95-144">İlk olarak, yükleme `WindowsPSModulePath` PowerShell Galerisi'nden modül:</span><span class="sxs-lookup"><span data-stu-id="01e95-144">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="01e95-145">Bu modül yükledikten sonra çalıştırmak `Add-WindowsPSModulePath` Windows PowerShell eklemek için cmdlet `PSModulePath` PowerShell çekirdek için:</span><span class="sxs-lookup"><span data-stu-id="01e95-145">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[Topluluk desteği]: https://github.com/powershell/powershell/issues
[community support]: https://github.com/powershell/powershell/issues
[Microsoft Topluluğu]: https://answers.microsoft.com/
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell Teknoloji Topluluğu]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[Yardım desteği]: https://support.microsoft.com/assistedsupportproducts
[assisted support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT lisansı]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
['WindowsPSModulePath']: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
