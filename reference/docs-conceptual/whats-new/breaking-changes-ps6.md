---
ms.date: 05/17/2018
keywords: PowerShell, çekirdek
title: PowerShell 6,0 için son değişiklikler
ms.openlocfilehash: 186e55c1ac46ce3fc172df18995f8c15d9eeb8eb
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "67843933"
---
# <a name="breaking-changes-for-powershell-60"></a>PowerShell 6,0 için son değişiklikler

## <a name="features-no-longer-available-in-powershell-core"></a>PowerShell Core 'da artık kullanılamayan özellikler

### <a name="powershell-workflow"></a>PowerShell iş akışı

[PowerShell Iş akışı][workflow] , Windows PowerShell 'de, uzun süreli veya paralel görevler için sağlam runbook 'ların oluşturulmasına izin veren [Windows Workflow Foundation (WF)][workflow-foundation] üzerinde derleme yapan bir özelliktir.

.NET Core 'daki Windows Workflow Foundation desteğinin olmamasından dolayı PowerShell Core 'da PowerShell Iş akışını desteklemeye devam eteceğiz.

Gelecekte PowerShell Iş akışına gerek olmadan PowerShell dilinde yerel paralellik/eşzamanlılık özelliğini etkinleştirmek istiyoruz.

[workflow]: https://docs.microsoft.com/powershell/scripting/core-powershell/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Özel ek bileşenler

PowerShell [ek bileşenleri][snapin] , PowerShell topluluğunda geniş kapsamlı benimseme gerektirmeyen PowerShell modüllerine yönelik bir öncülü vardır.

Ek bileşenlerin, topluluk içindeki kullanım eksikliğinden ve bu kullanıcıların topluluk içindeki kullanım eksikliğinden dolayı artık PowerShell Core 'da özel ek bileşenleri desteklemiyoruz.

Günümüzde, Windows ve Windows `ActiveDirectory` Server `DnsClient` 'daki ve modülleri bu şekilde kesilir.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>WMI v1 cmdlet 'leri

İki WMI tabanlı modül kümesini destekleme karmaşıklığı nedeniyle, WMI v1 cmdlet 'lerini PowerShell Core 'dan kaldırdık:

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

Bunun yerine, yeni işlevlerle aynı işlevselliği ve yeniden tasarlanan bir sözdizimi sağlayan CıM (diğer adıyla WMI v2) cmdlet 'lerini kullanmanızı öneririz:

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

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft. PowerShell. LocalAccounts

Desteklenmeyen API 'lerin kullanılması nedeniyle, `Microsoft.PowerShell.LocalAccounts` daha iyi bir çözüm bulunana kadar PowerShell Core 'dan kaldırılmıştır.

### <a name="-computer-cmdlets"></a>`*-Computer`öğelerini

Desteklenmeyen API 'lerin kullanılması nedeniyle, daha iyi bir çözüm bulunana kadar aşağıdaki cmdlet 'ler PowerShell çekirdekden kaldırılmıştır.

- Add-Computer
- Checkpoint-Computer
- Remove-Computer
- Geri yükleme-bilgisayar

### <a name="-counter-cmdlets"></a>`*-Counter`öğelerini

Desteklenmeyen API `*-Counter` 'lerin kullanılması nedeniyle, daha iyi bir çözüm bulunana kadar PowerShell Core 'dan kaldırılmıştır.

### <a name="-eventlog-cmdlets"></a>`*-EventLog`öğelerini

Desteklenmeyen API `*-EventLog` 'lerin kullanılması nedeniyle, PowerShell Core 'dan kaldırılmıştır. daha iyi bir çözüm bulunana kadar. `Get-WinEvent`ve `Create-WinEvent` Windows 'da olayları almak ve oluşturmak için kullanılabilir.

## <a name="enginelanguage-changes"></a>Motor/dil değişiklikleri

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>`powershell.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101) olarak `pwsh.exe` yeniden adlandır

Kullanıcılara PowerShell Core 'u Windows üzerinde (Windows PowerShell 'in aksine) çağırmak için belirleyici bir yöntem sağlamak üzere, PowerShell Core ikilisi Windows ve `pwsh.exe` `pwsh` Windows dışı platformlarda olarak değiştirilmiştir.

Kısaltılmış ad, Windows dışı platformlarda kabukların adlandırılmasıyla de tutarlıdır.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>Çıktıya satır sonları eklemeyin (tablolar hariç) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Daha önce, çıkış konsolun genişliğine hizalanır ve konsolun bitiş genişliğine göre satır sonları eklenmiştir, bu da terminalin yeniden boyutlandırılması durumunda çıktının beklendiği gibi yeniden biçimlendirilmediği anlamına gelir. Sütunları hizalı tutmak için satır sonları gerekli olduğundan bu değişiklik tablolara uygulanmadı.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>Değer türü öğe türü olan koleksiyonlar için null öğe denetimini atlayın [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

`Mandatory` Parametresi`ValidateNotNull` ve öznitelikleriiçin,koleksiyonunöğetürüdeğertüründeisenullöğedenetiminiatlayın.`ValidateNotNullOrEmpty`

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>ASCII `$OutputEncoding` [#5369](https://github.com/PowerShell/PowerShell/issues/5369) yerine `UTF-8 NoBOM` kodlamayı kullanacak şekilde değiştirin

Önceki kodlama, ASCII (7 bit), bazı durumlarda çıkışın yanlış şekilde değişmeye neden olur. Bu değişiklik varsayılan hale `UTF-8 NoBOM` gelir, ancak çoğu araç ve işletim sistemi tarafından desteklenen bir kodlama ile Unicode çıktısını korur.

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>En `AllScope` çok varsayılan diğer adlarla Kaldır [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

Kapsam oluşturmayı hızlandırmak için, `AllScope` en çok varsayılan diğer adlarla kaldırılmıştır. `AllScope`aramanın daha hızlı olduğu bazı sık kullanılan diğer adlar için ayrılmıştı.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose`artık geçersiz `$ErrorActionPreference` kılınmayacak [#5113](https://github.com/PowerShell/PowerShell/issues/5113) `-Debug`

Daha önce, `-Verbose` veya `-Debug` belirtilmişse davranışının `$ErrorActionPreference`üzerine gelin. Bu değişiklik `-Verbose` `-Debug` ile artıkdavranışınıetkilemez.`$ErrorActionPreference`

## <a name="cmdlet-changes"></a>Cmdlet değişiklikleri

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>Invoke-RestMethod hiçbir veri döndürülmediğinde yararlı bilgiler döndürmez. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

Bir API yalnızca `null`döndürdüğü zaman Invoke-RestMethod bunun yerine `$null`dize `"null"` olarak serileştiriliydi. Bu değişiklik, ' deki geçerli `Invoke-RestMethod` tek değerli JSON `null` sabit `$null`değerini doğru şekilde serileştirmek için içindeki mantığı düzeltir.

### <a name="remove--protocol-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>Cmdlet `-Protocol` 'lerden `*-Computer` Kaldır [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

Corefx 'te RPC uzaktan iletişim sorunları (özellikle Windows dışı platformlarda) ve PowerShell 'de tutarlı bir uzaktan iletişim deneyimi sağlamak nedeniyle, `-Protocol` parametre `\*-Computer` cmdlet 'lerden kaldırılmıştır. Uzaktan erişim için DCOM artık desteklenmiyor. Aşağıdaki cmdlet 'ler yalnızca WSMAN uzaktan iletişimini destekler:

- Yeniden adlandır-bilgisayar
- Restart-Computer
- Bilgisayarı durdur

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>Cmdlet `-ComputerName` 'lerden `*-Service` Kaldır [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

PSRP 'nin tutarlı kullanımını teşvik etmek için, `-ComputerName` parametresi cmdlet 'lerden `*-Service` kaldırılmıştır.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>Hata `Get-Item -LiteralPath a*b` döndürmek `a*b` için gerçekten yoksa, bu hatayı düzeltir [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

Daha önce `-LiteralPath` , bir joker karakter buna benzer şekilde `-Path` davranır ve joker karakter dosya buluyorsa sessizce çıkış olur. Doğru davranış, dosya yoksa `-LiteralPath` hata olması için değişmez değer olmalıdır. Değişiklik, kullanılan `-Literal` joker karakterleri değişmez değer olarak değerlendirilir.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>`Import-Csv`CSV [#5134](https://github.com/PowerShell/PowerShell/issues/5134) tür bilgisi mevcut olduğunda içeri aktarma sırasındauygulanmalıdır`PSTypeNames`

Daha önce, ile `Export-CSV` `TypeInformation` `ConvertFrom-Csv` içeri aktarılan ile kullanılarak aktarılan nesneler tür bilgilerini saklamadı. Bu değişiklik CSV dosyasından kullanılabiliyorsa, tür `PSTypeNames` bilgilerini üyeye ekler.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`-NoTypeInformation``Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131) varsayılan olmalıdır

Bu değişiklik, tür bilgilerini dahil etmek için varsayılan davranış olan `Export-CSV` müşteri geri bildirimlerine yönelik olarak bildirimde bulunuldu.

Daha önce cmdlet 'i nesnenin tür adını içeren ilk satır olarak bir yorum çıktısı verebilir. Bu değişiklik, çoğu araç tarafından anlaşılmadığından varsayılan olarak bunu göstermez. Önceki `-IncludeTypeInformation` davranışı sürdürmek için kullanın.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>Şifrelenmemiş bağlantılar üzerinden gönderildiğinde Web `-Credential` cmdlet 'leri uyarmalıdır [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

HTTP kullanırken, parolalar dahil içerik şifresiz metin olarak gönderilir. Bu değişiklik, varsayılan olarak buna izin verilmez ve kimlik bilgileri güvenli olmayan bir şekilde geçiriliyorsa bir hata döndürür. Kullanıcılar, `-AllowUnencryptedAuthentication` anahtarı kullanarak bunu atlayabilir.

## <a name="api-changes"></a>API değişiklikleri

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>Sınıf `AddTypeCommandBase` [#5407](https://github.com/PowerShell/PowerShell/issues/5407) kaldır

Sınıfı `AddTypeCommandBase` , performansı artırmak için `Add-Type` sürümünden kaldırılmıştır. Bu sınıf yalnızca Add-Type cmdlet 'i tarafından kullanılır ve kullanıcıları etkilememelidir.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>Cmdlet 'i `-Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080) türü `System.Text.Encoding` olacak şekilde bütünleştirme

`-Encoding` Değer`Byte` , dosya sistemi sağlayıcısı cmdlet 'lerinden kaldırılmıştır. Artık yeni bir parametre `-AsByteStream`, bir bayt akışının giriş olarak gerekli olduğunu veya çıktının bir bayt akışı olduğunu belirtmek için kullanılır.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>Boş ve null `-UFormat` parametresi için daha iyi hata iletisi ekleyin [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

Daha önce, boş bir biçim dizesi `-UFormat`' a geçirilirken, faydalı olmayan bir hata iletisi görüntülenir. Daha açıklayıcı bir hata eklendi.

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>Konsol kodunu Temizleme [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

Aşağıdaki özellikler PowerShell Core 'da desteklenmediğinden kaldırılmıştır ve Windows PowerShell için eski nedenlerden dolayı destek eklemek için herhangi bir plan yoktur: `-psconsolefile` anahtar ve kod, `-importsystemmodules` anahtar ve kod ve yazı tipi değiştirme kodu.

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>Destek `RunspaceConfiguration` [#4942](https://github.com/PowerShell/PowerShell/issues/4942) kaldırıldı

Daha önce, API 'yi kullanarak program aracılığıyla bir PowerShell çalışma alanı oluştururken, eski [`RunspaceConfiguration`][runspaceconfig] veya daha yeni bir sürümünü [`InitialSessionState`][iss]kullanabilirsiniz. Bu değişiklik `RunspaceConfiguration` , ve yalnızca desteğini destekler `InitialSessionState`.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript`bağımsız değişkenleri `$input` [](https://github.com/PowerShell/PowerShell/issues/4923) #4923 `$args` yerine bağlama

Parametrenin yanlış konumu, bağımsız değişkenler yerine giriş olarak geçirilen bağımsız değişkenler ile sonuçlandı.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>Desteklenmeyen `-showwindow` [anahtarı #4903](https://github.com/PowerShell/PowerShell/issues/4903) Kaldır `Get-Help`

`-showwindow`CoreCLR 'de desteklenmeyen WPF kullanır.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>`Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866) için kayıt defteri yolunda * kullanılmasına izin ver

Daha önce `-LiteralPath` , bir joker karakter buna benzer şekilde `-Path` davranır ve joker karakter dosya buluyorsa sessizce çıkış olur. Doğru davranış, dosya yoksa `-LiteralPath` hata olması için değişmez değer olmalıdır. Değişiklik, kullanılan `-Literal` joker karakterleri değişmez değer olarak değerlendirilir.

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>Başarısız `Set-Service` test [#4802](https://github.com/PowerShell/PowerShell/issues/4802) düzeltmesini düzeltir

Daha önce kullanıldıysa, `foo` yoksayıldı ve hizmet bir varsayılan başlangıç türüyle oluşturulmuştur. `New-Service -StartupType foo` Bu değişiklik, geçersiz bir başlangıç türü için açıkça bir hata oluşturmak için kullanılır.

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>`$IsOSX` [#4700](https://github.com/PowerShell/PowerShell/issues/4700) olarak `$IsMacOS` yeniden adlandır

PowerShell 'deki adlandırma, adlandırma ve Apple 'ın OSX yerine macOS kullanımı ile uyumlu olmalıdır. Bununla birlikte, okunabilirlik ve sürekli olarak Pascal büyük küçük harfe yaklaşıyoruz.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>Geçersiz bağımsız değişken geçirildiğinde daha iyi bir hata olduğunda hata iletisinin tutarlı olmasını sağlayın [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

UNIX kurallarıyla hizalamak `pwsh.exe` için çıkış kodlarını değiştirme

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>Ve cmdlet 'leri modüllerden `Diagnostics`kaldırma. `LocalAccount` [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

Desteklenmeyen API 'ler `LocalAccounts` nedeniyle modül `Counter` ve `Diagnostics` modüldeki cmdlet 'ler daha iyi bir çözüm bulunana kadar kaldırılmıştır.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>PowerShell betiği bool parametresiyle yürütülemedi [#4036](https://github.com/PowerShell/PowerShell/issues/4036) çalışmıyor

Daha önce, bir `-File` PowerShell betiğini çalıştırmak için **PowerShell. exe** ' yi (şimdi **pwsh. exe**) kullanarak, parametre değerleri `$true` olarak geçirilecek / `$false` hiçbir yöntem sağlanmaz. Parametrelereayrıştırılmışdeğerlerolarakdestekeklendi.`$true` / `$false` Şu anda belgelenmiş sözdizimi çalışmamakta olduğundan anahtar değerleri de desteklenir.

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>Özelliği #4027 Kaldır `ClrVersion` `$PSVersionTable` [](https://github.com/PowerShell/PowerShell/issues/4027)

`ClrVersion` Özelliği CoreCLRileyararlıdeğildir,sonkullanıcılarbudeğeriuyumluluğu`$PSVersionTable` belirlemede kullanmamalıdır.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>`powershell.exe` Konumundan #4019`-Command`konum parametresini [](https://github.com/PowerShell/PowerShell/issues/4019) Değiştir `-File`

Windows dışı platformlarda PowerShell 'in el ile kullanımını etkinleştirin. Bu, UNIX tabanlı sistemlerde, açıkça `pwsh`çağırmak yerine PowerShell 'i otomatik olarak çağırabilecek bir betik çalıştırılabilir hale getirebilirsiniz. Bu, artık ya `powershell foo.ps1` `powershell fooScript` da belirtmeksizin `-File`gibi işlemleri yapabileceğiniz anlamına gelir. Bununla birlikte, bu değişiklik artık, gibi `-c` `powershell.exe Get-Command`işlemleri açıkça belirtmenizi `-Command` veya ne zaman yapmaya gerek duymanız gerekir.

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>Unicode kaçış ayrıştırma [#3958](https://github.com/PowerShell/PowerShell/issues/3958) uygulama

`` `u####``ya `` `u{####}`` da karşılık gelen Unicode karaktere dönüştürüldü. Bir sabit değere `` `u``çıkış yapmak için, geri değer: ``` ``u```' i kaçış:.

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>Kodlamayı `New-ModuleManifest` Windows dışı `UTF8NoBOM` platformlarda olarak değiştirin [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

Daha önce `New-ModuleManifest` , Linux araçları için bir sorun oluşturarak psd1 bildirimlerini, bom ile UTF-16 içinde oluşturur. Bu son değişiklik, ' nin `New-ModuleManifest` kodlamasını Windows olmayan platformlarda UTF (BOM yok) olarak değiştirir.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>Çözümlemeyin 'e (#1875) yineleme yapılmasını engelleyin `Get-ChildItem` . [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Bu değişiklik, `Get-ChildItem` Unix `ls -r` ve Windows `dir /s` Native komutlarıyla daha fazla bilgi sunar. Belirtilen komutlar gibi cmdlet, özyineleme sırasında bulunan dizinlere yönelik sembolik bağlantıları görüntüler, ancak bunlarla aynı değildir.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>Döndürülen `Get-Content -Delimiter` satırlarda sınırlayıcıyı dahil etmek için düzeltilir [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Daha önce, kullanırken `Get-Content -Delimiter` çıktı, sınırlandırıcının kaldırılması için verilerin daha fazla işlenmesini gerektirdiğinden tutarsızdı ve uygun değildir. Bu değişiklik döndürülen satırlardaki sınırlayıcıları kaldırır.

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320) biçim-onaltılık uygulama

`-Raw` Parametresi artık "No-Op" (hiçbir şey yapmaz) olur. Tüm çıktının ileri doğru olması, türünün tüm baytlarını içeren sayıların gerçek bir gösterimiyle görüntülenir (Bu değişiklikten önce `-Raw` parametrenin resmi olarak yaptığı şey).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>Varsayılan kabuk olarak PowerShell komut dosyası komutuyla çalışmaz [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

UNIX üzerinde, kabukların etkileşimli bir kabuğu kabul `-i` etmesi ve birçok araç bu davranışı beklediği (`script` Örneğin, PowerShell 'i varsayılan kabuk olarak ayarlarken) ve kabuğu `-i` anahtarla çağıran bir kuraldır. Bu değişiklik, daha önce de `-i` eşleşmesi `-inputformat`gereken `-in`kısa bir süre olarak kullanılabilecek bir parçadır.

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Get-ComputerInfo özellik adında typo onarımı [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber`yanlış yazıldı `BiosSeralNumber` ve doğru yazımla değiştirilmiştir.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>Ve `Get-StringHash` cmdlet`Get-FileHash` 'leri ekleme [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Bu değişiklik, bazı karma algoritmaların CoreFX tarafından desteklenmediği, bu nedenle artık kullanılabilir olmalarıdır:

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>$Null bir hata `Get-*` yerine tüm nesneleri döndüren cmdlet 'lerde doğrulama ekleyin [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

Aşağıdakilerden `$null` herhangi birine geçirilmesi bir hata oluşturur:

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

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a>`Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482) destek W3C Genişletilmiş günlük dosyası biçimi ekleme

Daha önce `Import-Csv` cmdlet 'i, günlük dosyalarını doğrudan W3C Genişletilmiş günlük biçiminde içeri aktarmak için kullanılamaz ve ek eylem gerekli olacaktır. Bu değişiklik ile W3C Genişletilmiş günlük biçimi desteklenir.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>PS işlevlerinde parametre bağlama `ValueFromRemainingArguments` sorunu [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments`Şimdi değerleri bir dizi olan tek bir değer yerine dizi olarak döndürür.

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>`BuildVersion``$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415) kaldırılır

`BuildVersion` Özelliğini öğesinden`$PSVersionTable`kaldırın. Bu özellik Windows Build sürümüne bağlı. Bunun yerine, PowerShell Core 'un derleme `GitCommitId` sürümünü tam olarak almak için kullanmanızı öneririz.

### <a name="changes-to-web-cmdlets"></a>Web cmdlet 'Lerinde yapılan değişiklikler

Web cmdlet 'lerinin temel alınan .NET API 'SI olarak `System.Net.Http.HttpClient`değiştirilmiştir. Bu değişiklik birçok avantaj sağlar. Ancak, bu değişiklik, Internet Explorer ile birlikte çalışabilirliğin yanı sıra ve `Invoke-WebRequest` `Invoke-RestMethod`içindeki çeşitli önemli değişikliklere neden oldu.

- `Invoke-WebRequest`Artık yalnızca temel HTML ayrıştırmasını desteklemektedir. `Invoke-WebRequest`her zaman bir `BasicHtmlWebResponseObject` nesne döndürür. `ParsedHtml` Ve`Forms` özellikleri kaldırılmıştır.
- `BasicHtmlWebResponseObject.Headers`değerler artık `String[]` `String`yerine.
- `BasicHtmlWebResponseObject.BaseResponse`Artık bir `System.Net.Http.HttpResponseMessage` nesnedir.
- Web cmdlet özel durumlarının `System.Net.Http.HttpResponseMessage` özelliğiartıkbirnesnedir.`Response`
- Katı RFC üstbilgi ayrıştırma artık `-Headers` ve `-UserAgent` parametresi için varsayılandır. Bu, ile `-SkipHeaderValidation`atlanabilir.
- `file://`ve `ftp://` URI şemaları artık desteklenmiyor.
- `System.Net.ServicePointManager`ayarlar artık kabul edilemez.
- Şu anda macOS 'ta sertifika tabanlı kimlik doğrulaması yok.
- URI`http://` üzerinden kullanılması hataya neden olur. `-Credential` Bir `https://` URI kullanın veya hatayı bastırmak `-AllowUnencryptedAuthentication` için parametresini sağlayın.
- `-MaximumRedirection`Şimdi yeniden yönlendirme denemeleri, son yeniden yönlendirmenin sonuçlarını döndürmek yerine, belirtilen limiti aştığında bir sonlandırma hatası veriyor.
