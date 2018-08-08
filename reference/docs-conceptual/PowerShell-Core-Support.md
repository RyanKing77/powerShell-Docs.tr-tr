---
title: PowerShell Core Destek Yaşam Döngüsü
description: PowerShell Core için ilkelerimizin desteği
ms.date: 08/06/2018
ms.openlocfilehash: 2e0ca1b9c133e6f316a40aff13365d0489059165
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587168"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="ff990-103">PowerShell Core Destek Yaşam Döngüsü</span><span class="sxs-lookup"><span data-stu-id="ff990-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="ff990-104">PowerShell Core araçları ve bileşenlerin sevk, yüklü ve Windows PowerShell üzerinden ayrı olarak yapılandırılmış ayrı bir kümesidir.</span><span class="sxs-lookup"><span data-stu-id="ff990-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="ff990-105">Bu nedenle, PowerShell Core Windows 7/8.1/10 veya Windows Server Lisans anlaşmalarındaki dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="ff990-105">Therefore, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="ff990-106">PowerShell Core gibi geleneksel Microsoft destek sözleşmeleri altında ancak desteklenen [Premier][], [Microsoft Kurumsal Anlaşma][enterprise-agreement]ve [Microsoft Yazılım Güvencesi][assurance].</span><span class="sxs-lookup"><span data-stu-id="ff990-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="ff990-107">İçin de ödeme yapabilirsiniz [Yardımlı Destek][] sorununuzu bir destek isteği dosyalama tarafından PowerShell Core için.</span><span class="sxs-lookup"><span data-stu-id="ff990-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="ff990-108">Ayrıca sunuyoruz [topluluk desteği][] burada dosyası bir sorun, hata veya özellik isteği GitHub üzerinde.</span><span class="sxs-lookup"><span data-stu-id="ff990-108">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="ff990-109">Alternatif olarak, genel diğer topluluk üyelerinden Yardım bulabilirsiniz [Microsoft Community][] veya Microsoft [PowerShell Teknoloji Topluluğu][].</span><span class="sxs-lookup"><span data-stu-id="ff990-109">Alternatively, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="ff990-110">Sorununuzu ele veya kaldırılacak zamanında giderilmiş olduğunu garanti var. sunuyoruz.</span><span class="sxs-lookup"><span data-stu-id="ff990-110">We offer no guarantee there that your issue will be addressed or resolved in a timely manner.</span></span>
<span data-ttu-id="ff990-111">Hemen ilgilenilmesi gereken bir sorununuz varsa, Geleneksel, Ücretli destek seçenekleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff990-111">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="ff990-112">PowerShell Core yaşam döngüsü</span><span class="sxs-lookup"><span data-stu-id="ff990-112">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="ff990-113">PowerShell Core benimseme [Microsoft Modern yaşam döngüsü ilkesi][modern].</span><span class="sxs-lookup"><span data-stu-id="ff990-113">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="ff990-114">Bu destek yaşam döngüsü, müşterilerin en yeni sürümlerinin güncel tutmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ff990-114">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="ff990-115">PowerShell Core sürüm 6.x dalını yaklaşık altı ayda güncelleştirilir (örneğin 6.0, 6.1, 6.2, vs.)</span><span class="sxs-lookup"><span data-stu-id="ff990-115">The version 6.x branch of PowerShell Core will be updated approximately once every six months (e.g. 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ff990-116">Her yeni bir ikincil sürüm sonra destek almaya devam etmek için altı ay içinde güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff990-116">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="ff990-117">1 Temmuz 2018'de PowerShell Core 6.1 yayımlandığında Örneğin, 1 Ocak desteğin sürmesi için 2019 tarafından PowerShell Core 6.1 için güncelleştirilecek beklediğiniz.</span><span class="sxs-lookup"><span data-stu-id="ff990-117">For example, if PowerShell Core 6.1 is released on July 1st, 2018, you would be expected to update to PowerShell Core 6.1 by January 1st, 2019 to maintain support.</span></span>

![PowerShell Core dal yaşam döngüsü][lifecycle-chart]

<span data-ttu-id="ff990-119">Microsoft müşterilere 12 ay (yani, PowerShell Core) ürün desteği kaldırmadan önce bildirimde, Modern yaşam döngüsü ilkesi de gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ff990-119">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (i.e. PowerShell Core).</span></span>

<span data-ttu-id="ff990-120">Sonuç olarak, PowerShell Core, "uzun süreli bakım" olmadığını benimseyin bekliyoruz burada biz içerseydi yalnızca Bakım ve güvenlik yaklaşımı güncelleştirmeleri belirli bir dal/sürümünü 6.x desteği sayesinde sizde.</span><span class="sxs-lookup"><span data-stu-id="ff990-120">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach where we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="ff990-121">Desteklenen platformlar</span><span class="sxs-lookup"><span data-stu-id="ff990-121">Supported platforms</span></span>

<span data-ttu-id="ff990-122">Lütfen PowerShell Core kullanmakta olduğunuz sürümünü resmi olarak desteklenen platformdan görmek için aşağıdaki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="ff990-122">Please see the following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="ff990-123">Topluluğumuza da bazı platformlar için paketleri katkılarıyla, ancak resmi olarak desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="ff990-123">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="ff990-124">Bu paketleri olarak işaretlenmiş `Community` tabloda.</span><span class="sxs-lookup"><span data-stu-id="ff990-124">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="ff990-125">Olarak listelenen platformların `Experimental` resmi olarak desteklenmez, ancak deneme ve geri bildirim için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ff990-125">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="ff990-126">6.0</span><span class="sxs-lookup"><span data-stu-id="ff990-126">6.0</span></span>         | <span data-ttu-id="ff990-127">6.1</span><span class="sxs-lookup"><span data-stu-id="ff990-127">6.1</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="ff990-128">Windows 7, 8.1 ve 10</span><span class="sxs-lookup"><span data-stu-id="ff990-128">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="ff990-129">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-129">Supported</span></span>   | <span data-ttu-id="ff990-130">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-130">Supported</span></span>   |
| <span data-ttu-id="ff990-131">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="ff990-131">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="ff990-132">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-132">Supported</span></span>   | <span data-ttu-id="ff990-133">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-133">Supported</span></span>   |
| <span data-ttu-id="ff990-134">[Windows Server yarı yıllık kanal][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="ff990-134">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="ff990-135">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-135">Supported</span></span>   | <span data-ttu-id="ff990-136">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-136">Supported</span></span>   |
| <span data-ttu-id="ff990-137">Ubuntu 14.04 ve 16.04</span><span class="sxs-lookup"><span data-stu-id="ff990-137">Ubuntu 14.04 and, 16.04</span></span>                           | <span data-ttu-id="ff990-138">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-138">Supported</span></span>   | <span data-ttu-id="ff990-139">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-139">Supported</span></span>   |
| <span data-ttu-id="ff990-140">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ff990-140">Ubuntu 18.04</span></span>                                      |             | <span data-ttu-id="ff990-141">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-141">Supported</span></span>   |
| <span data-ttu-id="ff990-142">Ubuntu 18.10 (aracılığıyla yaslama paketi)</span><span class="sxs-lookup"><span data-stu-id="ff990-142">Ubuntu 18.10 (via Snap Package)</span></span>                   |             | <span data-ttu-id="ff990-143">Topluluk</span><span class="sxs-lookup"><span data-stu-id="ff990-143">Community</span></span>   |
| <span data-ttu-id="ff990-144">Debian 8,7 + ve 9</span><span class="sxs-lookup"><span data-stu-id="ff990-144">Debian 8.7+, and 9</span></span>                                | <span data-ttu-id="ff990-145">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-145">Supported</span></span>   | <span data-ttu-id="ff990-146">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-146">Supported</span></span>   |
| <span data-ttu-id="ff990-147">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ff990-147">CentOS 7</span></span>                                          | <span data-ttu-id="ff990-148">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-148">Supported</span></span>   | <span data-ttu-id="ff990-149">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-149">Supported</span></span>   |
| <span data-ttu-id="ff990-150">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="ff990-150">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="ff990-151">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-151">Supported</span></span>   | <span data-ttu-id="ff990-152">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-152">Supported</span></span>   |
| <span data-ttu-id="ff990-153">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="ff990-153">OpenSUSE 42.3</span></span>                                     | <span data-ttu-id="ff990-154">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-154">Supported</span></span>   | <span data-ttu-id="ff990-155">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-155">Supported</span></span>   |
| <span data-ttu-id="ff990-156">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="ff990-156">Fedora 27</span></span>                                         | <span data-ttu-id="ff990-157">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-157">Supported</span></span>   | <span data-ttu-id="ff990-158">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-158">Supported</span></span>   |
| <span data-ttu-id="ff990-159">28 fedora</span><span class="sxs-lookup"><span data-stu-id="ff990-159">Fedora 28</span></span>                                         |             | <span data-ttu-id="ff990-160">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-160">Supported</span></span>   |
| <span data-ttu-id="ff990-161">macOS 10.12 +</span><span class="sxs-lookup"><span data-stu-id="ff990-161">macOS 10.12+</span></span>                                      | <span data-ttu-id="ff990-162">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-162">Supported</span></span>   | <span data-ttu-id="ff990-163">Desteklenir</span><span class="sxs-lookup"><span data-stu-id="ff990-163">Supported</span></span>   |
| <span data-ttu-id="ff990-164">Arch</span><span class="sxs-lookup"><span data-stu-id="ff990-164">Arch</span></span>                                              | <span data-ttu-id="ff990-165">Topluluk</span><span class="sxs-lookup"><span data-stu-id="ff990-165">Community</span></span>   | <span data-ttu-id="ff990-166">Topluluk</span><span class="sxs-lookup"><span data-stu-id="ff990-166">Community</span></span>   |
| <span data-ttu-id="ff990-167">Raspbian</span><span class="sxs-lookup"><span data-stu-id="ff990-167">Raspbian</span></span>                                          | <span data-ttu-id="ff990-168">Deneysel</span><span class="sxs-lookup"><span data-stu-id="ff990-168">Experimental</span></span>| <span data-ttu-id="ff990-169">Topluluk</span><span class="sxs-lookup"><span data-stu-id="ff990-169">Community</span></span>   |
| <span data-ttu-id="ff990-170">Kali</span><span class="sxs-lookup"><span data-stu-id="ff990-170">Kali</span></span>                                              | <span data-ttu-id="ff990-171">Topluluk</span><span class="sxs-lookup"><span data-stu-id="ff990-171">Community</span></span>   | <span data-ttu-id="ff990-172">Topluluk</span><span class="sxs-lookup"><span data-stu-id="ff990-172">Community</span></span>   |
| <span data-ttu-id="ff990-173">AppImage (birden çok Linux platformlarında çalışır)</span><span class="sxs-lookup"><span data-stu-id="ff990-173">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="ff990-174">Topluluk</span><span class="sxs-lookup"><span data-stu-id="ff990-174">Community</span></span>   | <span data-ttu-id="ff990-175">Topluluk</span><span class="sxs-lookup"><span data-stu-id="ff990-175">Community</span></span>   |
| [<span data-ttu-id="ff990-176">Paket Yasla</span><span class="sxs-lookup"><span data-stu-id="ff990-176">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="ff990-177">Bkz. Not</span><span class="sxs-lookup"><span data-stu-id="ff990-177">See note</span></span>    | <span data-ttu-id="ff990-178">Bkz. Not</span><span class="sxs-lookup"><span data-stu-id="ff990-178">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="ff990-179">Yaslama paketleri bir süre için Deneysel olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ff990-179">Snap packages will be experimental for a period.</span></span>  <span data-ttu-id="ff990-180">Sonra ek yeni destek sorunları sunmaz, destek paketini çalıştırmakta olduğunuz dağıtım izleyeceği başarılara duyuyoruz.</span><span class="sxs-lookup"><span data-stu-id="ff990-180">After, we are confident that Snap does not introduce new support issues, the support will follow the distribution you are running the package on.</span></span>

## <a name="platform-which-are-out-of-support"></a><span data-ttu-id="ff990-181">Destek kapsamı dışında olan platform</span><span class="sxs-lookup"><span data-stu-id="ff990-181">Platform which are out of support</span></span>

<span data-ttu-id="ff990-182">Platform sürümü uç platformu sahibi tarafından tanımlandığı şekilde yaşam ulaştığında, PowerShell Core, platform sürümü için destek sağlamak de sona erecek.</span><span class="sxs-lookup"><span data-stu-id="ff990-182">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to provide support for that platform version.</span></span> <span data-ttu-id="ff990-183">Daha önce yayımlanmış paketleri erişim ancak resmi destek ihtiyaç duyan müşteriler için kullanılabilir halde kalacak ve herhangi bir türdeki güncelleştirmeleri artık sağlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="ff990-183">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="ff990-184">Bu nedenle, aşağıdaki sürümleri dağıtım sahipleri tarafından sonlandırıldı ve desteklenmeyen desteği.</span><span class="sxs-lookup"><span data-stu-id="ff990-184">Therefore, support for the following versions was ended by the distribution owners and are not supported.</span></span>

| <span data-ttu-id="ff990-185">İşletim sistemi</span><span class="sxs-lookup"><span data-stu-id="ff990-185">OS</span></span>       | <span data-ttu-id="ff990-186">Sürüm</span><span class="sxs-lookup"><span data-stu-id="ff990-186">Version</span></span> | <span data-ttu-id="ff990-187">Kullanım ömrü</span><span class="sxs-lookup"><span data-stu-id="ff990-187">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="ff990-188">Fedora</span><span class="sxs-lookup"><span data-stu-id="ff990-188">Fedora</span></span>   | <span data-ttu-id="ff990-189">24</span><span class="sxs-lookup"><span data-stu-id="ff990-189">24</span></span>      | [<span data-ttu-id="ff990-190">Ağustos 2017</span><span class="sxs-lookup"><span data-stu-id="ff990-190">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="ff990-191">Fedora</span><span class="sxs-lookup"><span data-stu-id="ff990-191">Fedora</span></span>   | <span data-ttu-id="ff990-192">25</span><span class="sxs-lookup"><span data-stu-id="ff990-192">25</span></span>      | [<span data-ttu-id="ff990-193">Aralık 2017</span><span class="sxs-lookup"><span data-stu-id="ff990-193">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="ff990-194">Fedora</span><span class="sxs-lookup"><span data-stu-id="ff990-194">Fedora</span></span>   | <span data-ttu-id="ff990-195">26</span><span class="sxs-lookup"><span data-stu-id="ff990-195">26</span></span>      | [<span data-ttu-id="ff990-196">Mayıs 2018</span><span class="sxs-lookup"><span data-stu-id="ff990-196">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="ff990-197">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="ff990-197">openSUSE</span></span> | <span data-ttu-id="ff990-198">42.1</span><span class="sxs-lookup"><span data-stu-id="ff990-198">42.1</span></span>    | [<span data-ttu-id="ff990-199">Mayıs 2017</span><span class="sxs-lookup"><span data-stu-id="ff990-199">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="ff990-200">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="ff990-200">openSUSE</span></span> | <span data-ttu-id="ff990-201">42.2</span><span class="sxs-lookup"><span data-stu-id="ff990-201">42.2</span></span>    | [<span data-ttu-id="ff990-202">Ocak 2018</span><span class="sxs-lookup"><span data-stu-id="ff990-202">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="ff990-203">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="ff990-203">Ubuntu</span></span>   | <span data-ttu-id="ff990-204">16.10</span><span class="sxs-lookup"><span data-stu-id="ff990-204">16.10</span></span>   | [<span data-ttu-id="ff990-205">Temmuz 2017</span><span class="sxs-lookup"><span data-stu-id="ff990-205">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="ff990-206">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="ff990-206">Ubuntu</span></span>   | <span data-ttu-id="ff990-207">17.04</span><span class="sxs-lookup"><span data-stu-id="ff990-207">17.04</span></span>   | [<span data-ttu-id="ff990-208">Ocak 2018</span><span class="sxs-lookup"><span data-stu-id="ff990-208">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="ff990-209">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="ff990-209">Ubuntu</span></span>   | <span data-ttu-id="ff990-210">17.10</span><span class="sxs-lookup"><span data-stu-id="ff990-210">17.10</span></span>   | [<span data-ttu-id="ff990-211">Temmuz 2018</span><span class="sxs-lookup"><span data-stu-id="ff990-211">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |

## <a name="notes-on-licensing"></a><span data-ttu-id="ff990-212">Lisanslama notları</span><span class="sxs-lookup"><span data-stu-id="ff990-212">Notes on licensing</span></span>

<span data-ttu-id="ff990-213">PowerShell Core altında yayımlanır [MIT lisansı][].</span><span class="sxs-lookup"><span data-stu-id="ff990-213">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="ff990-214">Bu lisansı altında ve bir Ücretli bir destek sözleşmesi olmaması, kullanıcılar için sınırlı [topluluk desteği][].</span><span class="sxs-lookup"><span data-stu-id="ff990-214">Under this license, and in the absence of a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="ff990-215">Topluluk desteği sayesinde, Microsoft yanıtlama hızı veya düzeltmeleri garanti vermez.</span><span class="sxs-lookup"><span data-stu-id="ff990-215">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="ff990-216">Windows PowerShell Modülü</span><span class="sxs-lookup"><span data-stu-id="ff990-216">Windows PowerShell Module</span></span>

<span data-ttu-id="ff990-217">Desteklemek için bu modülleri PowerShell Core açıkça desteklemedikçe PowerShell Core diğer ürün modüllerle kapsamaz.</span><span class="sxs-lookup"><span data-stu-id="ff990-217">Support for PowerShell Core does not extend to other product modules unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="ff990-218">Örneğin, kullanarak `ActiveDirectory` desteklenmeyen bir senaryo Windows Server'ın bir parçası olduğu gibi birlikte gelen modülü.</span><span class="sxs-lookup"><span data-stu-id="ff990-218">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="ff990-219">Ancak, açıkça PowerShell Core desteklemeyen modülleri bazı durumlarda uyumlu olabilir.</span><span class="sxs-lookup"><span data-stu-id="ff990-219">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="ff990-220">Yükleyerek [ `WindowsPSModulePath` ][] modülü, Windows PowerShell ekleyebilir `PSModulePath` , PowerShell Core `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="ff990-220">By installing the [`WindowsPSModulePath`][] module, you can append the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="ff990-221">İlk olarak, yükleme `WindowsPSModulePath` modülü PowerShell Galerisi'ndeki:</span><span class="sxs-lookup"><span data-stu-id="ff990-221">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="ff990-222">Bu modülü yükledikten sonra çalıştırın `Add-WindowsPSModulePath` eklemek için Windows PowerShell cmdlet'ini `PSModulePath` PowerShell Core için:</span><span class="sxs-lookup"><span data-stu-id="ff990-222">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

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
['WindowsPSModulePath']: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
