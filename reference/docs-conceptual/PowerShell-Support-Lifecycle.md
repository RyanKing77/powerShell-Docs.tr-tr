---
title: PowerShell Core Destek Yaşam Döngüsü
description: PowerShell Core desteğini yöneten ilkeler
ms.date: 08/06/2018
ms.openlocfilehash: 60999ed54ca3be15232ffee3ab0c49cb94873a8f
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986749"
---
# <a name="powershell-core-support-lifecycle"></a>PowerShell Core Destek Yaşam Döngüsü

PowerShell Core, Windows PowerShell 'den ayrı olarak gönderilen, yüklenen ve yapılandırılan ayrı bir araç ve bileşen kümesidir. Bu nedenle, PowerShell Core, Windows 7/8.1/10 veya Windows Server Lisanslama sözleşmelerine dahil değildir.

Bununla birlikte, PowerShell Core, [Premier][], [Microsoft Kurumsal sözleşmeleri][enterprise-agreement]ve [Microsoft yazılım güvencesi][assurance]dahil geleneksel Microsoft destek anlaşmaları altında desteklenir.
Sorun için bir destek isteği kaydederek PowerShell Core için [yardımlı destek][] için de ödeme yapabilirsiniz.

## <a name="community-support"></a>Topluluk desteği

Ayrıca, GitHub üzerinde bir sorun, hata veya özellik isteği olarak dosya oluşturabileceğiniz [topluluk desteğiyle][] sunuyoruz.
Ayrıca, genel [Microsoft Topluluğu][] veya Microsoft [PowerShell teknik topluluğu][]'nda topluluğun diğer üyelerinden yardım bulabilirsiniz. Topluluğun sorununuzu zamanında ele alabilmesini veya çözeceğimizi garanti etmez. Hemen ilgilenilmesi gereken bir sorununuz varsa, geleneksel, ücretli destek seçeneklerini kullanmanız gerekir.

## <a name="lifecycle-of-powershell-core"></a>PowerShell Core yaşam döngüsü

PowerShell Core, [Microsoft modern yaşam döngüsü ilkesini][modern]benimseme. Bu destek yaşam döngüsü, müşterileri en son sürümlerle güncel tutmaya yöneliktir.

PowerShell Core sürümü 6. x dalı her altı ayda bir ve yaklaşık olarak güncelleştirilir (örnek: 6,0, 6,1, 6,2, vb.)

> [!IMPORTANT]
> Destek almaya devam etmek için her yeni alt sürüm sürümünden sonra altı ay içinde güncelleştirmeniz gerekir.

Örneğin, PowerShell Core 6,1, 1 Temmuz 2018 ' de yayınlanmışsa, destek sağlamak için 1 Ocak 2019 tarihine kadar PowerShell Core 6,1 ' i güncelleştirmeniz beklenmektedir.

> [!IMPORTANT]
> Destek almaya devam etmek için her yeni düzeltme sürümü sürümünden 30 gün sonra güncelleştirmeniz gerekir.

Örneğin, PowerShell Core 6,1 çalıştırıyorsanız ve 6.1.3 19 Şubat 2019 ' de yayımlandıysa, destek sağlamak için sürümden sonra 30 gün sonra, PowerShell Core 6.1.3 ' yi 21 Mart 2019 ' ye güncelleştirmeniz beklenmektedir. Gerekli bir düzeltme bulunursa, düzeltmeler bir sonraki toplu güncelleştirmede yayımlanır.

Modern yaşam döngüsü Ilkesi, Microsoft 'un müşterilere bir ürün (yani, PowerShell çekirdeği) için destek vermeden önce 12 ay bildirimi vermesini de gerektirir.

Sonuç olarak, PowerShell Core 'un uzun süreli bakım yaklaşımını benimsemesini bekledik. Bu bakım yaklaşımında, yalnızca bakım ve güvenlik güncelleştirmelerinin belirli bir sürüm/6. x sürümü üzerinde kalması gerekir.

## <a name="supported-platforms"></a>Desteklenen platformlar

Platformunuzun ve PowerShell Core sürümünüzün resmi olarak desteklenip desteklenmediğini doğrulamak için aşağıdaki tabloya bakın.

Topluluğumuz bazı platformlar için de paketlere katkıda bulunur, ancak resmi olarak desteklenmez. Bu paketler tabloda olarak `Community` işaretlenir.

Resmi olarak `Experimental` desteklenmeyen, ancak deneme ve geri bildirimde bulunan platformlar.

| Platform                                          | 6.1         | 6.2         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8,1 ve 10                            | Desteklenir   | Desteklenir   |
| Windows Server 2008 R2, 2012 R2, 2016             | Desteklenir   | Desteklenir   |
| [Windows Server yarı yıllık Kanal][semi-annual] | Desteklenir   | Desteklenir   |
| Ubuntu 16,04 ve 18,04                            | Desteklenir   | Desteklenir   |
| Ubuntu 18,10 (Snap paketi aracılığıyla)                   | Topluluk   | Topluluk   |
| Ubuntu 19,04 (Snap paketi aracılığıyla)                   | Topluluk   | Topluluk   |
| Debian 9                                          | Desteklenir   | Desteklenir   |
| CentOS 7                                          | Desteklenir   | Desteklenir   |
| Red Hat Enterprise Linux 7                        | Desteklenir   | Desteklenir   |
| openSUSE 42,3                                     | Desteklenir   | Desteklenir   |
| Fedora 28                                         | Desteklenir   | Desteklenir   |
| macOS 10.12 +                                      | Desteklenir   | Desteklenir   |
| Mimari                                              | Topluluk   | Topluluk   |
| Raspbian                                          | Topluluk   | Topluluk   |
| Kalı                                              | Topluluk   | Topluluk   |
| Appımage (birden çok Linux platformunda geçerlidir)      | Topluluk   | Topluluk   |
| [Yaslama paketi](https://snapcraft.io/powershell)   | Bkz. nota    | Bkz. nota    |

> [!NOTE]
> Yaslama paketleri, paketini çalıştırdığınız dağıtımla aynı şekilde desteklenir.

## <a name="powershell-releases-end-of-life"></a>PowerShell yayınları yaşam sonu

[PowerShell Core yaşam](#lifecycle-of-powershell-core)döngüsüne bağlı olarak, aşağıdaki tabloda, çeşitli yayınların artık desteklenmemesi için tarihleri listelenmektedir.

| Sürüm | Yaşam bitişi                   |
|---------|-------------------------------|
| 6.0     | 13 Şubat 2019             |
| 6.1     | 28 Eylül 2019            |
| 6.2     | 6 ay sonra 7 sürüm     |

## <a name="unsupported-platforms"></a>Desteklenmeyen platformlar

Platform sürümü, platform sahibi tarafından tanımlanan yaşam sonuna ulaştığında, PowerShell Core da bu platform sürümünü desteklemeyi de durduracaktır. Daha önce yayınlanan paketler, erişim gerektiren müşteriler, ancak resmi destek ve her türlü güncelleştirme için kullanılabilir olmaya devam edecektir.

Bu nedenle, dağıtım sahipleri aşağıdaki sürümler için desteği sona ermiştir ve desteklenmez.

| Platform | Sürüm | Yaşam sonu                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 24      | [Ağustos 2017](https://fedoramagazine.org/fedora-24-eol/)                                    |
| Fedora   | 25      | [Aralık 2017](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 26      | [Mayıs 2018](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| openSUSE | 42.1    | [Mayıs 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| openSUSE | 42,2    | [Ocak 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| Ubuntu   | 16,10   | [2017 Temmuz](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| Ubuntu   | 17,04   | [Ocak 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 17,10   | [2018 Temmuz](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| Debian   | 8       | [Haziran 2018](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| Fedora   | 27      | [2018 Kasım](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| Ubuntu   | 14.04   | [2019 Nisan](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a>Lisanslama hakkında notlar

PowerShell Core, [MıT lisansı][]altında serbest bırakıldı. Bu lisans kapsamında ve ücretli destek sözleşmesi olmadan kullanıcılar [topluluk desteğiyle][]sınırlandırılmıştır. Topluluk desteğiyle Microsoft, yanıt verme veya düzeltme garantisi vermez.

## <a name="windows-powershell-module"></a>Windows PowerShell modülü

PowerShell Core desteği, PowerShell Core 'u açıkça desteklemediğinden, bu modüller ürün modüllerini içermez. Örneğin, Windows Server 'ın `ActiveDirectory` bir parçası olarak gelen modülün kullanılması desteklenmeyen bir senaryodur.

Ancak, PowerShell çekirdeğini açıkça desteklemeyen modüller bazı durumlarda uyumlu olabilir. [`WindowsPSModulePath`][] Modülünü yükleyerek, PowerShell çekirdeğe `PSModulePath`Windows PowerShell `PSModulePath` ekleyebilirsiniz.

İlk olarak, PowerShell Galerisi `WindowsPSModulePath` modülü ' nden yüklemeniz gerekir:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Bu modülü yükledikten sonra, PowerShell Core `Add-WindowsPSModulePath` 'a Windows PowerShell `PSModulePath` eklemek için cmdlet 'ini çalıştırın:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a>Deneysel özellikler

[Deneysel Özellikler][] [topluluk desteğiyle](#community-support)sınırlıdır.

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[topluluk desteğiyle]: https://github.com/powershell/powershell/issues
[Microsoft Topluluğu]: https://answers.microsoft.com/
[PowerShell teknik topluluğu]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[Yardımlı destek]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MıT lisansı]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[' WindowsPSModulePath ']: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Deneysel özellikler]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
