---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: PowerShell Galerisi UI etkisi öğesi bildirim değerleri
ms.openlocfilehash: 39522396b179c54b981e6292cddacec27b32506c
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
ms.locfileid: "34049104"
---
# <a name="item-manifest-values-that-impact-the-powershell-gallery-ui"></a>PowerShell Galerisi UI etkisi öğesi bildirim değerleri

Bu konu, böylece PowerShellGet cmdlet'leri ve PowerShell Galerisi UI özelliklerini etkilenecek kendi PowerShell Galerisi yayınlar için bildirim değiştirme konusunda özet bilgileri olan yayımcı sağlar.
Bu içerik, değişiklik, Orta kısım, ardından sol gezinti alanını sürümünden itibaren görüneceği yeri tarafından düzenlenir. Bir ayrıntı bölümü yoktur kapsayıcı etiketleri, önemli etiketleri, aynı zamanda bazıları etiketleri yaygın olarak kullanılan tanımlar.
Bildirim örnekler sağlayan iki konuları vardır:

- Modülleri için bkz: [modülü güncelleştirme bildirimi](https://docs.microsoft.com/powershell/gallery/psget/module/psget_update-modulemanifest)
- Komut dosyaları için bkz: [meta verilerle komut dosyası oluştur](https://docs.microsoft.com/powershell/gallery/psget/script/psget_new-scriptfileinfo)

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>PowerShell Galerisi özellik öğeleri listesi tarafından denetlenir

Aşağıdaki tabloda, yayımcı tarafından denetlenen PowerShell Galerisi öğesi sayfanın UI öğelerini gösterir.
Bu modül veya komut dosyası bildirimi tarafından denetlenmesi, her bir öğeyi gösterir.

| Kullanıcı Arabirimi öğesi | Açıklama | Modül | Betik |
| --- | --- | --- | --- |
| **Başlık** | Galeriye yayımlanan öğesi adıdır  | Hayır | Hayır |
| **Sürüm** | Görüntülenen meta verilerde sürüm dizesi sürümüdür ve yayın öncesi IF belirtilir. Birincil bir modül bildirimi sürümünde ModuleVersion bölümüdür. Bir betik için onu olarak tanımlanır. Sürüm. Bir yayın öncesi sürüm dizesi belirtilirse, bu modülleri için ModuleVersion eklenen, veya kaldırılacak parçası olarak belirtilen. Komut dosyalarının sürümü. Yayın öncesi dizelerde belirtmek için belge yok [modülleri](https://docs.microsoft.com/en-us/powershell/gallery/psget/module/prereleasemodule)hem de [komut dosyaları](https://docs.microsoft.com/en-us/powershell/gallery/psget/script/prereleasescript) | Evet | Evet |
| **Açıklama** | Bu modül bildiriminde bir açıklama ve bir komut dosyası bildiriminde olur. AÇIKLAMA | Evet | Evet |
| **Lisans kabulünü gerektirir** | Bir modül modül bildirimi değiştirerek kullanıcı bir lisans kabul etmenizi gerektiriyor RequireLicenseAcceptance ile bir LicenseURI sağlayarak ve kök modül klasörünün license.txt dosyasında sağlama $true =. Ek bilgi sağlanmıştır [gerektiren lisans kabulünü](https://docs.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_requires_license_acceptance) konu. | Evet | Hayır |
| **Sürüm notları** | Modülleri için bu bilgileri ReleaseNotes bölümünde PSData\PrivateData çizilir. Komut dosyası bildirimleri olduğu. RELEASENOTES öğesi. | Evet | Evet |
| **Sahipleri** | Sahipleri olan bir öğeyi güncelleştirebilirsiniz PowerShell Galerisi kullanıcılar listesi verilmiştir. Sahibi liste öğesi bildiriminde dahil edilmez. Ek belgeler açıklar nasıl [öğesi sahiplerini yönetme](https://docs.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners). | Hayır | Hayır |
| **Yazar** | Bu modül bildirimi yazarı olarak ve bir betik bildirim dahil edilir. YAZAR. Yazar alanı, genellikle bir şirket veya kuruluş bir öğesiyle ilişkili belirtmek için kullanılır. | Evet | Evet |
| **Telif Hakkı** | Bu modül bildiriminde telif hakkı alanıdır ve. Bir komut dosyası bildiriminde telif hakkı. | Evet | Evet |
| **FileList** | PowerShell Galerisi yayımlandığında dosya listesini paketinden çizilir. Bildirim bilgileriyle denetlenebilir değil. Not: bir sistemde öğeyi yükledikten sonra mevcut değil PowerShell galerisinde her bir öğesiyle listelenen bir ek .nuspec dosyası yok. Bu öğe için Nuget paket bildirim ve yok sayılabilir. | Hayır | Hayır |
| **Etiketleri** | Modüller için etiketleri PSData\PrivateData altında bulunur. Komut dosyaları için bölüm etiketli. ETİKETLER. Tırnak içine olsalar bile etiketler Not boşluk içeremez. Etiketleri ek gereksinimler ve etiket Ayrıntıları bölümünde bu konunun ilerleyen bölümlerinde açıklanan anlama sahiptir. | Evet | Evet |
| **Cmdlet’ler** | Bu modül bildiriminde CmdletsToExport kullanılarak sağlanır. Joker karakter kullanılması yerine açıkça öğeleri listelemek için en iyisi olduğuna dikkat edin "*" gibi kullanıcılar için yük modülü performansı iyileştirir. | Evet | Hayır |
| **İşlevler** | Bu modül bildiriminde FunctionsToExport kullanılarak sağlanır. Joker karakter kullanılması yerine açıkça öğeleri listelemek için en iyisi olduğuna dikkat edin "*" gibi kullanıcılar için yük modülü performansı iyileştirir. | Evet | Hayır |
| **DSC kaynakları** | PowerShell sürüm 5.0 ve üstü kullanılacak modülleri için bu DscResourcesToExport kullanarak bildiriminde sağlanır. Modül PowerShell 4'te kullanılacak ise, desteklenen bir bildirim anahtar olmadığından DSCResourcesToExport kullanılmamalıdır. (DSC PowerShell 4 önce yoktu.) | Evet | Hayır |
| **İş Akışları** | İş akışları için PowerShell Galerisi komut dosyaları olarak yayımlanan ve iş akışları olarak tanımlanan (bkz [Connect-AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1) bir örnek) kod. Bu bildirimi tarafından denetlenmeyen. | Hayır | Hayır |
| **Rol özellikleri** | JEA tarafından kullanılan bir veya daha fazla rolü özelliği (.psrc) dosyaları, PowerShell Galerisi yayımlanmış modül içerdiğinde, bu listede görüntülenir. Daha fazla ayrıntı için JEA belgelerine bakın [rol özellikleri](https://docs.microsoft.com/en-us/powershell/jea/role-capabilities). | Evet | Hayır |
| **PowerShell sürümleri** | Bu komut dosyası veya modül bildiriminde belirtilir. Aşağıda, bu PowerShell 5.0 ile kullanılmak üzere tasarlanmış modülleri için etiketleri kullanılarak denetlenir. Masaüstü için PSEdition_Desktop etiketi kullanın ve PSEdition_Core etiketi çekirdek için kullanın. Yalnızca PowerShell 5.1 ve üstü için kullanılacak olan modüller için ana bildiriminde CompatiblePSEditions anahtarı yok. Ek ayrıntılar için PS Edition özelliğinde gözden [PowerShell Get belgelerine](https://docs.microsoft.com/en-us/powershell/gallery/psget/module/modulewithpseditionsupport). | Evet | Evet |
| **Bağımlılıklar** | Bağımlılıkları olan ya da modülü RequiredModules olarak veya komut dosyası bildirimi bildirilen PowerShell Galerisi modüllerde #Requires – Modülü (ad). | Evet | Evet |
| **En düşük Powershell sürümü** | Bu modül bildiriminde PowerShellVersion belirtilebilir. | Evet | Hayır |
| **Sürüm Geçmişi** | Sürüm Geçmişi PowerShell Galerisi modülünde yapılan güncelleştirmeler yansıtır. Bir öğenin sürümü Sil özelliğini kullanarak gizli ise, bu sürüm geçmişinde dışında öğesi sahiplerine görüntülenmez. | Hayır | Hayır |
| **Proje sitesi** | Proje sitesi bir ProjectURI belirterek modülleri modül bildirimi Privatedata\PSData bölümünde sağlanır. Komut dosyası bildiriminde belirterek denetlenir. PROJECTURI. | Evet | Evet |
| **Lisans** | Bir lisans bağlantı bir LicenseURI belirterek modülleri modül bildirimi Privatedata\PSData bölümünde sağlanır. Komut dosyası bildiriminde belirterek denetlenir. LICENSEURI. Bir lisans LicenseURI sağlanmadı ya da bir modül içinde PowerShell Galerisi için kullanım koşullarını ardından kullanım koşullarını öğesi için belirtin. dikkate almak önemlidir. Kullanım koşulları Ayrıntılar için bkz. | Evet | Evet |

## <a name="editing-item-details"></a>Öğe ayrıntıları düzenleme

PowerShell galeri öğesi sayfasını Düzenle birkaç bir öğe için özellikle görüntülenen alanları değiştirmek yayımcılar sağlar:

- Başlık
- Açıklama
- Özet
- Simge URL'si
- Proje giriş sayfası URL'si
- yazarları
- Telif Hakkı
- Etiketler
- Sürüm notları
- Lisans gerektirir

Bu yaklaşım genellikle, bir modül daha eski bir sürümü için görüntülenenleri düzeltmek için gerekli dışında önerilmez.
Modülü Al kullanıcılar meta veri öğesi endişeniz başlatır PowerShell galerisinde görüntülenenleri eşleşmiyor görürsünüz.
Bu sıkça Değişikliği onaylamak için öğeyi sahiplerine gidip sorguları neden olur.
Bu yaklaşım kullanılır, dilediğiniz zaman aynı değişikliklerle öğenin yeni bir sürümü yayınlanmalıdır önerilir.

## <a name="tag-details"></a>Etiket ayrıntıları

Etiketler öğeleri bulmak için basit dizeler tüketicileri kullanım içindir.
Tutarlı olarak aynı konu ile ilgili birçok öğeleri arasında kullanıldığında, bunların etiketlerini en değerli. Aynı birden fazla sürümünü kullanarak word (örneğin veritabanı ve veritabanları veya test ve test) genellikle az avantajı sağlar.
Etiketler Tek sözcüklü büyük küçük harf duyarsız dizelerdir ve boşluk içeremez. Kullanıcıları arar düşünüyorsanız tümcecik ise öğeyi açıklama eklemek ve arama sonuçlarında bulunamadı. Okunabilirliğini artırmak çalışıyorsanız Pascal büyük/küçük harf, tire, alt çizgi veya nokta kullanın. Genellikle yanlış olarak uzun, karmaşık ve olağan dışı etiketler oluşturma hakkında dikkatli olun.

Dikkat edilecek önemli etiketleri, PowerShell Galerisi ve PowerShellGet cmdlet'leri bunları benzersiz olarak işler. PSEdition_Desktop PSEdition_Core belirli örnekler ve yukarıda açıklanan.

Tutarlı bir şekilde arasında çok sayıda öğe belirli ve kullanılan olduklarında yukarıda belirtildiği gibi etiketleri en yüksek değeri sağlayın.
Kullanmak için en iyi etiketleri bulmaya çalışan bir yayımcı olarak, en kolay yaklaşım, değerlendiriyorsanız etiketleri için PowerShell Galerisi arama yapmaktır.
İdeal olarak, döndürülen öğe olacaktır ve madde açıklamaları, bu anahtar sözcük kullanımı ile hizalanır.

Başvuru için en yaygın kullanılan bazı etiketler 14/12/2017'dan sonra şunlardır.
Bazı durumlarda, benzer ancak belki de etiketi listelenen ideal seçenekleri daha az vardır.
Bu daha az gürültü neden ve daha iyi arama sonuçları Tüketiciler için tercih edilen etiketi olarak kullanmak için en iyi uygulamadır.


| **Tercih edilen etiketi** | **Alternatifleri ve notlar** |
| --- | --- |
| **Azure** |  |
| **DSC** | DesiredStateConfiguration daha az tercih edilir, çok uzun |
| **ResourceManager** | ARM işlemci grubu tanımlamak için kullanılır ve Azure Resource Manager için kullanılmamalıdır | **DSCResourceKit** |  |
| **SQL** |  |
| **AWS** |  |
| **DSCResource** |  |
| **Otomasyon** |  |
| **REST** |  |
| **Active Directory** | Tek başına AD şu anda kullanılmıyor  |
| **SQLServer** |  |
| **DBA** |  |
| **Güvenlik** | Savunma daha az kesin |
| **Veritabanı** | Veritabanları (çoğul) daha az tercih |
| **DevOps** |  |
| **Windows** |  |
| **Derleme** |  |
| **Dağıtım** | Dağıtma biraz daha az sıklıkta kullanılır |
| **Bulut** |  |
| **GIT** |  |
| **test etme** | Sınama daha az tercih edilir |
| **VersionControl** | Sürüm daha sık kullanılır ancak daha az kesin  |
| **Günlüğe kaydetme** | Tercih edilen bir eylem olarak günlük kullanımı |
| **Günlük** | Bir şey olarak tercih edilen kullanımını günlük |
| **Yedekleme** |  |
| **Iaas** |  |
| **Linux** |  |
| **IIS** |  |
| **AzureAutomation** |  |
| **Depolama** |  |
| **GitHub** |  |
| **JSON** |  |
| **Exchange** |  |
| **Ağ** | Ağ daha az sıklıkta kullanılan, benzer |
| **SharePoint** |  |
| **Raporlama** | Raporlama bir eylem, bir şey rapor. |
| **Raporu** | Rapor bir şey. |
| **WinRM** |  |
| **İzleme** |  |
| **VSTS** |  |
| **Excel** |  |
| **Google** |  |
| **Renk** |  |
| **DNS** |  |
| **Office365** | Out Office Yazım tercih edilir. O365 daha az yaygın olarak, kısa ancak kullanılır | **Gitlab** |  |
| **Pester** |  |
| **AzureAD** |  |
| **HTML** |  |
| **Hyper-V** | HyperV etiket olarak daha az yaygındır |
| **Yapılandırma** |  |
| **ChatOps** |  |
| **PackageManagement** |  |
| **WMI** |  |
| **Güvenlik Duvarı** |  |
| **Docker** |  |
| **Appveyor** |  |
| **AzureRm** | Öncelikle AzureRM modülleri için kullanılır |
| **Zip** |  |
| **MSI** |  |
| **Mac** |  |
| **PoshBot** |  |