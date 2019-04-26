---
title: PowerShell Core 6.0 yenilikler nelerdir?
description: Yeni özellikler ve PowerShell Core 6. 0'yayımlanan değişiklikleri
ms.date: 08/06/2018
ms.openlocfilehash: 83c104d838db9d86fe1d485e92245a9c8f2d2057
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62059024"
---
# <a name="whats-new-in-powershell-core-60"></a>PowerShell Core 6.0 yenilikler nelerdir?

[PowerShell Core 6.0] [ github] yeni platformlar arası (Windows, macOS ve Linux) olan bir PowerShell sürümüdür, açık kaynaklı ve heterojen ortamlar ve hibrit bulut için oluşturulmuştur.

## <a name="moved-from-net-framework-to-net-core"></a>.NET Core ile .NET Framework'ten taşındı

PowerShell Core kullanan [.NET Core 2.0][] kendi çalışma zamanı.
.NET core 2.0 (Windows, macOS ve Linux) birden çok platformda çalışması PowerShell Core sağlar.
PowerShell Core PowerShell cmdlet'leri ve komut dosyalarında kullanılacak .NET Core 2.0 tarafından sunulan API kümesini de gösterir.

Windows PowerShell, .NET Framework çalışma zamanı PowerShell altyapısı barındırmak için kullanılır.
Başka bir deyişle, Windows PowerShell, .NET Framework tarafından sağlanan API kümesini kullanıma sunar.

.NET Core ve .NET Framework arasında paylaşılan API'leri bir parçası olarak tanımlanan [.NET Standard][].

Bu PowerShell Core ve Windows PowerShell modülü/komut dosyası uyumluluğu nasıl etkilediği hakkında daha fazla bilgi için bkz: [Backwards uyumluluk Windows PowerShell ile](#backwards-compatibility-with-windows-powershell).

## <a name="support-for-macos-and-linux"></a>MacOS ve Linux desteği

PowerShell artık resmi olarak desteklemektedir macOS ve Linux dahil olmak üzere:

- Windows 7, 8.1 ve 10
- Windows Server 2008 R2, 2012 R2, 2016
- [Windows Server yarı yıllık kanal][semi-annual]
- Ubuntu 14.04 ve 16.04 17.04
- Debian 8,7 + ve 9
- CentOS 7
- Red Hat Enterprise Linux 7
- OpenSUSE 42.2
- Fedora 25, 26
- macOS 10.12 +

Topluluğumuza paketleri aşağıdaki platformlar için de katkılarıyla ancak resmi olarak desteklenmez:

- Linux arch
- Kali Linux
- AppImage (birden çok Linux platformlarında çalışır)

Aşağıdaki platformlar için Deneysel (desteklenmeyen) sürümleri de sahibiz:

- Windows üzerinde ARM32/ARM64
- Raspbian (Esnetme)

Bir dizi değişiklik, daha iyi olmayan Windows sistemlerinde çalışması için PowerShell Core 6. 0'için yapıldı.
Bunlardan bazıları aynı zamanda Windows etkileyen değişiklikler ayırırsınız.
Diğerleri yalnızca yok veya geçerli olmayan Windows yüklemelerinde PowerShell Core ise.

- Unix platformlarında yerel komut Genelleştirme için destek eklendi.
- `more` İşlevselliği uyar Linux `$PAGER` ve varsayılan olarak `less`.
  Bu artık kullanabileceğiniz joker karakterler yerel ikili dosyaları/komutlarıyla anlamına gelir (örneğin, `ls *.txt`). (#3463)
- Sondaki ters eğik çizgi, otomatik olarak yerel komut bağımsız değişkenleri ile ilgilenirken kaçırılmışsa. (#4965)
- Yoksay `-ExecutionPolicy` PowerShell betik imzalama şu anda desteklenmediğinden Windows dışı platformlarda çalışırken geçin. (#3481)
- Kabul etmenin ConsoleHost sabit `NoEcho` Unix platformlarında. (#3801)
- Sabit `Get-Help` Unix platformlarında büyük küçük harfe duyarlı desen eşleştirme desteklemek için. (#3852)
- `powershell` Pakete eklenen man sayfası

### <a name="logging"></a>Günlük

MacOS, yerel PowerShell kullanan `os_log` Apple oturum API'leri [birleştirilmiş günlük sistemi][os_log].
Linux üzerinde PowerShell kullanan [Syslog][], bulunabilen günlüğü çözüm.

### <a name="filesystem"></a>dosya sistemi

Bir dizi değişiklik, macOS ve Linux'ta Windows üzerinde değil, geleneksel olarak desteklenen dosya adı karakterleri desteklemek için yapılmıştır:

- Cmdlet'leri için verilen şimdi eğik çizgi çift yaşamaz yollardır (hem / ve \ dizin ayırıcı olarak çalışır)
- XDG temel dizin belirtimi dikkate ve varsayılan olarak kullanılabilir:
  - Linux/macOS profil yolu bulunur `~/.config/powershell/profile.ps1`
  - Geçmişini kaydetme yolu şu konumdadır: `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`
  - Kullanıcı modül yolu bulunur `~/.local/share/powershell/Modules`
- UNIX virgül karakteri içeren dosya ve klasör adları için destek. (#4959)
- Betik adı veya virgül olan tam yolu için destek. (#4136) (Performanstan [ @TimCurwick ](https://github.com/TimCurwick)!)
- Algılama `-LiteralPath` Gezinti cmdlet'leri için joker karakter genişletmesi gizlemek için kullanılır. (#5038)
- Güncelleştirilmiş `Get-ChildItem` daha fazla benzer çalışmak için * nix `ls -R` ve Windows `DIR /S` yerel komutları.
  `Get-ChildItem` yinelemeli arama sırasında karşılaşılan sembolik bağlantıları artık döndürür ve dizinleri aramaz, bu bağlantıları hedef. (#3780)

### <a name="case-sensitivity"></a>Büyük/küçük harfe duyarlılık

Linux ve Macos'ta durumu korurken Windows büyük küçük harf duyarsız olmakla birlikte, büyük/küçük harfe olma eğilimindedir.
Genel olarak, PowerShell, büyük/küçük harf ve büyük harflere duyarlı değildir.

Örneğin, ortam değişkenleri macOS ve Linux'ta, büyük küçük harfe duyarlıdır böylece büyük/küçük harfleri, `PSModulePath` ortam değişkeni standart. (#3255) `Import-Module` modülün adını belirlemek için bir dosya yolu kullanırken büyük/küçük harfe duyarlıdır. (#5097)

## <a name="support-for-side-by-side-installations"></a>Yan yana yüklemeleri için destek

PowerShell Core yüklü, yapılandırılmış ve Windows PowerShell üzerinden ayrı olarak yürütülür.
PowerShell Core "taşınabilir" bir ZIP paketini sahiptir.
ZIP paketini kullanarak, herhangi bir sayıda sürümleri herhangi bir diskte, yerel PowerShell bağımlılık olarak alan bir uygulamaya dahil olmak üzere yükleyebilirsiniz.
Yan yana yükleme zamanla PowerShell ve geçirme mevcut betiklerini yeni sürümlerini test etmek kolaylaştırır.
Betikleri ihtiyaç duydukları belirli sürümleri için sabitlenebilir gibi yan yana da geriye dönük uyumluluk sağlar.

> [!NOTE]
> Varsayılan olarak, Windows üzerinde MSI tabanlı yükleyicide yerinde güncelleştirme yüklemeyi desteklemez.
>

## <a name="renamed-powershellexe-to-pwshexe"></a>Yeniden adlandırılan `powershell(.exe)` için `pwsh(.exe)`

PowerShell Core için ikili dosya adı değiştirilmiştir `powershell(.exe)` için `pwsh(.exe)`.
Bu değişikliğin yan yana Windows PowerShell ve PowerShell Core yüklemeleri desteklemek için PowerShell Core makinelerde çalıştırılmak üzere kullanıcıların belirleyici bir yol sağlar.
`pwsh` Ayrıca, daha kısa ve yazmak daha kolay olur.

Ek değişiklikler `pwsh(.exe)` gelen `powershell.exe`:

- İlk konumsal parametresinden değiştirilen `-Command` için `-File`.
  Bu değişiklik kullanımını düzeltmeleri `#!` (diğer adıyla olarak bir shebang'i) PowerShell olmayan Kabukları Windows dışı platformlarda yürütülür PowerShell komut.
  Ayrıca gibi komutları çalıştırabilirsiniz geldiğini `pwsh foo.ps1` veya `pwsh fooScript` belirtmeden `-File`.
  Ancak, bu değişiklik açıkça belirttiğiniz gerektirir `-c` veya `-Command` gibi komutları çalıştırmak çalışırken `pwsh.exe -Command Get-Command`. (#4019)
- PowerShell Core kabul `-i` (veya `-Interactive`) etkileşimli bir kabuk göstermek için anahtar. (#3558) Bu, bir Unix platformlarında üzerindeki varsayılan kabuk olarak kullanılmak üzere PowerShell sağlar.
- Parametreleri kaldırıldı `-importsystemmodules` ve `-psconsoleFile` gelen `pwsh.exe`. (#4995)
- Değiştirilen `pwsh -version` ve yerleşik Yardım `pwsh.exe` yerel diğer araçlar ile hizalamak için. (#4958 & #4931) (Thanks [@iSazonov](https://github.com/iSazonov))
- Geçersiz bağımsız değişken için hata iletileri `-File` ve `-Command` ve çıkış kodları UNIX standartları ile tutarlı (#4573)
- Eklenen `-WindowStyle` Windows parametresi. (#4573) Benzer şekilde, paket tabanlı yüklemeler güncelleştirmeleri Windows dışı platformlarda yerinde güncelleştirmelerdir.

## <a name="backwards-compatibility-with-windows-powershell"></a>Geriye dönük uyumluluk Windows PowerShell ile

PowerShell Core Windows PowerShell ile mümkün olduğu kadar uyumlu kalmasını hedefidir.
PowerShell Core kullanan [.NET Standard][] 2.0 ile mevcut .NET derlemelerini ikili uyumluluk sağlamak için.
Bu bütünleştirilmiş kodları (genellikle saatler dll), çok sayıda PowerShell modülü bağımlı böylece .NET Standard .NET Core ile çalışmaya devam etmelerini sağlar.
PowerShell Core, Genel Derleme Önbelleği genellikle .NET Framework DLL bağımlılıkları bulmak için diskte yer aldığı gibi iyi bilinen klasörlerde--aramak için bir buluşsal yöntem de içerir.

.NET Standard hakkında daha fazla bilgi edinebilirsiniz [.NET blogu][], bu [YouTube][] video ve bu aracılığıyla [SSS][] GitHub üzerinde.

Dil ve "yerleşik" PowerShell modüllerine emin olmak için en iyi çaba yapıldı (gibi `Microsoft.PowerShell.Management`, `Microsoft.PowerShell.Utility`, vs.) Windows PowerShell'de bunu aynı şekilde işler.
Çoğu durumda, bir topluluk yardımıyla yeni özellikler ve hata düzeltmeleri cmdlet'ler için ekledik.
Bazı durumlarda, temel alınan .NET katmanlarında eksik bir bağımlılık nedeniyle işlevi kaldırıldı veya kullanılamıyor.

Windows bir parçası olarak gönderilen modüllerinin çoğu (örneğin, `DnsClient`, `Hyper-V`, `NetTCPIP`, `Storage`, vs.) ve Azure ve Office gibi diğer Microsoft ürünleri karşılanmadığını *açıkça* için verilir. NET Core henüz.
PowerShell ekibi, bu ürün gruplarını ve takımlar kendi mevcut modülleri PowerShell Core için bağlantı noktası ve doğrulamak için birlikte çalışıyor.
.NET Standard ile ve [CDXML][], birçok geleneksel bu Windows PowerShell modülleri PowerShell Core ortağımdan ancak bunlar resmi olarak doğrulanmamış ve resmi olarak desteklenmez.

Yükleyerek [ `WindowsPSModulePath` ] [ windowspsmodulepath] modülü, Windows PowerShell ekleyerek Windows PowerShell modüllerini kullanabilirsiniz `PSModulePath` , PowerShell Core `PSModulePath`.

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

## <a name="docker-support"></a>Docker desteği

PowerShell Core, Docker kapsayıcıları için (birden çok Linux dağıtımları, Windows Sunucu Çekirdeği ve Nano sunucu dahil) destekliyoruz tüm büyük platformlar için destek ekler.

Etiketleri tam listesi için kontrol [ `microsoft/powershell` Docker hub'da][docker-hub].
Docker ve PowerShell Core hakkında daha fazla bilgi için bkz. [Docker][] GitHub üzerinde.

## <a name="ssh-based-powershell-remoting"></a>SSH tabanlı PowerShell uzaktan iletişimi

PowerShell uzaktan iletişim protokolü (PSRP) artık güvenli Kabuk (SSH) protokolünü geleneksel WinRM tabanlı PSRP yanı sıra ile çalışır.

Bu cmdlet'leri gibi kullanabileceğiniz anlamına gelir `Enter-PSSession` ve `New-PSSession` ve SSH kullanarak kimlik doğrulaması.
Yapmanız gereken tek şey bir OpenSSH tabanlı SSH sunucusu ile bir alt olarak PowerShell kaydetmek ve mevcut SSH tabanlı kullanabilirsiniz (örneğin, parolalar veya özel anahtarlar) mekanizmaları geleneksel ile kimlik doğrulaması `PSSession` semantiği.

Yapılandırma ve SSH tabanlı uzaktan iletişimini kullanma hakkında daha fazla bilgi için bkz. [SSH üzerinden PowerShell uzaktan iletişimi][ssh-remoting].

## <a name="default-encoding-is-utf-8-without-a-bom-except-for-new-modulemanifest"></a>Varsayılan kodlama: UTF-8 içermeyen yeni ModuleManifest dışında bir ürün reçetesi

Geçmişte, Windows PowerShell cmdlet'leri ister `Get-Content`, `Set-Content` ASCII ve UTF-16 gibi farklı kodlamaları kullanılır.
Fark, kodlama varsayılan olarak, cmdlet'leri bir kodlama belirtmeden kullanırken sorunları oluşturuldu.

Windows dışındaki platformlara kodlama metin dosyaları için varsayılan olarak UTF-8 bir bayt sırası işareti (BOM) olmadan geleneksel olarak kullanın.
Daha fazla Windows uygulama ve araçların uzağa UTF-16 ve BOM daha az UTF-8 kodlaması doğrultusunda geçiş yapıyor.
PowerShell Core için varsayılan kodlama ile daha geniş ekosistemlerini uyacak şekilde değiştirir.

Tüm yerleşik cmdlet'ler kullanan başka bir deyişle `-Encoding` parametresi kullanımı `UTF8NoBOM` varsayılan değeri.
Bu değişiklikten aşağıdaki cmdlet'ler etkilenir:

- İçerik Ekle
- Dışarı aktarma Clixml
- Export-Csv
- Export-PSSession
- Format-Hex
- Get-içerik
- Import-Csv
- Dış dosya
- Dize seçin
- Send-MailMessage
- Set-içerik

Bu cmdlet'leri ayrıca güncelleştirdik böylece `-Encoding` Evrensel parametreyi kabul eden `System.Text.Encoding`.

Varsayılan değer olan `$OutputEncoding` UTF-8 olarak değiştirildi.

En iyi uygulama, açıkça betiklerini kullanarak Kodlamalar ayarlamalısınız `-Encoding` platformlar arasında belirleyici davranışı oluşturmak için parametre.

`New-ModuleManifest` cmdlet yok **kodlama** parametresi. İle oluşturulan modül bildirimi (.psd1) dosyanın kodlamasını `New-ModuleManifest` cmdlet'i ortama bağlıdır: PowerShell Core ise Linux üzerinde çalışan ardından kodlama UTF-8 (hiçbir BOM); Aksi takdirde kodlama UTF-16 (BOM). (#3940)

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>İşlem hatlarını ve işareti ile arka planda işleme desteği (`&`) (#3360)

Yerleştirme `&` bir ardışık düzen sonunda ardışık bir PowerShell iş çalıştırılmasına neden olur.
Bir işlem hattı backgrounded, işi nesne döndürülür.
İşlem hattı, bir iş olarak, tüm standart çalışmaya başladıktan sonra `*-Job` cmdlet'leri, işi yönetmek için kullanılabilir.
İşlem hattında kullanılan (işleme özel değişkenleri yoksayar) değişkenlerini otomatik olarak kopyalanıp kopyalanmayacağını işe kadar `Copy-Item $foo $bar &` yalnızca çalışır.
İş yerine kullanıcının ana dizini geçerli dizinde da çalıştırılır.
PowerShell işleri hakkında daha fazla bilgi için bkz. [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs).

## <a name="semantic-versioning"></a>Semantic versioning

- Yapılan `SemanticVersion` uyumlu `SemVer 2.0`. (#5037) (Thanks [@iSazonov](https://github.com/iSazonov)!)
- Değiştirilen varsayılan `ModuleVersion` içinde `New-ModuleManifest` için `0.0.1` SemVer ile hizalamak için. (#4842) (Thanks [@LDSpits](https://github.com/LDSpits))
- Eklenen `semver` için tür Hızlandırıcı olarak `System.Management.Automation.SemanticVersion`. (#4142) (Performanstan [ @oising ](https://github.com/oising)!)
- Karşılaştırma arasında etkin bir `SemanticVersion` örneği ve bir `Version` yalnızca ile oluşturulan örnek `Major` ve `Minor` sürüm değerleri.

## <a name="language-updates"></a>Dil güncelleştirmeleri

- Unicode kaçış kullanıcılar Unicode karakter bağımsız değişkenleri, dize veya değişken adları kullanabilmesi için ayrıştırma uygulayın. (#3958) (Performanstan [ @rkeithhill ](https://github.com/rkeithhill)!)
- Eklenen yeni kaçış karakteri ESC için: `` `e``
- Numaralandırmalar (#4318) dize dönüştürme için destek eklendi (teşekkürler [ @KirkMunro ](https://github.com/KirkMunro))
- Sabit atama tek öğeli bir dizi için bir genel koleksiyon. (#3170)
- Eklenen karakter aralığı aşırı `..` işleci, bu nedenle `'a'..'z'` 'bir kaynak'-'z' karakterleri döndürür. (#5026) (Thanks [@IISResetMe](https://github.com/IISResetMe)!)
- Salt okunur değişkenler üzerine değil, sabit değişken ataması
- Otomatik değişkenlerin Yereller 'DottedScopes' için betik cmdlet'lerini dotting push (#4709)
- Bölme işleci 'Singleline, çok satırlı' seçeneğinin kullanımını etkinleştir (#4721) (teşekkürler [ @iSazonov ](https://github.com/iSazonov))

## <a name="engine-updates"></a>Altyapı güncelleştirmeleri

- `$PSVersionTable` dört yeni özelliklere sahiptir:
  - `PSEdition`: Bu ayar `Core` PowerShell core'da ve `Desktop` Windows PowerShell
  - `GitCommitId`: Burada PowerShell oluşturulmuş Git dalı veya da etiketi Git işleme kimliği budur.
    Yayımlanan sürümlerde, büyük olasılıkla aynı olacaktır `PSVersion`.
  - `OS`: Tarafından döndürülen bir işletim sistemi sürümü dize budur. `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription`
  - `Platform`: Tarafından döndürülen bu `[System.Environment]::OSVersion.Platform` ayarlanır `Win32NT` , Windows üzerinde `Unix` , MacOS ve `Unix` Linux üzerinde.
- Kaldırılan `BuildVersion` özelliğinden `$PSVersionTable`.
  Bu özellik, Windows yapı sürümüne bağlı.
  Bunun yerine kullanmanızı öneriyoruz `GitCommitId` PowerShell Core tam derleme sürümü almak için. (#3877) (Performanstan [ @iSazonov ](https://github.com/iSazonov)!)
- Kaldırma `ClrVersion` özelliğinden `$PSVersionTable`.
  Bu özellik, .NET Core için ilgisizdir ve PowerShell için geçerli değil ve eski belirli amaçlar için de .NET Core yalnızca korundu.
- PowerShell belirli bir işletim sisteminde çalışır durumda olup olmadığını belirlemek için üç yeni Otomatik değişkenleri eklenmiştir: `$IsWindows`, `$IsMacOs`, ve `$IsLinux`.
- Ekleme `GitCommitId` için PowerShell Core başlığı.
  Şimdi Çalıştır gerekmez `$PSVersionTable` sürümü almak için PowerShell başlar başlamaz! (#3916) (Performanstan [ @iSazonov ](https://github.com/iSazonov)!)
- Adlı bir JSON yapılandırma dosyasını ekleyin `powershell.config.json` içinde `$PSHome` başlangıç zamanından önce gereken bazı ayarları depolamak için (örneğin `ExecutionPolicy`).
- İşlem hattı Windows EXE'ın çalıştırırken engelleme
- COM koleksiyonları etkin numaralandırması. (#4553)

## <a name="cmdlet-updates"></a>Cmdlet güncelleştirmeleri

### <a name="new-cmdlets"></a>Yeni cmdlet'ler

- Add `Get-Uptime` to `Microsoft.PowerShell.Utility`.
- Ekleme `Remove-Alias` komutu. (#5143) (Teşekkürler [ @PowershellNinja ](https://github.com/PowershellNinja)!)
- Ekleme `Remove-Service` yönetim modülü. (#4858) (Thanks [@joandrsn](https://github.com/joandrsn)!)

### <a name="web-cmdlets"></a>Web cmdlet'leri

- Web cmdlet'leri için sertifika kimlik doğrulaması desteği eklendi. (#4646) (Thanks [@markekraus](https://github.com/markekraus))
- İçerik üstbilgileri için destek web cmdlet'leri eklendi. (#4494 & #4640) (Thanks [@markekraus](https://github.com/markekraus))
- Web Cmdlet'lerine birden çok bağlantı üstbilgi desteği eklendi. (#5265) (Thanks [@markekraus](https://github.com/markekraus)!)
- Bağlantı üstbilgi sayfalandırma web cmdlet'lerinde destek (#3828)
  - İçin `Invoke-WebRequest`, oluşturduğumuz RelationLink özelliği URL'leri temsil eden bir sözlük olarak bir bağlantı üstbilgisi yanıt içerir ve `rel` öznitelikleri ve geliştirici kullanmayı kolaylaştırmak için mutlak URL'ler olduğundan emin olun.
  - İçin `Invoke-RestMethod`, yanıt kullanıma sunuyoruz bağlantı üstbilgi içerdiğinde bir `-FollowRelLink` otomatik olarak izlemek için anahtar `next` `rel` artık mevcut kadar bağlantılar veya bir kez biz isabet isteğe bağlı `-MaximumFollowRelLink` parametre değeri.
- Ekleme `-CustomMethod` web cmdlet'leri için standart yöntemi fiillere izin vermek için parametre. (#3142) (Performanstan [ @Lee303 ](https://github.com/Lee303)!)
- Ekleme `SslProtocol` Web cmdlet'leri için destek. (#5329) (Thanks [@markekraus](https://github.com/markekraus)!)
- Çok bölümlü ekleme web cmdlet'leri için destek. (#4782) (Thanks [@markekraus](https://github.com/markekraus))
- Ekleme `-NoProxy` web Cmdlet'lerine böylece bunlar sistem genelinde proxy ayarı yoksayar. (#3447) (Performanstan [ @TheFlyingCorpse ](https://github.com/TheFlyingCorpse)!)
- Kullanıcı Aracısı, Web cmdlet'leri, işletim sistemi platformu artık raporları (#4937) (teşekkürler [ @LDSpits ](https://github.com/LDSpits))
- Ekleme `-SkipHeaderValidation` üstbilgi değeri doğrulamadan ekleme üstbilgileri destekleyen web cmdlet'ler geçin. (#4085)
- Sunucusunun HTTPS sertifikası gerekli değil doğrulanacak web cmdlet'leri etkinleştirin.
- Kimlik doğrulama parametreleriyle web Cmdlet'lerine eklendi. (#5052) (Thanks [@markekraus](https://github.com/markekraus))
  - Ekleme `-Authentication` bu seçeneklerin üçünü de sunar: Temel, OAuth ve taşıyıcı.
  - Ekleme `-Token` OAuth ve taşıyıcı seçeneklerini taşıyıcı belirteci alma işlemi.
  - Ekleme `-AllowUnencryptedAuthentication` HTTPS dışında herhangi bir taşıma şeması için sağlanan kimlik doğrulamasını atlamak için.
- Ekleme `-ResponseHeadersVariable` için `Invoke-RestMethod` yanıt üst bilgilerini yakalama olanağı. (#4888) (Thanks [@markekraus](https://github.com/markekraus))
- HTTP yanıtı yanıt durum kodu başarılı olmadığında özel duruma dahil etmek için web cmdlet'leri düzeltildi. (#3201)
- Değiştirme web cmdlet'leri `UserAgent` gelen `WindowsPowerShell` için `PowerShell`. (#4914) (Thanks [@markekraus](https://github.com/markekraus))
- Açık ekleme `ContentType` algılamayı `Invoke-RestMethod` (#4692)
- Web cmdlet'leri düzeltme `-SkipHeaderValidation` standart kullanıcı aracısını üst bilgileri ile çalışmak için. (#4479 & #4512) (Teşekkürler [ @markekraus ](https://github.com/markekraus))

### <a name="json-cmdlets"></a>JSON cmdlet'leri

- Ekleme `-AsHashtable` için `ConvertFrom-Json` döndürülecek bir `Hashtable` yerine. (#5043) (Teşekkürler [ @bergmeister ](https://github.com/bergmeister)!)
- İle prettier biçimlendiricisini kullanmayı `ConvertTo-Json` çıktı. (#2787) (Performanstan @kittholland!)
- Ekleme `Jobject` serileştirme desteklemek için `ConvertTo-Json`. (#5141)
- Düzeltme `ConvertFrom-Json` işlem hattından birlikte eksiksiz bir JSON dizesi oluşturmak bir dize dizisi seri durumdan çıkarılacak.
  Bu, bazı durumlarda yeni satırlardan JSON ayrıştırma nerede kesmek düzeltir. (#3823)
- Kaldırma `AliasProperty "Count"` için tanımlanan `System.Array`.
  Bu fazlalık kaldırır `Count` bazı özellik `ConvertFrom-Json` çıktı. (#3231) (Performanstan [ @PetSerAl ](https://github.com/PetSerAl)!)

### <a name="csv-cmdlets"></a>CSV cmdlet'leri

- Ekleme `PSTypeName` desteği `Import-Csv` ve `ConvertFrom-Csv`. (#5389) (Thanks [@markekraus](https://github.com/markekraus)!)
- Olun `Import-Csv` Destek `CR`, `LF`, ve `CRLF` ayırıcıları hat. (#5363) (Thanks [@iSazonov](https://github.com/iSazonov)!)
- Olun `-NoTypeInformation` varsayılan `Export-Csv` ve `ConvertTo-Csv`. (#5164) (Thanks [@markekraus](https://github.com/markekraus))

### <a name="service-cmdlets"></a>Hizmeti cmdlet'leri

- Özellikler ekleme `UserName`, `Description`, `DelayedAutoStart`, `BinaryPathName`, ve `StartupType` için `ServiceController` tarafından döndürülen nesne `Get-Service`. (#4907) (Thanks [@joandrsn](https://github.com/joandrsn))
- Kimlik bilgilerini ayarlamak için işlevsellik ekleyen `Set-Service` komutu. (#4844) (Thanks [@joandrsn](https://github.com/joandrsn))

### <a name="other-cmdlets"></a>Diğer cmdlet'ler

- Bir parametre ekleyin `Get-ChildItem` adlı `-FollowSymlink` bağlantı döngüler için denetimleri ile isteğe bağlı olarak çözümlemeyin erişir. (#4020)
- Güncelleştirme `Add-Type` desteklemek için `CSharpVersion7`. (#3933) (Performanstan [ @iSazonov ](https://github.com/iSazonov))
- Kaldırma `Microsoft.PowerShell.LocalAccounts` daha iyi bir çözüm bulunana kadar desteklenmeyen API kullanımı nedeniyle modülü. (#4302)
- Kaldırma `*-Counter` cmdlet'leri `Microsoft.PowerShell.Diagnostics` daha iyi bir çözüm bulunana kadar desteklenmeyen API kullanımı nedeniyle. (#4303)
- İçin destek ekleme `Invoke-Item -Path <folder>`. (#4262)
- Ekleme `-Extension` ve `-LeafBase` geçer `Split-Path` böylece dosya adı uzantısı ve dosya adını geri kalanı arasındaki yolları bölebilirsiniz. (#2721) (Performanstan [ @powercode ](https://github.com/powercode)!)
- Parametre ekleme `-Top` ve `-Bottom` için `Sort-Object` için üst/alt N sıralama
- Bir işlem üst işlemi ekleyerek kullanıma `CodeProperty "Parent"` için `System.Diagnostics.Process`. (#2850) (Performanstan [ @powercode ](https://github.com/powercode)!)
- MB bellek sütunlar için KB yerine kullanın. `Get-Process`
- Ekleme `-NoNewLine` için geçiş `Out-String`. (#5056) (Thanks [@raghav710](https://github.com/raghav710))
- `Move-Item` cmdlet geliştirir `-Include`, `-Exclude`, ve `-Filter` parametreleri. (#3878)
- İzin `*` kayıt defteri yolu için kullanılacak `Remove-Item`. (#4866)
- Ekleme `-Title` için `Get-Credential` ve platformlar arasında istemi deneyimi birleştirin.
- Ekleme `-TimeOut` parametresi `Test-Connection`. (#2492)
- `Get-AuthenticodeSignature` cmdlet'leri artık dosya imza zaman damgası alabilirsiniz. (#4061)
- Desteklenmeyen Kaldır `-ShowWindow` geçmek `Get-Help`. (#4903)
- Düzeltme `Get-Content -Delimiter` (#3706) döndürülen dizi öğelerinde sınırlayıcı eklememeyi (teşekkürler [ @mklement0 ](https://github.com/mklement0))
- Ekleme `Meta`, `Charset`, ve `Transitional` parametreleri `ConvertTo-HTML` (#4184) (teşekkürler [ @ergo3114 ](https://github.com/ergo3114))
- Ekleme `WindowsUBR` ve `WindowsVersion` özelliklerine `Get-ComputerInfo` sonucu
- Ekleme `-Group` parametresi `Get-Verb`
- Ekleme `ShouldProcess` desteği `New-FileCatalog` ve `Test-FileCatalog` (düzeltmeler `-WhatIf` ve `-Confirm`). (#3074) (Performanstan [ @iSazonov ](https://github.com/iSazonov)!)
- Ekleme `-WhatIf` geçin `Start-Process` cmdlet'i (#4735) (teşekkürler [ @sarithsutha ](https://github.com/sarithsutha))
- Ekleme `ValidateNotNullOrEmpty` var olan çok fazla sayıda parametre.

## <a name="tab-completion"></a>Sekme tamamlama

- Çalışma zamanı değişken değerlerine göre sekme tamamlama içinde tür çıkarımı iyileştirdik. (#2744) (Performanstan [ @powercode ](https://github.com/powercode)!) Bu gibi durumlarda sekme tamamlama sağlar:

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- Hashtable için sekmesinde tamamlama ekleme `-Property` , `Select-Object`. (#3625) (Performanstan [ @powercode ](https://github.com/powercode))
- Bağımsız değişkeni için otomatik tamamlanmasını etkinleştirin `-ExcludeProperty` ve `-ExpandProperty` , `Select-Object`. (#3443) (Performanstan [ @iSazonov ](https://github.com/iSazonov)!)
- Bir hatayı düzeltme yapmak için sekme tamamlamayı `native.exe --<tab>` olanak sağlayacak tamamlayıcısı yerel çağrı. (#3633) (Performanstan [ @powercode ](https://github.com/powercode)!)

## <a name="breaking-changes"></a>Yeni değişiklikler

Bir dizi PowerShell Core 6. 0'ı bozucu değişiklik tanıttık.
Daha fazla bilgi için bunları hakkında ayrıntılı görmek [bozucu değişiklikleri PowerShell Core 6. 0'ı][breaking-changes].

## <a name="debugging"></a>Hata Ayıklama

- Uzaktan step-in için hata ayıklama desteği `Invoke-Command -ComputerName`. (#3015)
- Bağlayıcı hata ayıklama PowerShell Core günlüğünü etkinleştir

## <a name="filesystem-updates"></a>Dosya sistemi güncelleştirmeleri

- Bir UNC yolu dosya sistemi sağlayıcısından kullanımını etkinleştirin. ($4998)
- `Split-Path` Şimdi UNC kökü ile çalışır
- `cd` bağımsız değişken olmadan artık olarak davranır `cd ~`
- 260 karakterden uzun yollar kullanımına olanak tanımak için sabit PowerShell Core. (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>Hata düzeltmeleri ve performans iyileştirmeleri

Yaptık *birçok* başlatma süresi, çeşitli yerleşik cmdlet'ler ve yerel ikili dosyaları ile etkileşimi dahil olmak üzere PowerShell üzerinden performans geliştirmeleri.

PowerShell Core hataların sayısını da düzelttik.
Düzeltmeler ve değişiklikler tam listesi için kullanıma sunduğumuz [changelog][] GitHub üzerinde.

## <a name="telemetry"></a>Telemetri

- PowerShell Core eklenen 6.0 telemetri raporu iki konsol konağına değerleri (#3620):
  - işletim sistemi Platformu (`$PSVersionTable.OSDescription`)
  - PowerShell'ün tam sürümünü (`$PSVersionTable.GitCommitId`)

Çevirme bu telemetri isterseniz, basitçe oluşturma `POWERSHELL_TELEMETRY_OPTOUT` ortam değişkeni aşağıdaki değerlerden biriyle: `true`, `1` veya `yes`.
Değişken oluşturma PowerShell ilk çalıştırmada önce tüm telemetri atlar.
Ayrıca bu telemetri verilerini ve biz telemetriden bı'yi ınsights gösterme üzerinde planlıyoruz [topluluk Panosu][community-dashboard].
Biz bu verileri bu kullanma hakkında daha fazla bilgi bulabilirsiniz [blog gönderisi][telemetry-blog].

[github]: https://github.com/PowerShell/PowerShell
[.NET core 2.0]: https://docs.microsoft.com/dotnet/core/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[os_log]: https://developer.apple.com/documentation/os/logging
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[breaking-changes]: breaking-changes-ps6.md
[Changelog]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[telemetry-blog]: https://blogs.msdn.microsoft.com/powershell/2017/01/31/powershell-open-source-community-dashboard/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[.NET blogu]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
[SSS]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[CDXML]: https://msdn.microsoft.com/library/jj542525(v=vs.85).aspx
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[Docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
