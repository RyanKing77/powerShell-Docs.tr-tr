# <a name="powershell-core-support-lifecycle"></a>PowerShell Core Destek Yaşam Döngüsü

PowerShell Core araçları ve bileşenlerin sevk, yüklü ve Windows PowerShell üzerinden ayrı olarak yapılandırılmış ayrı bir kümesidir.
Bu nedenle, PowerShell Core Windows 7/8.1/10 veya Windows Server Lisans anlaşmalarındaki dahil edilmez.

PowerShell Core gibi geleneksel Microsoft destek sözleşmeleri altında ancak desteklenen [Premier][], [Microsoft Kurumsal Anlaşma][enterprise-agreement]ve [Microsoft Yazılım Güvencesi][assurance].
İçin de ödeme yapabilirsiniz [Yardımlı Destek][] sorununuzu bir destek isteği dosyalama tarafından PowerShell Core için.

Ayrıca sunuyoruz [topluluk desteği][] burada dosyası bir sorun, hata veya özellik isteği GitHub üzerinde.
Alternatif olarak, genel diğer topluluk üyelerinden Yardım bulabilirsiniz [Microsoft Community][] veya Microsoft [PowerShell Teknoloji Topluluğu][].
Sorununuzu ele veya kaldırılacak zamanında giderilmiş olduğunu garanti var. sunuyoruz.
Hemen ilgilenilmesi gereken bir sorununuz varsa, Geleneksel, Ücretli destek seçenekleri kullanmanız gerekir.

## <a name="lifecycle-of-powershell-core"></a>PowerShell Core yaşam döngüsü

PowerShell Core benimseme [Microsoft Modern yaşam döngüsü ilkesi][modern].
Bu destek yaşam döngüsü, müşterilerin en yeni sürümlerinin güncel tutmak için tasarlanmıştır.

PowerShell Core sürüm 6.x dalını yaklaşık altı ayda güncelleştirilir (örneğin 6.0, 6.1, 6.2, vs.)

> [!IMPORTANT]
> Her yeni bir ikincil sürüm sonra destek almaya devam etmek için altı ay içinde güncelleştirmeniz gerekir.

1 Temmuz 2018'de PowerShell Core 6.1 yayımlandığında Örneğin, 1 Ocak desteğin sürmesi için 2019 tarafından PowerShell Core 6.1 için güncelleştirilecek beklediğiniz.

![PowerShell Core dal yaşam döngüsü][lifecycle-chart]

Microsoft müşterilere 12 ay (yani, PowerShell Core) ürün desteği kaldırmadan önce bildirimde, Modern yaşam döngüsü ilkesi de gerektirir.

Sonuç olarak, PowerShell Core, "uzun süreli bakım" olmadığını benimseyin bekliyoruz burada biz içerseydi yalnızca Bakım ve güvenlik yaklaşımı güncelleştirmeleri belirli bir dal/sürümünü 6.x desteği sayesinde sizde.

## <a name="supported-platforms"></a>Desteklenen platformlar

Lütfen PowerShell Core kullanmakta olduğunuz sürümünü resmi olarak desteklenen platformdan görmek için aşağıdaki tabloya bakın.

Topluluğumuza da bazı platformlar için paketleri katkılarıyla, ancak resmi olarak desteklenmez.
Bu paketleri olarak işaretlenmiş `Community` tabloda.

Olarak listelenen platformların `Experimental` resmi olarak desteklenmez, ancak deneme ve geri bildirim için kullanılabilir.

|                                                   | 6.0         | 6.1         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 ve 10                            | Desteklenir   | Desteklenir   |
| Windows Server 2008 R2, 2012 R2, 2016             | Desteklenir   | Desteklenir   |
| [Windows Server yarı yıllık kanal][semi-annual] | Desteklenir   | Desteklenir   |
| Ubuntu 14.04 ve 16.04                           | Desteklenir   | Desteklenir   |
| Ubuntu 17.10 ve 18.04                           |             | Desteklenir   |
| Debian 8,7 + ve 9                                | Desteklenir   | Desteklenir   |
| CentOS 7                                          | Desteklenir   | Desteklenir   |
| Red Hat Enterprise Linux 7                        | Desteklenir   | Desteklenir   |
| OpenSUSE 42.2                                     | Desteklenir   | Desteklenir   |
| Fedora 27                                         | Desteklenir   | Desteklenir   |
| 28 fedora                                         |             | Desteklenir   |
| macOS 10.12 +                                      | Desteklenir   | Desteklenir   |
| Arch                                              | Topluluk   | Topluluk   |
| Raspbian                                          | Deneysel| Topluluk   |
| Kali                                              | Topluluk   | Topluluk   |
| AppImage (birden çok Linux platformlarında çalışır)     | Topluluk   | Topluluk   |

## <a name="platform-which-are-out-of-support"></a>Destek kapsamı dışında olan platform

Platform sürümü uç platformu sahibi tarafından tanımlandığı şekilde yaşam ulaştığında, PowerShell Core, platform sürümü için destek sağlamak de sona erecek. Daha önce yayımlanmış paketleri erişim ancak resmi destek ihtiyaç duyan müşteriler için kullanılabilir halde kalacak ve herhangi bir türdeki güncelleştirmeleri artık sağlanacaktır.

Bu nedenle, aşağıdaki sürümleri dağıtım sahipleri tarafından sonlandırıldı ve desteklenmeyen desteği.

| İşletim sistemi       | Sürüm | Kullanım ömrü                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 26      | [Mayıs 2018](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| Fedora   | 25      | [Aralık 2017](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 24      | [Ağustos 2017](https://fedoramagazine.org/fedora-24-eol/)                                    |
| OpenSUSE | 42.2    | [Ocak 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| OpenSUSE | 42.1    | [Mayıs 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| Ubuntu   | 17.04   | [Ocak 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 16.10   | [Temmuz 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |

## <a name="notes-on-licensing"></a>Lisanslama notları

PowerShell Core altında yayımlanır [MIT lisansı][].
Bu lisansı altında ve bir Ücretli bir destek sözleşmesi olmaması, kullanıcılar için sınırlı [topluluk desteği][].
Topluluk desteği sayesinde, Microsoft yanıtlama hızı veya düzeltmeleri garanti vermez.

## <a name="windows-powershell-module"></a>Windows PowerShell Modülü

Desteklemek için bu modülleri PowerShell Core açıkça desteklemedikçe PowerShell Core diğer ürün modüllerle kapsamaz.
Örneğin, kullanarak `ActiveDirectory` desteklenmeyen bir senaryo Windows Server'ın bir parçası olduğu gibi birlikte gelen modülü.

Ancak, açıkça PowerShell Core desteklemeyen modülleri bazı durumlarda uyumlu olabilir.
Yükleyerek [ `WindowsPSModulePath` ][] modülü, Windows PowerShell ekleyebilir `PSModulePath` , PowerShell Core `PSModulePath`.

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
['WindowsPSModulePath']: https://www.powershellgallery.com/packages/WindowsPSModulePath/
