---
title: PowerShell Core Destek Yaşam Döngüsü
description: PowerShell Core için ilkelerimizin desteği
ms.date: 08/06/2018
ms.openlocfilehash: b8dd4891ecf245b87c3fe2fa61cd241a12209b57
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854372"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="f1ab1-103">PowerShell Core Destek Yaşam Döngüsü</span><span class="sxs-lookup"><span data-stu-id="f1ab1-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="f1ab1-104">PowerShell Core araçları ve bileşenlerin sevk, yüklü ve Windows PowerShell üzerinden ayrı olarak yapılandırılmış ayrı bir kümesidir.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="f1ab1-105">Bu nedenle, PowerShell Core Windows 7/8.1/10 veya Windows Server Lisans anlaşmalarındaki dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-105">So, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="f1ab1-106">PowerShell Core gibi geleneksel Microsoft destek sözleşmeleri altında ancak desteklenen [Premier][], [Microsoft Kurumsal Anlaşma][enterprise-agreement]ve [Microsoft Yazılım Güvencesi][assurance].</span><span class="sxs-lookup"><span data-stu-id="f1ab1-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="f1ab1-107">İçin de ödeme yapabilirsiniz [Yardımlı Destek][] sorununuzu bir destek isteği dosyalama tarafından PowerShell Core için.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

## <a name="community-support"></a><span data-ttu-id="f1ab1-108">Topluluk desteği</span><span class="sxs-lookup"><span data-stu-id="f1ab1-108">Community Support</span></span>

<span data-ttu-id="f1ab1-109">Ayrıca sunuyoruz [topluluk desteği][] burada dosyası bir sorun, hata veya özellik isteği GitHub üzerinde.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-109">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="f1ab1-110">Ayrıca, genel diğer topluluk üyelerinden Yardım bulabilirsiniz [Microsoft Community][] veya Microsoft [PowerShell Teknoloji Topluluğu][].</span><span class="sxs-lookup"><span data-stu-id="f1ab1-110">Also, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="f1ab1-111">Topluluk adres veya zamanında sorununuzu garantisi vardır sunuyoruz.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-111">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span>
<span data-ttu-id="f1ab1-112">Hemen ilgilenilmesi gereken bir sorununuz varsa, Geleneksel, Ücretli destek seçenekleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-112">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="f1ab1-113">PowerShell Core yaşam döngüsü</span><span class="sxs-lookup"><span data-stu-id="f1ab1-113">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="f1ab1-114">PowerShell Core benimseme [Microsoft Modern yaşam döngüsü ilkesi][modern].</span><span class="sxs-lookup"><span data-stu-id="f1ab1-114">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="f1ab1-115">Bu destek yaşam döngüsü, müşterilerin en yeni sürümlerinin güncel tutmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-115">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="f1ab1-116">PowerShell Core sürüm 6.x dalını yaklaşık altı ayda güncelleştirilir (örnekler: 6.0, 6.1, 6.2, vs.)</span><span class="sxs-lookup"><span data-stu-id="f1ab1-116">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f1ab1-117">Her yeni bir ikincil sürüm sonra destek almaya devam etmek için altı ay içinde güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-117">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="f1ab1-118">1 Temmuz 2018'de PowerShell Core 6.1 yayımlandığında Örneğin, 1 Ocak desteğin sürmesi için 2019 tarafından PowerShell Core 6.1 için güncelleştirilecek beklediğiniz.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-118">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f1ab1-119">Destek almaya devam etmek için her yeni bir düzeltme eki sürüm sonraki 30 gün içinde güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-119">You must update within 30 days after each new patch version release to continue receiving support.</span></span>

<span data-ttu-id="f1ab1-120">Örneğin, PowerShell Core 6.1 çalıştırıyorsanız ve 6.1.3 19 Şubat 2019 üzerinde yayımlanan PowerShell desteğin sürmesi için yayımlanmasının ardından 30 gün ise çekirdek 6.1.3 21 Mart 2019 tarafından güncelleştirmek için beklediğiniz.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-120">For example, If you are running PowerShell Core 6.1 and 6.1.3 was released on February 19, 2019, you would be expected to update to PowerShell Core 6.1.3 by March 21, 2019, which is 30 days after the release to maintain support.</span></span>
<span data-ttu-id="f1ab1-121">Gerekli tüm düzeltmeleri bulunamazsa, düzeltmeler bizim sonraki toplu güncelleştirmede yayınlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-121">If any fixes are found to be required, the fixes will be released in our next cumulative update.</span></span>

<span data-ttu-id="f1ab1-122">Microsoft müşterilere 12 ay (diğer bir deyişle, PowerShell Core) ürün desteği kaldırmadan önce bildirimde, Modern yaşam döngüsü ilkesi de gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-122">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="f1ab1-123">Sonuç olarak, PowerShell Core, "uzun süreli bakım" olmadığını benimseyin bekliyoruz yaklaşım.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-123">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach.</span></span>
<span data-ttu-id="f1ab1-124">Hizmet Bu yaklaşımda, biz 6.x'ın belirli bir dal/sürümünde destek kalmak için yalnızca Bakım ve güvenlik güncelleştirmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-124">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="f1ab1-125">Desteklenen platformlar</span><span class="sxs-lookup"><span data-stu-id="f1ab1-125">Supported platforms</span></span>

<span data-ttu-id="f1ab1-126">PowerShell Core kullanmakta olduğunuz sürümünü platformdan görmek için aşağıdaki tabloyu resmi olarak desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-126">The following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="f1ab1-127">Topluluğumuza da bazı platformlar için paketleri katkılarıyla, ancak resmi olarak desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-127">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="f1ab1-128">Bu paketleri olarak işaretlenmiş `Community` tabloda.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-128">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="f1ab1-129">Olarak listelenen platformların `Experimental` resmi olarak desteklenmez, ancak deneme ve geri bildirim için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-129">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="f1ab1-130">6.1</span><span class="sxs-lookup"><span data-stu-id="f1ab1-130">6.1</span></span>         | <span data-ttu-id="f1ab1-131">6.2</span><span class="sxs-lookup"><span data-stu-id="f1ab1-131">6.2</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="f1ab1-132">Windows 7, 8.1 ve 10</span><span class="sxs-lookup"><span data-stu-id="f1ab1-132">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="f1ab1-133">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="f1ab1-133">Supported</span></span>   | <span data-ttu-id="f1ab1-134">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="f1ab1-134">Supported</span></span>   |
| <span data-ttu-id="f1ab1-135">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="f1ab1-135">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="f1ab1-136">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="f1ab1-136">Supported</span></span>   | <span data-ttu-id="f1ab1-137">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="f1ab1-137">Supported</span></span>   |
| <span data-ttu-id="f1ab1-138">[Windows Server yarı yıllık kanal][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="f1ab1-138">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="f1ab1-139">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="f1ab1-139">Supported</span></span>   | <span data-ttu-id="f1ab1-140">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="f1ab1-140">Supported</span></span>   |
| <span data-ttu-id="f1ab1-141">Ubuntu 16.04 ve 18.04</span><span class="sxs-lookup"><span data-stu-id="f1ab1-141">Ubuntu 16.04 and 18.04</span></span>                            | <span data-ttu-id="f1ab1-142">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="f1ab1-142">Supported</span></span>   | <span data-ttu-id="f1ab1-143">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="f1ab1-143">Supported</span></span>   |
| <span data-ttu-id="f1ab1-144">Ubuntu 18.10 (aracılığıyla yaslama paketi)</span><span class="sxs-lookup"><span data-stu-id="f1ab1-144">Ubuntu 18.10 (via Snap Package)</span></span>                   | <span data-ttu-id="f1ab1-145">Topluluk</span><span class="sxs-lookup"><span data-stu-id="f1ab1-145">Community</span></span>   | <span data-ttu-id="f1ab1-146">Topluluk</span><span class="sxs-lookup"><span data-stu-id="f1ab1-146">Community</span></span>   |
| <span data-ttu-id="f1ab1-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="f1ab1-147">Debian 9</span></span>                                          | <span data-ttu-id="f1ab1-148">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="f1ab1-148">Supported</span></span>   | <span data-ttu-id="f1ab1-149">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="f1ab1-149">Supported</span></span>   |
| <span data-ttu-id="f1ab1-150">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="f1ab1-150">CentOS 7</span></span>                                          | <span data-ttu-id="f1ab1-151">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="f1ab1-151">Supported</span></span>   | <span data-ttu-id="f1ab1-152">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="f1ab1-152">Supported</span></span>   |
| <span data-ttu-id="f1ab1-153">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="f1ab1-153">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="f1ab1-154">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="f1ab1-154">Supported</span></span>   | <span data-ttu-id="f1ab1-155">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="f1ab1-155">Supported</span></span>   |
| <span data-ttu-id="f1ab1-156">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="f1ab1-156">openSUSE 42.3</span></span>                                     | <span data-ttu-id="f1ab1-157">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="f1ab1-157">Supported</span></span>   | <span data-ttu-id="f1ab1-158">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="f1ab1-158">Supported</span></span>   |
| <span data-ttu-id="f1ab1-159">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="f1ab1-159">Fedora 28</span></span>                                         | <span data-ttu-id="f1ab1-160">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="f1ab1-160">Supported</span></span>   | <span data-ttu-id="f1ab1-161">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="f1ab1-161">Supported</span></span>   |
| <span data-ttu-id="f1ab1-162">macOS 10.12 +</span><span class="sxs-lookup"><span data-stu-id="f1ab1-162">macOS 10.12+</span></span>                                      | <span data-ttu-id="f1ab1-163">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="f1ab1-163">Supported</span></span>   | <span data-ttu-id="f1ab1-164">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="f1ab1-164">Supported</span></span>   |
| <span data-ttu-id="f1ab1-165">Arch</span><span class="sxs-lookup"><span data-stu-id="f1ab1-165">Arch</span></span>                                              | <span data-ttu-id="f1ab1-166">Topluluk</span><span class="sxs-lookup"><span data-stu-id="f1ab1-166">Community</span></span>   | <span data-ttu-id="f1ab1-167">Topluluk</span><span class="sxs-lookup"><span data-stu-id="f1ab1-167">Community</span></span>   |
| <span data-ttu-id="f1ab1-168">Raspbian</span><span class="sxs-lookup"><span data-stu-id="f1ab1-168">Raspbian</span></span>                                          | <span data-ttu-id="f1ab1-169">Topluluk</span><span class="sxs-lookup"><span data-stu-id="f1ab1-169">Community</span></span>   | <span data-ttu-id="f1ab1-170">Topluluk</span><span class="sxs-lookup"><span data-stu-id="f1ab1-170">Community</span></span>   |
| <span data-ttu-id="f1ab1-171">Kali</span><span class="sxs-lookup"><span data-stu-id="f1ab1-171">Kali</span></span>                                              | <span data-ttu-id="f1ab1-172">Topluluk</span><span class="sxs-lookup"><span data-stu-id="f1ab1-172">Community</span></span>   | <span data-ttu-id="f1ab1-173">Topluluk</span><span class="sxs-lookup"><span data-stu-id="f1ab1-173">Community</span></span>   |
| <span data-ttu-id="f1ab1-174">AppImage (birden çok Linux platformlarında çalışır)</span><span class="sxs-lookup"><span data-stu-id="f1ab1-174">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="f1ab1-175">Topluluk</span><span class="sxs-lookup"><span data-stu-id="f1ab1-175">Community</span></span>   | <span data-ttu-id="f1ab1-176">Topluluk</span><span class="sxs-lookup"><span data-stu-id="f1ab1-176">Community</span></span>   |
| [<span data-ttu-id="f1ab1-177">Paket Yasla</span><span class="sxs-lookup"><span data-stu-id="f1ab1-177">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="f1ab1-178">Bkz. Not</span><span class="sxs-lookup"><span data-stu-id="f1ab1-178">See note</span></span>    | <span data-ttu-id="f1ab1-179">Bkz. Not</span><span class="sxs-lookup"><span data-stu-id="f1ab1-179">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="f1ab1-180">Paketleri desteklenir Yasla aynı dağıtım paketi çalıştırdığınız.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-180">Snap packages are supported the same as the distribution you are running the package on.</span></span>

## <a name="powershell-release-end-of-life"></a><span data-ttu-id="f1ab1-181">PowerShell sürüm sona erecek</span><span class="sxs-lookup"><span data-stu-id="f1ab1-181">PowerShell release end of life</span></span>

<span data-ttu-id="f1ab1-182">Temel [PowerShell Core yaşam döngüsü](#lifecycle-of-powershell-core), aşağıdaki tabloda, çeşitli sürüm artık desteklenir tarihleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-182">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various release will no longer be supported.</span></span>

| <span data-ttu-id="f1ab1-183">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f1ab1-183">Version</span></span> | <span data-ttu-id="f1ab1-184">Kullanım ömrü</span><span class="sxs-lookup"><span data-stu-id="f1ab1-184">End Of Life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="f1ab1-185">6.0</span><span class="sxs-lookup"><span data-stu-id="f1ab1-185">6.0</span></span>     | <span data-ttu-id="f1ab1-186">13 Şubat 2019</span><span class="sxs-lookup"><span data-stu-id="f1ab1-186">February 13, 2019</span></span>             |
| <span data-ttu-id="f1ab1-187">6.1</span><span class="sxs-lookup"><span data-stu-id="f1ab1-187">6.1</span></span>     | <span data-ttu-id="f1ab1-188">28 Eylül 2019</span><span class="sxs-lookup"><span data-stu-id="f1ab1-188">September 28, 2019</span></span>            |
| <span data-ttu-id="f1ab1-189">6.2</span><span class="sxs-lookup"><span data-stu-id="f1ab1-189">6.2</span></span>     | <span data-ttu-id="f1ab1-190">7 yayınlar sonra 6 ay</span><span class="sxs-lookup"><span data-stu-id="f1ab1-190">6 months after 7 releases</span></span>     |

## <a name="platforms-which-are-out-of-support"></a><span data-ttu-id="f1ab1-191">Desteklenmeyen platformlar</span><span class="sxs-lookup"><span data-stu-id="f1ab1-191">Platforms, which are out of support</span></span>

<span data-ttu-id="f1ab1-192">Platform sürümü platform sahibi tarafından tanımlanan son yaşam ulaştığında, PowerShell Core bu platform sürümü desteklemek de sona erecek.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-192">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span>
<span data-ttu-id="f1ab1-193">Daha önce yayımlanmış paketleri erişim ancak resmi destek ihtiyaç duyan müşteriler için kullanılabilir halde kalacak ve herhangi bir türdeki güncelleştirmeleri artık sağlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-193">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="f1ab1-194">Bu nedenle, dağıtım sahipleri aşağıdaki sürümleri için destek sona erdi ve desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-194">So, the distribution owners ended support for the following versions and are not supported.</span></span>

| <span data-ttu-id="f1ab1-195">İşletim sistemi</span><span class="sxs-lookup"><span data-stu-id="f1ab1-195">OS</span></span>       | <span data-ttu-id="f1ab1-196">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f1ab1-196">Version</span></span> | <span data-ttu-id="f1ab1-197">Kullanım ömrü</span><span class="sxs-lookup"><span data-stu-id="f1ab1-197">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="f1ab1-198">Fedora</span><span class="sxs-lookup"><span data-stu-id="f1ab1-198">Fedora</span></span>   | <span data-ttu-id="f1ab1-199">24</span><span class="sxs-lookup"><span data-stu-id="f1ab1-199">24</span></span>      | [<span data-ttu-id="f1ab1-200">Ağustos 2017</span><span class="sxs-lookup"><span data-stu-id="f1ab1-200">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="f1ab1-201">Fedora</span><span class="sxs-lookup"><span data-stu-id="f1ab1-201">Fedora</span></span>   | <span data-ttu-id="f1ab1-202">25</span><span class="sxs-lookup"><span data-stu-id="f1ab1-202">25</span></span>      | [<span data-ttu-id="f1ab1-203">Aralık 2017</span><span class="sxs-lookup"><span data-stu-id="f1ab1-203">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="f1ab1-204">Fedora</span><span class="sxs-lookup"><span data-stu-id="f1ab1-204">Fedora</span></span>   | <span data-ttu-id="f1ab1-205">26</span><span class="sxs-lookup"><span data-stu-id="f1ab1-205">26</span></span>      | [<span data-ttu-id="f1ab1-206">Mayıs 2018</span><span class="sxs-lookup"><span data-stu-id="f1ab1-206">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="f1ab1-207">openSUSE</span><span class="sxs-lookup"><span data-stu-id="f1ab1-207">openSUSE</span></span> | <span data-ttu-id="f1ab1-208">42.1</span><span class="sxs-lookup"><span data-stu-id="f1ab1-208">42.1</span></span>    | [<span data-ttu-id="f1ab1-209">Mayıs 2017</span><span class="sxs-lookup"><span data-stu-id="f1ab1-209">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="f1ab1-210">openSUSE</span><span class="sxs-lookup"><span data-stu-id="f1ab1-210">openSUSE</span></span> | <span data-ttu-id="f1ab1-211">42.2</span><span class="sxs-lookup"><span data-stu-id="f1ab1-211">42.2</span></span>    | [<span data-ttu-id="f1ab1-212">Ocak 2018</span><span class="sxs-lookup"><span data-stu-id="f1ab1-212">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="f1ab1-213">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="f1ab1-213">Ubuntu</span></span>   | <span data-ttu-id="f1ab1-214">16.10</span><span class="sxs-lookup"><span data-stu-id="f1ab1-214">16.10</span></span>   | [<span data-ttu-id="f1ab1-215">Temmuz 2017</span><span class="sxs-lookup"><span data-stu-id="f1ab1-215">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="f1ab1-216">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="f1ab1-216">Ubuntu</span></span>   | <span data-ttu-id="f1ab1-217">17.04</span><span class="sxs-lookup"><span data-stu-id="f1ab1-217">17.04</span></span>   | [<span data-ttu-id="f1ab1-218">Ocak 2018</span><span class="sxs-lookup"><span data-stu-id="f1ab1-218">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="f1ab1-219">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="f1ab1-219">Ubuntu</span></span>   | <span data-ttu-id="f1ab1-220">17.10</span><span class="sxs-lookup"><span data-stu-id="f1ab1-220">17.10</span></span>   | [<span data-ttu-id="f1ab1-221">Temmuz 2018</span><span class="sxs-lookup"><span data-stu-id="f1ab1-221">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="f1ab1-222">Debian</span><span class="sxs-lookup"><span data-stu-id="f1ab1-222">Debian</span></span>   | <span data-ttu-id="f1ab1-223">8</span><span class="sxs-lookup"><span data-stu-id="f1ab1-223">8</span></span>       | [<span data-ttu-id="f1ab1-224">Haziran 2018</span><span class="sxs-lookup"><span data-stu-id="f1ab1-224">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="f1ab1-225">Fedora</span><span class="sxs-lookup"><span data-stu-id="f1ab1-225">Fedora</span></span>   | <span data-ttu-id="f1ab1-226">27</span><span class="sxs-lookup"><span data-stu-id="f1ab1-226">27</span></span>      | [<span data-ttu-id="f1ab1-227">Kasım 2018</span><span class="sxs-lookup"><span data-stu-id="f1ab1-227">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| <span data-ttu-id="f1ab1-228">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="f1ab1-228">Ubuntu</span></span>   | <span data-ttu-id="f1ab1-229">14.04</span><span class="sxs-lookup"><span data-stu-id="f1ab1-229">14.04</span></span>   | [<span data-ttu-id="f1ab1-230">Nisan 2019</span><span class="sxs-lookup"><span data-stu-id="f1ab1-230">April 2019</span></span>](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a><span data-ttu-id="f1ab1-231">Lisanslama notları</span><span class="sxs-lookup"><span data-stu-id="f1ab1-231">Notes on licensing</span></span>

<span data-ttu-id="f1ab1-232">PowerShell Core altında yayımlanır [MIT lisansı][].</span><span class="sxs-lookup"><span data-stu-id="f1ab1-232">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="f1ab1-233">Bu lisansı altında ve bir Ücretli destek anlaşması olmadan kullanıcılar sınırlı [topluluk desteği][].</span><span class="sxs-lookup"><span data-stu-id="f1ab1-233">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="f1ab1-234">Topluluk desteği sayesinde, Microsoft yanıtlama hızı veya düzeltmeleri garanti vermez.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-234">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="f1ab1-235">Windows PowerShell Modülü</span><span class="sxs-lookup"><span data-stu-id="f1ab1-235">Windows PowerShell Module</span></span>

<span data-ttu-id="f1ab1-236">Desteklemek için bu modülleri PowerShell Core açıkça desteklemedikçe ürün modülleri PowerShell Core içermez.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-236">Support for PowerShell Core does not include product modules, unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="f1ab1-237">Örneğin, kullanarak `ActiveDirectory` desteklenmeyen bir senaryo Windows Server'ın bir parçası olduğu gibi birlikte gelen modülü.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-237">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="f1ab1-238">Ancak, açıkça PowerShell Core desteklemeyen modülleri bazı durumlarda uyumlu olabilir.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-238">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="f1ab1-239">Yükleyerek [ `WindowsPSModulePath` ][] modülü, Windows PowerShell ekleyebilirsiniz `PSModulePath` , PowerShell Core `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-239">By installing the [`WindowsPSModulePath`][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="f1ab1-240">İlk olarak, yükleme `WindowsPSModulePath` modülü PowerShell Galerisi'ndeki:</span><span class="sxs-lookup"><span data-stu-id="f1ab1-240">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="f1ab1-241">Bu modülü yükledikten sonra çalıştırın `Add-WindowsPSModulePath` eklemek için Windows PowerShell cmdlet'ini `PSModulePath` PowerShell Core için:</span><span class="sxs-lookup"><span data-stu-id="f1ab1-241">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a><span data-ttu-id="f1ab1-242">Deneysel Özellikler</span><span class="sxs-lookup"><span data-stu-id="f1ab1-242">Experimental features</span></span>

<span data-ttu-id="f1ab1-243">[Deneysel Özellikler][] sınırlıdır [topluluk desteği](#community-support).</span><span class="sxs-lookup"><span data-stu-id="f1ab1-243">[Experimental features][] are limited to [community support](#community-support).</span></span>

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[Topluluk desteği]: https://github.com/powershell/powershell/issues
[community support]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell Teknoloji Topluluğu]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[Yardımlı Destek]: https://support.microsoft.com/assistedsupportproducts
[assisted support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT lisansı]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Deneysel Özellikler]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
[Experimental features]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
