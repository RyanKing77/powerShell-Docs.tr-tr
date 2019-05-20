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
# <a name="powershell-core-support-lifecycle"></a>PowerShell Core Destek Yaşam Döngüsü

PowerShell Core araçları ve bileşenlerin sevk, yüklü ve Windows PowerShell üzerinden ayrı olarak yapılandırılmış ayrı bir kümesidir.
Bu nedenle, PowerShell Core Windows 7/8.1/10 veya Windows Server Lisans anlaşmalarındaki dahil edilmez.

PowerShell Core gibi geleneksel Microsoft destek sözleşmeleri altında ancak desteklenen [Premier][], [Microsoft Kurumsal Anlaşma][enterprise-agreement]ve [Microsoft Yazılım Güvencesi][assurance].
İçin de ödeme yapabilirsiniz [Yardımlı Destek][] sorununuzu bir destek isteği dosyalama tarafından PowerShell Core için.

## <a name="community-support"></a>Topluluk desteği

Ayrıca sunuyoruz [topluluk desteği][] burada dosyası bir sorun, hata veya özellik isteği GitHub üzerinde.
Ayrıca, genel diğer topluluk üyelerinden Yardım bulabilirsiniz [Microsoft Community][] veya Microsoft [PowerShell Teknoloji Topluluğu][].
Topluluk adres veya zamanında sorununuzu garantisi vardır sunuyoruz.
Hemen ilgilenilmesi gereken bir sorununuz varsa, Geleneksel, Ücretli destek seçenekleri kullanmanız gerekir.

## <a name="lifecycle-of-powershell-core"></a>PowerShell Core yaşam döngüsü

PowerShell Core benimseme [Microsoft Modern yaşam döngüsü ilkesi][modern].
Bu destek yaşam döngüsü, müşterilerin en yeni sürümlerinin güncel tutmak için tasarlanmıştır.

PowerShell Core sürüm 6.x dalını yaklaşık altı ayda güncelleştirilir (örnekler: 6.0, 6.1, 6.2, vs.)

> [!IMPORTANT]
> Her yeni bir ikincil sürüm sonra destek almaya devam etmek için altı ay içinde güncelleştirmeniz gerekir.

1 Temmuz 2018'de PowerShell Core 6.1 yayımlandığında Örneğin, 1 Ocak desteğin sürmesi için 2019 tarafından PowerShell Core 6.1 için güncelleştirilecek beklediğiniz.

> [!IMPORTANT]
> Destek almaya devam etmek için her yeni bir düzeltme eki sürüm sonraki 30 gün içinde güncelleştirmeniz gerekir.

Örneğin, PowerShell Core 6.1 çalıştırıyorsanız ve 6.1.3 19 Şubat 2019 üzerinde yayımlanan PowerShell desteğin sürmesi için yayımlanmasının ardından 30 gün ise çekirdek 6.1.3 21 Mart 2019 tarafından güncelleştirmek için beklediğiniz.
Gerekli tüm düzeltmeleri bulunamazsa, düzeltmeler bizim sonraki toplu güncelleştirmede yayınlanacaktır.

Microsoft müşterilere 12 ay (diğer bir deyişle, PowerShell Core) ürün desteği kaldırmadan önce bildirimde, Modern yaşam döngüsü ilkesi de gerektirir.

Sonuç olarak, PowerShell Core, "uzun süreli bakım" olmadığını benimseyin bekliyoruz yaklaşım.
Hizmet Bu yaklaşımda, biz 6.x'ın belirli bir dal/sürümünde destek kalmak için yalnızca Bakım ve güvenlik güncelleştirmeleri gerekir.

## <a name="supported-platforms"></a>Desteklenen platformlar

PowerShell Core kullanmakta olduğunuz sürümünü platformdan görmek için aşağıdaki tabloyu resmi olarak desteklenmektedir.

Topluluğumuza da bazı platformlar için paketleri katkılarıyla, ancak resmi olarak desteklenmez.
Bu paketleri olarak işaretlenmiş `Community` tabloda.

Olarak listelenen platformların `Experimental` resmi olarak desteklenmez, ancak deneme ve geri bildirim için kullanılabilir.

|                                                   | 6.1         | 6.2         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 ve 10                            | Desteklenir   | Desteklenir   |
| Windows Server 2008 R2, 2012 R2, 2016             | Desteklenir   | Desteklenir   |
| [Windows Server yarı yıllık kanal][semi-annual] | Desteklenir   | Desteklenir   |
| Ubuntu 16.04 ve 18.04                            | Desteklenir   | Desteklenir   |
| Ubuntu 18.10 (aracılığıyla yaslama paketi)                   | Topluluk   | Topluluk   |
| Debian 9                                          | Desteklenir   | Desteklenir   |
| CentOS 7                                          | Desteklenir   | Desteklenir   |
| Red Hat Enterprise Linux 7                        | Desteklenir   | Desteklenir   |
| openSUSE 42.3                                     | Desteklenir   | Desteklenir   |
| Fedora 28                                         | Desteklenir   | Desteklenir   |
| macOS 10.12 +                                      | Desteklenir   | Desteklenir   |
| Arch                                              | Topluluk   | Topluluk   |
| Raspbian                                          | Topluluk   | Topluluk   |
| Kali                                              | Topluluk   | Topluluk   |
| AppImage (birden çok Linux platformlarında çalışır)     | Topluluk   | Topluluk   |
| [Paket Yasla](https://snapcraft.io/powershell)   | Bkz. Not    | Bkz. Not    |

> [!NOTE]
> Paketleri desteklenir Yasla aynı dağıtım paketi çalıştırdığınız.

## <a name="powershell-release-end-of-life"></a>PowerShell sürüm sona erecek

Temel [PowerShell Core yaşam döngüsü](#lifecycle-of-powershell-core), aşağıdaki tabloda, çeşitli sürüm artık desteklenir tarihleri listelenmektedir.

| Sürüm | Kullanım ömrü                   |
|---------|-------------------------------|
| 6.0     | 13 Şubat 2019             |
| 6.1     | 28 Eylül 2019            |
| 6.2     | 7 yayınlar sonra 6 ay     |

## <a name="platforms-which-are-out-of-support"></a>Desteklenmeyen platformlar

Platform sürümü platform sahibi tarafından tanımlanan son yaşam ulaştığında, PowerShell Core bu platform sürümü desteklemek de sona erecek.
Daha önce yayımlanmış paketleri erişim ancak resmi destek ihtiyaç duyan müşteriler için kullanılabilir halde kalacak ve herhangi bir türdeki güncelleştirmeleri artık sağlanacaktır.

Bu nedenle, dağıtım sahipleri aşağıdaki sürümleri için destek sona erdi ve desteklenmez.

| İşletim sistemi       | Sürüm | Kullanım ömrü                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 24      | [Ağustos 2017](https://fedoramagazine.org/fedora-24-eol/)                                    |
| Fedora   | 25      | [Aralık 2017](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 26      | [Mayıs 2018](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| openSUSE | 42.1    | [Mayıs 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| openSUSE | 42.2    | [Ocak 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| Ubuntu   | 16.10   | [Temmuz 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| Ubuntu   | 17.04   | [Ocak 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 17.10   | [Temmuz 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| Debian   | 8       | [Haziran 2018](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| Fedora   | 27      | [Kasım 2018](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| Ubuntu   | 14.04   | [Nisan 2019](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a>Lisanslama notları

PowerShell Core altında yayımlanır [MIT lisansı][].
Bu lisansı altında ve bir Ücretli destek anlaşması olmadan kullanıcılar sınırlı [topluluk desteği][].
Topluluk desteği sayesinde, Microsoft yanıtlama hızı veya düzeltmeleri garanti vermez.

## <a name="windows-powershell-module"></a>Windows PowerShell Modülü

Desteklemek için bu modülleri PowerShell Core açıkça desteklemedikçe ürün modülleri PowerShell Core içermez.
Örneğin, kullanarak `ActiveDirectory` desteklenmeyen bir senaryo Windows Server'ın bir parçası olduğu gibi birlikte gelen modülü.

Ancak, açıkça PowerShell Core desteklemeyen modülleri bazı durumlarda uyumlu olabilir.
Yükleyerek [ `WindowsPSModulePath` ][] modülü, Windows PowerShell ekleyebilirsiniz `PSModulePath` , PowerShell Core `PSModulePath`.

İlk olarak, yükleme `WindowsPSModulePath` modülü PowerShell Galerisi'ndeki:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Bu modülü yükledikten sonra çalıştırın `Add-WindowsPSModulePath` eklemek için Windows PowerShell cmdlet'ini `PSModulePath` PowerShell Core için:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a>Deneysel Özellikler

[Deneysel Özellikler][] sınırlıdır [topluluk desteği](#community-support).

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[Topluluk desteği]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell Teknoloji Topluluğu]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[Yardımlı Destek]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT lisansı]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Deneysel Özellikler]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
