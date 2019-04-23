---
title: PowerShell Core 6.2 yenilikler nelerdir?
description: Yeni özellikler ve PowerShell Core 6.2 yayımlanan değişiklikleri
ms.date: 03/28/2019
ms.openlocfilehash: 6a0da8a410e602ae3963e0bc7bace745317d7d4b
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984502"
---
# <a name="whats-new-in-powershell-core-62"></a>PowerShell Core 6.2 yenilikler nelerdir?

PowerShell Core 6.2 yayın performans geliştirmeleri, hata düzeltmeleri ve kalitesini artırmak daha küçük cmdlet'i ve dil geliştirmelerini üzerinde odaklanır. Geliştirmelerinin tam listesi görmek için sunduğumuz ayrıntılı denetle [changelogs](https://github.com/PowerShell/PowerShell/releases) GitHub üzerinde.

## <a name="experimental-features"></a>Deneysel Özellikler

Daha önce için desteği etkinleştirdik [Deneysel Özellikler][]. 6.2 sürümde denemek için dört Deneysel özellikler sahibiz. Biz geliştirmeler yapmak için lütfen geri bildirim sağlamak ve bu özellik için temel durum yükseltme değer olup olmadığına karar vermek için.

Kullanım `Get-ExperimentalFeature` kullanılabilir Deneysel özellikler listesini almak için. Etkinleştirin veya bu özellikleri devre dışı `Enable-ExperimentalFeature` ve `Disable-ExperimentalFeature`.

### <a name="command-not-found-suggestions"></a>Öneri bulunamadı komutu

Bu özellik, komutları veya cmdlet'leri için öneriler, yanlış yazmış olabilirsiniz bulmak için benzer öğe eşleştirmesi kullanır.

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a>Örnek

Bu örnekte, birkaç önerileri için büyük olasılıkla'den az büyük olasılıkla eşleşen, yanlış yazılmış cmdlet adı belirsiz.

```powershell
Get-Commnd
```

```Output
Get-Commnd : The term 'Get-Commnd' is not recognized as the name of a cmdlet, function, script file, or operable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-Commnd
+ ~~~~~~~~~~
+ CategoryInfo          : ObjectNotFound: (Get-Commnd:String) [], CommandNotFoundException
+ FullyQualifiedErrorId : CommandNotFoundException


Suggestion [4,General]: The most similar commands are: Get-Command, Get-Content, Get-Job, Get-Module, Get-Event, Get-Host, Get-Member, Get-Item, Set-Content.
```

### <a name="implicit-remoting-batching"></a>Örtük uzak iletişim toplu işleme

Kullanırken [örtük uzak iletişim](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) bağımsız olarak her komut işlem hattındaki bir işlem hattında, PowerShell değerlendirir. Nesneleri tekrar tekrar serileştirilmiş ve `de-serialized` istemci ve işlem hattı yürütme üzerinden uzak sistem arasında.

Bu özellik ile PowerShell, komut çalıştırılmasının güvenli olduğundan ve hedef sistemde mevcut belirlemek için işlem hattı analiz eder. TRUE olduğunda, PowerShell işlem hattının tamamına uzaktan yürütür ve yalnızca serileştirir ve `de-serializes` sonuçları istemciye.

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

Bir gerçek testi `Get-Process | Sort-Object` localhost üzerinde azaltır 10-15 saniyeden 20-30 **milisaniye**. Bu özellik yalnızca istemcide etkinleştirilmesi gerekir. Değişiklik sunucusunda gerekli değildir.

### <a name="temp-drive"></a>Geçici sürücü

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

Farklı işletim sistemlerinde PowerShell Core kullanıyorsanız, geçici dizin bulmak için ortam değişkenini Windows, macOS ve Linux'ta farklı olduğunu keşfedeceksiniz! Bu özellik, size bir [PSDrive][] adlı `Temp:` , otomatik olarak eşleştirilir kullanmakta olduğunuz işletim sistemi için geçici bir klasör.

#### <a name="example"></a>Örnek

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> `Get-Content` Temp:/hello.txt
Hello World!
```

Unutmayın, yerel dosya komutları (gibi `ls` Linux üzerinde) PSDrives farkında değildir ve bu görmezsiniz `Temp:` sürücü.

### <a name="abbreviation-expansion"></a>Kısaltması genişletme

PowerShell cmdlet'leri, açıklayıcı adlar olması beklenir. Bu, yazmak daha zor olan uzun adları sonuçlanır. Bu özellik yalnızca büyük harf karakterler cmdlet'inin yazın ve bir eşleşme bulmak için sekme tamamlamayı kullanma sağlar.

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a>Örnek

```powershell
PS> i-arsavsf
```

Sekme isabet ve Azure PowerShell'in [Az](https://www.powershellgallery.com/packages/Az) Modülü yüklü için otomatik tamamlama yapar:

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> Bu özellik, etkileşimli olarak kullanılması amaçlanmıştır. Cmdlet'lerin kısaltılmış forms yürütülemez.
> Bu özellik, diğer adları yerine kullanılamaz.

## <a name="breaking-changes"></a>Hataya Neden Olan Değişiklikler

- Düzeltme `-NoEnumerate` davranışı `Write-Output` Windows PowerShell ile tutarlı olacak şekilde. (#9069)
- Olun `Join-String -InputObject 1,2,3` eşit neden `1,2,3 | Join-String` neden (#8611) (teşekkürler @sethvs!)
- Ekleme `-Stable` için `Sort-Object` ve ilgili testler (#7862) (teşekkürler @KirkMunro!)
- Geliştirmek `Start-Sleep` Kesirli saniye kabul etmek için cmdlet'i (#8537) (teşekkürler @Prototyyppi!)
- Değiştirme olmasını Ordinalıgnorecase kullanılacak hashtable `case-insensitive` bütün kültürler (#8566)
- Düzeltme **LiteralPath** içinde `Import-Csv` bağlamak için `Get-ChildItem` çıktı (#8277) (teşekkürler @iSazonov!)
- Adı olmayan bir sütunu çift tırnak işareti ayırıcı kullanılırsa artık atlar `Import-Csv` (#7899) (teşekkürler @Topping!)
- `Get-ExperimentalFeature` artık `-ListAvailable` (#8318) geçiş
- Parametre şimdi kümeleri hata ayıklama `$DebugPreference` için **devam** yerine **Inquire** (#8195) (teşekkürler @KirkMunro!)
- Uy `-OutputFormat` pwsh ile kullanılan etkileşimli olmayan, yeniden yönlendirilen, kodlanmış komutta belirtilmişse (#8115)
- GAC yüklemeye çalışmadan önce modülü taban yoldan bütünleştirilmiş kod yükle (#8073)
- Tilde Linux Önizleme paketten Kaldır (#8244)
- İşlenmesini taşıma `-WorkingDirectory` profillerinin işlemeden önce (#8079)
- Eklemeyin `PATHEXT` UNIX ortam değişkenine (#7697) (teşekkürler @iSazonov!)

## <a name="known-issues"></a>Bilinen Sorunlar

- Uzak Windows IOT ARM platformlarında modülleri yüklenirken bir sorun var. See (#8053)

## <a name="general-updates-and-fixes"></a>Genel güncelleştirme ve düzeltme

- Büyük küçük harfe duyarlı dosya sistemi üzerindeki dosya ve klasörleri için büyük küçük harf duyarsız sekme tamamlamayı etkinleştirme (#8128)
- Make PSVersionInfo.PSVersion and PSVersionInfo.PSEdition public (#8054) (Thanks @KirkMunro!)
- Tür çıkarımı için ekleme `$_`  /  `$PSItem` içinde `catch{ }` engeller (#8020) (teşekkürler @vexx32!)
- Statik yöntem çağırma tür çıkarımı düzeltme (#8018) (teşekkürler @SeeminglyScience!)
- İçin çıkarsanan tür oluşturma `Select-Object`, `Group-Object`, **PSObject** ve **Hashtable** (#7231) (teşekkürler @powercode!)
- Destek yöntemi çağrılırken `ByRef-like` tür parametrelerindeki (#7721)
- Windows PowerShell modülü yol olduğu zaten ortamın PSModulePath içinde durumu işlemek (#7727)
- Etkinleştirme `SecureString` cmdlet'leri için Windows olmayan düz metin depolayarak (#9199)
- Windows olmayan hata iletisini clixml securestring ile içeri aktarılırken geliştirmek (#7997)
- Parametre ReplyTo eklemek için `Send-MailMessage` (#8727) (teşekkürler @replicaJunction!)
- Geçersiz ileti Ekle `Send-MailMessage` (#9178)
- Düzeltme `Restart-Computer` üzerinde çalışmak için `localhost` WinRM olmadığında (#9160) sunar.
- Olun `Start-Job` throw (#9128) barındırılan PowerShell yüklenirken hata sonlandırılıyor
- Ekleme C# stili türü hızlandırıcıları ve soneki ushort, uint, ulong ve kısa değişmez değerleri (#7813) (teşekkürler @vexx32!)
- Sayısal sabit değerleri - eklenen yeni sonekleri bkz [about_Numeric_Literals][] (#7901) (teşekkürler @vexx32!)
- '(#8209) true olarak ' SupportsShouldProcess ayarlanmadığında etki düzeyi doğru şekilde rapor (teşekkürler @vexx32!)
- Web cmdlet'leri isteği Charset sorunları düzeltme (#8742) (teşekkürler @markekraus!)
- Expect düzeltme `100-continue` Web cmdlet'leri ile ilgili sorun (#8679) (teşekkürler @markekraus!)
- Web cmdlet'leri ile dosya engelleme sorunu düzeltme (#7676) (teşekkürler @Claustn!)
- Kod sayfası ayrıştırma sorunu düzeltme `Invoke-RestMethod` (#8694) (teşekkürler @markekraus!)
- Yeniden düzenleme `ConvertTo-Json` JsonObject.ConvertToJson Genel API olarak kullanıma sunmak için (#8682)
- Yapılandırılabilir maksimum derinlik ekleme `ConvertFrom-Json` ile - derinliği (#8199) (teşekkürler @louistio!)
- EscapeHandling parametreyi ekleyin `ConvertTo-Json` cmdlet'i (#7775) (teşekkürler @iSazonov!)
- Ekleme `-CustomPipeName` pwsh için ve `Enter-PSHostProcess` (#8889)
- İle Windows üzerinde göreli sembolik bağlantıları oluşturmayı etkinleştirmek `New-Item` (#8783)
- Yükseltme olmadan çözümlemeyin oluşturmak için geliştirici modunda Windows kullanıcıların (#8534)
- Etkinleştirme `Write-Information` kabul edecek şekilde `$null` (#8774)
- Düzeltme `Get-Help` MAML ile gelişmiş işlevleri için Yardım içeriği (#8353)
- Düzeltme `Get-Help` PSTypeName sorun - yalnızca bir parametresi (#8754) olarak bildirildiğinde parametre (teşekkürler @pougetat!)
- Belirteç hesaplama düzeltme `Get-Help` açıklama Yardım için ScriptBlock üzerinde yürütülür. (#8238) (Thanks @hubuk!)
- Değişiklik `Get-Help` cmdlet-Parameter parametresi dize kabul eder (#8454) diziler (teşekkürler @sethvs!)
- Diskteki yolu içeriyorsa, çağrı CİHAZI alanları (#8571) gidermek (teşekkürler @pougetat!)
- Komut isteminde kullanımı eklemek `less` kullanıcı (#7998) çıkma istemek için ' Yardım' işlevindeki
- Destek enum ve karakter türleri ekleme `Format-Hex` cmdlet'i (#8191) (teşekkürler @iSazonov!)
- ShouldProcess öğesinden kaldırmak `Format-Hex` (#8178)
- Yeni uzaklık ve sayı parametre eklemek `Format-Hex` ve cmdlet'ini yeniden düzenleme (#7877) (teşekkürler @iSazonov!)
- 'Bir diğer ad anahtarı olarak 'etiketi' name' izin `ConvertTo-Html`, bir tamsayı olacak şekilde 'width' giriş izin ver (#8426) (teşekkürler @mklement0!)
- Yapma scriptblock göre hesaplanan özellikleri yeniden iş `ConvertTo-Html` (#8427) (teşekkürler @mklement0!)
- Cmdlet'i eklendi `Join-String` metin (#7660) giriş işlem hattını oluşturmak için (teşekkürler @powercode!)
- Düzeltme `Join-String` FormatString parametresi mantıksal cmdlet'i (#8449) (teşekkürler @sethvs!)
- Değişiklik `Clear-Host` kullanımına geri `$RAWUI` ve Temizle remoting çalışmak için (#8609)
- Değişiklik `Clear-Host` yalnızca izin `[console]::clear` ve net bir diğer ad UNIX kaldırma (#8603)
- İçinde LiteralPath düzeltme `Import-Csv` bağlamak için `Get-ChildItem` çıktı (#8277) (teşekkürler @iSazonov!)
- Yardım işlevi için AliasHelpInfo çağrı kullanmak olmamalıdır (#8552)
- Ekleme `-UseMinimalHeader` için `Start-Transcript` döküm üstbilgi en aza indirmek için (#8402) (teşekkürler @lukexjeremy!)
- Ekleme `Enable-ExperimentalFeature` ve `Disable-ExperimentalFeature` cmdlet'leri (#8318)
- Tüm cmdlet'leri kullanıma **PSDiagnostics** logman.exe kullanılabilir (#8366) ise
- Kaldırma **kalan** parametresinden `New-PSDrive` üzerinde `non-Windows` Platformu (#8291) (teşekkürler @lukexjeremy!)
- İçin destek ekleme `cd +` (#7206) (teşekkürler @bergmeister!)
- Etkinleştirme `Set-Location -LiteralPath` adlı - klasörlerle ve + (#8089)
- `Test-Path` döndürür `$false` boş verildiğinde veya `$null` yolu (#8080) değeri (teşekkürler @vexx32!)
- Yol herhangi bir sağlayıcı eşleşmiyor olsa bile döndürülecek dinamik parametre izin ver (#7957)
- Destek `Get-PSHostProcessInfo` ve `Enter-PSHostProcess` Unix platformlarında (#8232)
- Ayırmalar halinde azaltma `Get-Content` cmdlet'i (#8103) (teşekkürler @iSazonov!)
- Etkinleştirme `Add-Content` okuma erişimi diğer araçlarla yazılırken içerik paylaşmak için (#8091)
- `Get/Add-Content` bir kapsayıcı hedeflenirken Gelişmiş bir hata oluşturur (#7823) (teşekkürler @kvprasoon!)
- Ekleme `-Name`, `-NoUserOverrides` ve `-ListAvailable` parametreleri `Get-Culture` cmdlet'i (#7702) (teşekkürler @iSazonov!)
- Tamamlama için birleştirilmiş öznitelik Ekle **kodlama** parametresi. (#7732) (Thanks @ThreeFive-O!)
- Sayısal kimlikleri ve kayıtlı kod sayfalarında adını izin **kodlama** parametreleri (#7636) (teşekkürler @iSazonov!)
- Düzeltme `Rename-Item -Path` ile joker karakter (#7398) (teşekkürler @kwkam!)
- Kullanırken `Start-Transcript` ve dosya var, dosya yerine boş (#8131) silme değerinden (teşekkürler @paalbra!)
- Olun `Add-Type` açık kaynak dosyalarını içeren **FileAccess.Read** ve **FileShare.Read** açıkça (#7915) (teşekkürler @IISResetMe!)
- Düzeltme `Enter-PSSession -ContainerId` en son Windows için (#7883)
- Olun **NestedModules** özelliği tarafından doldurulan `Test-ModuleManifest` (#7859)
- Ekleme `%F` için büyük/küçük harf `Get-Date` - UFormat (#7630) (teşekkürler @britishben!)
- Düzeltme `Set-Service -Status Stopped` bağımlılıkları olan hizmeti durduramadı (#5525) (teşekkürler @zhenggu!)

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Deneysel Özellikler]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
