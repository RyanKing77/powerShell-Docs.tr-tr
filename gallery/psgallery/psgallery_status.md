---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: psgallery_status
ms.openlocfilehash: 08d09ce83b5133598152186e12fc8ced90c36a88
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
<a name="powershell-gallery-status"></a>PowerShell Galerisi durumu
=========================
## <a name="10102017---powershell-gallery-unavailable-for-2-hours-101017"></a>10/10/2017-2 saat kullanılamaz PowerShell Galerisi 10/10/17

__Özet etkisi__: PowerShell Galerisi aralıklı bağlantısı sorunları yaklaşık 5 pm (saati) itibaren kaynaklanan bir süre çok yüksek gecikme yaşadı 10/10/17. Sorunu çözerken, site için yaklaşık 10 pm (saati) başlangıç 2 saat çevrimdışı duruma. Site gece yarısından kısa süre önce geri 10/10/2017.

__Kök neden__: yüksek gecikme kök nedenini hala incelenmektedir.

__Çözümleme__: web hizmetleri çevrimdışına gerekiyordu ve birincil sorunu gidermek için geri.

__Sonraki adımlar__: özgün sorunun kök nedeni incelenmektedir.

## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a>Azure Automation şu anda kullanılabilir 06/01/2017-'ı dağıtma

__Özet etkisi__: bağımlılıkları olan öğeleri için Azure Otomasyonu PowerShell Galerisi'nden dağıtma şu anda kullanılamıyor.  PowerShell Galerisi'nden öğeleri içeri aktarma içinde Azure Otomasyonu hala kullanılabilir değil.

__Kök nedeni__: bazılarında bağımlılıklara sahip ve Azure otomasyonu için daha önce dağıtmış olan öğeleri için Azure Otomasyonu değil dağıtılacak. Mühendisleri nasıl ARM şablonlarını öğeleri için bağımlılıkları olan Azure Otomasyonu işlevine dağıtma için oluşturulan ile ilgili bir sorun tanımladınız.

__Çözümleme__: mühendisleri sorunu gidermek için çalışıyor.  PowerShell Galerisi'nden öğe aktarmak için kullanıcılar için geçerli geçici çözümü olan Azure Otomasyonu içinde.

__Sonraki adımlar__: mühendisleri yayın düzeltme kısa süre içinde.  Bu arada, önerilen geçici çözüm Lütfen kullanın.


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a>11/04/2017 - kullanıcıların Azure Active Directory (AAD) hesaplarıyla oturum oturum açamıyor

__Özet etkisi__: Azure AD hesapları kullanan bazı kullanıcılar için PowerShell Galerisi oturum açamıyor.

__Kök nedeni__: daha güvenli bir şekilde AAD ile etkileşim kurmak için bir güncelleştirme sırasında bir ayar değişikliğinin eksik.
Dağıtım proceeded şekilde değişikliğini doğrulamak için yapılan sınama, AAD hesaplarının, belirli türde içermiyordu.

__Çözümleme__: mühendisleri eksik ayarı tanımlanır ve sorun düzeltilmiştir.

__Sonraki adımlar__: biz bizim AAD hesap türleri için daha geniş bir dizi dahil etmek için test değiştirme.

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>03/27/2017 - ÇÖZÜMLENDİ: tek tek modülü ve komut dosyası sayfalarında Görülemedi

__Özet etkisi__: doğrudan bağlantılar ayrı ayrı modülü ve komut dosyası sayfalara https://www.powershellgallery.com bozulur. Bu bölgeler arasında raporlandığını. Bu PowerShellGet cmdlet'lerinden herhangi birini IE etkisi olmuştur değil., Install-Module, yükleme betiği, Update-modülü, Update-komut dosyası, yayımlama-Module Yayımla-Scirpt devam çalışmak.

__Kök neden__: mühendisleri neden sayfaya düğmeleri gibi Facebook sosyal medya getiren bir sorun olarak tanımlanır.

__Çözümleme__: mühendisleri Facebook sayımı bilgilerini devre dışı bırakarak sorun düzeltilmiştir.

__Sonraki adımlar__: biz Facebook API'si bizim kullanımını düzeltmek için bir iç izleme sorunu açılır.

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a>12/15/2016 - PowerShellGallery Web sitesi aracılığıyla e-posta gönderilemedi

__Özet etkisi__: 13/12/2016 ile 15/12/2016 arasında kişi sahipleri, sahiplerini yönetme, Destek birimine başvurun veya rapor kötüye gönderilen iletiler PowerShell Galerisi yöneticileri tarafından alınmadı.
__Kök neden__: mühendisleri bir kimlik doğrulama sorunu nedeni SMTP sunucusu ile tanımlanır.
__Çözümleme__: mühendisleri kimlik doğrulama sorunu çözün ve SMTP sunucusuna bağlantı geri yükleyebilirsiniz.
__Sonraki adımlar__: ileti göndermek için kişi sahipleri, sahiplerini yönetme, Destek birimine başvurun veya rapor kötüye bağlantılar kullandıysanız cgadmin@microsoft.com bu sırasında zaman ve biz vermediniz, lütfen yeniden deneyin. Verdiğimiz rahatsızlıktan dolayı özür dileriz.



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>8/10/2016 - çözümlendi: e-postalar için gönderilemedi cgadmin@microsoft.com

__Özet etkisi__: 8/5/2016 ile 8/10/2016 arasında müşteriler için e-posta gönderemiyor cgadmin@microsoft.com, ya da bize özelliğini kullanın.
__Kök neden__: mühendisleri tanımlanan neden e-posta hesabı bir yapılandırma değişikliği.
__Çözümleme__: mühendisleri çalışılan yapılandırma sorunu gidermek için.
__Sonraki adımlar__: bize bağlantı kullanılan veya posta gönderilen cgadmin@microsoft.com bu sırasında zaman ve biz vermediniz, lütfen yeniden deneyin. Anlayışınız için teşekkür ederiz.



## <a name="7132016---download-items-failed"></a>Başarısız olan öğe 7/13/2016 - indirin

__Özet etkisi__: 11/7/2016 ile 13/7/2016 arasında bir alt kümesini müşteriler PowerShell Galerisi'nden öğe indirme sorunları yaşadı. Olası sorun kendisini yükleme Modül/yükleme betiği ve kaydetme modülü/Kaydet betiği döndürülen aşağıdaki hata iletisini bildirilmiş:

```powershell
PS C:\> Install-Module xStorage
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because:
End of Central Directory record could not be found. At C:\Program
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ...
$null = PackageManagement\Install-Package @PSBoundParameters +
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult:
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}'
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage
```

__Ön kök nedeni__: mühendisleri ile Azure içerik teslim ağı (PowerShell Galerisi 11/7/2016 tarihinde dağıtmış CDN), bir sorun tanımlanmış.
__Azaltma__: mühendisleri Azure CDN PowerShell galerisinde devre dışı.
__Sonraki adımlar__: temel alınan kök nedeni araştırın ve gelecekteki oluşumları önlemek için bir çözüm geliştirme.


## <a name="5192016---download-items-failed"></a>Başarısız olan öğe sayısı 5/19/2016 - indirin
__Özet etkisi__: bir alt kümesini müşteriler 17/5/2016 ve 5/19/2016 arasında PowerShell Galerisi'nden öğe indirme sorunları yaşadı. Olası sorun kendisini yükleme Modül/yükleme betiği ve kaydetme modülü/Kaydet betiği döndürülen aşağıdaki hata iletisini bildirilmiş:

```powershell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because:
End of Central Directory record could not be found.
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install.
WARNING: Package 'AzureRM' failed to install.
VERBOSE: Module 'AzureRM.Network' was saved successfully.
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the
module 'AzureRM'.
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully.
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 +
$null = PackageManagement\Save-Package @PSBoundParameters +
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ +
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage)
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage
```

__Ön kök nedeni__: mühendisleri kesinti, Azure içerik teslim ağı (PowerShell Galerisi 17/5/2016 tarihinde dağıtmış CDN), temel alınan sağlayıcı olarak tanımlanır.
__Azaltma__: mühendisleri Azure CDN PowerShell galerisinde devre dışı.
__Sonraki adımlar__: temel alınan kök nedeni araştırın ve gelecekteki oluşumları önlemek için bir çözüm geliştirme.