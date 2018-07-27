---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: PowerShell Galerisi UI etkileyen öğe bildirimi değerleri
ms.openlocfilehash: 60415193129fe040b53d35b1f8701408cfc4989d
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268186"
---
# <a name="item-manifest-values-that-impact-the-powershell-gallery-ui"></a>PowerShell Galerisi UI etkileyen öğe bildirimi değerleri

Bu konu, böylece PowerShellGet cmdlet'leri ve PowerShell galeri kullanıcı Arabirimi özelliklerini etkilenecek PowerShell Galerisi yayınlarını bildirimi değiştirme konusunda yayımcılar Özet bilgilerle birlikte sağlar. Bu içerik, değişiklik, Orta kısım, sonra da sol taraftaki gezinti alanına başlayarak görüneceği yeri tarafından düzenlenir. Bir ayrıntı bölümü yoktur kapsayan etiketler, etiketler etiketleri yanı sıra bazı daha yaygın olarak kullanılan önemli tanımlayan. Bildirim örnekleri sağlayan iki konuları vardır:

- Modüller için bkz: [modülü güncelleştirme bildirimi](/powershell/module/powershellget/Update-ModuleManifest)
- Betikler için bkz: [meta veriler ile betik dosyası oluştur](/powershell/module/powershellget/New-ScriptFileInfo)

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>PowerShell Galerisi özellik öğeleri listesi tarafından denetlenir

Aşağıdaki tabloda, yayımcı tarafından denetlenen PowerShell Galerisi öğesi sayfası kullanıcı Arabirimi öğelerini gösterir. Her öğe, modül veya betik bildirimi tarafından kontrol edilebilir olmadığını belirtir.

| Kullanıcı Arabirimi öğesi | Açıklama | Modül | Betik |
| --- | --- | --- | --- |
| **Başlık** | Galeride yayımlanmış öğesi adıdır  | Hayır | Hayır |
| **Sürüm** | Görüntülenen meta veri sürümü dizesini sürümüdür ve yayın öncesi bir IF belirtilir. Birincil modül bildirimindeki sürüm ModuleVersion bölümüdür. Bir betik için onu olarak tanımlanır. Sürüm. Yayın öncesi sürüm dizesi belirtilirse, ModuleVersion modüller için eklenen, veya yüklenecek bir parçası olarak belirtilen. Komut dosyalarının sürümü. Yayın öncesi dizelerde belirtmek için belgeleri yoktur [modülleri](module-prerelease-support.md)hem de [betikleri](script-prerelease-support.md) | Evet | Evet |
| **Açıklama** | Bu modül bildirimindeki açıklamasıdır ve bir betik dosyası bildiriminde olduğu. AÇIKLAMASI | Evet | Evet |
| **Lisans kabulü gerektir** | Bir modül, modül bildirimini değiştirerek kullanıcı bir lisans kabul etmelerini zorunlu tutabilirsiniz RequireLicenseAcceptance ile bir LicenseURI sağlama ve modül klasörün kökünde bir license.txt dosyasına sağlayarak $true =. Ek bilgi sağlanmıştır [lisans kabulü gerektiren](../how-to/working-with-items/items-that-require-license-acceptance.md) konu. | Evet | Hayır |
| **Sürüm notları** | Modüller için bu bilgileri ReleaseNotes bölümünde PSData\PrivateData çizilir. Betik Bildirimlerde öyledir. RELEASENOTES öğesi. | Evet | Evet |
| **Sahipleri** | Sahip olan bir öğe güncelleştirebilirsiniz PowerShell galerisinde bulunan kullanıcılar listesidir. Sahip listesi öğesi bildiriminde yer almaz. Ek belgelerde nasıl [öğe sahiplerini yönetme](../how-to/publishing-items/managing-item-owners.md). | Hayır | Hayır |
| **Yazar** | Bu, yazarı olarak modül bildirimindeki ve bir betik bildirim dahil edilir. YAZAR. Yazar alanı, genellikle bir şirket veya kuruluş bir öğeyle ilişkili belirtmek için kullanılır. | Evet | Evet |
| **Telif Hakkı** | Bu modül bildirimindeki telif hakkı alanıdır ve. Bir betik bildiriminde telif hakkı. | Evet | Evet |
| **FileList** | PowerShell Galerisi'nde yayımlandığında, dosya listesi paketten çizilir. Bildirim bilgileri tarafından denetlenebilir değil. Not: her öğe, öğe bir sistemde yükledikten sonra mevcut değilse PowerShell Galerisi ile listelenmiş bir ek .nuspec dosyası yoktur. Bu öğe için Nuget paket bildirim ve yok sayılabilir. | Hayır | Hayır |
| **Etiketleri** | Modüller için etiketleri PSData\PrivateData altında bulunur. Betikler için bölüm etiketlendiğini. ETİKETLER. Tırnak işaretleri olduklarında bile etiketleri Not boşluk içeremez. Etiketler, ek gereksinimler ve etiket Ayrıntıları bölümünde bu konunun ilerleyen bölümlerinde açıklanan bir anlamı vardır. | Evet | Evet |
| **Cmdlet’ler** | Bu modül bildiriminde CmdletsToExport kullanılarak sağlanır. Joker karakter kullanılması yerine açıkça öğelerini listelemek için en iyi olduğuna dikkat edin "*", kullanıcılar için yükleme-module performansını artıracak şekilde. | Evet | Hayır |
| **İşlevleri** | Bu modül bildiriminde FunctionsToExport kullanılarak sağlanır. Joker karakter kullanılması yerine açıkça öğelerini listelemek için en iyi olduğuna dikkat edin "*", kullanıcılar için yükleme-module performansını artıracak şekilde. | Evet | Hayır |
| **DSC kaynakları** | PowerShell sürüm 5.0 ve üzeri için kullanılacak olan modüller için bu DscResourcesToExport kullanılarak bildirimde sağlanır. Modülü, PowerShell 4'te kullanılacak ise, desteklenen bir bildirim anahtar olmadığından DSCResourcesToExport kullanılmamalıdır. (DSC, PowerShell 4 önce yoktu.) | Evet | Hayır |
| **İş Akışları** | İş akışları betikler PowerShell Galerisi'nde yayımlanmış ve iş akışları olarak tanımlanır (bkz [Connect-AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1) bir örnek) kod. Bu bildirimi tarafından denetlenmez. | Hayır | Hayır |
| **Rol işlevleri** | JEA tarafından kullanılan bir veya daha fazla rol (.psrc) dosyaları, modülün PowerShell Galerisi'nde yayımlanmış içerdiğinde, bu listede görüntülenir. İlgili daha fazla ayrıntı için JEA belgelere bakın [rol işlevleri](/powershell/jea/role-capabilities). | Evet | Hayır |
| **PowerShell sürümleri** | Bu, bir komut veya modül bildiriminde belirtilir. Aşağıda, bu PowerShell 5.0 ile kullanılmak üzere tasarlanmış modüller için etiketleri kullanılarak denetlenir. Masaüstü için PSEdition_Desktop etiketini kullanın ve PSEdition_Core etiket core için kullanın. Yalnızca PowerShell 5.1 ve üzeri için kullanılacak olan modüller için ana bildiriminde CompatiblePSEditions anahtar yoktur. Ek ayrıntılar için PS Edition özelliği gözden [PowerShell Get belgeleri](module-psedition-support.md). | Evet | Evet |
| **Bağımlılıkları** | Bağımlılıkları olan ya da modül RequiredModules olarak ya da komut bildirim bildirilen PowerShell Galerisi modülleri #Requires – Modülü (ad). | Evet | Evet |
| **En düşük Powershell sürümü** | Bu modül bildiriminde PowerShellVersion belirtilebilir. | Evet | Hayır |
| **Sürüm Geçmişi** | Sürüm Geçmişi bir modülün PowerShell Galerisi'nde yapılan güncelleştirmeleri yansıtır. Bir öğenin sürümünü silme özelliği kullanarak gizli ise, bu sürüm geçmişine dışında öğesi sahiplerine görüntülenmez. | Hayır | Hayır |
| **Proje sitesi** | Proje sitesi bir ProjectURI belirterek modüllerin modül bildirimini Privatedata\PSData bölümünde sağlanır. Betik bildiriminde belirterek denetlenir. PROJECTURI. | Evet | Evet |
| **Lisans** | Bir lisans bağlantı bir LicenseURI belirterek modül bildirimini Privatedata\PSData bölümünde modüller için sağlanır. Betik bildiriminde belirterek denetlenir. LICENSEURI. Bir lisansı LicenseURI sağlanmadı veya içinde bir modül, PowerShell Galerisi için kullanım koşullarını ardından kullanım koşullarını öğe için belirtin. dikkat etmeniz önemlidir. Kullanım koşullarını ayrıntılı bilgi için bkz. | Evet | Evet |

## <a name="editing-item-details"></a>Öğe ayrıntılarını düzenleme

PowerShell Galerisi öğesi sayfasını Düzenle birkaç özellikle bir öğe için görüntülenen alanları değiştirmek yayımcılar sağlar:

- Başlık
- Açıklama
- Özet
- Simge URL'si
- Proje giriş sayfası URL'si
- Yazarları
- Telif Hakkı
- Etiketler
- Sürüm notları
- Lisansı

Bu yaklaşım genellikle bir modülün daha eski bir sürümü görüntülenenleri düzeltmek için gerekli dışında önerilmez. Modülü Al kullanıcılar, meta veri öğesi ile ilgili endişelerini başlatır PowerShell galerisinde görüntülenen eşleşmiyor görürsünüz. Bu sık gidip Değişikliği onaylamak için öğe sahipleriyle sorguları sonuçlanır. Bu yaklaşımın kullanılması, istediğiniz zaman aynı değişikliklerle öğenin yeni bir sürümü yayımlanmasına önemle tavsiye edilir.

## <a name="tag-details"></a>Etiket ayrıntıları

Etiketler, öğeleri bulmak için basit dizeler tüketiciler kullanım içindir. Etiketler en değerli alındığında bunlar aynı konu ile ilgili birçok öğeleri arasında tutarlı bir şekilde kullanılır. Aynı değinirken kullanarak sözcük (örneğin veritabanı ve veritabanları veya test ve test) genellikle az yarar sağlar. Etiketler Tek sözcüklü büyük küçük harf duyarsız dizelerdir ve boşluklar içeremez. Kullanıcılar için arama düşündüğünüz bir ifade ise madde açıklaması eklemek ve arama sonuçlarında bulunamadı. Okunabilirliğin çalışıyorsanız Pascal büyük/küçük harf, tire, alt çizgi veya nokta kullanın.
Genellikle yanlış olarak uzun, karmaşık ve olağan dışı etiketler oluşturma hakkında dikkatli olun.

PowerShell Galerisi ve PowerShellGet olarak cmdlet'leri bunları benzersiz olarak işleme, dikkat edilecek önemli etiketleri vardır. PSEdition_Desktop PSEdition_Core belirli örnekler ve yukarıda açıklanan.

Tutarlı bir şekilde birçok öğeleriniz genelinde belirli ve kullanılan olduklarında yukarıda belirtildiği gibi etiketleri en yüksek değeri sağlar. Kullanmak için en iyi etiketleri bulmaya çalışırken bir yayımcı, en kolay yaklaşım PowerShell Galerisi, değerlendiriyorsanız etiketleri için arama gerçekleştirmektir. İdeal olarak, döndürülen öğe sayısını olacaktır ve öğesi açıklamaları, bu anahtar sözcük kullanımını ile hizalanır.

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
| Derleme |  |
| Dağıtım | Dağıtma biraz daha az sıklıkta kullanılan |
| Bulut |  |
| GIT |  |
| Test | Testi daha az tercih edilir |
| VersionControl | Sürüm daha sık kullanılan olsa da daha az kesin  |
| Günlük | Tercih edilen bir eylem olarak günlük kullanımı |
| Günlük | Bir şey olarak tercih edilen kullanım günlüğü |
| Yedek |  |
| Iaas |  |
| Linux |  |
| IIS |  |
| AzureAutomation |  |
| Depolama |  |
| GitHub |  |
| JSON |  |
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
| Mac |  |
| PoshBot |  |