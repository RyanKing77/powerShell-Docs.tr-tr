---
ms.date: 05/17/2018
keywords: PowerShell, çekirdek
title: PowerShell 6.0 için bozucu değişiklikler
ms.openlocfilehash: d477a9b27e8d5df6653ee40f8b606879b60a80c7
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655455"
---
# <a name="breaking-changes-for-powershell-60"></a>PowerShell 6.0 için bozucu değişiklikler

## <a name="features-no-longer-available-in-powershell-core"></a>PowerShell Core artık kullanılabilir özellikler

### <a name="powershell-workflow"></a>PowerShell iş akışı

[PowerShell iş akışı] [ workflow] üst kısmındaki oluşturan bir Windows PowerShell bir özelliktir [Windows Workflow Foundation (WF)] [ workflow-foundation] oluşturulmasını sağlar uzun süreli veya paralel görevler için güçlü runbook.

Windows Workflow Foundation'da .NET Core desteği eksikliği nedeniyle, biz de PowerShell Core PowerShell iş akışı desteklemeye devam etmeyecek.

Gelecekte, PowerShell iş akışı gerek kalmadan PowerShell dilinde yerel paralellik/eşzamanlılık sağlamak istiyoruz.

[workflow]: https://docs.microsoft.com/powershell/scripting/core-powershell/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Özel bileşenler

[PowerShell ek bileşenleri] [ snapin] PowerShell topluluğunda yaygın olmayan PowerShell modülleri için öncül olan.

Ek bileşenleri ve bunların kullanım yetersizliği topluluk destekleyen karmaşıklığı nedeniyle, artık özel ek bileşenler de PowerShell Core desteklemiyoruz.

Günümüzde, bu keser `ActiveDirectory` ve `DnsClient` modülleri Windows ve Windows Server.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>WMI v1 cmdlet'leri

Modüller VMI tabanlı iki kümesini destekleyen karmaşıklığı nedeniyle, WMI v1 cmdlet'leri PowerShell çekirdek kaldırıldı:

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

Bunun yerine, öneririz, yeni işlevsellik ve yeniden tasarlanan bir söz dizimi ile aynı işlevselliği sağlayan (WMI v2 olarak da bilinir) CIM cmdlet'leri kullanın:

- `Get-CimAssociatedInstance`
- `Get-CimClass`
- `Get-CimInstance`
- `Get-CimSession`
- `Invoke-CimMethod`
- `New-CimInstance`
- `New-CimSession`
- `New-CimSessionOption`
- `Register-CimIndicationEvent`
- `Remove-CimInstance`
- `Remove-CimSession`
- `Set-CimInstance`

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft.PowerShell.LocalAccounts

Desteklenmeyen API kullanımı nedeniyle `Microsoft.PowerShell.LocalAccounts` PowerShell çekirdek, daha iyi bir çözüm bulunana kadar kaldırıldı.

### <a name="-counter-cmdlets"></a>`*-Counter` cmdlet'leri

Desteklenmeyen API kullanımı nedeniyle `*-Counter` PowerShell çekirdek, daha iyi bir çözüm bulunana kadar kaldırıldı.

## <a name="enginelanguage-changes"></a>Altyapısı/dil değişiklikleri

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>Yeniden adlandırma `powershell.exe` için `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

Kullanıcılar (aksine, Windows PowerShell) Windows PowerShell Core çağırmak için belirlenimci bir şekilde tanımak için PowerShell Core ikili değiştirilmiştir `pwsh.exe` Windows üzerinde ve `pwsh` Windows dışı platformlarda.

Kısaltılmış adı, Windows dışı platformlarda Kabukları adlandırma ile tutarlıdır.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>(Tablolar hariç) çıktısını almak için satır sonları eklemeyin [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Daha önce çıkış konsolunun genişliğine hizalı ve çıkış terminal boyutlandırılmış beklendiği gibi yeniden biçimlendirildi istemediğiniz anlamına gelir konsolun son genişlikte satır sonları eklenmiştir. Satır sonları hizalı sütunları tutmak gerekli olduğundan tablo, bu değişiklik uygulanmadı.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>Atla null öğe onay için bir değer türünün öğe türü olan koleksiyonları [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

İçin `Mandatory` parametresi ve `ValidateNotNull` ve `ValidateNotNullOrEmpty` öznitelikleri, koleksiyonun öğe türü, değer türü ise null öğe onay atlayın.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>Değişiklik `$OutputEncoding` kullanılacak `UTF-8 NoBOM` yerine ASCII kodlaması [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

Önceki, ASCII (7-bit), kodlama çıkış bazı durumlarda yanlış değişikliğinin neden olur. Bu değişiklik yapmaktır `UTF-8 NoBOM` varsayılan, araçları ve işletim sistemleri tarafından desteklenen kodlama ile Unicode çıkış korur.

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>Kaldırma `AllScope` çoğu varsayılan eş ad alanından [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

Kapsam, oluşumunu hızlandırma için `AllScope` birçok varsayılan diğer ad kaldırıldı. `AllScope` arama daha hızlı olduğu için sık kullanılan bazı diğer adlar bırakıldı.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose` ve `-Debug` artık geçersiz kılmalar `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

Daha önce varsa `-Verbose` veya `-Debug` belirtilmiş davranışını geçersiz kılınmış `$ErrorActionPreference`. Bu değişikliğe `-Verbose` ve `-Debug` artık davranışını etkileyen `$ErrorActionPreference`.

## <a name="cmdlet-changes"></a>Cmdlet değişiklikleri

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>Hiçbir veri döndürülmez olduğunda çağırma RestMethod yararlı bilgiler döndürmek zorunda değildir. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

Bir API döndürdüğünde yalnızca `null`, Invoke-RestMethod serileştirme Bu dize olarak `"null"` yerine `$null`. Bu değişiklik mantığında düzeltmeleri `Invoke-RestMethod` düzgün geçerli tek değer JSON seri hale getirmek için `null` değişmez değer olarak `$null`.

### <a name="remove--computername-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>Kaldırma `-ComputerName` gelen `*-Computer` cmdlet'leri [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

RPC remoting Corefx'te (özellikle de Windows olmayan platformlar için) ve bir PowerShell tutarlı remoting deneyimi sağlama ile ilgili sorunlar nedeniyle `-ComputerName` parametresi üzerinden kaldırıldı `\*-Computer` cmdlet'leri. Kullanım `Invoke-Command` cmdlet'leri uzaktan yürütülecek şekilde yerine.

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>Kaldırma `-ComputerName` gelen `*-Service` cmdlet'leri [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

PSRP, tutarlı kullanımını teşvik etmek için `-ComputerName` parametresi üzerinden kaldırıldı `*-Service` cmdlet'leri.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>Düzeltme `Get-Item -LiteralPath a*b` varsa `a*b` gerçekten hata döndüreceğini yok [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

Daha önce `-LiteralPath` söz konusu bir joker karakter, disklerle aynı şekilde işlem `-Path` ve joker karakter hiçbir dosya bulunamazsa, sessizce çıkmak. Doğru davranışı, olmalıdır `-LiteralPath` dosya yoksa hata gerektiği şekilde sabitidir. Değişikliktir ile kullanılan joker karakterler değerlendirilecek `-Literal` sabit değer olarak.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>`Import-Csv` uygulamalıdır `PSTypeNames` CSV'ye tür bilgisi varsa içeri aktarma sırasında [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

Nesne daha önce dışarı kullanarak `Export-CSV` ile `TypeInformation` içeri `ConvertFrom-Csv` tür bilgilerini koruyarak değil. Bu değişiklik türü bilgileri ekler `PSTypeNames` üyesi kullanılabilir durumdaysa CSV dosyasındaki.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`-NoTypeInformation` Varsayılan değer olmalıdır `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Bu değişiklik adresi Müşteri geri bildirimi varsayılan davranışını bulunuldu `Export-CSV` tür bilgileri içerecek şekilde.

Daha önce cmdlet'i bir yorum nesnenin türü adını içeren ilk satırı çıktı. Çoğu araçları tarafından anlaşılmayan gibi varsayılan olarak bu bastırmak için farklıdır. Kullanım `-IncludeTypeInformation` önceki davranışı korumak için.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>Web cmdlet'leri uyar `-Credential` şifrelenmemiş bir bağlantı üzerinden gönderilir [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

HTTP kullanarak parolaları da dahil olmak üzere içerik düz metin gönderilir. Bu değişiklik, değil Bu varsayılan olarak izin verir ve kimlik bilgilerini güvenli bir şekilde geçirilirse, bir hata döndürebilir oluşturmaktır. Kullanıcılar bu kullanarak konusunda atlayabilir `-AllowUnencryptedAuthentication` geçin.

## <a name="api-changes"></a>API değişiklikleri

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>Kaldırma `AddTypeCommandBase` sınıfı [#5407](https://github.com/PowerShell/PowerShell/issues/5407)

`AddTypeCommandBase` Sınıfı üzerinden kaldırıldı `Add-Type` performansını artırmak için. Bu sınıf, yalnızca Add-Type cmdlet'i tarafından kullanılır ve kullanıcıların etkilememesi gerekir.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>Cmdlet parametresi ile birleştirin `-Encoding` türünde olmasını `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

`-Encoding` Değer `Byte` dosya sistemi sağlayıcısı cmdlet'leri kaldırıldı. Yeni bir parametre `-AsByteStream`, bayt akışı olarak gerekli olduğunu belirtmek için artık kullanılan giriş veya çıkış bayt akışı alınır.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>Daha iyi hata iletisi boş ve null ekleme `-UFormat` parametre [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

Daha önce ne zaman geçirme boş bir biçim dizesi için `-UFormat`, faydasız bir ileti görüntülenir. Daha açıklayıcı hata eklendi.

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>Konsol kod Temizleme [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

PowerShell Core içinde desteklenmez ve Windows PowerShell için eski nedenlerle oldukları gibi desteği eklemek için bir plan yok olarak aşağıdaki özellikler kaldırıldı: `-psconsolefile` anahtar ve kodu `-importsystemmodules` geçiş kodu ve kod değiştirme yazı tipi.

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>Kaldırılan `RunspaceConfiguration` Destek [#4942](https://github.com/PowerShell/PowerShell/issues/4942)

Daha önce bir PowerShell çalışma program aracılığıyla oluştururken API'sini kullanarak eski kullanabileceğinizi [ `RunspaceConfiguration` ] [ runspaceconfig] veya yeni [ `InitialSessionState` ] [ iss]. Bu değişiklik desteği kaldırıldı `RunspaceConfiguration` ve yalnızca destekler `InitialSessionState`.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript` bağımsız değişken bağlama `$input` yerine `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

Bağımsız olarak yerine Giriş bağımsız değişken olarak geçirilen bağımsız değişkenler olarak hatalı bir parametre konumunu sonuçlandı.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>Desteklenmeyen Kaldır `-showwindow` geçmek `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow` Coreclr'de desteklenmeyen WPF kullanır.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>İzin ver * için kayıt defteri yolunda kullanılacak `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

Daha önce `-LiteralPath` söz konusu bir joker karakter, disklerle aynı şekilde işlem `-Path` ve joker karakter hiçbir dosya bulunamazsa, sessizce çıkmak. Doğru davranışı, olmalıdır `-LiteralPath` dosya yoksa hata gerektiği şekilde sabitidir. Değişikliktir ile kullanılan joker karakterler değerlendirilecek `-Literal` sabit değer olarak.

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>Düzeltme `Set-Service` sınama başarısız [#4802](https://github.com/PowerShell/PowerShell/issues/4802)

Daha önce varsa `New-Service -StartupType foo` kullanılan `foo` yok sayıldı ve bazı varsayılan başlatma türüyle hizmet oluşturuldu. Bu değişiklik, açıkça geçersiz başlangıç türü için bir hata durum oluşturmaktır.

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>Yeniden adlandırma `$IsOSX` için `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

PowerShell'de adlandırma bizim adlandırma ile tutarlı ve macOS OSX yerine Apple'nın kullanımı için uygun olması gerekir. Ancak, okunabilirlik için ve tutarlı bir şekilde biz ile Pascal kaldığını büyük/küçük harf.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>Geçersiz betik geçirildiğinde hata iletisi tutarlı hale getirmek için - dosya, daha iyi belirsiz bağımsız değişken geçirildi hatası [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

Çıkış kodlarını değiştirmek `pwsh.exe` UNIX kuralları ile hizalamak için

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>Kaldırılmasını `LocalAccount` ve cmdlet'lerinden `Diagnostics` modüller. [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

Desteklenmeyen API nedeniyle `LocalAccounts` modülü ve `Counter` cmdlet'leri `Diagnostics` daha iyi bir çözüm bulunana kadar modülü kaldırıldı.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>Bool parametresiyle birlikte PowerShell Betiği Yürütülüyor çalışmıyor [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

Daha önce powershell.exe kullanarak (artık `pwsh.exe`) kullanarak bir PowerShell Betiği yürütmek için `-File` $true başarılı şekilde sağlanan/$false olarak parametre değerleri. $True desteği/$false ayrıştırılmış değerler için parametre olarak eklendi. Şu anda belgelenmiş söz dizimi işe yaramazsa gibi anahtar değerlerini de desteklenir.

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>Kaldırma `ClrVersion` özelliğinden `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

`ClrVersion` Özelliği `$PSVersionTable` olduğu CoreCLR ile kullanışlı değil, son kullanıcılar bu değeri uyumluluğunu belirlemek için kullanılmaması gereken.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>Değiştirmek için konumsal parametresi `powershell.exe` gelen `-Command` için `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

Windows dışı platformlarda shebang'i PowerShell kullanımını etkinleştirin. Başka bir deyişle, UNIX tabanlı sistemlerde PowerShell çağıracaktır bir komut dosyası yürütülebilir yapabilirsiniz açıkça çağırmak yerine otomatik olarak `pwsh`. Ayrıca gibi şeyler yapmak, yani `powershell foo.ps1` veya `powershell fooScript` belirtmeden `-File`. Ancak, bu değişiklik hemen açıkça belirttiğiniz gerektirir `-c` veya `-Command` yapma çalışırken `powershell.exe Get-Command`.

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>Unicode kaçış ayrıştırma uygulamak [#3958](https://github.com/PowerShell/PowerShell/issues/3958)

`` `u#### `` veya `` `u{####} `` karşılık gelen bir Unicode karakter için dönüştürülür. Bir sabit değer çıkış `` `u ``, kaçış vurgulamasını belirtir: ``` ``u ```.

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>Değişiklik `New-ModuleManifest` kodlamasını `UTF8NoBOM` Windows dışı platformlarda [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

Daha önce `New-ModuleManifest` Linux araçları için sorun oluşturma, BOM ile UTF-16 psd1 bildirimleri oluşturur. Bu değişiklik, kodlama değişiklikleri `New-ModuleManifest` Windows dışı platformlarda UTF (hiçbir BOM) olacak şekilde.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>Engelleme `Get-ChildItem` çözümlemeyin recursing gelen (#1875). [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Bu değişiklik getirir `Get-ChildItem` UNIX ayarlarına uygun olarak daha fazla `ls -r` ve Windows `dir /s` yerel komutları. Belirtilen komutları gibi cmdlet özyineleme sırasında bulunan dizinler için simgesel bağlantılar görüntüler, ancak bunları recurse değil.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>Düzeltme `Get-Content -Delimiter` sınırlayıcı döndürülen satırları içermeyecek şekilde [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Kullanırken daha önce çıkış `Get-Content -Delimiter` tutarsız ve daha fazla sınırlayıcı kaldırmak için veri işleme gerektiği şekilde kullanışsız. Bu değişiklik, sınırlayıcı döndürülen satırları kaldırır.

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>Biçimi onaltılık olarak uygulamak C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

`-Raw` Parametredir şimdi bir "İşlemsiz" (hiçbir şey yapmasa unutmayın). Tüm çıktı gösterilecek olan kendi türü için bayt hepsini içerir numaralarını temsil ileride (ne `-Raw` parametresi resmi önce bu değişiklik yaptığını).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>PowerShell varsayılan kabuğunu olarak komut ile işe yaramazsa [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

İsteğe bağlı olarak, UNIX için Kabukları kabul etmek bir kuralı olan `-i` etkileşimli bir kabuk ve birçok araçları bu davranışı beklediğiniz için (`script` örneğin ve PowerShell varsayılan kabuğunu ayarlama) ve kabuğunda çağırır `-i` geçin. Bu değişiklik, bozucu `-i` kısa ele eşleştirmek için daha önce kullanılabilir `-inputformat`, olması gerekir böylece `-in`.

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Get-Computerınfo özellik adında yazım hatası düzeltme [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber` olarak yanlış `BiosSeralNumber` ve yazımını için değiştirildi.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>Ekleme `Get-StringHash` ve `Get-FileHash` cmdlet'leri [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Bu değişiklik, bazı karma algoritmaları Corefx'te tarafından desteklenmiyor, bu nedenle bunlar artık kullanılabilir olan:

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>Doğrulama eklemek `Get-*` $null geçirme döndüğü hatası yerine tüm nesneler cmdlet'lerini [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

Geçirme `$null` herhangi bir hata şu anda oluşturur:

- `Get-Credential -UserName`
- `Get-Event -SourceIdentifier`
- `Get-EventSubscriber -SourceIdentifier`
- `Get-Help -Name`
- `Get-PSBreakpoint -Script`
- `Get-PSProvider -PSProvider`
- `Get-PSSessionConfiguration -Name`
- `Get-PSSnapin -Name`
- `Get-Runspace -Name`
- `Get-RunspaceDebug -RunspaceName`
- `Get-Service -Name`
- `Get-TraceSource -Name`
- `Get-Variable -Name`
- `Get-WmiObject -Class`
- `Get-WmiObject -Property`

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a>Ekleme desteği W3C Genişletilmiş günlük dosyası biçimi ' `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

Daha önce `Import-Csv` cmdlet'i, doğrudan W3C Genişletilmiş günlük biçiminde günlük dosyalarını içeri aktarmak için kullanılamaz ve başka bir işlem gerekli olacaktır. Bu değişiklik, W3C Genişletilmiş günlük biçimini desteklenir.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>Parametre bağlama sorun `ValueFromRemainingArguments` PS işlevlerde [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments` değerleri yerine tek bir dizi olarak döndürür kendisi değer artık bir dizidir.

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>`BuildVersion` kaldırılır `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Kaldırma `BuildVersion` özelliğinden `$PSVersionTable`. Bu özellik Windows yapı sürümüne bağlı. Bunun yerine kullanmanızı öneriyoruz `GitCommitId` PowerShell Core tam derleme sürümü almak için.

### <a name="changes-to-web-cmdlets"></a>Değişiklikleri Web cmdlet'leri

Temel .NET API Web cmdlet'lerinin değiştirildi `System.Net.Http.HttpClient`. Bu değişiklik, birçok avantaj sunar. Ancak, bu değişiklikle birlikte Internet Explorer ile birlikte çalışabilirlik eksikliği sonuçlandı içindeki çeşitli bozucu değişiklikler `Invoke-WebRequest` ve `Invoke-RestMethod`.

- `Invoke-WebRequest` Şimdi temel HTML Ayrıştırma yalnızca destekler. `Invoke-WebRequest` her zaman döndüren bir `BasicHtmlWebResponseObject` nesne. `ParsedHtml` Ve `Forms` özellikleri kaldırıldı.
- `BasicHtmlWebResponseObject.Headers` değerler şimdi `String[]` yerine `String`.
- `BasicHtmlWebResponseObject.BaseResponse` artık bir `System.Net.Http.HttpResponseMessage` nesne.
- `Response` Web Cmdlet özel durum özelliği, artık bir `System.Net.Http.HttpResponseMessage` nesne.
- Katı RFC üstbilgi ayrıştırma, artık varsayılan `-Headers` ve `-UserAgent` parametresi. Bu ile atlanabilir `-SkipHeaderValidation`.
- `file://` ve `ftp://` URI düzenleri artık desteklenmiyor.
- `System.Net.ServicePointManager` ayarları artık dikkate alınır.
- Var. şu anda hiçbir sertifika tabanlı kimlik doğrulaması macOS üzerinde
- Kullanım `-Credential` üzerinden bir `http://` URI hataya neden olur. Kullanım bir `https://` URI veya tedarik `-AllowUnencryptedAuthentication` hata bastırmak için parametre.
- `-MaximumRedirection` Şimdi yeniden yönlendirme denemeleri son yeniden yönlendirme sonuçlarını döndürmek yerine belirtilen sınırı aşan bir sonlandırma hatası oluşturur.
