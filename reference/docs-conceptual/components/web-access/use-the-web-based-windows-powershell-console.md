---
ms.date: 08/23/2017
keywords: PowerShell cmdlet'i
title: web tabanlı windows powershell konsolunu kullanma
ms.openlocfilehash: 2bb9c6ef486ef32012a15f9890997cf2fa6a3a0b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086654"
---
# <a name="use-the-web-based-windows-powershell-console"></a>Web tabanlı Windows PowerShell konsolunu kullanma

Güncelleme tarihi: 24 Haziran 2013

Uygulama hedefi: Windows Server 2012 R2, Windows Server 2012

Windows PowerShell Web erişimi güvenli bir Web sitesine oturum açmasına olanak tanır; bir uzak bilgisayarı yönetmek için Windows PowerShell oturumları, cmdlet'leri ve komut dosyaları'nı kullanmak için.

Windows PowerShell konsolu bir web tarayıcısında çalıştığından, çok çeşitli istemci cihazları açılabilir; neredeyse tüm cihazlara bir web tarayıcısı ile çalışır.

Web tabanlı Windows PowerShell konsolunda kullanıcı tarafından oturum açma işleminin bir parçası belirtilen bir uzak bilgisayar hedef alır.

Bu konuda, oturum açmanız ve Windows PowerShell Web erişimi web tabanlı konsolda kullanmaya başlamak açıklar.

Bu konu, Windows PowerShell kullanma veya cmdlet'leri veya betikleri çalıştırma açıklamaz.
Windows PowerShell ve komut dosyası oluşturma kaynakları kullanma hakkında daha fazla bilgi için bkz: [ayrıca](#see-also) bölümünde bu konunun sonunda.

## <a name="supported-browsers-and-client-devices"></a>Desteklenen tarayıcılar ve istemci cihazlar

Windows PowerShell Web erişimi, aşağıdaki Internet tarayıcılarını destekler.
Mobil tarayıcılar resmi olarak desteklemiyor olsa da, birçok web tabanlı Windows PowerShell konsolunu çalıştırmak mümkün olabilir.
Diğer tarayıcılarda tanımlama bilgileri, JavaScript çalıştıran ve HTTPS Web sitelerini çalıştıran iş, ancak bunlar resmi olarak beklenen kabul test.

### <a name="supported-desktop-computer-browsers"></a>Desteklenen masaüstü bilgisayar tarayıcıları

- Microsoft Windows 8.0, 9.0, 10.0 ve 11.0 için Windows Internet Explorer
- Mozilla Firefox 10.0.2
- Windows için Google Chrome 17.0.963.56m
- Windows için Apple Safari 5.1.2
- Mac OS için Apple Safari 5.1.2

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Minimumda test edilen mobil cihazlar veya tarayıcılar

- Windows Phone 7 ve 7.5
- Google Android WebKit 3.1 tarayıcısı Android 2.2.1 (Kernel 2.6)
- İPhone işletim sistemi 5.0.1 için Apple Safari
- İPad 2 işletim sistemi 5.0.1 için Apple Safari

### <a name="browser-requirements"></a>Tarayıcı gereksinimleri

Windows PowerShell Web erişimi web tabanlı konsolunu kullanmak için tarayıcılar aşağıdakileri yapmanız gerekir.

- Windows PowerShell Web erişimi ağ geçidi Web sitesinden tanımlama bilgilerine izin verin.
- Açın ve HTTPS sayfaları oku mümkün olmayacaktır.
- Açın ve JavaScript kullanan Web siteleri çalıştırın.

## <a name="signing-in-to-windows-powershell-web-access"></a>Windows PowerShell Web erişimi için oturum açma

Windows PowerShell Web erişimi yöneticinize kuruluşlar Windows PowerShell Web erişimi ağ geçidini sitenizin adresi bir URL sağlamanız gerekir.
Varsayılan olarak, bu Web sitesi adresidir *https://\<sunucu_adı\>/pswa*.

Windows PowerShell Web erişimi için oturum açmadan önce adı veya IP adresi, yönetmek istediğiniz uzak bilgisayarın sahip olduğunuzdan emin olun.
Uzak bilgisayarda yetkili bir kullanıcı olmalıdır ve Uzaktan yönetime izin verecek şekilde yapılandırılmalıdır.
Bilgisayarınızı uzaktan yönetime izin verecek şekilde yapılandırma hakkında daha fazla bilgi için bkz. [kullanım Windows PowerShell'de uzak komutları etkinleştirme ve](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting).

Bilgisayarınızı uzaktan yönetime izin verecek şekilde yapılandırmanın en basit yöntem çalıştırmaktır **Enable-PSRemoting - force** cmdlet'i ile açılmış bir Windows PowerShell oturumunda bilgisayarda yükseltilmiş kullanıcı haklarıyla (**Yönetici olarak çalıştır**).

### <a name="to-sign-in-to-windows-powershell-web-access"></a>Windows PowerShell Web erişimi için oturum açmak için

1. Windows PowerShell Web Erişimi Web sitesi, bir Internet tarayıcısı penceresi veya sekmesi açın.

1. Windows PowerShell Web erişimi oturum açma sayfasında, ağ kullanıcı adınızı, parolanızı ve yönetmek istediğiniz bilgisayarın (ve yetkili bir kullanıcı olduğunuz) adını sağlayın. Windows PowerShell Web Erişim Yöneticisi, bir bilgisayar adı yerine özel bir site veya proxy sunucusu için bir URI kullanılacak istedi, seçin **bağlantı URI'si** içinde **bağlantı türü** alan ve ardından bir URI sağlayın.

    > ![Not](images/Note.jpeg) **Not**:
    >
    > - Hedef bilgisayarın bir çalışma grubunda ise, kullanıcı adınızı sağlamak ve bilgisayara oturum açmak için aşağıdaki sözdizimini kullanın: `<workgroup_name>\<user_name>`
    > - Hedef bilgisayarın ağ geçidi sunucusu olup olmadığını belirtebilirsiniz `localhost` bilgisayar ad alanında
    > - Hedef bilgisayar ağ geçidi sunucusuysa ve ağ geçidi sunucusu bir çalışma grubundaysa, kullanmalısınız `<workgroup name>\<user_name>` Dosyalanan kullanıcı adı. Kullanabileceğiniz `localhost` bilgisayar ad alanında.

1. **İsteğe bağlı bağlantı ayarları** bölümü için yönetmek istediğiniz uzak bilgisayarın yetkilendirme gereksinimleriyle ilgilidir. İsteğe bağlı bağlantı ayarlarına eşdeğer parametreler hakkında daha fazla bilgi için bkz: [Enter-PSSession](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet Yardım.

    Genellikle, Windows PowerShell Web erişimi ağ geçidi üzerinden geçmek için kullandığınız kimlik bilgileri, yönetmek istediğiniz uzak bilgisayar tarafından tanınan aynıdır. Ancak, uzak bilgisayarı yönetmek için farklı kimlik bilgileri kullanmak istiyorsanız, 2. adımda belirttiğiniz, genişletme **isteğe bağlı bağlantı ayarları** bölümünde ve alternatif kimlik bilgilerini sağlayın. Aksi takdirde, 6. adıma atlayın.

1. Windows PowerShell Web erişimi yönetici Windows PowerShell Web erişimi kullanıcılar için bir özel oturum yapılandırması oluşturduysa, adını, oturum yapılandırma adı **yapılandırma adı** alan. Oturum yapılandırmaları hakkında daha fazla bilgi için bkz: [about_Session_Configurations](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Tutun **kimlik doğrulama türü** kümesine **varsayılan** , aksi takdirde Windows PowerShell Web Erişim Yöneticisi tarafından yapmak için verilmedikçe.

1. Tıklayın **oturum**.

## <a name="signing-out-and-timing-out"></a>Oturum kapatma ve zaman aşımına uğruyor

Aşağıdakilerden herhangi birini imzalar, web tabanlı Windows PowerShell oturumu dışında.

- Tıklayarak **oturumunuzu** konsolunun sağ alt köşedeki. (Yalnızca Windows Server 2012)

- Tıklayarak **Kaydet** veya **çıkış** alt sağ köşesindeki konsolunun (yalnızca Windows Server 2012 R2). Tıklayarak **Kaydet** kaydeder ve kapatır; Windows PowerShell Web erişimi oturumunuzu daha sonra oturuma bağlanabilirsiniz. Windows PowerShell Web erişimi için yeniden oturum açtığınızda, Windows PowerShell Web erişimi, kaydedilen oturumlarınızın bir listesini görüntüler; seçin kaydedilmiş bir oturuma yeniden bağlanmak veya yeni bir oturum başlatın. Kayıtlı ve etkin kullanıcıların verilen açık oturum sayısı, Ağ Geçidi Yöneticisi tarafından yapılandırılır.

    Tıklayarak **çıkış** kaydetmeden dışında Windows PowerShell Web erişimi oturum açar.

- Aynı tarayıcı oturumunda veya aynı tarayıcı oturumunun yeni bir sekmede farklı bir uzak bilgisayarı yönetmek oturum açmaya çalışmak. (Ağ geçidi sunucusu Windows Server 2012 R2 çalıştırıyorsa Bu geçerli değildir; Windows Server 2012 R2 üzerinde çalışan Windows PowerShell Web erişimi birden çok kullanıcı oturumuna yeni sekmelerde aynı tarayıcı oturumunda izin vermiyor.) Aynı bilgisayara birden fazla etkin oturum kullanma hakkında daha fazla bilgi için bkz: birden çok hedef bilgisayara aynı anda içinde bağlanma [web tabanlı konsol sınırlamaları](#limitations-of-the-web-based-console) bu konudaki.

- oturumda 20 dakika etkin olmama. Ağ Geçidi Yöneticisi, etkin olmama zaman aşımı süresini özelleştirebilir; Daha fazla bilgi için [oturum yönetimi](authorization-rules-and-security-features-of-windows-powershell-web-access.md#session-management).

    - Bir ağ hatası veya diğer planlanmamış kapatma veya hata nedeniyle bir oturumdan web tabanlı konsolda kesilir ve oturum kapatmadıkları kendiniz, Windows PowerShell Web Erişimi'ni çalıştırmak için oturumu devam hedefe bağlı istemci tarafı kesildiyse zaman aşımı süresi kadar bilgisayar. Varsayılan olarak, bu zaman aşımı süresi 20 dakikadır ve Ağ Geçidi Yöneticisi tarafından yapılandırılır. Oturumu sonra ya da varsayılan 20 dakika kesildiğinde veya Ağ Geçidi Yöneticisi tarafından belirtilen zaman aşımı süresi sonrasında, hangisi daha kısaysa.

        Ağ Geçidi sunucusu Windows Server 2012 R2 çalıştırıyorsa, Windows PowerShell Web erişimi kullanıcıların kaydedilmiş oturumlara daha sonra yeniden izin verir, ancak bakın veya ağ geçidi tarafından belirtilen zaman aşımı süresinden sonra yönetici sahip kadar kaydedilmiş oturumları yeniden onlara.

- Tarayıcı penceresini veya sekmesini kapatma.

- İstemci cihaz üzerinde tarayıcıda çalışan veya ağ bağlantısının kesilmesi kapatma.

- Çalışan **çıkış** web konsolunda komutu. Kendisine bağlı olduğunuz oturum yapılandırması desteklemek üzere yapılandırılmışsa, bu komut işe yaramazsa [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) modunda veya kısıtlanmış çalışma.

Yeniden oturum açmak istiyorsanız, Windows PowerShell Web erişimi web sayfasını yeniden açın ve oturum içindeki adımları izleyerek [Windows PowerShell Web erişimi için oturum açarken](#signing-in-to-windows-powershell-web-access) bu konuda.

## <a name="differences-in-the-web-based-windows-powershell-console"></a>Web tabanlı Windows PowerShell konsolundaki farklılıklar

Windows PowerShell Web erişimi için oturum açtıktan sonra Tarayıcı pencerenizde veya sekmenizde bir web tabanlı Windows PowerShell konsolu açılır. Konsol oturum açma işlemi sırasında belirttiğiniz uzak bilgisayara bağlı olduğundan, yalnızca Windows PowerShell cmdlet'leri veya uzak bilgisayarda kullanılabilen komut dosyaları konsolda kullanılabilir. Bu bölümde Windows PowerShell Web erişimi konsolları ve Windows PowerShell Web erişimi konsolları ile yüklü arasındaki farklar diğer sınırlamaları açıklanmaktadır **PowerShell.exe** Konsolu.

### <a name="functional-disparity-with-powershellexe"></a>PowerShell.exe ile işlevsel farklar

Windows PowerShell ana bilgisayar işlevi çoğu Windows PowerShell Web erişimi web tabanlı konsolda kullanılabilir, ancak mevcut olmayan bazı özellikler mevcuttur.

- İç içe ilerleme durumunu görüntüler.

  Windows PowerShell Web erişimi cmdlet'leri için ilerleme durumu GUI Bu rapor ilerleme durumunu görüntüler, ancak yalnızca üst düzey ilerleme durumu bilgileri görüntülenir.

- Giriş rengi değiştirme.

  Giriş rengi (ön ve arka plan) değiştirilemez. Çıkış, uyarı, ayrıntı ve hata iletileri stilini tüm komut dosyası çalıştırılarak değiştirilebilir.

- Pshostrawuserınterface.

  Windows PowerShell Web erişimi, Windows PowerShell uzak yönetim uygulanır ve bir uzak çalışma alanı kullanır. Windows PowerShell Web erişimi, bu arabirimde bazı yöntemleri uygulamaz; Örneğin, Windows konsoluna yazan herhangi komut. Gibi komutlar **PowerTab** Windows PowerShell Web Erişimi'nde çalışmaz.

- İşlev tuşları.

  Windows PowerShell Web erişimi çoğu durumda bazı işlev tuşlarını desteklemez, çünkü komutların tarayıcı tarafından ayrılmış.

### <a name="unsupported-shortcut-keys"></a>Desteklenmeyen kısayol tuşları

İşlev tuşu | Eylem
-- | --
Ctrl+C | Windows PowerShell Web erişiminde, **Ctrl + C** tarayıcı tarafından içerik kopyalamak için kullanılır. Konsol sunan bir **iptal** düğmesi ve kullanıcılar da kullanabilirsiniz **Ctrl + Q** komutları iptal etmek için.
Alt-boşluk, e, l | Ekran arabelleğinde kaydırma
Alt + boşluk, e, f | Ekran arabelleğinde metin ara
Alt + boşluk, e, k | Ekran arabelleğinden kopyalanacak metni Seç
Alt + boşluk, e, p | Windows PowerShell konsolunda Pano içeriğini yapıştırın
Alt + boşluk, c | Windows PowerShell konsolunu kapatın
Ctrl+Break tuşu | Windows PowerShell penceresini kapanmaya zorla
Ctrl+Home | Geçerli komut satırını başından itibaren siler
Ctrl+End | Komut satırının sonuna kadar siler
F1 | İmleci bir karakter, komut satırında Sağa Taşı
F2 | Son komutunuzu, yazdığınız karaktere kadar kopyalayarak yeni bir komut oluşturur.
F3 | Komut satırı son komut satırınızdan içerikle tamamlayın
F4 | İmleç konumundan karakterleri siler
F5 | Komut geçmişinizde geriye doğru tarayın. Windows PowerShell Web erişimi içinde komut geçmişindeki komutlara erişmek için tıklayın **geçmişi** kaydırma düğmelerine web tabanlı konsolda.
F7 | Etkileşimli olarak komut geçmişinizden bir komut seçin
F8 | Geçerli metinle eşleşen komutları görüntüleyen tarama geçmişi
F9 | Geçmişten belirli bir numaralı komut çalıştırın
Page Up | Geçmişteki ilk komutu çalıştırın
Page Down | Geçmişteki son komutu çalıştırın
Alt+F7 | Komut geçmişi listesi temizleyin

### <a name="limitations-of-the-web-based-console"></a>Web tabanlı konsol sınırlamaları

- Çift atlama

    Çift atlama (veya ilk bağlantıdan ikinci bir bilgisayara bağlanma) sınırlamasıyla oluşturmayı veya Windows PowerShell Web Erişimi'ni kullanarak yeni bir oturumda çalışmayı denerseniz. Windows PowerShell Web erişimi, bir uzak çalışma alanı kullanır ve şu anda, **PowerShell.exe** uzak bir bağlantı uzak bir çalışma alanından ikinci bir bilgisayara kurmayı desteklememektedir. Kullanarak mevcut bir bağlantıdan ikinci bir uzak bilgisayara bağlanmaya çalışırsanız **Enter-PSSession** cmdlet'i, örneğin, alabilirsiniz çeşitli hatalar ağ kaynakları gibi €œCannot alın.

    Çift atlama hatalarını önlemek için yöneticinize, kuruluşların ağ ortamında CredSSP kimlik doğrulaması yapılandırmanız gerekir. CredSSP kimlik doğrulaması yapılandırma hakkında daha fazla bilgi için bkz. [ikinci atlama uzaktan iletişimi için CredSSP](https://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) Microsoft Web sitesinde. İkinci bir uzak bilgisayarı yönetmek istediğiniz zaman açık kimlik bilgileri de sağlayabilirsiniz; örtük kimlik bilgilerinin ikinci atlama atlamaya izin vermesi olası değildir.

- Uzaktan iletişim

    Windows PowerShell Web erişimi kullanır ve uzak Windows PowerShell oturumu onunla aynı sınırlamalara sahiptir. Komutlar veya onlara yazmadıklarından standart giriş, çıkış ve hata kanallarını okumadıklarından konsol tabanlı düzenleyiciler veya metin tabanlı menü programları için olanlar gibi Windows Konsolu API'lerini doğrudan çağıran komutlar çalışmaz. Bu nedenle, bir yürütülebilir dosyayı başlatmak komutları, gibi dosya **notepad.exe**, veya bir GUI görüntüleyen `OpenGridView` veya `ogv`, çalışmıyor. Deneyiminiz Bu davranıştan etkilenir; için Windows PowerShell Web erişimi, komutunuza yanıt vermediğini görünür.

- Sekme tamamlama

    Sekme tamamlama olan bir oturum yapılandırmasında sınırlı bir çalışma veya çalışmıyor **NoLanguage** modu. Yöneticiler, sekme tamamlanmasını desteklemek için bir oturum yapılandırabilse de, aşağıdaki bilgileri yetkisiz kullanıcılara sunabileceğinden güvenlik nedenleriyle önerilmez.

    - İç dosya sistemi yolları

    - İç bilgisayarlarda paylaşılan klasörler

    - Çalışma alanındaki değişkenler

    - Yüklenen türler veya.NET Framework ad alanları

    - Ortam değişkenleri

- **NoLanguage** oturumu veya sınırlı bir çalışma

    Oturum açmış kullanıcılar bir **NoLanguage** oturum yapılandırması veya Windows PowerShell Web erişimi sınırlı bir çalışma çalıştırılamaz **çıkış** oturumunu sona erdirmek için komutu. Oturumu kapatmak için kullanıcıların tıklatmalısınız **oturum kapatma** konsol sayfasında.

- Aynı anda birden çok hedef bilgisayarlara bağlanma.

    Ağ Geçidi sunucusu Windows Server 2012 çalıştırıyorsa, Windows PowerShell Web erişimi, tarayıcı oturumu başına yalnızca bir uzak bilgisayar bağlantısına izin verir; Kullanıcıların bir kez oturum açmasına ve ayrı tarayıcı sekmeleri kullanarak birden çok uzak bilgisayara bağlanmasına izin vermez. Yeni bir sekme veya yeni bir tarayıcı penceresi açtığınızda, yeni (veya aynı) bağlanabilmesi için Windows PowerShell Web erişimi, mevcut oturumunuzun bağlantısını kesmenizi ve yeni bir oturum başlatmanızı ister uzak bilgisayar. Ancak, uzak bilgisayarlara iki veya daha fazla ayrı oturumu isteniyorsa Internet Explorer'daki bir özellik, yeni bir oturum oluşturmanızı sağlar. Internet Explorer'da yeni bir tarayıcı oturumu başlatmak için basın **ALT**açın **dosya** menüsüne ve ardından **yeni oturumu**. Ardından, yeni oturumda Windows PowerShell Web Erişimi Web sitesini açın ve başka bir uzak bilgisayara erişmek için oturum açın.

    Windows Server 2012 R2'de Windows PowerShell Web erişimi ağ geçidini çalıştırırken, kullanıcılar farklı tarayıcı sekmelerinde uzak bilgisayarlara birden çok bağlantı açabilir. Web tabanlı Windows PowerShell konsolunu kullanarak bir uzak bilgisayara birden fazla bağlantı açmak istiyorsanız, bu özellik ağ geçidi sunucusu tarafından desteklenip desteklenmediğini öğrenmek için Windows PowerShell Web erişimi ağ geçidi yöneticinize danışın.

- Kalıcı Windows PowerShell oturumları (yeniden bağlanma).

    Zaman aşımını sonra Windows PowerShell Web erişimi ağ geçidini, ağ geçidi ve hedef bilgisayar arasındaki uzak bağlantı kapatılır. Bu, herhangi bir cmdlet'i ya da mevcut durumda işlemde olan betikler durdurur. Windows PowerShell kullanmanız teşvik **-iş** işleri başlatmak, bilgisayar bağlantısını kesebilmeniz, daha sonra yeniden bağlanabilmeniz ve işlerin kalıcı böylece, uzun süre çalışan görevler gerçekleştirirken altyapı. Kullanmanın başka bir faydası **-iş** cmdlet'lerini Windows PowerShell Web Erişimi'ni kullanarak başlangıç oturumu kapatın ve ardından daha sonra çalışan Windows PowerShell Web erişimi veya başka bir ana bilgisayara (örneğin, Windows PowerShell yeniden olduğu Komut dosyası ortamı (ISE) tümleşik).

- Konsol yeniden boyutlandırma.

    **PowerShell.exe** konsol penceresi yeniden boyutlandırılabilir aşağıdaki üç yolla.

    - Sürükleme ve konsol penceresi boyutunu fareyle Ayarla

    - Konsol özellikleri için bir GUI kullanarak yükseklik ve genişlik özelliklerini değiştir

    - Yüksekliğini ve genişliğini bir cmdlet ile konsol pencerelerinin değiştirme

        Windows PowerShell Web erişimi için konsol penceresi, aşağıdaki gibi cmdlet'ler kullanarak yapılandırılabilir. Aşağıdaki örnekte, bir kullanıcı için Windows PowerShell Web erişimi konsolunun genişliğini değişiklikleri **20**.

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        Konsolun yüksekliğini benzer şekilde değiştirebilirsiniz.

        Konsol görünümünü özelleştirmek için ek örnekler kullanılabilir [Windows PowerShell ekibi blogu](https://blogs.msdn.com/b/powershell/).

## <a name="see-also"></a>Ayrıca bkz:

- [Windows PowerShell Cmdlet başvurusu](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
- [Microsoft TechNet'te Windows PowerShell](https://technet.microsoft.com/library/bb978526.aspx)
- [TechNet Komut Merkezi havuzu](https://gallery.technet.microsoft.com/scriptcenter)
- [Merkezi - Hey, Scripting Guy betik!](https://technet.microsoft.com/scriptcenter)
- [Windows PowerShell ekibi blogu](https://blogs.msdn.com/b/powershell/)