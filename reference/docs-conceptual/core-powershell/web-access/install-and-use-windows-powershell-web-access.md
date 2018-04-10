---
ms.date: 08/23/2017
keywords: PowerShell cmdlet'i
title: Yükleme ve windows powershell web erişimi kullanma
ms.openlocfilehash: 8f140e73ce833fd1cfadbe1d8ee0fe0bb2d08873
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="install-and-use-windows-powershell-web-access"></a>Windows PowerShell Web Erişimi Yükleme ve Kullanma

Güncelleştirilmiş: 5 Kasım 2013 (düzenlenebilir: 23 Ağustos 2017)

İçin geçerlidir: Windows Server 2012 R2, Windows Server 2012

## <a name="introduction"></a>Giriş

İlk Windows Server 2012'de kullanıma sunulan Windows PowerShell Web erişimi bir uzak bilgisayara hedeflenen web tabanlı bir Windows PowerShell Konsolu sağlayan bir Windows PowerShell ağ geçidi olarak davranır. BT uzmanları, Windows PowerShell konsolundan hiçbir Windows PowerShell, uzaktan yönetim yazılımı veya tarayıcı eklentisi yüklemesine istemci aygıtında gereken bir web tarayıcısında Windows PowerShell komutları ve komut dosyaları çalıştırmak etkinleştirir. Web tabanlı Windows PowerShell konsolunu çalıştırmak için gerekli olan tek şey düzgün yapılandırılmış Windows PowerShell Web erişimi ağ geçidi ve JavaScript destekleyen ve tanımlama bilgilerini kabul eden bir istemci cihazdır.

Dizüstü bilgisayarlar, çalışma amaçlı olmayan kişisel bilgisayarlar, ödünç alınan bilgisayarlar, tablet bilgisayarlar, web bilgi noktaları, Windows tabanlı bir işletim sistemi çalışan bilgisayarlar ve cep telefonu tarayıcıları, istemci cihazların örneklerindendir. BT uzmanları bir İnternet bağlantısına ve web tarayıcısına erişimi olan cihazlardan Windows tabanlı uzak sunucularda kritik yönetim görevlerini gerçekleştirebilir.

Başarılı ağ geçidi kurulumu ve yapılandırmasının ardından kullanıcılar bir web tarayıcısı kullanarak bir Windows PowerShell Konsolu erişebilir. Kullanıcılar Güvenli Windows PowerShell Web Erişimi Web sitesini açtığında, başarılı kimlik doğrulamasının ardından web tabanlı Windows PowerShell konsolunda çalıştırabilirler.

Windows PowerShell Web erişimi kurulumu ve yapılandırması üç adımlık bir işlem şöyledir:

1. [Windows PowerShell Web erişimi yükleme](#install-windows-powershell-web-access)
1. [Ağ geçidini yapılandırma](#configure-the-gateway)
1. [Kısıtlayıcı yetkilendirme kuralı yapılandırma](#configure-a-restrictive-authorization-rule)

Yüklemeden ve Windows PowerShell Web erişimi yapılandırmadan önce nasıl yükleneceği hakkında yönergeler içeren bu kılavuzun tamamının, okuma güvenli ve Windows PowerShell Web erişimini kaldırma öneririz.
[Web tabanlı Windows PowerShell konsolunu kullanma](https://technet.microsoft.com/library/hh831417(v=ws.11).aspx) konu, kullanıcıların web tabanlı konsolda nasıl oturum açtığını açıklar ve web tabanlı Windows PowerShell Konsolu arasındaki sınırlamaları ve farklılıkları kapsar ve  **PowerShell.exe** konsol. Web tabanlı konsolun son kullanıcıların kimler [kullanım Web tabanlı Windows PowerShell Konsolu](use-the-web-based-windows-powershell-console.md), ancak bu kılavuzun ilerleyen okuma gerekmez.

Bu konuda ayrıntılı IIS Web sunucusu işlem yönergelerini sağlamaz; Bu konu yalnızca Windows PowerShell Web erişimi ağ geçidini yapılandırmak için gerekli adımları açıklanmaktadır. IIS’te web sitelerini yapılandırma ve güvenliğini sağlama hakkında daha fazla bilgi için Ayrıca Bkz bölümündeki IIS belge kaynaklarına bakın.

Aşağıdaki diyagramda, Windows PowerShell Web erişimi nasıl çalıştığı gösterilmektedir.

![Windows PowerShell Web Erişim diyagramı](images/Windows-PowerShell-Web-Access-diagram.jpg)

## <a name="requirements-for-running-windows-powershell-web-access"></a>Windows PowerShell Web Erişimini çalıştırma gereksinimleri

Windows PowerShell Web Erişimi Web sunucusu (IIS), .NET Framework 4.5 ve Windows PowerShell 3.0 veya Windows PowerShell 4. 0'i, ağ geçidini çalıştırmak istediğiniz sunucu üzerinde çalışıyor olmasını gerektirir. Windows PowerShell Web erişimi, Sunucu Yöneticisi'nin Rol Ekle ve Özellikler Sihirbazı'nı Sunucu Yöneticisi veya Windows PowerShell dağıtım cmdlet'leri kullanarak Windows Server 2012 R2 çalıştıran bir sunucu veya Windows Server 2012'de yükleyebilirsiniz. Sunucu Yöneticisi veya dağıtım cmdlet'lerini kullanarak Windows PowerShell Web erişimi yüklerken, gerekli rolleri ve özellikleri yükleme işleminin bir parçası olarak otomatik olarak eklenir.

Windows PowerShell Web erişimi, uzak kullanıcıların bir web tarayıcısından Windows PowerShell kullanarak kuruluşunuzdaki bilgisayarlara erişmesine olanak tanır. Windows PowerShell Web erişimi kullanışlı ve güçlü yönetim aracı olsa da, web tabanlı erişim güvenlik riskleri doğurur ve mümkün olduğunca güvenli bir şekilde yapılandırılmış olması gerekir. Windows PowerShell Web erişimi ağ geçidini yapılandıran yöneticilerin kullanılabilen güvenlik katmanları kullanın, cmdlet tabanlı yetkilendirme kuralları hem Windows PowerShell Web erişimi ve güvenlik ile Web sunucusu (kullanılabilir olan katmanları dahil öneririz IIS) ve üçüncü taraf uygulamalar. Bu belgeler hem yalnızca test ortamları için önerilen güvensiz örnekleri hem de güvenli dağıtımlar için önerilen örnekleri içerir.

## <a name="browser-and-client-device-support"></a>Tarayıcı ve istemci cihaz desteği

Windows PowerShell Web erişimi aşağıdaki Internet tarayıcılarını destekler.
Mobil tarayıcılar resmi olarak desteklenmese de, birçok web tabanlı Windows PowerShell konsolunda çalıştırmanız mümkün olabilir. Yalnızca tanımlama bilgilerini kabul eden, JavaScript çalıştıran ve HTTPS web sitelerini çalıştıran diğer tarayıcıların çalışması beklenir, ancak bunlar resmi olarak test edilmemiştir.

### <a name="supported-desktop-computer-browsers"></a>Desteklenen masaüstü bilgisayar tarayıcıları

- Microsoft Windows 8.0, 9.0, 10.0 ve 11.0 için Windows Internet Explorer
- Mozilla Firefox 10.0.2
- Windows için Google Chrome 17.0.963.56m
- Windows için Apple Safari 5.1.2
- Mac OS için Apple Safari 5.1.2

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Minimumda test edilen mobil cihazlar veya tarayıcılar

- Windows Phone 7 ve 7.5
- Google Android WebKit 3.1 tarayıcısı Android 2.2.1 (Kernel 2.6)
- iPhone işletim sistemi 5.0.1 için Apple Safari
- İPad 2 işletim sistemi 5.0.1 için Apple Safari

### <a name="browser-requirements"></a>Tarayıcı gereksinimleri

Windows PowerShell Web erişimi web tabanlı konsolunu kullanmak için tarayıcılar aşağıdakileri yapmanız gerekir.

- Windows PowerShell Web erişimi ağ geçidi Web sitesinden tanımlama bilgilerine izin verin.
- HTTPS sayfalarını açabilir ve okuyabilir hale gelin.
- JavaScript kullanan web sitelerini açın ve çalıştırın.

## <a name="recommended-quick-deployment"></a>Önerilen hızlı dağıtım

Ya da Windows PowerShell cmdlet'lerini kullanarak veya Rol Ekle ve Sunucu Yöneticisi içinde açılmış özellikleri Sihirbazı'nı kullanarak, Windows Server 2012 R2 çalıştıran bir sunucu veya Windows Server 2012'de Windows PowerShell Web erişimi ağ geçidini yükleyebilirsiniz. Hızlı yükleme ve yapılandırma için Windows PowerShell cmdlet'leri, bu bölümde açıklandığı gibi kullanın.

1. [Windows PowerShell Web erişimi yükleme](#install-Windows-powershell-web-access)
1. [Ağ geçidini yapılandırma](#configure-the-gateway)
1. [Kısıtlayıcı yetkilendirme kuralı yapılandırma](#configure-a-restrictive-authorization-rule)

### <a name="install-windows-powershell-web-access"></a>Windows PowerShell Web erişimi yükleme

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a>Windows PowerShell cmdlet'lerini kullanarak Windows PowerShell Web Erişimi yüklemek için

1. Yükseltilmiş kullanıcı haklarıyla bir Windows PowerShell oturumu açmak için aşağıdakilerden birini yapın.
    - Windows masaüstünde, sağ **Windows PowerShell** görev ve ardından **yönetici olarak çalıştır**.
    - Windows **Başlat** ekranında, sağ **Windows PowerShell**ve ardından **yönetici olarak çalıştır**.

    >**![Not](images/note.jpeg) Not** içinde Windows PowerShell 3.0 ve 4.0, modülün parçası olan cmdlet'leri çalıştırmadan önce Windows PowerShell oturumuna Sunucu Yöneticisi'ni cmdlet modülünün içeri aktarmak için gerek yoktur. Modülün parçası olan bir cmdlet'i ilk kez çalıştırdığınızda otomatik olarak modül içeri aktarılır. Ayrıca, Windows PowerShell cmdlet'leri büyük küçük harfe duyarlı değildir.

1. Aşağıdaki komutu yazın ve sonra basın **Enter**, burada *bilgisayar_adı* üzerinde Windows PowerShell Web erişimi, yüklemek istediğiniz varsa Uzak bir bilgisayarı temsil eder. Gerekirse `-Restart` parametresi hedef sunucuları otomatik olarak yeniden başlatır.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart`

   >**![Not](images/note.jpeg) Not**
   >
   >Windows PowerShell cmdlet'lerini kullanarak Windows PowerShell Web erişimi yükleme, Web sunucusu (IIS) yönetim araçları varsayılan olarak eklemez. Windows PowerShell Web erişimi ağ geçidi ile aynı sunucuda yönetim araçlarını yüklemek istiyorsanız, ekleme `-IncludeManagementTools` (Bu adımda anlatıldığı gibi) yükleme komut parametresi. Windows PowerShell Web Erişimi Web sitesini uzak bir bilgisayardan yönetiyorsanız, IIS Yöneticisi ek bileşenini yükleyerek yüklemenizi [uzak sunucu yönetim Toolsfor Windows 8.1](http://go.microsoft.com/fwlink/?LinkID=304145) veya [uzak sunucu yönetim Windows 8 için Araçları](http://go.microsoft.com/fwlink/p/?LinkID=238560) ağ geçidini yönetmek istediğiniz bilgisayarı üzerinde.

   Çevrimdışı bir VHD’ye rol ve özellikler yüklemek için hem `-ComputerName` parametresini hem de `-VHD` parametresini eklemeniz gerekir. `-ComputerName` parametresi, VHD’nin bağlanacağı sunucunun adını içerir ve `-VHD` parametresi de belirtilen sunucuda VHD dosyasının yolunu içerir.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart`

1. Yükleme tamamlandığında, Windows PowerShell Web erişimi çalıştırarak hedef sunucularda yüklendiğini doğrulama **Get-WindowsFeature** açılmış bir Windows PowerShell konsolunda bir hedef sunucuda cmdlet'i yükseltilmiş kullanıcı haklarına sahip. Windows PowerShell Web erişimi sunucu yöneticisi konsolunda bulunan bir hedef sunucuya seçerek yüklendiğini doğrulayabilirsiniz **tüm sunucuları** sayfa ve ardından görüntüleyerek **roller ve Özellikler** bölme seçili sunucu için. Windows PowerShell Web erişimi için Benioku dosyasını da görüntüleyebilirsiniz.

1. Windows PowerShell Web erişimi yüklendikten sonra ağ geçidi için temel, gerekli kurulum yönergelerini içeren Benioku dosyasını gözden istenir. Bu kurulum yönergeleri aşağıdaki bölümde ayrıca olan [ağ geçidini yapılandırma](#configure-the-gateway). Benioku dosyasının yolu **C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt**.

### <a name="configure-the-gateway"></a>Ağ geçidini yapılandırma

**Install-PswaWebApplication** cmdlet'tir yapılandırılmış Windows PowerShell Web erişimi almak için hızlı bir şekilde. `UseTestCertificate` parametresini `Install-PswaWebApplication` cmdlet’ine ekleyerek test amacıyla otomatik olarak imzalanan bir SSL sertifikası yükleyebilseniz de, bu yöntem güvenli değildir; güvenli bir üretim ortamı için her zaman bir sertifika yetkilisi (CA) tarafından imzalanmış geçerli bir SSL sertifikası kullanın.
Yöneticiler IIS Yöneticisi konsolunu kullanarak test sertifikasını kendi seçtikleri imzalı bir sertifika ile değiştirebilir.

Çalıştırarak Windows PowerShell Web erişimi web uygulaması yapılandırmasını tamamlayabilirsiniz `Install-PswaWebApplication` cmdlet'ini veya IIS Yöneticisi'nde GUI tabanlı yapılandırma adımları gerçekleştirerek. Varsayılan olarak, web uygulaması cmdlet yükler **pswa** (ve ona ait bir uygulama havuzu **pswa_pool**), **varsayılan Web sitesi** kapsayıcı, IIS Yöneticisi'nde; gösterildiği gibi İstenen, web uygulamasının varsayılan site kapsayıcısını değiştirmesini isteyebilirsiniz söyleyebilirsiniz. IIS Yöneticisi, bağlantı noktasını veya Güvenli Yuva Katmanı (SSL) sertifikasını değiştirme gibi web uygulamaları için kullanılabilir olan yapılandırma seçenekleri sunar.

>**![Güvenlik Notu](images/securitynote.jpeg) güvenlik notu**
>
>Yöneticilerin ağ geçidini bir CA tarafından imzalanmış geçerli bir sertifika kullanacak şekilde yapılandırması önerilir.

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a>Windows PowerShell Web Erişimi ağ geçidini Install-PswaWebApplication kullanarak bir test sertifikasıyla yapılandırmak için

1. Bir Windows PowerShell oturumu açmak için aşağıdakilerden birini yapın.

    - Windows masaüstünde, sağ **Windows PowerShell** görev çubuğunda.

    - Windows **Başlat** ekranında **Windows PowerShell**.

2. Aşağıdaki komutu yazın ve sonra basın **Enter**.

    **Install-PswaWebApplication - UseTestCertificate**

  >**![Güvenlik Notu](images/securitynote.jpeg) güvenlik notu**
  >
  >`UseTestCertificate` parametresi yalnızca özel bir test ortamında kullanılmalıdır. Güvenli bir üretim ortamı için CA tarafından imzalanmış geçerli bir sertifika kullanılması önerilir.

Cmdlet'ini çalıştırarak IIS varsayılan Web sitesi kapsayıcı içindeki Windows PowerShell Web erişimi web uygulamasını yükler. Cmdlet varsayılan Web sitesinde, Windows PowerShell Web erişimi çalıştırmak için gerekli altyapıyı oluşturur `https://<server_name>/pswa`. Web uygulamasını farklı bir web sitesine yüklemek için `WebSiteName` parametresini ekleyerek web sitesi adını belirtin. Web uygulamasının adını değiştirmek için (varsayılan `pswa`), `WebApplicationName` parametresini ekleyin.

Aşağıdaki ayarlar cmdlet çalıştırılarak yapılandırılır. İsterseniz bunları IIS Yöneticisi konsolunda el ile değiştirebilirsiniz.

- Path: /pswa
- ApplicationPool: pswa_pool
- EnabledProtocols: http
- PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot

**Örnek**: `Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate`

Bu örnekte, https:// sonuçta elde edilen Web sitesi için Windows PowerShell Web erişimi olan\<*sunucu_adı*\>/myWebApp.

>**![Not](images/note.jpeg) Not**
>
>Yetkilendirme kuralları eklenerek kullanıcılara web sitesi erişimi verilinceye kadar oturum açamazsınız. Daha fazla bilgi için bkz: [kısıtlayıcı yetkilendirme kuralı yapılandırma](#configure-a-restrictive-authorization-rule) ve [yetkilendirme kuralları ve güvenlik özellikleri, Windows PowerShell Web erişimi](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a>Windows PowerShell Web Erişimi ağ geçidini Install-PswaWebApplication ve IIS Yöneticisi kullanarak orijinal bir sertifika ile yapılandırmak için

1. Bir Windows PowerShell oturumu açmak için aşağıdakilerden birini yapın.

    - Windows masaüstünde, sağ **Windows PowerShell** görev çubuğunda.

    - Windows **Başlat** ekranında **Windows PowerShell**.

2. Aşağıdaki komutu yazın ve sonra basın **Enter**.

    **Install-PswaWebApplication**

    Aşağıdaki ağ geçidi ayarları cmdlet çalıştırılarak yapılandırılır.
    İsterseniz bunları IIS Yöneticisi konsolunda el ile değiştirebilirsiniz.
    `Install-PswaWebApplication` cmdlet’inin `WebsiteName` ve `WebApplicationName` parametreleri için de değer belirtebilirsiniz.

    - Path: /pswa

    - ApplicationPool: pswa_pool

    - EnabledProtocols: http

    - PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot

3. Aşağıdakilerden birini yaparak IIS Yöneticisi konsolunu açın.

    - Windows masaüstünde, Sunucu Yöneticisi'ni tıklatarak Başlat **Sunucu Yöneticisi'ni** Windows görev çubuğunda. Üzerinde **Araçları** Sunucu Yöneticisi ' nde menüsünü **Internet Information Services (IIS) Yöneticisi'ni**.

    - Windows **Başlat** ekranında **Sunucu Yöneticisi'ni**.

4. IIS Yöneticisi ağaç bölmesinde, Windows PowerShell Web erişimi yüklendiği kadar sunucu düğümünü genişletin **siteleri** klasördür görünür. Genişletme **siteleri** klasör.

5. Windows PowerShell Web erişimi web uygulamasını yüklediğiniz Web sitesini seçin. İçinde **Eylemler** bölmesinde tıklatın **bağlamaları**.

6. İçinde **Site bağlamasını** iletişim kutusu, tıklatın **Ekle**.

7. İçinde **Site bağlaması Ekle** iletişim kutusunda **türü** alan, select **https**.

8. İçinde **SSL sertifikası** alanında, aşağı açılır menüden imzalı sertifikanızı seçin. **Tamam**’a tıklayın. Bkz: [IIS Yöneticisi'nde bir SSL sertifikası yapılandırma](#to-configure-an-ssl-certificate-in-iis-Manager) bir sertifikanın nasıl alınacağı hakkında daha fazla bilgi için bu konudaki.

    Windows PowerShell Web erişimi web uygulaması, imzalı SSL sertifikanızı kullanacak şekilde yapılandırılmıştır.

    Windows PowerShell Web erişimi açarak erişebilir **https://\<sunucu_adı\>/pswa** bir tarayıcı penceresinde.

>**![Not](images/note.jpeg) Not**
>
>Yetkilendirme kuralları eklenerek kullanıcılara web sitesi erişimi verilinceye kadar oturum açamazsınız.
>Daha fazla bilgi için bkz: [kısıtlayıcı yetkilendirme kuralı yapılandırma](#configure-a-restrictive-authorization-rule), bu konu başlığı ve [yetkilendirme kuralları ve güvenlik özellikleri, Windows PowerShell Web erişimi](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>Kısıtlayıcı yetkilendirme kuralı yapılandırma

Windows PowerShell Web erişimi yüklendikten ve ağ geçidi yapılandırıldıktan sonra kullanıcılar oturum açma sayfasını bir tarayıcıda açabilir, ancak açıkça erişim Windows PowerShell Web erişimi yönetici kullanıcılar verene kadar kullanıcılar oturum açamaz. Windows PowerShell Web erişimi erişim denetimi, aşağıdaki tabloda açıklanan Windows PowerShell cmdlet'leri kümesi kullanılarak yönetilir. Yetkilendirme kuralları eklemek veya yönetmek için karşılaştırılabilir GUI yoktur. Windows PowerShell Web erişimi cmdlet'leri hakkında daha ayrıntılı bilgi için cmdlet başvuru konularına bakın [Windows PowerShell Web erişimi cmdlet'leri](cmdlets/web-access-cmdlets.md).

Windows PowerShell Web Erişimi yetkilendirme kuralları ve güvenlik hakkında daha fazla ayrıntı için [yetkilendirme kuralları ve güvenlik özellikleri, Windows PowerShell Web erişimi](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>Kısıtlayıcı yetkilendirme kuralı ekleme

1. Yükseltilmiş kullanıcı haklarıyla bir Windows PowerShell oturumu açmak için aşağıdakilerden birini yapın.

    - Windows masaüstünde, sağ **Windows PowerShell** görev ve ardından **yönetici olarak çalıştır**.

    - Windows **Başlat** ekranında, sağ **Windows PowerShell**ve ardından **yönetici olarak çalıştır**.

2. Kullanıcı erişimini oturum yapılandırmaları kullanarak kısıtlamak için isteğe bağlı adım: kullanmak, kurallarınızı zaten istediğiniz oturum yapılandırmaları mevcut olduğunu doğrulayın. Bunlar henüz oluşturulmadı, içindeki oturum yapılandırmaları oluşturmak için yönergeleri kullanın [about_Session_Configuration_Files](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Aşağıdaki komutu yazın ve sonra basın **Enter**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Bu yetkilendirme kuralı genelde, kullanıcının tipik komut dosyası için kapsamlı bir özel oturum yapılandırması erişimi ile erişimi ve cmdlet gereksinimlerine ağ üzerinde bir bilgisayara belirli kullanıcı erişimi sağlar.

   Aşağıdaki örnekte, `Contoso` etki alanında `JSmith` adlı bir kullanıcıya, `Contoso_214` bilgisayarını yönetmek ve `NewAdminsOnly` adlı bir oturum yapılandırması kullanmak için erişim verilir.

   `Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

4. Kural ya da çalıştırarak oluşturulduğunu doğrulayın `Get-PswaAuthorizationRule` cmdlet'ini veya `Test-PswaAuthorizationRule -UserName <domain\user> -ComputerName <computer-name>`

5. Örneğin, `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

Bir yetkilendirme kuralını yapılandırdıktan sonra yetkili kullanıcıların web tabanlı konsolda oturum açması ve Windows PowerShell Web Erişimi'ı kullanmaya başlamak için hazır olursunuz.

## <a name="custom-deployment"></a>Özel dağıtım

Windows PowerShell Web erişimi ağ geçidini, Sunucu Yöneticisi'nde Ekle roller ve Özellikler Sihirbazı'nı kullanarak Windows Server 2012 R2 çalıştıran bir sunucu veya Windows Server 2012'de yükleyebilirsiniz. Windows PowerShell Web erişimi yüklendikten sonra IIS Yöneticisi'nde ağ geçidi yapılandırmasını özelleştirebilirsiniz.

### <a name="install-windows-powershell-web-access"></a>Windows PowerShell Web erişimi yükleme

#### <a name="to-install-windows-powershell-web-access-by-using-the-add-roles-and-features-wizard"></a>Roller ve Özellikler Ekleme Sihirbazı’nı kullanarak Windows PowerShell Web Erişimi’ni yüklemek için

1. Sunucu Yöneticisi'ni zaten açıksa sonraki adıma geçin. Sunucu Yöneticisi'ni zaten açık değilse aşağıdakilerden birini yaparak açın.

    - Windows masaüstünde, Sunucu Yöneticisi'ni tıklatarak Başlat **Sunucu Yöneticisi'ni** Windows görev çubuğunda.

    - Windows **Başlat** ekranında **Sunucu Yöneticisi'ni**.

2. Üzerinde **Yönet** menüsünde tıklatın **rol ve Özellik Ekle**.

3. Üzerinde **yükleme türünü seçin** sayfasında **rol tabanlı veya özellik tabanlı yükleme**. **İleri**’ye tıklayın.

4. Üzerinde **Select hedef sunucu** sayfasında, sunucu havuzundan bir sunucu seçin ya da çevrimdışı bir VHD seçin. Çevrimdışı bir VHD’yi hedef sunucunuz olarak seçmek için önce VHD’nin bağlanacağı sunucuyu ve sonra VHD dosyasını seçin. Sunucuları sunucu havuzunuza ekleme hakkında daha fazla bilgi için Sunucu Yöneticisi'ni yardımına bakın. Hedef sunucuyu seçtikten sonra tıklayın **sonraki**.

5. Üzerinde **seçin özellikleri** Sayfa Sihirbazı'nın genişletin **Windows PowerShell**ve ardından **Windows PowerShell Web erişimi**.

6. .NET Framework 4.5 ve Web Sunucusu’nun (IIS) rol hizmetleri gibi gerekli özellikleri eklemeniz istenir. Gerekli özellikleri ekleyin ve devam edin.

    >**![Not](images/note.jpeg) Not**
    >
    >Ekle roller ve Özellikler Sihirbazı'nı kullanarak Windows PowerShell Web erişimi yükleme, Web sunucusu (IIS Yöneticisi ek bileşenini dahil olmak üzere IIS), yükler. Ekle roller ve Özellikler Sihirbazı'nı kullanıyorsanız ek bileşenini ve diğer IIS Yönetim Araçları varsayılan olarak yüklenir. Aşağıdaki yordamda açıklandığı gibi Windows PowerShell cmdlet'lerini kullanarak Windows PowerShell Web erişimi yüklerseniz, Yönetim Araçları varsayılan olarak eklenmez.

7. Üzerinde **Yükleme Seçimlerini Onayla** sayfasında, özellik dosyaları adım 4 ' te seçtiğiniz hedef sunucuda Windows PowerShell Web erişimi depolanmaz için tıklatırsanız **alternatifkaynakyolbelirtme**ve özellik dosyalarının yolunu belirtin. Aksi takdirde tıklatın **yükleme**.

8. Tıklattıktan sonra **yükleme**, **yükleme ilerleme durumu** sayfası, yüklemenin ilerleme durumunu, sonuçları ve uyarılar, hatalar veya yükleme sonrası yapılandırma adımları gibi iletileri görüntüler Windows PowerShell Web erişimi için gereklidir. Windows PowerShell Web erişimi yüklendikten sonra ağ geçidi için temel, gerekli kurulum yönergelerini içeren Benioku dosyasını gözden istenir. Bu yönergeleri bu konuya da dahil edilmiştir. Benioku dosyasının yolu `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>Ağ geçidini yapılandırma

Bir alt ve Web sitenizin kök dizininde değil Windows PowerShell Web erişimi web uygulamasını yüklemek için bu bölümdeki yönergeleri verilmiştir. Bu yordam, `Install-PswaWebApplication` cmdlet’i tarafından gerçekleştirilen eylemlerin GUI tabanlı eşdeğeridir. Bu bölümde, IIS Yöneticisi'ni Windows PowerShell Web erişimi ağ geçidini kök Web sitesi olarak yapılandırmak için nasıl kullanılacağını ilişkin yönergeleri de içerir.

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a>IIS Yöneticisi’ni kullanarak mevcut bir web sitesinde ağ geçidini yapılandırmak için

1. Aşağıdakilerden birini yaparak IIS Yöneticisi konsolunu açın.

    - Windows masaüstünde, Sunucu Yöneticisi'ni tıklatarak Başlat **Sunucu Yöneticisi'ni** Windows görev çubuğunda. Üzerinde **Araçları** Sunucu Yöneticisi ' nde menüsünü **Internet Information Services (IIS) Yöneticisi'ni**.

    - Windows **Başlat** adının bir kısmını ekranında, **Internet Information Services (IIS) Yöneticisi'ni**. İçinde gösterildiğinde kısayola tıklayın **uygulamaları** sonuçları.

2. Windows PowerShell Web erişimi için yeni bir uygulama havuzu oluşturun. IIS Yöneticisi ağaç bölmesinde, Ağ Geçidi sunucusunun düğümünü genişletin **uygulama havuzları**, tıklatıp **uygulama havuzu Ekle** içinde **Eylemler** bölmesi.

3. Adlı yeni bir uygulama havuzu Ekle **pswa_pool**, ya da başka bir ad sağlayın. **Tamam**’a tıklayın.

4. IIS Yöneticisi ağaç bölmesinde, Windows PowerShell Web erişimi yüklendiği kadar sunucu düğümünü genişletin **siteleri** klasördür görünür. Seçin **siteleri** klasör.

5. Web sitesini sağ tıklayın (örneğin, **varsayılan Web sitesi**), Windows PowerShell Web Erişimi Web sitesini ekleyin ve ardından istediğiniz için **uygulama Ekle**.

6. İçinde **diğer** alanına pswa yazın veya başka bir diğer ad belirtin. Diğer ad, sanal dizin adı olur. Örneğin, **pswa** Bu adımda belirtilen diğer adı aşağıdaki URL'yi temsil eder: **https://\<sunucu adı\>/pswa**.

7. İçinde **uygulama havuzu** alanında, adım 3'te oluşturduğunuz uygulama havuzunu seçin.

8. İçinde **fiziksel yolu** alan, uygulamanın konumu için göz atın. %windir%/Web/PowerShellWebAccess/wwwroot varsayılan konumunu kullanabilirsiniz. **Tamam**’a tıklayın.

9. Bu konudaki IIS manager](#to-configure-an-ssl-certificate-in-iis-Manager) bir SSL sertifikası yapılandırmak için yordamdaki adımları izleyin.

10. ![](images/SecurityNote.jpeg) İsteğe bağlı güvenlik adımı:

    Ağaç bölmesinde seçilen Web sitesiyle çift **SSL ayarları** içerik bölmesindeki.
Seçin **SSL iste**ve ardından **Eylemler** bölmesinde tıklatın **Uygula**.
İsteğe bağlı olarak **SSL ayarları** bölmesinde, Windows PowerShell Web Erişimi Web sitesine bağlanan kullanıcıların istemci sertifikalarını sahip gerektirebilirsiniz. İstemci sertifikaları bir istemci cihaz kullanıcısının kimliğini doğrulamaya yardımcı olur.
İstemci sertifika istemenin Windows PowerShell Web erişimi güvenliğini nasıl artırabilirsiniz hakkında daha fazla bilgi için bkz: [yetkilendirme kuralları ve güvenlik özellikleri, Windows PowerShell Web erişimi](authorization-rules-and-security-features-of-windows-powershell-web-access.md) bu kılavuzdaki.

11. Bir istemci cihazda tarayıcı oturumu açın. Desteklenen tarayıcılar ve cihazlar hakkında daha fazla bilgi için bkz: [tarayıcı ve istemci aygıt destek](#browser-and-client-device-support) bu konuda.

12. Yeni Windows PowerShell Web Erişimi Web sitesini açın **https://\<*ağ geçidi sunucusu adı*\>/pswa**.

    Tarayıcı, Windows PowerShell Web erişimi konsol oturum açma sayfası görüntülemelidir.

    >**![Not](images/note.jpeg) Not**
    >
    >Yetkilendirme kuralları eklenerek kullanıcılara web sitesi erişimi verilinceye kadar oturum açamazsınız.
    >Daha fazla bilgi için bkz: [kısıtlayıcı yetkilendirme kuralı yapılandırma](#configure-a-restrictive-authorization-rule), bu konu başlığı ve [yetkilendirme kuralları ve güvenlik özellikleri, Windows PowerShell Web erişimi](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

13. Yükseltilmiş kullanıcı hakları (yönetici olarak çalıştır) ile açılmış bir Windows PowerShell oturumunda, aşağıdaki komut dosyası içinde çalıştığı *application_pool_name* 3. adımda oluşturduğunuz uygulama havuzu adını temsil eder Uygulama havuzu yetkilendirme dosyasına erişim hakkı vermek için.

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    Yetkilendirme dosyasındaki mevcut erişim haklarını görüntülemek için aşağıdaki komutu çalıştırın:

        c:\windows\system32\icacls.exe $authorizationFile

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a>IIS Yöneticisi’ni kullanarak bir test sertifikası ile ağ geçidini kök web sitesi olarak yapılandırmak için

1. Aşağıdakilerden birini yaparak IIS Yöneticisi konsolunu açın.

    - Windows masaüstünde, Sunucu Yöneticisi'ni tıklatarak Başlat **Sunucu Yöneticisi'ni** Windows görev çubuğunda. Üzerinde **Araçları** Sunucu Yöneticisi ' nde menüsünü **Internet Information Services (IIS) Yöneticisi'ni**.

    - Windows **Başlat** adının bir kısmını ekranında, **Internet Information Services (IIS) Yöneticisi'ni**. İçinde gösterildiğinde kısayola tıklayın **uygulamaları** sonuçları.

2. IIS Yöneticisi ağaç bölmesinde, Windows PowerShell Web erişimi yüklendiği kadar sunucu düğümünü genişletin **siteleri** klasördür görünür. Seçin **siteleri** klasör.

3. İçinde **Eylemler** bölmesinde tıklatın **Web sitesi Ekle**.

4. Web sitesi için bir ad yazın **Windows PowerShell Web erişimi**.

5. Yeni web sitesi için bir uygulama havuzu otomatik olarak oluşturulur. Farklı bir uygulama havuzu kullanmak için tıklatın **seçin** yeni Web sitesiyle ilişkilendirilecek bir uygulama havuzu seçin. Diğer uygulama havuzunu seçin **uygulama havuzu Seç** iletişim kutusunu ve ardından **Tamam**.

6. İçinde **fiziksel yolu** metin kutusunda, % gidin*windir*% / Web/PowerShellWebAccess/wwwroot.

7. İçinde **türü** alanını **bağlama** alanında **https**.

8. Web sitesine, başka bir site veya uygulama tarafından zaten kullanılmayan bir bağlantı noktası numarası atayın. Açık bağlantı noktalarını bulmak için çalıştırabilirsiniz **netstat** bir komut istemi penceresinde komutu. Varsayılan bağlantı noktası numarası 443'tür.

    Varsayılan bağlantı noktası 443 başka bir web sitesi tarafından zaten kullanılıyorsa veya bağlantı noktası numarasını değiştirmek için başka güvenlik nedenleriniz varsa varsayılan bağlantı noktasını değiştirin. Ağ geçidi sunucunuzda çalışan başka bir Web sitesi seçtiğiniz bağlantı noktasını kullanıyorsa, tıkladığınızda bir uyarı görüntülenir **Tamam** içinde **Web sitesi Ekle** iletişim kutusu. Windows PowerShell Web erişimi çalıştırmak için kullanılmayan bir bağlantı noktası kullanmanız gerekir.

9. İsteğe bağlı olarak, kuruluşunuz için gerekirse, kuruluş ve kullanıcılar gibi anlamlı bir ana bilgisayar adı belirtin **www.contoso.com**. **Tamam**’a tıklayın.

10. Daha güvenli bir üretim ortamı için CA tarafından imzalanmış geçerli bir sertifikanın belirtilmesi önerilir. Kullanıcılar yalnızca Windows PowerShell Web erişimi için bir HTTPS Web sitesi aracılığıyla bağlanabildiğinden bir SSL sertifikası sağlamanız gerekir. Bkz: [IIS Yöneticisi'nde bir SSL sertifikası yapılandırma](#to-configure-an-ssl-certificate-in-iis-Manager) bir sertifikanın nasıl alınacağı hakkında daha fazla bilgi için bu konudaki.

11. Tıklatın **Tamam** kapatmak için **Web sitesi Ekle** iletişim kutusu.

12. Yükseltilmiş kullanıcı hakları (yönetici olarak çalıştır) ile açılmış bir Windows PowerShell oturumunda, aşağıdaki komut dosyası içinde çalıştığı *application_pool_name* adım 4 ' te oluşturduğunuz uygulama havuzu adını temsil eder Uygulama havuzu yetkilendirme dosyasına erişim hakkı vermek için.

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    Yetkilendirme dosyasındaki mevcut erişim haklarını görüntülemek için aşağıdaki komutu çalıştırın:

        c:\windows\system32\icacls.exe $authorizationFile

13. IIS Yöneticisi ağaç bölmesinde seçili yeni Web sitesi ile tıklatın **Başlat** içinde **Eylemler** Web sitesini başlatmak için bölmesi.

14. Bir istemci cihazda tarayıcı oturumu açın. Desteklenen tarayıcılar ve cihazlar hakkında daha fazla bilgi için bkz: [tarayıcı ve istemci aygıt destek](#browser-and-client-device-support) bu belgedeki.

15. Yeni Windows PowerShell Web Erişimi Web sitesini açın.

    Kök Web sitesi Windows PowerShell Web erişimi klasöre işaret ettiğinden açtığınızda tarayıcı Windows PowerShell Web erişimi oturum açma sayfası görüntülemelidir **https://\<*gateway_server_name* \>**. Eklemek gerekmez **/pswa** URL.

    >**![Not](images/note.jpeg) Not**
    >
    >Yetkilendirme kuralları eklenerek kullanıcılara web sitesi erişimi verilinceye kadar oturum açamazsınız.
    >Daha fazla bilgi için bkz: [kısıtlayıcı yetkilendirme kuralı yapılandırma](#configure-a-restrictive-authorization-rule), bu konu başlığı ve [yetkilendirme kuralları ve güvenlik özellikleri, Windows PowerShell Web erişimi](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>Kısıtlayıcı yetkilendirme kuralı yapılandırma

Windows PowerShell Web erişimi yüklendikten ve ağ geçidi yapılandırıldıktan sonra kullanıcılar oturum açma sayfasını bir tarayıcıda açabilir, ancak açıkça erişim Windows PowerShell Web erişimi yönetici kullanıcılar verene kadar kullanıcılar oturum açamaz. Windows PowerShell Web erişimi erişim denetimi, aşağıdaki tabloda açıklanan Windows PowerShell cmdlet'leri kümesi kullanılarak yönetilir. Yetkilendirme kuralları eklemek veya yönetmek için karşılaştırılabilir GUI yoktur. Windows PowerShell Web erişimi cmdlet'leri hakkında daha ayrıntılı bilgi için cmdlet başvuru konularına bakın [Windows PowerShell Web erişimi cmdlet'leri](cmdlets/web-access-cmdlets.md).

Windows PowerShell Web Erişimi yetkilendirme kuralları ve güvenlik hakkında daha fazla ayrıntı için [yetkilendirme kuralları ve güvenlik özellikleri, Windows PowerShell Web erişimi](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>Kısıtlayıcı yetkilendirme kuralı ekleme

1. Yükseltilmiş kullanıcı haklarıyla bir Windows PowerShell oturumu açmak için aşağıdakilerden birini yapın.

    - Windows masaüstünde, sağ **Windows PowerShell** görev ve ardından **yönetici olarak çalıştır**.

    - Windows **Başlat** ekranında, sağ **Windows PowerShell**ve ardından **yönetici olarak çalıştır**.

2. ![Güvenlik Notu](images/SecurityNote.jpeg) Kullanıcı erişimini oturum yapılandırmaları kullanarak kısıtlamak için isteğe bağlı adım:

    Kurallarınızı içinde zaten kullanacağınız oturum yapılandırmaları var olduğunu doğrulayın. Bunlar henüz oluşturulmadı, içindeki oturum yapılandırmaları oluşturmak için yönergeleri kullanın [about_Session_Configuration_Files](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Aşağıdaki komutu yazın ve sonra basın **Enter**.

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    Bu yetkilendirme kuralı genelde sahip oldukları kullanıcı için kapsamlı bir özel oturum yapılandırması erişimi ile erişim ağınızdaki bir bilgisayara belirli kullanıcı erişimi sağlar '™ s tipik komut dosyası ve cmdlet gereksinimlerine.

    Aşağıdaki örnekte, `Contoso` etki alanında `JSmith` adlı bir kullanıcıya, `Contoso_214` bilgisayarını yönetmek ve `NewAdminsOnly` adlı bir oturum yapılandırması kullanmak için erişim verilir.

        Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4. Kural ya da çalıştırarak oluşturulduğunu doğrulayın `Get-PswaAuthorizationRule` cmdlet'ini veya `Test-PswaAuthorizationRule -UserName '<domain\user>' -ComputerName <computer-name>`.

    Örneğin, `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

Bir yetkilendirme kuralını yapılandırdıktan sonra yetkili kullanıcıların web tabanlı konsolda oturum açması ve Windows PowerShell Web Erişimi'ı kullanmaya başlamak için hazır olursunuz.

## <a name="configure-a-genuine-certificate"></a>Orijinal sertifika yapılandırma

Güvenli bir üretim ortamında her zaman bir sertifika yetkilisi (CA) tarafından imzalanmış geçerli bir SSL sertifikası kullanın. Bu bölümdeki yordam bir CA’dan geçerli bir SSL sertifikası edinme ve uygulama konularını açıklamaktadır.

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a>IIS Yöneticisi'nde bir SSL sertifikası yapılandırmak için

1. IIS Yöneticisi ağaç bölmesinde, Windows PowerShell Web erişimi yüklü olduğu sunucuyu seçin.

2. İçerik bölmesinde, çift tıklayarak **sunucu sertifikaları**.

3. İçinde **Eylemler** bölmesinde, aşağıdakilerden birini yapın. IIS'te sunucu sertifikalarını yapılandırma hakkında daha fazla bilgi için bkz: [IIS 7'de sunucu sertifikalarını yapılandırma](https://technet.microsoft.com/library/cc732230.aspx).

    - Tıklatın **alma** ağınızdaki bir konumdan mevcut, geçerli bir sertifikayı almak için.

    - Tıklatın **sertifika isteği oluştur** gibi bir CA'dan sertifika istemek için [VeriSign](http://www.verisign.com/), [Thawte](https://www.thawte.com/), veya [GeoTrust](https://www.geotrust.com/). Sertifikanın ortak adı, istekte konak üst bilgisi ile eşleşmelidir.

      Örneğin, istemci tarayıcısı isterse http://www.contoso.com/, ortak ad da olmalıdır http://www.contoso.com/. Windows PowerShell Web erişimi ağ geçidini sahip bir sertifika sağlamak için en güvenli ve önerilen seçenek budur.

    - Tıklatın **otomatik olarak imzalanan sertifika oluşturma** hemen kullanabilirsiniz ve daha sonra bir CA tarafından istenirse imzalanmış bir sertifika oluşturmak için. Otomatik olarak imzalanan sertifika için bir kolay ad belirtin **Windows PowerShell Web erişimi**. Bu seçenek güvenli olarak kabul edilmez ve yalnızca özel bir test ortamı için önerilir.

4. Oluşturma veya bir sertifikayı aldıktan sonra sertifikayı uygulandığı Web sitesini seçin (örneğin, **varsayılan Web sitesi**) IIS Yöneticisi ağaç bölmesinde ve ardından **bağlamaları** içinde**Eylemler** bölmesi.

5. İçinde **Site bağlaması Ekle** iletişim kutusunda, eklemek bir **https** bir zaten görüntülenmiyorsa, site için bağlama. Otomatik olarak imzalanan bir sertifika kullanmıyorsanız, bu yordamın 3. adımındaki konak adını belirtin. Otomatik olarak imzalanan bir sertifika kullanıyorsanız, bu adım gerekli değildir.

6. Elde edilen veya bu yordamın 3. adımında oluşturulan sertifikayı seçin ve ardından **Tamam**.

## <a name="using-the-web-based-windows-powershell-console"></a>Web tabanlı Windows PowerShell konsolunu kullanma

Windows PowerShell Web erişimi yüklendikten ve ağ geçidi yapılandırması bu konuda anlatıldığı gibi tamamlandıktan sonra Windows PowerShell web tabanlı Konsolu kullanıma hazır. Web tabanlı konsolunda alma hakkında daha fazla bilgi için bkz [Web tabanlı Windows PowerShell konsolunu kullanma](use-the-web-based-windows-powershell-console.md).

## <a name="see-also"></a>Ayrıca bkz:

- [Internet Information Services (IIS) 7.0 belgeleri](https://technet.microsoft.com/library/cc753433.aspx)
- [IIS Yöneticisi 7.0 Yardımı](https://technet.microsoft.com/library/cc732664.aspx)
- [Web sunucunuzun güvenliğini (IIS 7) yapılandırın](https://technet.microsoft.com/library/cc731278.aspx)
- [IPSec dağıtım kaynakları](https://technet.microsoft.com/network/bb531150)