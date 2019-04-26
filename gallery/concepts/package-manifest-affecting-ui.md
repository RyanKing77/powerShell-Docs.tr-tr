---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: PowerShell Galerisi UI etkileyen paket bildirim değerleri
ms.openlocfilehash: cedf81df8de29c54ef559a800d654305029491ec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084717"
---
# <a name="package-manifest-values-that-impact-the-powershell-gallery-ui"></a>PowerShell Galerisi UI etkileyen paket bildirim değerleri

Bu konu, böylece PowerShellGet cmdlet'leri ve PowerShell galeri kullanıcı Arabirimi özelliklerini etkilenecek PowerShell Galerisi yayınlarını bildirimi değiştirme konusunda yayımcılar Özet bilgilerle birlikte sağlar. Bu içerik, değişiklik, Orta kısım, sonra da sol taraftaki gezinti alanına başlayarak görüneceği yeri tarafından düzenlenir. Bir ayrıntı bölümü yoktur kapsayan etiketler, etiketler etiketleri yanı sıra bazı daha yaygın olarak kullanılan önemli tanımlayan. Bildirim örnekleri sağlayan iki konuları vardır:

- Modüller için bkz: [modülü güncelleştirme bildirimi](/powershell/module/powershellget/Update-ModuleManifest)
- Betikler için bkz: [meta veriler ile betik dosyası oluştur](/powershell/module/powershellget/New-ScriptFileInfo)

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>PowerShell Galerisi özellik öğeleri listesi tarafından denetlenir

Aşağıdaki tabloda, yayımcı tarafından denetlenen PowerShell Galerisi paket sayfası kullanıcı Arabirimi öğelerini gösterir. Her öğe, modül veya betik bildirimi tarafından kontrol edilebilir olmadığını belirtir.

| Kullanıcı Arabirimi öğesi | Açıklama | Modül | Betik |
| --- | --- | --- | --- |
| **Başlık** | Galeride yayımlanmış paket adıdır  | Hayır | Hayır |
| **Sürüm** | Görüntülenen meta veri sürümü dizesini sürümüdür ve yayın öncesi bir IF belirtilir. Birincil modül bildirimindeki sürüm ModuleVersion bölümüdür. Bir betik için onu olarak tanımlanır. Sürüm. Yayın öncesi sürüm dizesi belirtilirse, ModuleVersion modüller için eklenen, veya yüklenecek bir parçası olarak belirtilen. Komut dosyalarının sürümü. Yayın öncesi dizelerde belirtmek için belgeleri yoktur [modülleri](module-prerelease-support.md)hem de [betikleri](script-prerelease-support.md) | Evet | Evet |
| **Açıklama** | Bu modül bildirimindeki açıklamasıdır ve bir betik dosyası bildiriminde olduğu. AÇIKLAMASI | Evet | Evet |
| **Lisans kabulü gerektir** | Bir modül, modül bildirimini değiştirerek kullanıcı bir lisans kabul etmelerini zorunlu tutabilirsiniz RequireLicenseAcceptance ile bir LicenseURI sağlama ve modül klasörün kökünde bir license.txt dosyasına sağlayarak $true =. Ek bilgi sağlanmıştır [lisans kabulü gerektiren](../how-to/working-with-packages/packages-that-require-license-acceptance.md) konu. | Evet | Hayır |
| **Sürüm notları** | Modüller için bu bilgileri ReleaseNotes bölümünde PSData\PrivateData çizilir. Betik Bildirimlerde öyledir. RELEASENOTES öğesi. | Evet | Evet |
| **Sahipleri** | Sahip olan bir paketi güncelleştirebilirsiniz PowerShell galerisinde bulunan kullanıcılar listesidir. Sahip listesi paketi bildiriminde yer almaz. Ek belgelerde nasıl [öğe sahiplerini yönetme](../how-to/publishing-packages/managing-package-owners.md). | Hayır | Hayır |
| **Yazar** | Bu, yazarı olarak modül bildirimindeki ve bir betik bildirim dahil edilir. YAZAR. Yazar alanı, genellikle bir şirket veya bir paket ile ilişkili kuruluş belirtmek için kullanılır. | Evet | Evet |
| **Telif Hakkı** | Bu modül bildirimindeki telif hakkı alanıdır ve. Bir betik bildiriminde telif hakkı. | Evet | Evet |
| **FileList** | PowerShell Galerisi'nde yayımlandığında, dosya listesi paketten çizilir. Bildirim bilgileri tarafından denetlenebilir değil. Not: her pakette bir sistemde paket yüklendikten sonra mevcut değilse PowerShell galerisinde listelenmiş bir ek .nuspec dosyası yoktur. Bu paket için Nuget paket bildirim ve yok sayılabilir. | Hayır | Hayır |
| **Etiketler** | Modüller için etiketleri PSData\PrivateData altında bulunur. Betikler için bölüm etiketlendiğini. ETİKETLER. Tırnak işaretleri olduklarında bile etiketleri Not boşluk içeremez. Etiketler, ek gereksinimler ve etiket Ayrıntıları bölümünde bu konunun ilerleyen bölümlerinde açıklanan bir anlamı vardır. | Evet | Evet |
| **Cmdlet’ler** | Bu modül bildiriminde CmdletsToExport kullanılarak sağlanır. Joker karakter kullanılması yerine açıkça öğelerini listelemek için en iyi olduğuna dikkat edin "*", kullanıcılar için yükleme-module performansını artıracak şekilde. | Evet | Hayır |
| **İşlevleri** | Bu modül bildiriminde FunctionsToExport kullanılarak sağlanır. Joker karakter kullanılması yerine açıkça öğelerini listelemek için en iyi olduğuna dikkat edin "*", kullanıcılar için yükleme-module performansını artıracak şekilde. | Evet | Hayır |
| **DSC kaynakları** | PowerShell sürüm 5.0 ve üzeri için kullanılacak olan modüller için bu DscResourcesToExport kullanılarak bildirimde sağlanır. Modülü, PowerShell 4'te kullanılacak ise, desteklenen bir bildirim anahtar olmadığından DSCResourcesToExport kullanılmamalıdır. (DSC, PowerShell 4 önce yoktu.) | Evet | Hayır |
| **İş Akışları** | İş akışları betikler PowerShell Galerisi'nde yayımlanmış ve iş akışları olarak tanımlanır (bkz [Connect-AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1) bir örnek) kod. Bu bildirimi tarafından denetlenmez. | Hayır | Hayır |
| **Rol işlevleri** | JEA tarafından kullanılan bir veya daha fazla rol (.psrc) dosyaları, modülün PowerShell Galerisi'nde yayımlanmış içerdiğinde, bu listede görüntülenir. İlgili daha fazla ayrıntı için JEA belgelere bakın [rol işlevleri](/powershell/jea/role-capabilities). | Evet | Hayır |
| **PowerShell sürümleri** | Bu, bir komut veya modül bildiriminde belirtilir. Aşağıda, bu PowerShell 5.0 ile kullanılmak üzere tasarlanmış modüller için etiketleri kullanılarak denetlenir. Masaüstü için PSEdition_Desktop etiketini kullanın ve PSEdition_Core etiket core için kullanın. Yalnızca PowerShell 5.1 ve üzeri için kullanılacak olan modüller için ana bildiriminde CompatiblePSEditions anahtar yoktur. Ek ayrıntılar için PS Edition özelliği gözden [PowerShell Get belgeleri](module-psedition-support.md). | Evet | Evet |
| **Bağımlılıkları** | Bağımlılıkları olan ya da modül RequiredModules olarak ya da komut bildirim bildirilen PowerShell Galerisi modülleri #Requires – Modülü (ad). | Evet | Evet |
| **En düşük PowerShell sürümü** | Bu modül bildiriminde PowerShellVersion belirtilebilir. | Evet | Hayır |
| **Sürüm Geçmişi** | Sürüm Geçmişi bir modülün PowerShell Galerisi'nde yapılan güncelleştirmeleri yansıtır. Bir paketin bir sürümü silme özelliği kullanarak gizli ise, bu sürüm geçmişine dışında paket sahiplerine görüntülenmez. | Hayır | Hayır |
| **Proje sitesi** | Proje sitesi bir ProjectURI belirterek modüllerin modül bildirimini Privatedata\PSData bölümünde sağlanır. Betik bildiriminde belirterek denetlenir. PROJECTURI. | Evet | Evet |
| **Lisans** | Bir lisans bağlantı bir LicenseURI belirterek modül bildirimini Privatedata\PSData bölümünde modüller için sağlanır. Betik bildiriminde belirterek denetlenir. LICENSEURI. Bir lisansı LicenseURI sağlanmamışsa veya içinde bir modül, paket için kullanım koşullarını sonra PowerShell Galerisi için kullanım koşullarını belirtin, dikkat etmeniz önemlidir. Kullanım koşullarını ayrıntılı bilgi için bkz. | Evet | Evet |
| **Simgesi** | Bir simge PowerShell galerisinde herhangi bir paket için betik bildiriminde veya modül bildirimini Privatedata PSData bölümünde IconURI bayrağı sağlanarak belirtilebilir. Saydam arka planlı bir 32 x 32 görüntü için iconuri öğesinin işaret etmelidir. URI **gerekir** doğrudan resim URL'si olması ve **gerekir** görüntü veya PowerShell galeri paketi içindeki bir dosya içeren bir web sayfasına gidin. | Evet | Evet |


## <a name="editing-package-details"></a>Paket ayrıntılarını düzenleme

PowerShell Galerisi paket sayfasını Düzenle birkaç bir paket için özel olarak görüntülenen alanları değiştirmek yayımcılar sağlar:

- Başlık
- Açıklama
- Özet
- Simge URL'si
- Proje giriş sayfası URL'si
- Yazarlar
- Telif Hakkı
- Etiketler
- Sürüm notları
- Lisansı

Bu yaklaşım genellikle bir modülün daha eski bir sürümü görüntülenenleri düzeltmek için gerekli dışında önerilmez. Modülü Al kullanıcılar, meta veri paketi ile ilgili endişelerini başlatır PowerShell galerisinde görüntülenen eşleşmiyor görürsünüz. Bu sık Değişikliği onaylamak için paket sahipleri giderek sorguları sonuçlanır. Bu yaklaşımın kullanılması, istediğiniz zaman aynı değişiklikleri yeni bir paket sürümü yayımlanmasına önemle tavsiye edilir.

## <a name="tag-details"></a>Etiket ayrıntıları

Etiketler, paketleri bulmak için basit dizeler tüketiciler kullanım içindir. Etiketler en değerli alındığında bunlar aynı konu ile ilgili birçok paketleri arasında tutarlı bir şekilde kullanılır. Aynı değinirken kullanarak sözcük (örneğin veritabanı ve veritabanları veya test ve test) genellikle az yarar sağlar. Etiketler Tek sözcüklü büyük küçük harf duyarsız dizelerdir ve boşluklar içeremez. Kullanıcılar için arama düşündüğünüz bir ifade ise ve Paket açıklaması için eklemek ve arama sonuçlarında bulunamadı. Okunabilirliğin çalışıyorsanız Pascal büyük/küçük harf, tire, alt çizgi veya nokta kullanın.
Genellikle yanlış olarak uzun, karmaşık ve olağan dışı etiketler oluşturma hakkında dikkatli olun.

PowerShell Galerisi ve PowerShellGet olarak cmdlet'leri bunları benzersiz olarak işleme, dikkat edilecek önemli etiketleri vardır. PSEdition_Desktop PSEdition_Core belirli örnekler ve yukarıda açıklanan.

Tutarlı bir şekilde çok sayıda paket arasında belirli ve kullanılan olduklarında yukarıda belirtildiği gibi etiketleri en yüksek değeri sağlar. Kullanmak için en iyi etiketleri bulmaya çalışırken bir yayımcı, en kolay yaklaşım PowerShell Galerisi, değerlendiriyorsanız etiketleri için arama gerçekleştirmektir. İdeal olarak, döndürülen birçok paketi olacaktır ve paket açıklamaları, bu anahtar sözcük kullanımını ile hizalanır.

Başvuru için en yaygın kullanılan bazı etiketler 14/12/2017 itibarıyla aşağıda verilmiştir. Bazı durumlarda, benzer ancak belki de ideal seçenek etiketi listelenen daha az vardır. Daha az paraziti de neden ve tüketiciler için daha iyi arama sonuçları tercih edilen etiketini kullanmak için bir en iyi yöntemdir.

| Tercih edilen etiketi | Alternatifleri ve notlar |
| --- | --- |
| Azure |  |
| DSC | DesiredStateConfiguration daha az tercih edilir, çok uzun |
| ResourceManager | ARM işlemci grubu tanımlamak için kullanılır ve Azure Resource Manager için kullanılmamalıdır |
| DSCResourceKit |  |
| SQL |  |
| AWS |  |
| DSCResource |  |
| Otomasyon |  |
| REST |  |
| ActiveDirectory | Tek başına AD şu anda kullanılmıyor  |
| SQLServer |  |
| DBA |  |
| Güvenlik | Savunma daha az kesin |
| Veritabanı | Daha az tercih veritabanları (çoğul) |
| DevOps |  |
| Windows |  |
| Oluşturma |  |
| Dağıtım | Dağıtma biraz daha az sıklıkta kullanılan |
| Bulut |  |
| GIT |  |
| Test | Testi daha az tercih edilir |
| VersionControl | Sürüm daha sık kullanılan olsa da daha az kesin  |
| Günlük | Tercih edilen bir eylem olarak günlük kullanımı |
| Günlük | Bir şey olarak tercih edilen kullanım günlüğü |
| Yedekleme |  |
| IaaS |  |
| Linux |  |
| IIS |  |
| AzureAutomation |  |
| Depolama |  |
| GitHub |  |
| Json |  |
| Exchange |  |
| Ağ | Daha az sıklıkta kullanılan ağ benzer, |
| SharePoint |  |
| Raporlama | Raporlama bir eylem olduğundan, rapor bir şeydir |
| Rapor | Rapor bir şeydir |
| WinRM |  |
| İzleme |  |
| VSTS |  |
| Excel |  |
| Google |  |
| Renk |  |
| DNS |  |
| Office365 | Office Yazım tercih edilir. O365 daha az sık, daha kısa ancak kullanılır |
| Gitlab |  |
| Pester |  |
| AzureAD |  |
| HTML |  |
| Hyper-V | HyperV bir etiket olarak daha az yaygındır |
| Yapılandırma |  |
| ChatOps |  |
| PackageManagement |  |
| WMI |  |
| Güvenlik Duvarı |  |
| Docker |  |
| Appveyor |  |
| AzureRm | Öncelikle AzureRM modülleri için kullanılan |
| Zip |  |
| MSI |  |
| MacOS |  |
| PoshBot |  |
