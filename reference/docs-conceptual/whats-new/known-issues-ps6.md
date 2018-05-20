---
ms.date: 05/17/2018
keywords: PowerShell, çekirdek
title: PowerShell 6.0 için bilinen sorunlar
ms.openlocfilehash: 6ad1bcaf1de06f204b57eb8ce23b3053ba4a5b38
ms.sourcegitcommit: 2d9cf1ccb9a653db7726a408ebcb65530dcb1522
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2018
---
# <a name="known-issues-for-powershell-60"></a>PowerShell 6.0 için bilinen sorunlar

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a>PowerShell Windows olmayan platformlarında için bilinen sorunlar

Linux ve macOS PowerShell alfa sürümleri çoğunlukla işlevseldir, ancak bazı önemli sınırlamalar ve kullanılabilirlik sorunları vardır. Linux üzerinde PowerShell Beta serbest bırakır ve macOS daha işlevsel ve alfa sürümler, daha sağlam ancak hala bazı özellikler kümesi eksik ve hataları içerebilir. Bazı durumlarda bu, yalnızca sabit henüz yapmadıysanız hatalar sorunlardır. Diğer durumlarda (olduğu gibi varsayılan diğer adlar ls, cp, vb.), geri bildirim için vermiyoruz seçenekleri ile ilgili topluluktan arıyoruz.

Not: pek çok temel alınan alt sistemleri benzerlikler nedeniyle, Linux ve macOS PowerShell eğilimindedir olgunluk özellikler ve hatalar aynı düzeyde paylaşmak için. Aşağıda belirtildiği gibi bu bölümdeki konular, her iki işletim sistemleri için geçerli dışında.

### <a name="case-sensitivity-in-powershell"></a>PowerShell'de duyarlılık

Geçmişten beri PowerShell birkaç istisna dışında aynı şekilde duyarlı olmuştur. UNIX benzeri işletim sistemlerinde, dosya sisteminin standart PowerShell aynılarını ve dosya sistemi daha küçük harf duyarlıdır; Bu, çeşitli yollarla, açık ve belirgin olmayan sunulur.

#### <a name="directly"></a>doğrudan

- Bir dosya PowerShell'de belirtirken, doğru durumda kullanılması gerekir.

#### <a name="indirectly"></a>Dolaylı olarak

- Varsa bir modülünü yüklemek bir komut dosyası çalıştığında ve modül yüklemesi başarısız olur modül adı doğru ortası değil. Modül tarafından başvurulan adı gerçek dosya adı eşleşmiyorsa bu varolan komut dosyaları ile ilgili bir sorun neden olabilir.
- Sekme tamamlama değil otomatik tamamlama dosya adı yanlış durumda olur. Tamamlamak için parça düzgün ortası gerekir. (Tamamlama türü adı ve türü üye tamamlamalar için büyük küçük harfe duyarlıdır.)

### <a name="ps1-file-extensions"></a>. PS1 Dosya uzantıları

PowerShell komut dosyalarını bitmelidir `.ps1` yorumlayıcı yüklemek ve geçerli işlemde çalıştırmak nasıl anlamak için. Geçerli işlemde komut dosyaları çalıştırmak beklenen normal PowerShell davranıştır. `#!` Sihirli sayı olmayan bir komut dosyasına eklenmiş bir `.ps1` uzantısı, ancak bu komut dosyasının çalışmasını nesneleri alışverişi olduğunda engelliyor yeni bir PowerShell örneği çalıştırılacak komut dosyasını neden olur. (Not: Bu arzu davranışı bir PowerShell komut dosyasından yürütülürken olabilir `bash` veya başka bir kabuk.)

### <a name="missing-command-aliases"></a>Eksik komut diğer adları

Linux/macOS, "kolaylık sağlamak için diğer adlar" temel komutları üzerinde `ls`, `cp`, `mv`, `rm`, `cat`, `man`, `mount`, `ps` kaldırıldı. Windows PowerShell kullanım kolaylığı için Linux komut adları Eşle diğer adlar kümesi sağlar. Bu diğer adları Linux/macOS dağıtımları, bir yol belirtmeden çalıştırılmak üzere yerel yürütülebilir izin verme varsayılan PowerShell kaldırılmıştır.

Artıları ve eksileri Bunu yapmak için vardır. Diğer adlar kaldırma PowerShell kullanıcıya yerel komutu deneyimi sunar, ancak yerel komutlar nesneleri yerine dizeleri döner Kabuğu'nda işlevselliği azaltır.

> [!NOTE]
> Bu, PowerShell ekibi geri bildirim için burada arıyor bir alandır.
> Tercih edilen bir çözüm nedir? Biz veya geri kolaylık diğer adlar ekleyin gibi bırakmanız gerekir? Bkz: [#929 sorun](https://github.com/PowerShell/PowerShell/issues/929).

### <a name="missing-wildcard-globbing-support"></a>Joker karakter (genelleme) destek eksik

Şu anda, PowerShell yalnızca joker karakter genişletmesi (genelleme) Windows'da yerleşik cmdlet'leri ve cmdlet Linux'ta yanı sıra dış komutları veya ikili dosyaları için yapar. Bir komutu gibi yani `ls
*.txt` dosya adlarını eşleştirmek için yıldız işareti genişletilmeyecek başarısız olur. Bu sorunu yaparak çalışabilirsiniz `ls (gci *.txt | % name)` veya daha basit bir şekilde `gci *.txt` PowerShell yerleşik eşdeğer kullanarak `ls`.

Bkz: [#954](https://github.com/PowerShell/PowerShell/issues/954) bize Linux/macOS üzerinde genelleme deneyimini iyileştirmek nasıl geribildirim vermek için.

### <a name="net-framework-vs-net-core-framework"></a>.NET framework vs .NET Core Framework

Linux/macOS üzerinde PowerShell, Microsoft Windows tam .NET Framework'ün bir alt .NET Core kullanır. PowerShell doğrudan erişim sağlayan temel framework türleri, yöntemleri, vb. önemli olmasıdır. Sonuç olarak, Windows üzerinde çalışan komut dosyaları Windows dışı platformlarda çerçeveleri farklılıkları nedeniyle çalışmayabilir. .NET Core Framework hakkında daha fazla bilgi için bkz: <https://dotnetfoundation.org/net-core>

Geliştirilirken [.NET standart 2.0](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/), .NET Core 2.0 birçok geleneksel türleri ve yöntemleri sunmak tam .NET Framework geri getirecek. Başka bir deyişle, PowerShell çekirdek değişiklik gerektirmeden çoğu geleneksel Windows PowerShell modülleri yüklemek mümkün olacaktır. Bizim .NET standart 2.0 ilgili iş izleyebilirsiniz [burada](https://github.com/PowerShell/PowerShell/projects/4).

### <a name="redirection-issues"></a>Yeniden yönlendirme sorunlarını

Giriş yeniden yönlendirme PowerShell içinde herhangi bir platformda desteklenmiyor.
[Sorunu #1629](https://github.com/PowerShell/PowerShell/issues/1629)

Kullanım `Get-Content` ardışık düzenine bir dosyanın içeriğini yazmak için.

Varsayılan UTF-8 Kodlaması kullanıldığında, yeniden yönlendirilen çıktı Unicode bayt sırası işareti (BOM) içerir. Ürün reçetesi olmasını bekliyor musunuz yardımcı programları ile çalışırken veya bir dosyaya sonuna ekleme sorunlara neden olur. Kullanım `-Encoding Ascii` (hangi olma Unicode, bir ürün reçetesi olmaz) ASCII metni yazmak için. (Not: bkz [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71) bize tüm platformlarda PowerShell çekirdek için kodlama deneyimini geliştirir üzerinde geribildirim vermek için. Biz UTF-8 desteği olmadan bir ürün reçetesi çalışma ve potansiyel olarak çeşitli cmdlet'leri kodlama Varsayılanları platformlarında değiştirme.)

### <a name="job-control"></a>İş denetimi

Linux/macOS üzerinde PowerShell'de iş denetimini desteği yoktur.
`fg` Ve `bg` komutları kullanılabilir değildir.

Kullanabileceğiniz anda için [PowerShell işleri](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_jobs) , tüm platformlarda çalışma.

### <a name="remoting-support"></a>Remoting desteği

Şu anda, PowerShell çekirdek PowerShell uzaktan iletişim (PSRP) WSMan macOS ve Linux üzerinde temel kimlik doğrulaması ve NTLM tabanlı kimlik doğrulaması Linux'ta ile destekler. (Kerberos tabanlı kimlik doğrulama desteklenmiyor.)

WSMan tabanlı uzaktan iletişim için iş yapıldığını [psl OMI sağlayıcısı](https://github.com/PowerShell/psl-omi-provider) deposu.

PowerShell çekirdek, tüm platformlarda (Windows, macOS ve Linux) SSH üzerinden PowerShell uzaktan iletişim (PSRP) da destekler. Bu şu anda üretim desteklenmez, ancak bu ayarlama hakkında daha fazla bilgiyi [burada](../core-powershell/ssh-remoting-in-powershell-core.md).

### <a name="just-enough-administration-jea-support"></a>Yalnızca-yeterli-yönetim (JEA) desteği

Kısıtlanmış Yönetim (JEA) uzaktan iletişim uç noktaları oluşturma olanağı PowerShell Linux/macOS üzerinde şu anda kullanılabilir değil. Bu özellik şu anda 6.0 kapsamında değildir ve önemli tasarım çalışma gerektirdiği bir şey biz post 6.0 göz önüne alır.

### <a name="sudo-exec-and-powershell"></a>`sudo`, `exec`ve PowerShell

PowerShell (örneğin, Python veya Ruby) bellekte komutların çoğu çalıştığından, sudo doğrudan PowerShell öğelerin ile kullanamazsınız. (Doğal olarak, çalıştırabilirsiniz `powershell` sudo gelen.) Sudo ile Örneğin, PowerShell içinde bir PowerShell cmdlet'ini çalıştırmak gerekli değilse `sudo Set-Date 8/18/2016`, yapmayı tercih sonra `sudo powershell Set-Date 8/18/2016`. Benzer şekilde, exec yerleşik bir PowerShell doğrudan yükleyemezsiniz. Bunun yerine yapmak olurdu `exec powershell item_to_exec`.

Bu sorun şu anda #3232 bir parçası olarak izleniyor.

### <a name="missing-cmdlets"></a>Eksik cmdlet'leri

Çok sayıda PowerShell'de normalde kullanılabilir komutlar (cmdlet'leri) Linux/macOS üzerinde kullanılabilir değil. Çoğu durumda, bu komutları yok (örn. Windows özgü özellikler kayıt defteri gibi) bu platformlardaki anlamlı. Hizmet denetimi komutları (Get/başlangıç/Stop-Service) sunulan gibi diğer komutlar ancak çalışmıyor. Gelecek sürümlerde bozuk cmdlet'leri düzeltme ve zaman içinde yeni bir tane ekleyerek bu sorunları düzeltmek üzere kullanılabilir.

### <a name="command-availability"></a>Komut kullanılabilirliği

Aşağıdaki tabloda Linux/macOS üzerinde PowerShell'de çalışmıyor bilinen komutları listeler.

<table>
<th>Komutlar</th><th>İşlemsel durumu</th><th>Notlar</th>
<tr>
<td>Get-Service, yeni hizmet, hizmetini yeniden başlatın, Resume-hizmet, hizmet belirleme, Start-Service, Hizmeti Durdur, askıya alma hizmeti
<td>Kullanılamaz.
<td>Bu komutlar tanınan değil. Bu, bir sonraki sürümde düzeltilmelidir.
</tr>
<tr>
<td>Get-Acl, Set-Acl
<td>Kullanılamaz.
<td>Bu komutlar tanınan değil. Bu, bir sonraki sürümde düzeltilmelidir.
</tr>
<tr>
<td>Get-AuthenticodeSignature, Set-AuthenticodeSignature
<td>Kullanılamaz.
<td>Bu komutlar tanınan değil. Bu, bir sonraki sürümde düzeltilmelidir.
</tr>
<tr>
<td>Bekleme işlemi
<td>Kullanılabilir, düzgün çalışmıyor. <td>Örneğin `Start-Process gvim -PassThru | Wait-Process` işe yaramazsa; işlemin tamamlanmasını beklemek başarısız olur.
</tr>
<tr>
<td>Register-PSSessionConfiguration, Unregister-PSSessionConfiguration, Get-PSSessionConfiguration
<td>Kullanılabilir ancak işe yaramaz.
<td>Komutları çalışmıyor belirten bir hata iletisi yazar. Bu, bir sonraki sürümde düzeltilmelidir.
</tr>
<tr>
<td>Get-olay, yeni bir olay, Register-EngineEvent, Register-WmiEvent, Remove-olay kaydı olay
<td>Kullanılabilir, ancak hiçbir olay kaynakları kullanılabilir.
<td>PowerShell olay komutları var ancak komutlarını (örneğin, System.Timers.Timer) ile kullanılan olay kaynakları çoğunu komutları alfa sürümdeki gereksiz yapmadan Linux üzerinde kullanılabilir değil.
</tr>
<tr>
<td>Set-ExecutionPolicy
<td>Kullanılabilir ancak işe yaramaz.
<td>Bu platformda desteklenmiyor iletisini döndürür. Yürütme, bir kullanıcı odaklı "güvenliği kullanıcı pahalı hataları yapmasını önlemeye yardımcı olacak bandı" ilkesidir. Bu bir güvenlik sınırı yoktur.
</tr>
<tr>
<td>Yeni-PSSessionOption, PSTransportOption yeni
<td>Kullanılabilir, ancak yeni PSSession çalışmıyor.
<td>Yeni PSSessionOption ve yeni PSTransportOption şu anda yeni PSSession çalışır, artık çalışmak için doğrulanmadı.
</tr>
</table>
