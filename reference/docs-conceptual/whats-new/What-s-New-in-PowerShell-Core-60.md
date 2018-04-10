# <a name="whats-new-in-powershell-core-60"></a>PowerShell çekirdek 6.0 yenilikler nelerdir?

[PowerShell çekirdek 6.0] [ github] çapraz platform (Windows, macOS ve Linux) PowerShell yeni bir sürümü, açık kaynaklı ve oluşturulmuş heterojen ortamlar ve karma bulut.

## <a name="moved-from-net-framework-to-net-core"></a>.NET Framework'teki .NET Core taşındı

PowerShell çekirdek kullanan [.NET Core 2.0][] kendi çalışma zamanı olarak.
.NET core 2.0 birden çok Platformu (Windows, macOS ve Linux) çalışmak PowerShell çekirdek sağlar.
PowerShell çekirdek ayrıca PowerShell cmdlet'leri ve komut dosyalarında kullanılacak .NET Core 2.0 tarafından sunulan API kümesi gösterir.

Windows PowerShell, .NET Framework çalışma zamanının PowerShell altyapısı barındırmak için kullanılır.
Başka bir deyişle, Windows PowerShell, .NET Framework tarafından sunulan API kümesi kullanıma sunar.

.NET Core ve .NET Framework arasında paylaşılan API'leri parçası olarak tanımlanan [.NET standart][].

Bunun PowerShell çekirdek ve Windows PowerShell modülü/komut dosyası uyumluluğu nasıl etkilediği hakkında daha fazla bilgi için bkz: [Backwards uyumluluk Windows PowerShell ile](#backwards-compatibility-with-windows-powershell).

## <a name="support-for-macos-and-linux"></a>MacOS ve Linux desteği

PowerShell artık resmi olarak destekler macOS ve Linux dahil olmak üzere:

- Windows 7, 8.1 ve 10
- Windows Server 2008 R2, 2012 R2, 2016
- [Windows Server noktalı yıllık kanalı][semi-annual]
- Ubuntu 14.04 ve 16.04 17.04
- Debian 8.7 + ve 9
- CentOS 7
- Red Hat Enterprise Linux 7
- OpenSUSE 42.2
- Fedora 25 26
- macOS 10.12+

Topluluğumuz ayrıca aşağıdaki platformları için paketleri katıldığını ancak resmi olarak desteklenmez:

- Linux arch
- Kali Linux
- AppImage (birden çok Linux platformlar üzerinde çalışır)

Deneysel (desteklenmeyen) sürümleri aşağıdaki platformları için de sunuyoruz:

- ARM32/ARM64 Windows
- Raspbian (Esnetme)

Değişiklik sayısı PowerShell çekirdek 6. 0 ' Windows olmayan sistemleri üzerinde daha iyi çalışması için yapıldı.
Bunlardan bazıları aynı zamanda Windows etkileyen değişiklikleri ayırırsınız.
Başkalarının yalnızca yok veya PowerShell çekirdek Windows olmayan yüklemeleri için uygulanabilir.

- Yerel komutu genelleme UNIX platformlar için destek eklendi.
- `more` İşlevselliği uyar Linux `$PAGER` ve varsayılan olarak `less`.
  Şimdi kullanabileceğiniz joker karakterler yerel ikili/komutları ile bu anlamına gelir (örneğin, `ls *.txt`). (#3463)
- Ters eğik çizgi sonunda otomatik olarak yerel komut bağımsız değişkenlerini ilgilenirken kaçışlı. (#4965)
- Yoksay `-ExecutionPolicy` PowerShell komut dosyası imzalama şu anda desteklenmediğinden olmayan Windows platformlarında çalıştırırken geçin. (#3481)
- Vermenizin ConsoleHost sabit `NoEcho` UNIX platformlarda. (#3801)
- Sabit `Get-Help` UNIX platformlarında büyük küçük harfe duyarlı desen eşleştirme desteklemek için. (#3852)
- `powershell` Pakete eklenen adam sayfası

### <a name="logging"></a>Günlük

MacOS üzerinde yerel PowerShell kullanan `os_log` Apple için oturum API'leri [günlük sistem birleşik][os_log].
Linux üzerinde PowerShell kullanan [Syslog][], bulunabilen günlük çözümü.

### <a name="filesystem"></a>Dosya sistemi

Değişiklik sayısı macOS ve Linux üzerinde Windows olmayan geleneksel olarak desteklenen dosya adı karakterleri desteklemek için yapılmıştır:

- Cmdlet'leri için verilen şimdi eğik çizgi belirsiz yollardır (hem / ve \ dizin ayırıcı olarak çalışır)
- XDG temel dizin belirtimi dikkate ve varsayılan olarak kullanılabilir:
  - Linux/macOS profil yolu bulunur `~/.config/powershell/profile.ps1`
  - Geçmiş kaydetme yolu bulunur `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`
  - Kullanıcı modülü yolu bulunur `~/.local/share/powershell/Modules`
- UNIX iki nokta üst üste karakteri içeren dosya ve klasör adları için destek. (#4959)
- Komut dosyası adları veya virgül sahip tam yollar için destek. (#4136) (Teşekkürler @TimCurwick!)
- Algılama `-LiteralPath` Gezinti cmdlet'leri için joker karakter genişletmesi bastırmak için kullanılır. (#5038)
- Güncelleştirilmiş `Get-ChildItem` daha fazla benzer çalışmaya * nix `ls -R` ve Windows `DIR /S` yerel komutları.
  `Get-ChildItem` Şimdi bir özyinelemeli arama sırasında karşılaşılan sembolik bağlantılar döndürür ve dizinleri aramaz, bu bağlantılar hedef. (#3780)

### <a name="case-sensitivity"></a>Büyük/küçük harfe duyarlılık

Linux ve macOS Windows durum korurken büyük küçük harf duyarsız olsa da büyük küçük harfe duyarlı olma eğilimindedir.
Genel olarak, PowerShell büyük küçük harfe duyarlı.

Örneğin, ortam değişkenleri macOS ve Linux, büyük küçük harfe duyarlıdır kadar büyük/küçük harfleri, `PSModulePath` ortam değişkeni standartlaştırılmıştır. (#3255) `Import-Module` modülünün adını belirlemek için bir dosya yolu kullanırken büyük küçük harfe duyarlı değil. (#5097)

## <a name="support-for-side-by-side-installations"></a>Yan yana yüklemeler için destek

PowerShell çekirdek yüklenir, yapılandırılmış ve Windows Powershell'den ayrı olarak yürütülür.
PowerShell çekirdek "taşınabilir" ZIP paketini sahiptir.
ZIP paketini kullanarak, sürümleri herhangi bir sayıda herhangi bir yere yerel PowerShell bağımlılık olarak alan bir uygulamaya dahil olmak üzere diskteki yükleyebilirsiniz.
Yan yana yükleme zamanla PowerShell ve geçirme varolan komut dosyalarını yeni sürümlerini test etmek daha kolay hale getirir.
Komut dosyaları için gereksinim duydukları belirli sürümler sabitlenmiş olmak gibi yan yana ayrıca geriye dönük uyumluluk sağlar.

> [!NOTE]
> Varsayılan olarak, Windows Installer MSI tabanlı bir yerinde güncelleştirme yüklemesini desteklemez.
>

## <a name="renamed-powershellexe-to-pwshexe"></a>Yeniden adlandırılmış `powershell(.exe)` için `pwsh(.exe)`

PowerShell çekirdek için ikili dosya adı değiştirildi `powershell(.exe)` için `pwsh(.exe)`.
Bu değişiklik yan yana Windows PowerShell ve PowerShell çekirdeği yüklemelerini desteklemek için PowerShell çekirdek makineler üzerinde çalıştırılacak kullanıcılar belirleyici bir yol sağlar.
`pwsh` de çok daha kısa ve yazın daha kolay olur.

Ek değişiklikler `pwsh(.exe)` gelen `powershell.exe`:

- İlk konumsal parametresinden değiştirilen `-Command` için `-File`.
  Bu değişiklik kullanımını giderir `#!` (diğer adıyla olarak shebang) olmayan Windows platformlarında PowerShell olmayan Kabukları gelen yürütülen PowerShell komut.
  Aynı zamanda gibi komutları çalıştırabilirsiniz gelir `pwsh foo.ps1` veya `pwsh fooScript` belirtmeden `-File`.
  Ancak, bu değişikliği açıkça belirttiğiniz gerektirir `-c` veya `-Command` gibi komutları çalışmaya çalışırken `pwsh.exe -Command Get-Command`. (#4019)
- PowerShell çekirdek kabul `-i` (veya `-Interactive`) etkileşimli bir kabuk göstermek için anahtar. (#3558) Bu varsayılan kabuğunu UNIX platformlarda olarak kullanılacak PowerShell sağlar.
- Parametreleri kaldırılan `-importsystemmodules` ve `-psconsoleFile` gelen `pwsh.exe`. (#4995)
- Değiştirilen `pwsh -version` ve yerleşik Yardım için `pwsh.exe` diğer yerel araçlarıyla hizalamak için. (#4958 & #4931) (Teşekkürler @iSazonov)
- Geçersiz bağımsız değişken hata iletileri için `-File` ve `-Command` ve çıkış kodları UNIX standartları ile tutarlı (#4573)
- Eklenen `-WindowStyle` Windows parametresi. (#4573) Benzer şekilde, paket tabanlı yüklemeler olmayan Windows platformlarında yerinde güncelleştirmelerdir.

## <a name="backwards-compatibility-with-windows-powershell"></a>Geriye dönük uyumluluk Windows PowerShell ile

Windows PowerShell ile olabildiğince uyumlu olarak kalması için PowerShell çekirdek belirtilir.
PowerShell çekirdek kullanan [.NET standart][] varolan .NET derlemelerini ikili uyum sağlamak için 2.0.
Bu derlemeler (genellikle zaman DLL'ler), çok sayıda PowerShell modülü bağımlı böylece .NET standart .NET Core çalışmaya devam etmek bunları sağlar.
PowerShell çekirdek de Global Assembly Cache diskte--.NET Framework DLL bağımlılıkları bulmak için genellikle bulunduğu gibi bilinen klasörlerin--aramak için buluşsal yöntemi içerir.

Üzerinde .NET standart hakkında daha fazla bilgiyi [.NET Blog][], bu [YouTube][] video ve bu aracılığıyla [SSS][] github'da.

PowerShell dil ve "yerleşik" modülleri emin olmak için en iyi çaba yapıldı (gibi `Microsoft.PowerShell.Management`, `Microsoft.PowerShell.Utility`, vs.) Windows PowerShell içinde olduğu gibi aynı şekilde işler.
Çoğu durumda, topluluk yardımıyla yeni özellikler ve hata düzeltmeleri bu cmdlet'leri ekledik.
Bazı durumlarda, temel alınan .NET katmanlarında eksik bağımlılık nedeniyle işlevselliği kaldırıldı veya kullanılamıyor.

Windows'un bir parçası sevk modüllerin çoğu (örneğin, `DnsClient`, `Hyper-V`, `NetTCPIP`, `Storage`, vs.) ve Azure ve Office gibi diğer Microsoft ürünleri karşılanmadığını *açıkça* için bağlantı noktası kurulmuş. NET çekirdek henüz.
PowerShell ekibi, bu ürün grupları ve takımlar doğrulamak ve bunların varolan modüllerini PowerShell çekirdek bağlantı noktası ile çalışmaktadır.
.NET standart ile ve [CDXML][]geleneksel bu Windows PowerShell modülleri çoğunu PowerShell çekirdek iş görünüyor, ancak bunlar resmi olarak doğrulanmamış ve resmi olarak desteklenmez.

Yükleyerek [ `WindowsPSModulePath` ] [ windowspsmodulepath] modülü, Windows PowerShell ekleyerek Windows PowerShell modülleri kullanabilir `PSModulePath` PowerShell çekirdek için `PSModulePath`.

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

## <a name="docker-support"></a>Docker desteği

PowerShell çekirdek Docker kapsayıcıları (birden çok Linux distro'lar, Windows Sunucu Çekirdeği ve Nano Server dahil) destekliyoruz önde gelen tüm platformlar için destek ekler.

Etiketleri tam bir listesi için kontrol [ `microsoft/powershell` Docker hub'ındaki][docker-hub].
Docker ve PowerShell çekirdek hakkında daha fazla bilgi için bkz: [Docker][] github'da.

## <a name="ssh-based-powershell-remoting"></a>SSH tabanlı PowerShell uzaktan iletişim

PowerShell uzaktan iletişim protokolü (PSRP) şimdi geleneksel WinRM tabanlı PSRP yanı sıra güvenli Kabuk (SSH) protokolü ile çalışır.

Bu cmdlet'leri gibi kullanabileceğiniz anlamına gelir `Enter-PSSession` ve `New-PSSession` ve SSH kullanarak kimlik doğrulaması.
Yapmanız gereken tek şey PowerShell alt sistemi bir OpenSSH tabanlı SSH sunucusuyla olarak kaydettirmek ve SSH temelli varolan kullanabilirsiniz (örneğin, parolalar veya özel anahtarlar) mekanizmaları geleneksel ile kimlik doğrulaması `PSSession` semantiği.

Yapılandırma ve SSH temelli remoting kullanma hakkında daha fazla bilgi için bkz: [PowerShell uzaktan iletişimi SSH üzerinden][ssh-remoting].

## <a name="default-encoding-is-utf-8-without-a-bom-except-for-new-modulemanifest"></a>Varsayılan kodlamadır UTF-8 yeni ModuleManifest dışında bir ürün reçetesi olmadan

Geçmişte, Windows PowerShell cmdlet'leri ister `Get-Content`, `Set-Content` ASCII ve UTF-16 gibi farklı kodlamaları kullanılır.
Varsayılan kodlama varyansı sorunları cmdlet'leri bir kodlama belirtmeden kullanırken oluşturulur.

Windows olmayan platformları kodlama metin dosyaları için varsayılan olarak UTF-8 bir bayt sırası işareti (BOM) olmadan geleneksel olarak kullanın.
Daha fazla Windows uygulamaları ve araçları UTF-16 çıktığınızda ve ürün reçetesi daha az UTF-8 kodlaması doğru taşıma.
PowerShell çekirdek ile daha geniş ekosistemlerini uyacak şekilde kodlama varsayılan değiştirir.

Tüm yerleşik cmdlet'leri kullanan yani `-Encoding` parametresi kullanım `UTF8NoBOM` varsayılan değeri.
Aşağıdaki cmdlet, bu değişiklikten etkilenmez:

- İçerik Ekle
- Export-Clixml
- Export-Csv
- Export-PSSession
- Format-Hex
- Get-içerik
- Import-Csv
- Out-File
- Dize seçin
- Posta iletisi gönder
- Set-içerik

Bu cmdlet'leri ayrıca güncelleştirilmiş böylece `-Encoding` parametresi evrensel olarak kabul `System.Text.Encoding`.

Varsayılan değer olan `$OutputEncoding` UTF-8'de değişti.

En iyi uygulama, açıkça komut dosyalarını kullanarak Kodlamalar ayarlamalısınız `-Encoding` platformlarında belirleyici davranış üretmek için parametre.

`New-ModuleManifest` cmdlet yok **kodlama** parametresi. Modül bildirimi (.psd1) dosyasının kodlamasını ile oluşturulan `New-ModuleManifest` cmdlet ortama bağlıdır: PowerShell çekirdek ise Linux üzerinde çalışan sonra kodlama UTF-8 (ürün reçetesi); Aksi takdirde kodlama UTF-16 (BOM) sahip. (#3940)

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>Ardışık Düzen işareti, backgrounding desteği (`&`) (#3360)

Koyma `&` bir ardışık düzen sonunda bir PowerShell iş olarak çalıştırmak ardışık düzen neden olur.
Bir işlem hattı backgrounded, bir iş nesnesi döndürülür.
Ardışık Düzen iş olarak, tüm standart çalışmaya başladıktan sonra `*-Job` cmdlet'leri, işi yönetmek için kullanılabilir.
Ardışık düzeninde kullanılan (işleme özel değişkenler yoksayar) değişkenlerini otomatik olarak kopyalanır işi şekilde `Copy-Item $foo $bar &` yalnızca çalışır.
İş yerine kullanıcının giriş dizini geçerli dizinde da çalıştırılır.
PowerShell işleri hakkında daha fazla bilgi için bkz: [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs).

## <a name="semantic-versioning"></a>Anlamsal sürüm oluşturma

- Yapılan `SemanticVersion` uyumlu `SemVer 2.0`. (#5037) (Thanks @iSazonov!)
- Değiştirilen varsayılan `ModuleVersion` içinde `New-ModuleManifest` için `0.0.1` SemVer ile hizalamak için. (#4842) (Thanks @LDSpits)
- Eklenen `semver` için türü Hızlandırıcı olarak `System.Management.Automation.SemanticVersion`. (#4142) (Teşekkürler @oising!)
- Karşılaştırma arasında etkin bir `SemanticVersion` örneği ve `Version` yalnızca ile oluşturulan örnek `Major` ve `Minor` sürüm değerleri.

## <a name="language-updates"></a>Dil güncelleştirmeleri

- Kullanıcıların Unicode karakterler bağımsız değişkenleri, dize veya değişken adları kullanabilmesi için ayrıştırma Unicode kaçış uygulayın. (#3958) (Teşekkürler @rkeithhill!)
- Eklenen yeni kaçış karakteri ESC için: `` `e``
- Numaralandırmalar (#4318) dize dönüştürmek için destek eklenmiştir (teşekkürler @KirkMunro)
- Bir genel koleksiyon tek öğe diziye atama sabit. (#3170)
- Eklenen karakter aralığı aşırı yüklemesine `..` işleci, bu nedenle `'a'..'z'` 'z' 'a ' karakteri döndürür. (#5026) (Thanks @IISResetMe!)
- Salt okunur değişkenler üzerine değildir sabit değişkeni ataması
- Otomatik değişkenlerin Yereller 'DottedScopes' komut dosyası cmdlet'leri dotting push (#4709)
- Bölme işleci 'Singleline, çok satırlı' seçeneğinin kullanımını etkinleştirin (#4721) (teşekkürler @iSazonov)

## <a name="engine-updates"></a>Altyapı güncelleştirmeleri

- `$PSVersionTable` dört yeni özelliklere sahiptir:
  - `PSEdition`: Bu ayar `Core` PowerShell çekirdeği üzerinde ve `Desktop` , Windows PowerShell
  - `GitCommitId`: Bu Git yürütme Git şube veya etiketinin PowerShell burada oluşturulmuş kimliğidir.
    Yayın derlemeleri üzerinde bu büyük olasılıkla aynı olacaktır `PSVersion`.
  - `OS`: Bu tarafından döndürülen bir işletim sistemi sürüm dizesi değil `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription`
  - `Platform`: Bu tarafından döndürülen `[System.Environment]::OSVersion.Platform` ayarlanır `Win32NT` , Windows'da `Unix` macOS üzerinde ve `Unix` Linux üzerinde.
- Kaldırılan `BuildVersion` özelliğinden `$PSVersionTable`.
  Bu özellik, kesin Windows derleme sürüme bağlı.
  Bunun yerine, kullanmanızı öneririz `GitCommitId` PowerShell çekirdek tam yapı sürümü alınamadı. (#3877) (Teşekkürler @iSazonov!)
- Kaldırma `ClrVersion` özelliğinden `$PSVersionTable`.
  Bu özellik için .NET Core ilgisiz ve .NET Core PowerShell uygulanamaz belirli eski amaçlar için yalnızca korundu.
- PowerShell belirli bir işletim sisteminde çalışır durumda olup olmadığını belirlemek için üç yeni Otomatik değişkenleri eklenmiştir: `$IsWindows`, `$IsMacOs`, ve `$IsLinux`.
- Ekleme `GitCommitId` PowerShell çekirdek başlık için.
  Çalıştırmak zorunda değilsiniz artık `$PSVersionTable` sürümü almak için PowerShell başlar başlamaz! (#3916) (Teşekkürler @iSazonov!)
- Adlı bir JSON yapılandırma dosyası ekleme `powershell.config.json` içinde `$PSHome` başlangıç saatinden önce gereken bazı ayarları depolamak için (örneğin `ExecutionPolicy`).
- Ardışık Düzen Windows EXE'ın çalıştırırken engelleme
- COM koleksiyonları etkin numaralandırması. (#4553)

## <a name="cmdlet-updates"></a>Cmdlet güncelleştirmeleri

### <a name="new-cmdlets"></a>Yeni cmdlet'leri

- Ekleme `Get-Uptime` için `Microsoft.PowerShell.Utility`.
- Ekleme `Remove-Alias` komutu. (#5143) (Thanks @PowershellNinja!)
- Ekleme `Remove-Service` yönetim modülü için. (#4858) (Thanks @joandrsn!)

### <a name="web-cmdlets"></a>Web cmdlet'leri

- Web cmdlet'leri için sertifika kimlik doğrulama desteği ekleyin. (#4646) (Thanks @markekraus)
- İçerik üstbilgileri desteği web cmdlet'leri ekleyin. (#4494 & #4640) (Teşekkürler @markekraus)
- Birden çok bağlantı üstbilgisi desteği Web cmdlet'leri ekleyin. (#5265) (Thanks @markekraus!)
- Web cmdlet'leri bağlantı üstbilgi sayfalandırma desteği (#3828)
  - İçin `Invoke-WebRequest`, yanıt oluşturuyoruz RelationLink özelliği URL'leri temsil eden bir sözlük olarak bir bağlantı üstbilgisi bulunuyorsa ve `rel` öznitelikleri ve URL'leri kullanmak Geliştirici kolaylaştırmak için mutlak emin olun.
  - İçin `Invoke-RestMethod`, yanıt biz kullanıma bağlantı üstbilgi içerdiğinde bir `-FollowRelLink` otomatik olarak izlemek için anahtar `next` `rel` artık mevcut kadar bağlantıları veya bir kez biz isabet isteğe bağlı `-MaximumFollowRelLink` parametre değeri.
- Ekleme `-CustomMethod` için standart olmayan yöntemi fiillere izin vermek için web cmdlet'leri parametresi. (#3142) (Teşekkürler @Lee303!)
- Ekleme `SslProtocol` desteklemek için Web cmdlet'leri. (#5329) (Thanks @markekraus!)
- Çok bölümlü eklemek web cmdlet'leri için destek. (#4782) (Thanks @markekraus)
- Ekleme `-NoProxy` web cmdlet'leri böylece sistem genelinde proxy ayarı yoksayar. (#3447) (Teşekkürler @TheFlyingCorpse!)
- Kullanıcı Aracısı, Web cmdlet'leri şimdi raporları işletim sistemi Platformu (#4937) (teşekkürler @LDSpits)
- Ekleme `-SkipHeaderValidation` üstbilgi değeri doğrulamadan ekleme üstbilgileri desteklemek üzere web cmdlet'leri geçin. (#4085)
- Sunucunun HTTPS sertifikasının gerekirse değil doğrulanacak web cmdlet'leri sağlar.
- Kimlik doğrulama parametreleri web cmdlet'leri ekleyin. (#5052) (Thanks @markekraus)
  - Ekleme `-Authentication` üç seçenek sunar: Basic, OAuth ve taşıyıcı.
  - Ekleme `-Token` OAuth ve taşıyıcı seçeneklerini taşıyıcı belirtecini almak için.
  - Ekleme `-AllowUnencryptedAuthentication` HTTPS dışında herhangi bir aktarım düzeni için sağlanan kimlik doğrulamasını atlamak için.
- Ekleme `-ResponseHeadersVariable` için `Invoke-RestMethod` yanıt üstbilgilerini yakalama etkinleştirmek için. (#4888) (Thanks @markekraus)
- Yanıt durum kodu başarılı olmadığında HTTP yanıtı durum dahil etmek için web cmdlet'leri düzeltin. (#3201)
- Değiştirme web cmdlet'leri `UserAgent` gelen `WindowsPowerShell` için `PowerShell`. (#4914) (Thanks @markekraus)
- Açık eklemek `ContentType` algılama `Invoke-RestMethod` (#4692)
- Web cmdlet'leri düzeltme `-SkipHeaderValidation` standart User-Agent üstbilgileri ile çalışmak için. (#4479 & #4512) (Thanks @markekraus)

### <a name="json-cmdlets"></a>JSON cmdlet'leri

- Ekleme `-AsHashtable` için `ConvertFrom-Json` döndürmek için bir `Hashtable` yerine. (#5043) (Thanks @bergmeister!)
- İle prettier biçimlendirici kullanmak `ConvertTo-Json` çıktı. (#2787) (Teşekkürler @kittholland!)
- Ekleme `Jobject` serileştirme desteklemek için `ConvertTo-Json`. (#5141)
- Düzeltme `ConvertFrom-Json` ardışık düzendeki birlikte tam bir JSON dizesi oluşturmak bir dizeler dizisi seri durumdan çıkarılamadı.
  Satır başı ayrıştırma JSON burada ihlal edeceğinden bazı durumlarda giderir. (#3823)
- Kaldırma `AliasProperty "Count"` için tanımlanan `System.Array`.
  Bu yabancı kaldırır `Count` bazı özellik `ConvertFrom-Json` çıktı. (#3231) (Teşekkürler @PetSerAl!)

### <a name="csv-cmdlets"></a>CSV cmdlet'leri

- Ekleme `PSTypeName` desteği `Import-Csv` ve `ConvertFrom-Csv`. (#5389) (Thanks @markekraus!)
- Olun `Import-Csv` Destek `CR`, `LF`, ve `CRLF` sınırlayıcıları satır. (#5363) (Thanks @iSazonov!)
- Olun `-NoTypeInformation` varsayılan `Export-Csv` ve `ConvertTo-Csv`. (#5164) (Thanks @markekraus)

### <a name="service-cmdlets"></a>Hizmet cmdlet'leri

- Özellikler ekleme `UserName`, `Description`, `DelayedAutoStart`, `BinaryPathName`, ve `StartupType` için `ServiceController` tarafından döndürülen nesne `Get-Service`. (#4907) (Thanks @joandrsn)
- Kimlik bilgilerini ayarlamak için işlevsellik ekleyen `Set-Service` komutu. (#4844) (Thanks @joandrsn)

### <a name="other-cmdlets"></a>Diğer cmdlet'ler

- Bir parametre eklemek `Get-ChildItem` adlı `-FollowSymlink` bağlantı döngüler için denetimleri ile isteğe bağlı simgesel bağlantı erişir. (#4020)
- Güncelleştirme `Add-Type` desteklemek için `CSharpVersion7`. (#3933) (Teşekkürler @iSazonov)
- Kaldırma `Microsoft.PowerShell.LocalAccounts` daha iyi bir çözüm bulunana kadar desteklenmeyen API kullanımı nedeniyle modül. (#4302)
- Kaldırma `*-Counter` cmdlet'leri `Microsoft.PowerShell.Diagnostics` nedeniyle daha iyi bir çözüm bulunana kadar desteklenmeyen API'leri kullanın. (#4303)
- İçin destek eklemek `Invoke-Item -Path <folder>`. (#4262)
- Ekleme `-Extension` ve `-LeafBase` geçirir `Split-Path` böylece dosya adı uzantısı ve dosya adı geri kalanı arasında yollar bölebilirsiniz. (#2721) (Teşekkürler @powercode!)
- Parametre ekleme `-Top` ve `-Bottom` için `Sort-Object` üst/alt N sıralama için
- Bir işlemi üst işlemi ekleyerek kullanıma `CodeProperty "Parent"` için `System.Diagnostics.Process`. (#2850) (Teşekkürler @powercode!)
- MB yerine KB bellek sütunlar için kullanın. `Get-Process`
- Ekleme `-NoNewLine` için geçiş `Out-String`. (#5056) (Thanks @raghav710)
- `Move-Item` cmdlet geliştirir `-Include`, `-Exclude`, ve `-Filter` parametreleri. (#3878)
- İzin `*` kayıt defteri yolu için kullanılmak üzere `Remove-Item`. (#4866)
- Ekleme `-Title` için `Get-Credential` ve platformlar arası komut istemi deneyimi birleştirin.
- Ekleme `-TimeOut` parametresi `Test-Connection`. (#2492)
- `Get-AuthenticodeSignature` cmdlet'leri şimdi dosya imza zaman damgası elde edebilirsiniz. (#4061)
- Desteklenmeyen Kaldır `-ShowWindow` geçiş `Get-Help`. (#4903)
- Düzeltme `Get-Content -Delimiter` sınırlayıcı dizi öğeleri içermeyecek şekilde döndürdü (#3706) (teşekkürler @mklement0)
- Ekleme `Meta`, `Charset`, ve `Transitional` parametreleri `ConvertTo-HTML` (#4184) (teşekkürler @ergo3114)
- Ekleme `WindowsUBR` ve `WindowsVersion` özelliklerine `Get-ComputerInfo` sonucu
- Ekleme `-Group` parametresi `Get-Verb`
- Ekleme `ShouldProcess` için destek `New-FileCatalog` ve `Test-FileCatalog` (düzeltmeler `-WhatIf` ve `-Confirm`). (#3074) (Teşekkürler @iSazonov!)
- Ekleme `-WhatIf` geçiş `Start-Process` cmdlet (#4735) (teşekkürler @sarithsutha)
- Ekleme `ValidateNotNullOrEmpty` çok fazla mevcut parametre.

## <a name="tab-completion"></a>Sekme tamamlama

- Tür çıkarımı sekme tamamlama çalışma zamanı değişken değerlerine dayalı olarak geliştirilmiştir. (#2744) (Teşekkürler @powercode!) Bu sekme tamamlama gibi durumlarda sağlar:

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- Hashtable sekme tamamlanmasını eklemek `-Property` , `Select-Object`. (#3625) (Teşekkürler @powercode)
- Bağımsız değişkeni için otomatik tamamlama etkinleştirmek `-ExcludeProperty` ve `-ExpandProperty` , `Select-Object`. (#3443) (Teşekkürler @iSazonov!)
- Yapmak için sekme tamamlama hata düzeltme `native.exe --<tab>` yerel kendisinden içine çağrı yapar. (#3633) (Teşekkürler @powercode!)

## <a name="breaking-changes"></a>Yeni değişiklikler

Biz birkaç önemli değişiklikler PowerShell çekirdek 6. 0'ı ekledik.
Daha fazla bilgi için bunları hakkında ayrıntılı bkz [PowerShell çekirdek 6. 0'de yeni değişiklikler][breaking-changes].

## <a name="debugging"></a>Hata Ayıklama

- Uzak step-in için hata ayıklama desteği `Invoke-Command -ComputerName`. (#3015)
- Bağlayıcı hata ayıklama PowerShell çekirdek günlüğü etkinleştirme

## <a name="filesystem-updates"></a>Dosya sistemi güncelleştirmeleri

- Dosya sistemi Sağlayıcısı'ndan bir UNC yolu kullanımını etkinleştirin. ($4998)
- `Split-Path` Şimdi UNC kökleri ile çalışır
- `cd` bağımsız değişkenler olmadan olarak şimdi davranır. `cd ~`
- 260 karakterden uzun olan yollar kullanımına izin vermek için sabit PowerShell çekirdek. (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>Hata düzeltmeleri ve performans iyileştirmeleri

Yaptık *birçok* başlangıç zamanı, çeşitli yerleşik cmdlet'leri ve yerel ikili dosyaları ile etkileşimi dahil olmak üzere PowerShell boyunca performans geliştirmeleri.

PowerShell çekirdek içinde hataların sayısını da düzelttik.
Düzeltme ve değişikliklerin tam listesi için kullanıma bizim [değişim günlüğü][] github'da.

## <a name="telemetry"></a>Telemetri

- Rapor iki konsol konağa PowerShell eklenen çekirdek 6.0 telemetri değerleri (#3620):
  - işletim sistemi Platformu (`$PSVersionTable.OSDescription`)
  - PowerShell'ün tam sürümünü (`$PSVersionTable.GitCommitId`)

Bu telemetrinin çevirin etmek istiyorsanız, yalnızca silmeniz `$PSHome\DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` veya oluşturma `POWERSHELL_TELEMETRY_OPTOUT` ortam değişkeni aşağıdaki değerlerden biriyle: `true`, `1` veya `yes`.
Bu dosya silme veya değişkeni oluşturma PowerShell ilk çalıştırmada bile önce tüm telemetri atlar.
Biz de bu telemetri verilerini ve biz glean telemetri gelen öngörü gösterme üzerinde planlama [topluluk Pano][community-dashboard].
Biz bu verileri bu kullanma hakkında daha fazla bilgi için [blog gönderisi][telemetry-blog].

[github]: https://github.com/PowerShell/PowerShell
[.NET Core 2.0]: https://docs.microsoft.com/dotnet/core/
[.NET standart]: https://docs.microsoft.com/en-us/dotnet/standard/net-standard
[os_log]: https://developer.apple.com/documentation/os/logging
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[breaking-changes]: https://github.com/PowerShell/PowerShell/tree/master/docs/BREAKINGCHANGES.md
[değişim günlüğü]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[telemetry-blog]: https://blogs.msdn.microsoft.com/powershell/2017/01/31/powershell-open-source-community-dashboard/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[.NET Blog]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
[SSS]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[CDXML]: https://msdn.microsoft.com/library/jj542525(v=vs.85).aspx
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview