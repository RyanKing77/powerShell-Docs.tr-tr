---
title: VSCode ve PowerShell’de dosya kodlamayı anlama
description: VSCode ve PowerShell dosya kodlamasını yapılandırma
ms.date: 02/28/2019
ms.openlocfilehash: 6a00e45b3700f72f78e2fbcdf6e317f3a17b53c0
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984128"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a>VSCode ve PowerShell’de dosya kodlamayı anlama

VS Code kullanarak oluşturma ve PowerShell betiklerini Düzenle, dosyalarınızın doğru karakter kodlama biçimi kullanılarak kaydedilir önemlidir.

## <a name="what-is-file-encoding-and-why-is-it-important"></a>Dosya kodlama ve neden önemli olduğu nedir?

VSCode karakterlerin arabellek içine bir insan girme dizeleri ve dosya sistemi bayt okuma/yazma blokları arasındaki arabirim yönetir. VSCode bir dosyayı kaydederken, bir metin kodlama Bunu yapmak için kullanır.

PowerShell komut dosyası çalıştığında benzer şekilde, bunu bir dosyadaki bayt PowerShell programa dosyayı yeniden oluşturmak için karakter dönüştürmeniz gerekir. VSCode dosyaya yazar ve PowerShell dosyasını okur olduğundan, bunlar aynı kodlama sistem kullanmanız gerekir. Bu işlem, bir PowerShell Betiği ayrıştırma gider: *bayt* -> *karakter* -> *belirteçleri*  ->   *soyut sözdizimi ağacını* -> *yürütme*.

VSCode hem PowerShell mantıklı varsayılan kodlama yapılandırma ile yüklenir. Bununla birlikte, PowerShell uygulamaları tarafından kullanılan varsayılan kodlamayı PowerShell Core (v6.x) sürümü değişti. VSCode içinde PowerShell veya PowerShell uzantısını kullanarak herhangi bir sorun olduğundan emin VSCode ve PowerShell ayarlarınızı yapılandırmak gereken doğru.

## <a name="common-causes-of-encoding-issues"></a>Sorunları kodlama yaygın nedenleri

VSCode veya komut dosyanızı kodlama beklenen PowerShell kodlamasıyla eşleşmiyor kodlama sorunlar ortaya çıkar. Dosya kodlama otomatik olarak belirlemek PowerShell bir yolu yoktur.

Büyük olasılıkla içinde olmayan karakter kullanırken sorunları kodlamalı [7 bit ASCII karakter kümesi](https://ascii.cl/). Örneğin:

- Latin karakterler vurgulu (`É`, `ü`)
- Cyrilice gibi latin olmayan karakterler (`Д`, `Ц`)
- Han Çince (`脚`, `本`)

Kodlama sorunlarına yaygın nedenleri şunlardır:

- VSCode ve PowerShell için Kodlamalar kendi varsayılanlarından değiştirilmedi. Kodlama PowerShell 5.1 ve altında varsayılan Vscode'dan 's farklıdır.
- Başka bir düzenleyicide açtığı ya da yeni bir kodlama dosyanın üzerine. Bu genellikle işe ile gerçekleşir.
- Dosyayı farklı bir kodlama kaynak denetimine hangi VSCode ya da PowerShell bekliyor denetlenir. Ortak Çalışanlar ile farklı kodlama yapılandırmaları düzenleyicileri kullandığınızda bu durum oluşabilir.

### <a name="how-to-tell-when-you-have-encoding-issues"></a>Kodlama sorunlarına sahip olduğunuzda anlatma

Genellikle kodlama hatalarını kendilerini ayrıştırma hataları komut olarak sunar. Betiğinizde garip karakter sıraları fark ederseniz, bu sorunu olabilir. Bir tire aşağıdaki örnekte (`–`) karakterleriyle görünür `â€“`:

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

Bu sorun oluşur VSCode karakter kodlar `–` UTF-8 bayt olarak `0xE2 0x80 0x93`.
Bu bayt Windows-1252 çözülür, karakter olarak yorumlanır `â€“`.

Görebileceğiniz bazı ilginç karakter sıraları içerir:

<!-- markdownlint-disable MD038 -->
- `â€“` Onun yerine `–`
- `â€”` Onun yerine `—`
- `Ã„2` Onun yerine `Ä`
- `Â` yerine ` ` (bölünemez boşluk)
- `Ã©` Onun yerine `é`
<!-- markdownlint-enable MD038 -->

Bu kullanışlı [başvuru](https://www.i18nqa.com/debug/utf8-debug.html) UTF-8/Windows-1252 kodlama bir sorunu işaret eden ortak desenler listeler.

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a>VSCode PowerShell uzantı Kodlamalar ile nasıl etkileşim girer

PowerShell uzantısı solucanlar, betiklerde etkileşime geçer:

1. VSCode içinde komut dosyaları düzenlenirken, içeriği uzantısı tarafından VSCode gönderilir. [Dil sunucusu Protokolü][] gerektiren bu içerik UTF-8'de aktarılır. Bu nedenle, uzantısı yanlış kodlama almak mümkün değildir.
2. Doğrudan tümleşik konsolunda komut yürütüldüğünde dosyasından PowerShell tarafından doğrudan okurlar. Burada PowerShell'in kodlama Vscode'dan 's farklıysa, bir şeyler yanlış gidebilirsiniz.
3. VSCode içinde açık olan bir betik VSCode içinde açık değil başka bir komut dosyası başvuruları, genişletme dosya sisteminden, betiğin içeriği yüklemek için geri döner. PowerShell uzantısı UTF-8 kodlaması için'varsayılan olarak, ancak kullandığı [bayt sırası işareti][], veya AĞACI, algılama doğru kodlama seçin.

BOM daha az biçimlerini kodlama varsayılarak sorun oluşur (gibi [UTF-8][] hiçbir BOM ile ve [Windows-1252][]).
PowerShell uzantısı varsayılan UTF-8 olarak. Uzantı VSCode'nın kodlama ayarlarını değiştiremezsiniz.
Daha fazla bilgi için [sorun #824](https://github.com/Microsoft/vscode/issues/824).

## <a name="choosing-the-right-encoding"></a>Doğru kodlamayı seçme

Farklı sistemler ve uygulamalar farklı kodlamaları kullanabilirsiniz:

- .NET Standard'da web üzerinde ve Linux dünyada, UTF-8 baskın encoding'i şimdi içindir.
- Çoğu .NET Framework uygulamaları [UTF-16][]. Geçmiş nedeniyle buna bazen "Unicode" adı verilir, artık bir dönem için bir geniş başvuruyor [standart](https://en.wikipedia.org/wiki/Unicode) hem UTF-8 ve UTF-16 içerir.
- Windows üzerinde Unicode geçerler birçok yerel uygulamalar varsayılan olarak Windows-1252 kullanmaya devam edin.

Unicode kodlamaları de (BOM) işaretlemek bayt sırası kavramı vardır. Hangi kodlama metnini kullanarak bir kod çözücü bildirmek için metin başında ağaçları oluşur. Çok baytlı kodlamaları için ayrıca ürün reçetesi gösterir [endianness](https://en.wikipedia.org/wiki/Endianness) kodlaması. Ağaçları, bir ürün reçetesi mevcut olduğunda Unicode metin olduğunu makul bir tahmin izin vererek Unicode olmayan metinde nadiren gerçekleşen bayt olacak şekilde tasarlanmıştır.

Ağaçları isteğe bağlıdır ve güvenilir bir kuralı UTF-8'in her yerde kullanılan Linux dünyada yaygın olarak kullanıcıların benimseme değildir. Çoğu Linux uygulamaları, metin girişi UTF-8 olarak kodlanmış olduğunu varsayar. Çok sayıda Linux uygulamaları tanıması ve doğru bir şekilde bir BOM işlemek bir sayı yoktur, bu uygulamalarla yönetilen metin yapılara önde gelen.

**Bu nedenle**:

- Öncelikle Windows uygulamaları ve Windows PowerShell ile çalışıyorsanız, UTF-16 ya da BOM ile UTF-8 gibi bir kodlama tercih etmelisiniz.
- Platformlar arası çalışması, BOM ile UTF-8 tercih etmelisiniz.
- Ağırlıklı olarak Linux ilişkili bağlamlarda işe, UTF-8 içermeyen ürün reçetesi tercih etmelisiniz.
- Mümkünse kaçınmalısınız temelde eski Kodlamalar şunlardır: Windows-1252 ve latin-1.
  Ancak, bazı eski Windows uygulamaları bunlara bağımlı.
- Ayrıca kod imzalama olduğunu hatalarının ayıklanabileceğini belirtmekte yarar [kodlama bağımlı](https://github.com/PowerShell/PowerShell/issues/3466), imzalı bir komut kodlama değişikliği anlamı gerektirecek teslim.

## <a name="configuring-vscode"></a>VSCode yapılandırma

VSCode'nın varsayılan kodlama: UTF-8 içermeyen ürün reçetesi.

Ayarlanacak [VSCode'nın kodlama][]VSCode Ayarları'na gidin (<kbd>Ctrl</kbd>+<kbd>,</kbd>) ayarlayıp `"files.encoding"` ayarı:

```json
"files.encoding": "utf8bom"
```

Bazı olası değerler şunlardır:

- `utf8`: [UTF-8] içermeyen ürün reçetesi
- `utf8bom`: [UTF-8] BOM ile
- `utf16le`: Küçük endian [UTF-16]
- `utf16be`: Big endian [UTF-16]
- `windows1252`: [Windows-1252]

Bunun için bir açılan GUI Görünümü'nde almalısınız veya onun için tamamlamalar json'da görüntüleyebilirsiniz.

Ayrıca, mümkün olduğunda kodlamasını otomatik algıla için aşağıdakileri ekleyebilirsiniz:

```json
"files.autoGuessEncoding": true
```

Bu ayarlar, tüm dosya türlerini etkilemesini istemiyorsanız VSCode dil başına yapılandırmaları da sağlar. Ayarları koyarak bir dile özgü ayarı oluşturarak bir `[<language-name>]` alan. Örneğin:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>PowerShell yapılandırma

PowerShell'in varsayılan kodlamayı sürümüne göre farklılık gösterir:

- PowerShell 6 +, kodlama varsayılan UTF-8 içermeyen ürün reçetesi tüm platformlarda kodlamasıdır.
- Windows PowerShell'de varsayılan kodlamayı genellikle Windows-1252'ın bir uzantısı olan [latin-1][], ISO 8859-1 olarak da bilinir.

PowerShell'de 5 + varsayılan bu kodlamanızın bulabilirsiniz:

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

Aşağıdaki [betik](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) ne kodlama PowerShell oturumunuzda bir komut dosyası içermeyen bir ürün reçetesi çıkarsar belirlemek için kullanılabilir.

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

PowerShell bir verilen daha genel profil ayarları kullanarak kodlama kullanmak için yapılandırmak mümkündür. Aşağıdaki makalelere bakın:

- [@mklement0]ın [PowerShell StackOverflow kodlama hakkında yanıt](https://stackoverflow.com/a/40098904).
- [@rkeithhill]ın [PowerShell BOM daha az UTF-8 girişinde uğraşmanızı hakkındaki blog gönderisini](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).

Belirli bir giriş kodlama kullanmak için PowerShell kullanmaya zorlamak mümkün değil. PowerShell 5.1 ve varsayılan Windows-1252 hiçbir BOM olmadığında kodlama için aşağıda. Birlikte çalışabilirlik nedeniyle, bir Unicode biçiminde bir BOM ile komut dosyaları kaydetmek en iyisidir.

> [!IMPORTANT]
> Diğer araçlardan PowerShell betikleri kodlama seçimlerinizi tarafından etkilenebilecek veya başka bir kodlama için komut dosyalarınızı yeniden kodlamak dokunma sahip.

### <a name="existing-scripts"></a>Var olan betikler

Zaten dosya sisteminde betikleri, yeni seçilen kodlama için yeniden kodlanmış gerekebilir. Alt çubuğu, VSCode içinde UTF-8 etiket görürsünüz. Eylem çubuğunu açın ve seçmek için tıklatın **kodlamayla kaydetme**. Şimdi, bu dosya için yeni bir kodlama seçebilirsiniz. Bkz: [VSCode'nın kodlama][] tam yönergeler için.

Birden çok dosyayı yeniden kodlamanız gerekirse, aşağıdaki betiği kullanabilirsiniz:

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>PowerShell Tümleşik komut dosyası ortamı (ISE)

PowerShell ISE kullanarak komut dosyalarını da düzenlerseniz, kodlama ayarlarını eşitlemek gerekir.

ISE bir BOM uymanız, ancak aynı zamanda yansıma için kullanılacak olası [kümesi kodlaması](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).
Bu yeni işletmeler arasında kalıcı olmasını mıydı unutmayın.

### <a name="source-control-software"></a>Kaynak Denetim yazılımı

Bazı, git gibi kaynak denetimi araçları Kodlamalar yoksayın; Git, yalnızca bayt izler.
Diğer Azure DevOps veya Mercurial, gibi olmayabilir. Hatta bazı git tabanlı araçlar, metin, kod çözme hakkında kullanır.

Bu durum söz konusu olduğunda emin olun:

- Metin kodlaması kaynak denetiminizi VSCode yapılandırmanızla eşleşecek şekilde yapılandırın.
- Tüm dosyaları kaynak denetimine ilgili kodlamada seçildiğinden emin olun.
- Kaynak denetimi alınan kodlama için değişiklikleri dikkatli olun. Bir anahtar bu değişiklikler, ancak burada bir şey (bayta sahiptir ancak karakter olmayan çünkü) değiştirilmiş gibi görünüyor belirten bir fark işaretidir.

### <a name="collaborators-environments"></a>Ortak Çalışanlar ortamları

Kaynak denetimini yapılandırma üzerinde herhangi bir dosya paylaşımını şirket, çalışanlar, PowerShell dosyaları yeniden kodlayarak kodlama geçersiz kılma ayarları olmadığından emin olun.

### <a name="other-programs"></a>Diğer programları

Diğer program okuyan veya yazan bir PowerShell Betiği yeniden kodlayın.

Bazı örnekler şunlardır:

- Bir betiği kopyalayıp Pano'yu kullanıyor. Bu gibi senaryolarda yaygındır:
  - Bir betiği bir VM'ye kopyalama
  - Bir e-posta veya Web sayfası dışında bir komut dosyası kopyalanıyor
  - Bir komut dosyası içine veya dışına Microsoft Word veya PowerPoint belge kopyalama
- Başka bir metin düzenleyicisi gibi:
  - Not Defteri
  - vim
  - Diğer bir PowerShell komut dosyası Düzenleyicisi
- Gibi yardımcı programlar, düzenleme metni:
  - `Get-Content`/`Set-Content`/`Out-File`
  - PowerShell yönlendirme işleçlerini ister `>` ve `>>`
  - `sed`/`awk`
- Aktarım programları gibi dosya:
  - Komut dosyaları indirirken bir web tarayıcısı
  - Bir dosya paylaşımı

Bu araçlardan bazılarını ilgilenmenize metin yerine bayt, ancak diğerleri kodlama yapılandırmaları sunar. Bir kodlama yapılandırmak için gerek duyduğunuz Böyle durumlarda, bu sorunları önlemek için kodlama düzenleyiciniz aynı yapmanız gerekir.

## <a name="other-resources-on-encoding-in-powershell"></a>PowerShell'de kodlama diğer kaynaklar

Okuma olan kodlama ve kodlama PowerShell'de yapılandırma birkaç diğer iyi gönderileri vardır:

- [@mklement0]ın [PowerShell StackOverflow kodlama özeti](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- Önceki sorunları, sorunlar kodlaması için vscode-PowerShell açıldı:
  - [#1308](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [Klasik *Joel yazılım* Unicode hakkında Düzenle](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [.NET Standard'da kodlama](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[Latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[bayt sırası işareti]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Dil sunucusu Protokolü]: https://microsoft.github.io/language-server-protocol/
[VSCode'nın kodlama]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
