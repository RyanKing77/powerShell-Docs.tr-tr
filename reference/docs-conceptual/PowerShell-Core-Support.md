# <a name="powershell-core-support-lifecycle"></a>PowerShell Core Destek Yaşam Döngüsü

PowerShell çekirdek araçları ve sevk, yüklü ve ayrı ayrı Windows Powershell'den yapılandırılmış bileşenleri ayrı bir kümesidir.
Bu nedenle, PowerShell çekirdeği Windows 7/8.1/10 veya Windows Server Lisans anlaşmalarındaki dahil edilmez.

PowerShell çekirdek de dahil olmak üzere geleneksel Microsoft destek Anlaşmalarınızda ancak, desteklenen [Premier][], [Microsoft Kurumsal anlaşmalarındaki][enterprise-agreement]ve [Microsoft Yazılım Güvencesi][assurance].
İçin ödeme yapabildiği [destekli Destek][] PowerShell sorununuz için bir destek isteği dosyalama tarafından çekirdek için.

Ayrıca sunuyoruz [topluluk desteği][] nerede dosyası bir sorunu, hata veya özellik isteği github'da.
Alternatif olarak, genel diğer topluluk üyelerinden Yardım bulabilirsiniz [Microsoft Community][] veya Microsoft [PowerShell teknik topluluk][].
Sorunu ele veya kaldırılacak zamanında çözümlendi, hiçbir garanti var. sunuyoruz.
Hemen ilgilenilmesi gereken bir sorun varsa, Geleneksel, ücretli bir destek seçenekleri kullanmanız gerekir.

## <a name="lifecycle-of-powershell-core"></a>PowerShell çekirdek yaşam döngüsü

PowerShell çekirdek benimsenmesi [Microsoft Modern yaşam döngüsü ilkesi][modern].
Bu destek yaşam döngüsü, müşterilerin en son sürümleri ile güncel kalmasını sağlamak için tasarlanmıştır.

PowerShell çekirdek sürüm 6.x dalı yaklaşık altı ayda bir güncelleştirilir (örneğin 6.0, 6.1, 6.2, vs.)

> [!IMPORTANT]
> Her yeni alt sürümü yayımlandıktan sonra destek almaya devam etmek için altı ay içinde güncelleştirmeniz gerekir.

1 Temmuz 2018 üzerinde PowerShell çekirdek 6.1 yayımlanırsa Örneğin, 1 Ocak, destek korumak için 2019 tarafından PowerShell çekirdek 6.1 güncelleştirmek için beklediğiniz.

![PowerShell çekirdek şube yaşam döngüsü][lifecycle-chart]

Modern yaşam döngüsü ilkesi ayrıca Microsoft müşterileri 12 ay ürün (yani PowerShell çekirdek) için destek sona erdirme önce bildirimde olmasını gerektirir.

Sonuç olarak, PowerShell çekirdek benimsemeye "uzun süreli bakım" bekliyoruz yaklaşım burada biz duyar yalnızca Bakımı ve güvenlik güncelleştirmeleri destek almak için belirli bir şube/sürümünü 6.x kalmak için.

## <a name="supported-platforms"></a>Desteklenen platformlar

PowerShell çekirdek resmi olarak aşağıdaki platformlarda desteklenir:

* Windows 7, 8.1 ve 10
* Windows Server 2008 R2, 2012 R2, 2016
* [Windows Server noktalı yıllık kanalı][semi-annual]
* Ubuntu 14.04 ve 16.04 17.04
* Debian 8.7 + ve 9
* CentOS 7
* Red Hat Enterprise Linux 7
* OpenSUSE 42.2
* Fedora 25 26
* macOS 10.12+

Topluluğumuz ayrıca aşağıdaki platformları için paketleri katıldığını, ancak bunlar resmi olarak suppported değildir:

* Linux arch
* Kali Linux
* AppImage (birden çok Linux platformlar üzerinde çalışır)

## <a name="notes-on-licensing"></a>Lisans üzerinde notları

PowerShell çekirdeği altında yayımlanır [MIT lisansı][].
Bu lisansı altında ve Ücretli destek sözleşmesi olmadığında kullanıcılar için sınırlı [topluluk desteği][].
Topluluk desteği, Microsoft yanıtlama hızı veya düzeltmeleri hiçbir garanti vermez.

## <a name="windows-powershell-module"></a>Windows PowerShell Modülü

Desteklemek için bu modüller açıkça PowerShell çekirdek desteği sürece PowerShell çekirdek diğer ürün modüllerini erişmez.
Örneğin, kullanarak `ActiveDirectory` desteklenmeyen bir senaryodur Windows Server parçası olarak gelir modüldür.

Ancak, açıkça PowerShell çekirdek desteklemeyen modülleri bazı durumlarda uyumlu olabilir.
Yükleyerek [ `WindowsPSModulePath` ][] modülü, Windows PowerShell ekleyebilirsiniz `PSModulePath` PowerShell çekirdek için `PSModulePath`.

İlk olarak, yükleme `WindowsPSModulePath` PowerShell Galerisi'nden modül:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Bu modül yükledikten sonra çalıştırmak `Add-WindowsPSModulePath` Windows PowerShell eklemek için cmdlet `PSModulePath` PowerShell çekirdek için:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[topluluk desteği]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell teknik topluluk]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[destekli Destek]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT lisansı]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/