---
ms.date: 05/17/2018
keywords: PowerShell, çekirdek
title: PowerShell 6.0 için bilinen sorunlar
ms.openlocfilehash: 7fa6b9935ae75b62df72609b8a9ec16246b1c610
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893697"
---
# <a name="known-issues-for-powershell-60"></a>PowerShell 6.0 için bilinen sorunlar

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a>PowerShell Windows dışı platformlarda için bilinen sorunlar

Linux ve Macos'ta PowerShell alfa sürümleri çoğunlukla işlevsel ancak bazı önemli sınırlamalar ve kullanılabilirlik sorunlarını sahip değilsiniz. Linux'ta PowerShell beta sürümleri ve macOS daha işlevsel ve alfa sürümleri daha kararlı ancak yine de bazı özellikler kümesi eksik ve hataları içerebilir. Bazı durumlarda, bu, yalnızca sabit henüz yapmadıysanız hataları sorunlardır. Diğer durumlarda (olduğu gibi varsayılan takma adları ls, cp, vb.), geri bildirim için sunduğumuz seçenekler ile ilgili topluluğundan arıyoruz.

Not: birçok temel alt benzerlikler nedeniyle, Linux ve Macos'ta PowerShell eğilimli aynı hem özellikleri hem de hataları olgunluk düzeyini paylaşmak için. Aşağıda belirtildiği gibi bu bölümdeki konular, her iki işletim sistemlerine uygulanacak dışında.

### <a name="case-sensitivity-in-powershell"></a>Büyük küçük harf duyarlılığı PowerShell

Tarihsel olarak, PowerShell, birkaç özel durum dışında aynı şekilde duyarlı olmuştur. UNIX benzeri işletim sistemlerinde dosya sistemi ağırlıklı duyarlıdır ve PowerShell standart dosya sisteminin uyar; Bu, çeşitli yollarla, açık ve daha belirgin olmayan kullanıma sunulur.

#### <a name="directly"></a>Doğrudan

- Bir dosya PowerShell'de belirtirken, büyük/küçük kullanılması gerekir.

#### <a name="indirectly"></a>Dolaylı olarak

- Bir komut dosyası çalıştığında bir modül ve modülü yüklemek için adı sözcüklerden değil ve modül yükleme başarısız olur. Modül tarafından başvurulan ad gerçek dosya adı eşleşmiyorsa bu mevcut betikleri ile ilgili bir sorun neden olabilir.
- Sekme tamamlama değil otomatik tamamlama dosya adı yanlış bir durumda olacaktır. Parça tamamlamak için doğru büyük küçük harfleri gerekir. (Tamamlama, tür adı ve tür üyesi tamamlamaları için büyük küçük harfe duyarlıdır.)

### <a name="ps1-file-extensions"></a>. PS1 Dosya uzantıları

PowerShell betikleri bitmelidir `.ps1` için yorumlayıcıya yüklemek ve bunları geçerli işlemde çalışan öğrenin. Geçerli işlemde betikleri çalıştırma beklenen normal PowerShell davranışıdır. `#!` Sihirli sayı olmayan bir betiğe eklenebilir bir `.ps1` uzantısı, ancak bu komut dosyasının çalışmasını nesneleri değişiminin olduğunda engelliyor yeni bir PowerShell örneğinde çalıştırılacak betik neden olur. (Not: Bu bir PowerShell betiğini yürütme zaman istenen davranış olabilir `bash` veya başka bir kabuk.)

### <a name="missing-command-aliases"></a>Eksik komut diğer adları

Linux/macos'ta, temel komutlar için "kolaylık aliases" `ls`, `cp`, `mv`, `rm`, `cat`, `man`, `mount`, `ps` kaldırıldı. Windows üzerinde PowerShell, kullanıcı dostu Linux komut adlarını eşleyen adlar sunmaktadır. ' % S'varsayılan PowerShell yerel yürütülebilir bir yol belirtmeden çalıştırılacak izin vererek Linux/macOS dağıtımlarında, bu diğer adlar kaldırıldı.

Ve bunu yapmak için dezavantajları vardır. Diğer adlar kaldırma PowerShell kullanıcıya yerel komut deneyimi sunar, ancak yerel komutların yerine nesneleri dizeleri döndürdüğünden Kabuğu'nda işlevselliği azaltır.

> [!NOTE]
> Bu, burada PowerShell ekibi için geri bildirim arıyor bir alandır.
> Tercih edilen bir çözüm nedir? Biz, bunu geri kolaylık diğer ad eklemek veya bırakmanız gerekir? Bkz: [#929 sorun](https://github.com/PowerShell/PowerShell/issues/929).

### <a name="missing-wildcard-globbing-support"></a>Joker karakter (Glob) desteği yok

Şu anda PowerShell yalnızca joker karakter genişletmesi (Glob) yerleşik Cmdlet'lerde Windows ve Linux'ta cmdlet'lerinin yanı sıra dış komutları veya ikili dosyaları desteklemez. Bir komutu gibi yani `ls
*.txt` dosya adlarını eşleştirmek için yıldız işareti genişletilmeyecek nedeniyle başarısız olur. Bu sorunu yaparak çalışabilir `ls (gci *.txt | % name)` veya daha basit `gci *.txt` PowerShell yerleşik eşdeğerini kullanarak `ls`.

Bkz: [#954](https://github.com/PowerShell/PowerShell/issues/954) bize Linus/macos'ta Glob deneyimini geliştirmeye ilişkin geri bildirimler verebilirsiniz.

### <a name="net-framework-vs-net-core-framework"></a>.NET framework ve .NET Core Framework

Linux/macos'ta PowerShell, Microsoft Windows üzerinde tam .NET Framework'ün bir alt kümesi olan bir .NET Core kullanır. PowerShell, doğrudan erişim sağlar. temel alınan framework türleri, yöntemleri, vb. önemli olmasıdır. Sonuç olarak, Windows üzerinde çalışan komut dosyaları Windows dışı platformlarda çerçeveleri farklılıkları nedeniyle çalışmayabilir. .NET Core Framework hakkında daha fazla bilgi için bkz. <https://dotnetfoundation.org/net-core>

Geliştirilirken [.NET Standard2.0](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/), .NET Core 2.0 duruma getirmek arka tam .NET Framework birçok geleneksel türleri ve yöntemleri sunar. Başka bir deyişle, PowerShell Core yapmadan çok sayıda geleneksel Windows PowerShell modülü yüklemek mümkün olacaktır. .NET Standard 2.0 ilgili işimizi izleyebilirsiniz [burada](https://github.com/PowerShell/PowerShell/projects/4).

### <a name="redirection-issues"></a>Yeniden yönlendirme sorunları

Giriş yeniden yönlendirme PowerShell'de herhangi bir platformda desteklenmiyor.
[Sorun #1629](https://github.com/PowerShell/PowerShell/issues/1629)

Kullanım `Get-Content` ardışık düzene bir dosyanın içeriğini yazma.

Varsayılan UTF-8 Kodlaması kullanıldığında yeniden yönlendirilen Çıkışı Unicode bayt sırası işareti (BOM) içerir. BOM beklemediğiniz yardımcı programları ile çalışırken veya bir dosyaya ekleme sorunlara neden olur. Kullanım `-Encoding Ascii` (hangi aşamasında Unicode bir BOM olmaz) ASCII metin yazmak için.

> [!Note]
> bkz: [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71) bize PowerShell Core için kodlama deneyimi tüm platformlarda geliştirmeye geri bildirimler verebilirsiniz. Biz UTF-8 içermeyen bir ürün reçetesi desteklemek üzere çalışma ve potansiyel olarak çeşitli cmdlet'ler için kodlama Varsayılanları platformlar arasında değiştirme.

### <a name="job-control"></a>İş denetimi

Linux/macos'ta PowerShell iş denetimi desteği yoktur.
`fg` Ve `bg` komutları kullanılabilir değil.

Şimdilik, kullanabilirsiniz [PowerShell işleri](/powershell/module/microsoft.powershell.core/about/about_jobs) , tüm platformlardaki iş yapın.

### <a name="remoting-support"></a>Uzak destek

Şu anda PowerShell Core PowerShell uzaktan iletişimini (PSRP) WSMan macOS ve Linux'ta temel kimlik doğrulaması ve NTLM tabanlı kimlik doğrulaması Linux'ta destekler. (Kerberos tabanlı kimlik doğrulaması desteklenmiyor.)

WSMan tabanlı uzaktan iletişim için iş yapıldığını [psl OMI sağlayıcısı](https://github.com/PowerShell/psl-omi-provider) depo.

PowerShell Core, tüm platformlar (Windows, macOS ve Linux) SSH üzerinden PowerShell uzaktan iletişimini (PSRP) da destekler. Bu şu anda üretim ortamında desteklenmez, ancak bu ayarlama hakkında daha fazla bilgi edinebilirsiniz [burada](../core-powershell/ssh-remoting-in-powershell-core.md).

### <a name="just-enough-administration-jea-support"></a>Just-yeterli-yönetim (JEA) desteği

Kısıtlı Yönetim (JEA) uzaktan iletişimi uç noktaları oluşturma özelliği, Linux/macos'ta PowerShell şu anda kullanılabilir değil. Bu özellik şu anda 6.0 için kapsamda değildir ve önemli tasarım iş gerektirdiği bir şeyi biz post 6.0 dikkate alacaktır.

### <a name="sudo-exec-and-powershell"></a>`sudo`, `exec`ve PowerShell

PowerShell (örneğin, Python veya Ruby) bellekte komutların çoğu çalıştığından, sudo ile yerleşik PowerShell olanları doğrudan kullanamazsınız. (Doğal olarak çalıştırabileceğiniz `powershell` sudo gelen.) Sudo ile Örneğin, PowerShell içinde bir PowerShell cmdlet'i çalıştırmak gerekli değilse `sudo `Set-tarih` 8/18/2016`, yaptığınız sonra `sudo powershell `Set-tarih` 8/18/2016`. Benzer şekilde, bir yerleşik PowerShell exec doğrudan yükleyemezsiniz. Bunun yerine yapmak zorunda olabilirsiniz `exec powershell item_to_exec`.

Bu sorun şu anda #3232 bir parçası olarak izleniyor.

### <a name="missing-cmdlets"></a>Eksik cmdlet'leri

PowerShell'de normalde kullanılabilir komutları (cmdlet'leri) çok sayıda Linux/Macos'ta kullanılabilir değil. Çoğu durumda, bu komutlar (örn. Windows özgü özellikler kayıt defteri gibi) bu platformlardaki Algı olun. Hizmet denetimi komutları (Get/başlangıç/Stop-Service) sunulan gibi diğer komutlar, ancak çalışmıyor. Gelecek sürümlerde bozuk cmdlet'leri düzeltme ve zaman içinde yeni bir tane ekleyerek bu sorunları düzeltebilirsiniz.

### <a name="command-availability"></a>Komut kullanılabilirliği

Aşağıdaki tabloda, Linux/macos'ta PowerShell çalışmıyor bilinen komutları listeler.

|Komutlar |İşlemsel durumu | Notlar|
|---------|------------------|------|
|`Get-Service`, `New-Service`, `Restart-Service`, `Resume-Service`, `Set-Service`, `Start-Service`, `Stop-Service`, `Suspend-Service`|Kullanılabilir değil.|Bu komutlar tanınmaz. Bu, gelecekteki bir sürümde düzeltilmelidir.|
|`Get-Acl`, `Set-Acl`|Kullanılamaz.|Bu komutlar tanınmaz. Bu, gelecekteki bir sürümde düzeltilmelidir.|
|`Get-AuthenticodeSignature`, `Set-AuthenticodeSignature`|Kullanılamaz.|Bu komutlar tanınmaz. Bu, gelecekteki bir sürümde düzeltilmelidir.|
|`Wait-Process`|Kullanılabilir, düzgün şekilde çalışmaz. |Örneğin ' işlemini başlat gvim - PassThru | Bekleme işlem içi çalışmaz; işlemin tamamlanmasını beklemek başarısız olur.|
|`Register-PSSessionConfiguration`, `Unregister-PSSessionConfiguration`, `Get-PSSessionConfiguration`|Kullanılabilir ancak çalışmaz.|Komutları çalışmıyor belirten bir hata iletisi yazar. Bu, gelecekteki bir sürümde düzeltilmelidir.|
|`Get-Event`, `New-Event`, `Register-EngineEvent`, `Register-WmiEvent`, `Remove-Event`, `Unregister-Event`|Kullanılabilir, ancak hiçbir olay kaynakları kullanılabilir.|PowerShell olay komutlarını var ancak çoğu komutlarını (örneğin, System.Timers.Timer) ile birlikte olay kaynakları komutları alfa sürümü gereksiz yapmadan Linux'ta kullanılabilir değildir.|
|`Set-ExecutionPolicy`|Kullanılabilir ancak çalışmaz.|Bu platformda desteklenmiyor iletisini döndürür. Yürütme, bir kullanıcı odaklı "güvenlik kullanıcı pahalı hataları yapmasını önlemeye yardımcı olur, bandı" ilkesidir. Bu bir güvenlik sınırı yoktur.|
|`New-PSSessionOption`, `New-PSTransportOption`|Kullanılabilir ancak `New-PSSession` çalışmaz.|`New-PSSessionOption` ve `New-PSTransportOption` şu anda, artık çalışmak için doğrulanmamış `New-PSSession` çalışır.|