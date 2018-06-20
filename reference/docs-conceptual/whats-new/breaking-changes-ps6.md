---
ms.date: 05/17/2018
keywords: PowerShell, çekirdek
title: PowerShell 6.0 için yeni değişiklikler
ms.openlocfilehash: 60ce7a1676403bb08b57bf852ba725acde86a30c
ms.sourcegitcommit: 2d9cf1ccb9a653db7726a408ebcb65530dcb1522
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2018
ms.locfileid: "34309586"
---
# <a name="breaking-changes-for-powershell-60"></a>PowerShell 6.0 için yeni değişiklikler

## <a name="features-no-longer-available-in-powershell-core"></a>PowerShell çekirdek artık kullanılabilir özellikler

### <a name="powershell-workflow"></a>PowerShell iş akışı

[PowerShell iş akışı] [ workflow] üstünde derlemeler Windows PowerShell özelliğidir [Windows Workflow Foundation (WF)] [ workflow-foundation] oluşturulmasını etkinleştirir sağlam runbook'lar uzun süre çalışan veya paralel birkaç ölçeklendirin görevler için.

Windows Workflow Foundation, .NET Core için destek eksikliği nedeniyle, biz PowerShell çekirdek PowerShell iş akışı desteklemeye devam etmeyecek.

Gelecekte, yerel paralellik/eşzamanlılık PowerShell iş akışı gerek kalmadan PowerShell dilde etkinleştirmek isteriz.

[workflow]: https://docs.microsoft.com/powershell/scripting/core-powershell/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Özel bileşenler

[PowerShell eklentileri] [ snapin] yaygın PowerShell topluluğuna sahip olmayan PowerShell modülleri için öncülü olan.

Ek bileşenleri ve bunların kullanım yetersizliği topluluğuna destekleme karmaşıklığı nedeniyle, artık özel eklentileri PowerShell çekirdek destekliyoruz.

Günümüzde, bu keser `ActiveDirectory` ve `DnsClient` Windows ve Windows Server modülleri.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>WMI v1 cmdlet'leri

WMI tabanlı modüllerin iki kümeleri destekleyen karmaşıklığı nedeniyle, biz WMI v1 cmdlet'leri PowerShell çekirdek kaldırıldı:

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

Bunun yerine, öneririz, yeni işlevsellik ve yeniden tasarlanan bir sözdizimi ile aynı işlevselliği sağlayan CIM (diğer adıyla WMI v2) cmdlet'leri kullanın:

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

Desteklenmeyen API kullanımı nedeniyle `Microsoft.PowerShell.LocalAccounts` daha iyi bir çözüm bulunana kadar PowerShell çekirdek kaldırılmıştır.

### <a name="-counter-cmdlets"></a>`*-Counter` cmdlet'leri

Desteklenmeyen API kullanımı nedeniyle `*-Counter` daha iyi bir çözüm bulunana kadar PowerShell çekirdek kaldırılmıştır.

## <a name="enginelanguage-changes"></a>Altyapısı/dil değişiklikleri

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>Yeniden Adlandır `powershell.exe` için `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

Kullanıcılar (aksine, Windows PowerShell) Windows PowerShell çekirdek çağırmak için belirleyici bir yol sunmak için PowerShell çekirdek ikili değiştirilmiştir `pwsh.exe` Windows'da ve `pwsh` olmayan Windows platformlarında.

Kısaltılmış adı, Windows olmayan platformlarında Kabukları adlandırma ile tutarlıdır.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>Satır sonları (Tablolar hariç) çıkış eklemeyin [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Daha önce çıkış konsol genişliğini hizalı ve satır sonları çıkış terminal boyutlandırıldı beklendiği gibi yeniden biçimlendirilen kaydetmedi anlamına gelir konsolun son genişlikte eklenmiştir. Satır sonları hizalı sütunları tutmak gerekli olduğu kadar bu değişiklik, tablolara uygulanmadı.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>Atlamak için bir değer türü öğe türü olan koleksiyonları null öğe onay [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

İçin `Mandatory` parametre ve `ValidateNotNull` ve `ValidateNotNullOrEmpty` öznitelikleri, koleksiyonun öğe türü değer türü ise null öğe onay atlayın.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>Değişiklik `$OutputEncoding` kullanmak için `UTF-8 NoBOM` yerine ASCII kodlama [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

Önceki, ASCII (7-bit), kodlama çıkış bazı durumlarda yanlış değişikliğinin neden olur. Bu değişiklik yapmaktır `UTF-8 NoBOM` bir araçlar ve işletim sistemleri tarafından desteklenen kodlama ile Unicode çıkış korur varsayılan.

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>Kaldırma `AllScope` birçok varsayılan diğer ad alanından [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

Kapsam oluşturulmasını, hızlandırmak için `AllScope` birçok varsayılan diğer ad kaldırıldı. `AllScope` arama daha hızlı olduğu için birkaç sık kullanılan diğer adlar bırakıldı.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose` ve `-Debug` artık geçersiz kılmaları `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

Daha önce varsa `-Verbose` veya `-Debug` belirtilmiş davranışını geçersiz kılınmış `$ErrorActionPreference`. Bu değişikliği `-Verbose` ve `-Debug` artık davranışını etkilemez `$ErrorActionPreference`.

## <a name="cmdlet-changes"></a>Cmdlet değişiklikleri

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>Hiçbir veri döndürüldüğünde çağırma RestMethod yararlı bilgileri döndürmez. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

Bir API döndüğünde yalnızca `null`, Invoke-RestMethod seri hale getirilirken Bu dize olarak `"null"` yerine `$null`. Bu değişiklik mantık giderir `Invoke-RestMethod` düzgün bir şekilde geçerli bir tek değer JSON seri hale getirmek için `null` değişmez değer olarak `$null`.

### <a name="remove--computername-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>Kaldırma `-ComputerName` gelen `*-Computer` cmdlet'leri [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

RPC remoting CoreFX (özellikle platformlarda Windows dışı) ve PowerShell, tutarlı remoting deneyimi sağlama ile ilgili sorunları nedeniyle `-ComputerName` başarıyla parametre temizlendi `\*-Computer` cmdlet'leri. Kullanım `Invoke-Command` cmdlet'leri uzaktan çalıştırılacak şekilde yerine.

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>Kaldırma `-ComputerName` gelen `*-Service` cmdlet'leri [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

PSRP, tutarlı kullanımı teşvik için `-ComputerName` başarıyla parametre temizlendi `*-Service` cmdlet'leri.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>Düzeltme `Get-Item -LiteralPath a*b` varsa `a*b` hata döndürmek için gerçekten yok [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

Daha önce `-LiteralPath` bir joker karakter onu aynı şekilde işlem `-Path` ve joker karakter hiçbir dosya bulunursa, sessizce çıkmak. Doğru davranış, olmalıdır `-LiteralPath` dosya yoksa hata gerektiği şekilde değişmez değer olduğunu. Değişikliktir joker karakter ile kullanılan işlemek için `-Literal` sabit değer olarak.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>`Import-Csv` uygulamalıdır `PSTypeNames` türü bilgileri CSV dosyasında mevcut olduğunda içe aktarma üzerine [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

Nesne daha önce dışarı kullanarak `Export-CSV` ile `TypeInformation` ile içeri aktarılan `ConvertFrom-Csv` türü bilgileri korunuyor değil. Bu değişikliği türü bilgilerini ekler `PSTypeNames` üyesi kullanılabilir durumdaysa CSV dosyasından.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`-NoTypeInformation` Varsayılan olmalıdır `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Bu değişiklik varsayılan davranışını adresi Müşteri geri bildirimi için yapılmıştır `Export-CSV` türü bilgileri içerecek şekilde.

Cmdlet daha önce nesne türü adını içeren ilk satır bir açıklama çıktı. Bu varsayılan olarak, çoğu araçları tarafından anlaşılmayan gibi gizlemek için farklıdır. Kullanım `-IncludeTypeInformation` önceki davranışı korumak için.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>Web cmdlet'leri uyar `-Credential` şifrelenmemiş bağlantıları üzerinden gönderilen [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

HTTP kullanırken, parolalar dahil olmak üzere içerik düz metin gönderilir. Bu değişiklik olduğu değil Bu varsayılan olarak izin ve kimlik bilgilerini güvenli bir şekilde geçirilirse hata döndürür. Kullanıcılar bu kullanarak konusunda atlayabilir `-AllowUnencryptedAuthentication` geçin.

## <a name="api-changes"></a>API değişiklikleri

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>Kaldırma `AddTypeCommandBase` sınıfı [#5407](https://github.com/PowerShell/PowerShell/issues/5407)

`AddTypeCommandBase` Başarıyla sınıfı temizlendi `Add-Type` performansını artırmak için. Bu sınıf yalnızca tür Ekle cmdlet tarafından kullanılır ve kullanıcıları etkileyen değil.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>Cmdlet parametresi ile bütünleştirin `-Encoding` türünde olması `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

`-Encoding` Değeri `Byte` dosya sistemi sağlayıcısı cmdlet'leri kaldırılmıştır. Yeni bir parametre `-AsByteStream`, artık bir bayt akış olarak gerekli olduğunu belirtmek için kullanılan giriş veya çıkış akışı bayt alınır.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>Daha iyi hata iletisi boş ve null eklemek `-UFormat` parametresi [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

Daha önce ne zaman bir boş biçiminde geçirerek dize için `-UFormat`, faydasız hata iletisi görünür. Daha açıklayıcı bir hata eklendi.

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>Konsol kod Temizleme [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

Aşağıdaki özellikler PowerShell çekirdek desteklenmez ve Windows PowerShell için eski nedenlerle oldukları gibi desteği eklemek için herhangi bir plan yok gibi kaldırıldı: `-psconsolefile` anahtar ve kodu `-importsystemmodules` geçiş kodu ve yazı tipi kodu değiştirme.

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>Kaldırılan `RunspaceConfiguration` Destek [#4942](https://github.com/PowerShell/PowerShell/issues/4942)

Daha önce bir PowerShell çalışma program aracılığıyla oluştururken API'yi kullanarak eski kullanabilirsiniz [ `RunspaceConfiguration` ] [ runspaceconfig] ya da daha yeni [ `InitialSessionState` ] [ iss]. Bu değişiklik desteği kaldırıldı `RunspaceConfiguration` ve yalnızca destekliyorsa `InitialSessionState`.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript` bağımsız değişken bağlama `$input` yerine `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

Bir parametre yanlış bir konumunu yerine Giriş bağımsız değişken olarak geçirilen bağımsız değişken ile sonuçlandı.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>Desteklenmeyen Kaldır `-showwindow` geçiş `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow` üzerinde CoreCLR desteklenmiyor WPF kullanır.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>İzin * için kayıt defteri yolunda kullanılacak `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

Daha önce `-LiteralPath` bir joker karakter onu aynı şekilde işlem `-Path` ve joker karakter hiçbir dosya bulunursa, sessizce çıkmak. Doğru davranış, olmalıdır `-LiteralPath` dosya yoksa hata gerektiği şekilde değişmez değer olduğunu. Değişikliktir joker karakter ile kullanılan işlemek için `-Literal` sabit değer olarak.

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>Düzeltme `Set-Service` test başarısız [#4802](https://github.com/PowerShell/PowerShell/issues/4802)

Daha önce varsa `New-Service -StartupType foo` kullanılan `foo` yoksayıldı ve hizmeti bazı varsayılan başlangıç türü ile oluşturuldu. Bu değişiklik, açıkça geçersiz başlangıç türü için bir hata durum oluşturmaktır.

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>Yeniden Adlandır `$IsOSX` için `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

PowerShell'de adlandırma bizim adlandırma ile tutarlı ve OSX yerine macOS Apple'nın kullanımı için uygun olması gerekir. Ancak, okunabilirlik ve tutarlı bir şekilde biz ile Pascal kaldığını büyük/küçük harf.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>Geçersiz komut dosyası geçirildiğinde hata iletisi tutarlı hale getirmek için - dosya, daha iyi belirsiz bağımsız değişkeni geçirildiğinde hata [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

Çıkış kodlarını değiştirme `pwsh.exe` UNIX kurallarına hizalamak için

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>Kaldırılmasını `LocalAccount` ve cmdlet'leri `Diagnostics` modüller. [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

Desteklenmeyen API'leri nedeniyle `LocalAccounts` modülü ve `Counter` cmdlet'leri `Diagnostics` modülü daha iyi bir çözüm bulunana kadar kaldırıldı.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>Bool parametresiyle birlikte PowerShell Betiği yürütülürken çalışmıyor [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

Daha önce powershell.exe kullanarak (şimdi `pwsh.exe`) kullanarak bir PowerShell komut dosyasını çalıştırmak için `-File` $true geçirmek için hiçbir şekilde sağlanan/parametre değerleri olarak $false. $True desteği/$false parametreleri için ayrıştırılmış değer olarak eklendi. Şu anda belgelenen sözdizimi işe yaramazsa gibi anahtar değerlerini de desteklenir.

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>Kaldırma `ClrVersion` özelliğinden `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

`ClrVersion` Özelliği `$PSVersionTable` olan CoreCLR ile kullanışlı değil, son kullanıcılar bu değeri uyumluluğunu belirlemek için kullanılmaması gereken.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>Değiştirmek için konumsal parametresi `powershell.exe` gelen `-Command` için `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

PowerShell Windows olmayan platformlarında shebang kullanımını etkinleştirin. Yani UNIX tabanlı sistemlerde, PowerShell çağıracaktır bir komut dosyası yürütülebilir yapabilir açıkça çağırma yerine otomatik olarak `pwsh`. Bu aynı zamanda bunu şimdi gibi şeyler yapabilirsiniz gelir `powershell foo.ps1` veya `powershell fooScript` belirtmeden `-File`. Ancak, bu değişikliği şimdi açıkça belirttiğiniz gerektirir `-c` veya `-Command` gibi şeyler çalışılırken `powershell.exe Get-Command`.

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>Unicode kaçış ayrıştırma uygulamak [#3958](https://github.com/PowerShell/PowerShell/issues/3958)

`` `u#### `` veya `` `u{####} `` karşılık gelen Unicode karakter dönüştürülür. Bir hazır değer çıktısını almak için `` `u ``, backtick kaçış: ``` ``u ```.

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>Değişiklik `New-ModuleManifest` kodlamasını `UTF8NoBOM` olmayan Windows platformlarında [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

Daha önce `New-ModuleManifest` psd1 bildirimleri UTF-16 AĞACI, Linux araçları için sorun oluşturma ile oluşturur. Bu önemli değişiklik kodlamasını değiştirir `New-ModuleManifest` Windows olmayan platformlarda UTF (ürün reçetesi) olmalıdır.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>Engellemek `Get-ChildItem` simgesel bağlantı recursing gelen (#1875). [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Bu değişiklik getirir `Get-ChildItem` daha fazla UNIX uygun olarak `ls -r` ve Windows `dir /s` yerel komutları. Sözü edilen komutları gibi cmdlet sembolik bağlantılar sırasında özyineleme buldu dizinleri görüntüler, ancak bunlara recurse değil.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>Düzeltme `Get-Content -Delimiter` sınırlayıcı döndürülen satırları içermeyecek şekilde [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Daha önce kullanırken çıktı `Get-Content -Delimiter` tutarsız ve başka bir sınırlayıcı kaldırmak için veri işleme gerektiği şekilde kullanışsız bulabilir. Bu değişiklik sınırlayıcı döndürülen satırları kaldırır.

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>Biçim onaltılık C# ' ta uygulamak [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

`-Raw` Parametredir şimdi bir "no-op" (hiçbir şey yapmayacak unutmayın). Tüm çıktı gösterilecek tüm türü için bir bayt içeren numaralarını temsil ile ileride (ne `-Raw` parametresi bu değişiklik öncesinde resmi olarak yaptığını).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>Varsayılan kabuğunu olarak PowerShell betik komutu çalışmıyor [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

İsteğe bağlı olarak, UNIX Kabukları kabul etmek için bir kuralı olan `-i` etkileşimli bir kabuk ve birçok araçları bu davranışı beklediğiniz için (`script` örneğin ve PowerShell varsayılan kabuğunu ayarlama) ve kabuğunda çağırır `-i` geçin. Bu değişiklik, ihlal `-i` daha önce kısa bir ele eşleştirmek için kullanılabilecek `-inputformat`, şimdi olması gerekir `-in`.

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Get-ComputerInfo özellik adı yazım hatası düzeltme [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber` olarak yanlış `BiosSeralNumber` ve doğru yazım değiştirildi.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>Ekleme `Get-StringHash` ve `Get-FileHash` cmdlet'leri [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Bu değişiklik, bazı karma algoritmaları CoreFX tarafından desteklenmez, bu nedenle bunlar artık kullanılabilir olan:

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>Doğrulama eklemek `Get-*` $null geçirme döndüğü hatası yerine tüm nesneleri cmdlet'leri [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

Geçirme `$null` herhangi bir hata şu anda verir:

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

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a>Ekleme W3C Genişletilmiş günlük dosyası biçimi'Destek `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

Daha önce `Import-Csv` cmdlet, doğrudan W3C Genişletilmiş günlük biçimini günlük dosyalarını içeri aktarmak için kullanılamaz ve başka bir eylem gerekli olacaktır. Bu değişiklikle, W3C Genişletilmiş günlük biçimini desteklenir.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>Parametre bağlama sorun `ValueFromRemainingArguments` PS işlevlerinde [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments` döndürür değerleri yerine tek bir dizi olarak kendisi değer artık bir dizidir.

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>`BuildVersion` kaldırılır `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Kaldırma `BuildVersion` özelliğinden `$PSVersionTable`. Bu özellik Windows yapı sürümüne bağlı. Bunun yerine, kullanmanızı öneririz `GitCommitId` PowerShell çekirdek tam yapı sürümü alınamadı.

### <a name="changes-to-web-cmdlets"></a>Web cmdlet'leri yapılan değişiklikler

Temel alınan .NET API Web cmdlet'leri değiştirildi `System.Net.Http.HttpClient`. Bu değişiklik birçok avantaj sağlar. Ancak, bu değişiklik Internet Explorer ile birlikte çalışabilirlik eksikliği birlikte sonuçlandı içinde birkaç önemli değişiklikler `Invoke-WebRequest` ve `Invoke-RestMethod`.

- `Invoke-WebRequest` artık temel HTML Ayrıştırma yalnızca destekler. `Invoke-WebRequest` her zaman döndüren bir `BasicHtmlWebResponseObject` nesnesi. `ParsedHtml` Ve `Forms` özellikleri kaldırıldı.
- `BasicHtmlWebResponseObject.Headers` değerler: artık `String[]` yerine `String`.
- `BasicHtmlWebResponseObject.BaseResponse` artık bir `System.Net.Http.HttpResponseMessage` nesnesi.
- `Response` Web Cmdlet özel durum özelliği olan şimdi bir `System.Net.Http.HttpResponseMessage` nesnesi.
- Katı RFC üstbilgi ayrıştırma varsayılandır şimdi için `-Headers` ve `-UserAgent` parametresi. Bu ile atlanabilir `-SkipHeaderValidation`.
- `file://` ve `ftp://` URI şemaları artık desteklenmemektedir.
- `System.Net.ServicePointManager` ayarları artık dikkate alınır.
- Şu anda hiçbir sertifika tabanlı kimlik doğrulaması mevcut değil macOS üzerinde.
- Kullanımı `-Credential` üzerinden bir `http://` URI hataya neden olur. Kullanım bir `https://` URI veya sağlayın `-AllowUnencryptedAuthentication` hata gizlemek için parametre.
