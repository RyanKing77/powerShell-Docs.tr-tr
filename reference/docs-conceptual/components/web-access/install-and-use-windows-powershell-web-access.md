---
ms.date: 08/23/2017
keywords: PowerShell cmdlet'i
title: windows powershell web erişimi yükleme ve kullanma
ms.openlocfilehash: 53558f9be5065c7f630f06e535ddab4d7ad72d9e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058581"
---
# <a name="install-and-use-windows-powershell-web-access"></a>Windows PowerShell Web erişimi yükleme ve kullanma

Güncelleme tarihi: 5 Kasım 2013'ün (düzenlendi: 23 Ağustos 2017)

Uygulama hedefi: Windows Server 2012 R2, Windows Server 2012

## <a name="introduction"></a>Giriş

İlk Windows Server 2012'de kullanıma sunulan Windows PowerShell Web erişimi bir uzak bilgisayara hedeflenen web tabanlı bir Windows PowerShell Konsolu sağlayan bir Windows PowerShell ağ geçidi olarak davranır. Ancak, BT uzmanları, Windows PowerShell, uzaktan yönetim yazılımı veya tarayıcı eklentisi yüklemesine istemci cihazında gereken bir web tarayıcısında bir Windows PowerShell konsolundan Windows PowerShell komutları ve komut dosyaları çalıştırmak etkinleştirir. Web tabanlı Windows PowerShell konsolunu çalıştırmak için gerekli olan tek şey düzgün yapılandırılmış Windows PowerShell Web erişimi ağ geçidi ve JavaScript destekleyen ve tanımlama bilgilerini kabul eden bir istemci cihaz tarayıcısı.

İstemci cihazlarının örnekler, dizüstü bilgisayarlar, iş olmayan kişisel bilgisayarlar, ödünç alınan bilgisayarlar, tablet bilgisayarlar, web bilgi noktaları, Windows tabanlı bir işletim sistemi ve cep telefonu tarayıcıları çalışmayan bilgisayarları içerir. BT uzmanları bir Internet bağlantısı ve bir web tarayıcısına erişimi olan cihazlardan Windows tabanlı uzak sunucularda kritik yönetim görevlerini gerçekleştirebilirsiniz.

Başarılı ağ geçidi kurulumu ve yapılandırmasının ardından kullanıcılar bir web tarayıcısı kullanarak bir Windows PowerShell Konsolu erişebilir. Kullanıcılar Güvenli Windows PowerShell Web Erişimi Web sitesini açtığında, başarılı kimlik doğrulamasından sonra bir web tabanlı Windows PowerShell Konsolu çalışabilirler.

Windows PowerShell Web erişimi kurulumu ve yapılandırması üç adımlık bir işlemdir şöyledir:

1. [Windows PowerShell Web erişimi yükleme](#install-windows-powershell-web-access-using-powershell-cmdlets)
1. [Ağ geçidini yapılandırma](#configure-the-gateway)
1. [Kısıtlayıcı yetkilendirme kuralı yapılandırma](#configure-a-restrictive-authorization-rule)

Yükleme ve Windows PowerShell Web Erişimi'ı yapılandırmadan önce yükleme hakkında yönergeler içeren tüm bu kılavuzu okumadan güvenli ve Windows PowerShell Web erişimini kaldırma öneririz. [Web tabanlı Windows PowerShell Konsolu](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11)) konu kullanıcılar web tabanlı konsolda nasıl oturum açtığını açıklar ve web tabanlı Windows PowerShell Konsolu arasındaki sınırlamaları ve kapsar ve  **PowerShell.exe** Konsolu. Son kullanıcıların web tabanlı konsolun kimler [tabanlı Windows PowerShell konsolunu kullanma Web](use-the-web-based-windows-powershell-console.md), ancak bu kılavuzun geri kalanını okumaları gerekli değil.

Bu konuda ayrıntılı IIS Web sunucusu işlem yönergelerini sağlamaz; Bu konu başlığında Windows PowerShell Web erişimi ağ geçidini yapılandırmak için gereken adımlar açıklanmaktadır. Yapılandırma ve IIS Web sitelerinin güvenliğini sağlama hakkında daha fazla bilgi için Ayrıca Bkz bölümündeki IIS belge kaynaklarına bakın.

Aşağıdaki diyagramda, Windows PowerShell Web erişimi nasıl çalıştığı gösterilmektedir.

![Windows PowerShell Web erişim diyagramı](images/Windows-PowerShell-Web-Access-diagram.jpg)

## <a name="requirements-for-running-windows-powershell-web-access"></a>Windows PowerShell Web erişimini çalıştırma gereksinimleri

Windows PowerShell Web Erişimi Web sunucusu (IIS), .NET Framework 4.5 ve Windows PowerShell 3.0 veya ağ geçidini çalıştırmak istediğiniz sunucuda çalışıyor olması için Windows PowerShell 4.0 gerektirir. Windows PowerShell Web erişimi, Sunucu Yöneticisi'nin rol ve Özellikler Sihirbazı'nda Sunucu Yöneticisi veya Windows PowerShell dağıtım cmdlet'leri kullanarak Windows Server 2012 R2 çalıştıran bir sunucu veya Windows Server 2012 yükleyebilirsiniz. Sunucu Yöneticisi'ni veya dağıtım cmdlet'lerini kullanarak Windows PowerShell Web erişimi yükleme sırasında gerekli rolleri ve özellikleri yükleme işleminin bir parçası otomatik olarak eklenir.

Windows PowerShell Web erişimi, uzak kullanıcıların bir web tarayıcısında Windows PowerShell kullanarak kuruluşunuzdaki bilgisayarlara erişmesine olanak sağlar. Windows PowerShell Web erişimi kullanışlı ve güçlü yönetim aracı olsa da, web tabanlı erişim güvenlik riskleri doğurur ve mümkün olduğunca güvenli bir şekilde yapılandırılmış olması gerekir. Windows PowerShell Web erişimi ağ geçidini yapılandıran yöneticilerin kullanılabilir güvenlik katmanlarını kullanın, her iki cmdlet tabanlı yetkilendirme kuralları Web sunucusu (kullanılabilir olan katmanları Windows PowerShell Web erişimi ve güvenlik dahil öneririz IIS) ve üçüncü taraf uygulamaları. Bu belgeler, yalnızca test ortamları için önerilen güvensiz örnekleri hem de yanı sıra, güvenli dağıtımlar için önerilen örnekleri içerir.

## <a name="browser-and-client-device-support"></a>Tarayıcı ve istemci cihaz desteği

Windows PowerShell Web erişimi, aşağıdaki Internet tarayıcılarını destekler. Mobil tarayıcılar resmi olarak desteklemiyor olsa da, birçok web tabanlı Windows PowerShell konsolunu çalıştırmak mümkün olabilir.
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

## <a name="recommended-quick-deployment"></a>Önerilen hızlı dağıtım

Ya da Windows PowerShell cmdlet'lerini kullanarak veya Ekle roller ve Özellikler Sunucu Yöneticisi içinde açılan Sihirbazı'nı kullanarak, Windows Server 2012 R2 çalıştıran bir sunucu veya Windows Server 2012 üzerinde Windows PowerShell Web erişimi ağ geçidi yükleyebilirsiniz. Hızlı yükleme ve yapılandırma için bu bölümde açıklandığı gibi Windows PowerShell cmdlet'lerini kullanın.

1. [Windows PowerShell Web erişimi yükleme](#install-windows-powershell-web-access-using-powershell-cmdlets)
1. [Ağ geçidini yapılandırma](#configure-the-gateway)
1. [Kısıtlayıcı yetkilendirme kuralı yapılandırma](#configure-a-restrictive-authorization-rule)

### <a name="install-windows-powershell-web-access-using-powershell-cmdlets"></a>PowerShell cmdlet'lerini kullanarak Windows PowerShell Web erişimi yükleme

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a>Windows PowerShell cmdlet'lerini kullanarak Windows PowerShell Web erişimi yüklemek için

1. Bir Windows PowerShell oturumu yükseltilmiş kullanıcı haklarıyla açmak için aşağıdakilerden birini yapın.

   - Windows masaüstünde, sağ **Windows PowerShell** görev ve ardından **yönetici olarak çalıştır**.
   - Windows üzerinde **Başlat** ekranında, sağ **Windows PowerShell**ve ardından **yönetici olarak çalıştır**.

   > [!NOTE]
   > Windows PowerShell 3.0 ve 4.0, modülün parçası olan cmdlet'leri çalıştırmadan önce Windows PowerShell oturumuna Sunucu Yöneticisi'ni cmdlet modülünün içeri aktarmak için gerek yoktur. Bir modül, modülün parçası olan bir cmdlet'i ilk çalıştırıldığında otomatik olarak aktarılır.
   > Ayrıca, Windows PowerShell cmdlet'leri büyük küçük harfe duyarlı değildir.

1. Aşağıdaki komutu yazın ve ardından basın **Enter**burada *bilgisayar_adı* üzerinde Windows PowerShell Web erişimi, yüklemek istediğiniz varsa bir uzak bilgisayarı temsil eder. `-Restart` Parametre otomatik olarak hedef sunucuları yeniden başlatır gerekirse.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart`

   > [!NOTE]
   > Windows PowerShell cmdlet'lerini kullanarak Windows PowerShell Web erişimi yükleme, Web sunucusu (IIS) yönetim araçları varsayılan olarak eklemez. Yönetim Araçları Windows PowerShell Web erişimi ağ geçidiyle aynı sunucuya yüklemek istiyorsanız, ekleme `-IncludeManagementTools` (Bu adımda anlatıldığı gibi) yükleme komutuna parametre. Windows PowerShell Web Erişimi Web sitesini uzak bir bilgisayardan yönetiyorsanız, IIS Yöneticisi ek bileşenini yükleyerek yüklemenizi [uzak sunucu yönetim araçları için Windows 8.1](https://www.microsoft.com/en-us/download/details.aspx?id=39296) veya [uzak sunucu yönetim Windows 8 için Araçlar](https://www.microsoft.com/en-us/download/details.aspx?id=28972) tarafından geçidini yönetmek istediğiniz bilgisayarda.

   Çevrimdışı bir VHD'ye rol ve Özellikler yüklemek için her ikisi de eklemelisiniz `-ComputerName` parametresi ve `-VHD` parametresi. `-ComputerName` Parametresi VHD'nin bağlanacağı sunucunun adını içerir ve `-VHD` parametresi de belirtilen sunucuda VHD dosyasının yolunu içerir.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart`

1. Yükleme tamamlandığında, Windows PowerShell Web erişimi çalıştırarak hedef sunucularda yüklü olmadığını doğrulayın `Get-WindowsFeature` cmdlet'i ile açılmış bir Windows PowerShell konsolunda bir hedef sunucuda, yükseltilmiş kullanıcı hakları. Windows PowerShell Web erişimi sunucu yöneticisi konsolunda, hedef sunucu seçerek yüklendiğini doğrulayabilirsiniz **tüm sunucuları** sayfası ve ardından görüntüleyerek **roller ve Özellikler** Seçili sunucu için bir kutucuk. Windows PowerShell Web erişimi için Benioku dosyasını da görüntüleyebilirsiniz.

1. Windows PowerShell Web erişimi yüklendikten sonra ağ geçidi için temel, gerekli kurulum yönergelerini içeren Benioku dosyasını gözden istenir. Bu kurulum yönergeleri aşağıdaki bölümde de olan [ağ geçidini yapılandırma](#configure-the-gateway). Benioku dosyası yolu `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>Ağ geçidini yapılandırma

**Install-PswaWebApplication** cmdlet, Windows PowerShell Web erişim almak için hızlı bir yoludur. Eklemesi mümkün olsa da `UseTestCertificate` parametresi `Install-PswaWebApplication` test için otomatik olarak imzalanan bir SSL sertifikası yüklemek için cmdlet'i amacıyla, bu güvenli; güvenli bir üretim ortamı için her zaman tarafından imzalanmış geçerli bir SSL sertifikası kullanan bir Sertifika yetkilisi (CA). Yöneticiler, IIS Yöneticisi konsolunu kullanarak test sertifikası kendi seçtikleri imzalı bir sertifika ile değiştirebilirsiniz.

Çalıştırarak Windows PowerShell Web erişimi web uygulaması yapılandırmasını tamamlayabilirsiniz `Install-PswaWebApplication` cmdlet'ini veya IIS Yöneticisi'nde GUI tabanlı yapılandırma adımları gerçekleştirerek.
Varsayılan olarak, cmdlet web uygulaması yükler **pswa** (ve ona ait bir uygulama havuzu **pswa_pool**), **varsayılan Web sitesi** kapsayıcı, IIS Yöneticisi'nde; gösterildiği gibi isterseniz, web uygulamasının varsayılan site kapsayıcısını değiştirmesini isteyebilirsiniz bildirebilirsiniz. IIS Yöneticisi bağlantı noktasını veya Güvenli Yuva Katmanı (SSL) sertifikasını değiştirme gibi web uygulamaları için kullanılabilen yapılandırma seçenekleri sunar.

> **![Güvenlik Notu](images/securitynote.jpeg) güvenlik notu** yöneticilerin ağ geçidini bir CA tarafından imzalanmış geçerli bir sertifika yapılandırmanız önerilir.

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a>Windows PowerShell Web erişimi ağ geçidini Install-PswaWebApplication kullanarak bir test sertifikası ile yapılandırmak için

1. Bir Windows PowerShell oturumu açmak için aşağıdakilerden birini yapın.

   - Windows masaüstünde, sağ **Windows PowerShell** görev.
   - Windows üzerinde **Başlat** ekranında **Windows PowerShell**.

2. Aşağıdaki komutu yazın ve ardından basın **Enter**.

   `Install-PswaWebApplication -UseTestCertificate`

   > **![Güvenlik Notu](images/securitynote.jpeg) güvenlik notu** `UseTestCertificate` parametre özel test ortamında yalnızca kullanılmalıdır. Güvenli bir üretim ortamı için CA tarafından imzalanmış geçerli bir sertifika kullanmanızı öneririz.

   Cmdlet'ini çalıştırarak IIS varsayılan Web sitesi kapsayıcı içindeki Windows PowerShell Web erişimi web uygulaması yükler. Cmdlet varsayılan Web sitesinde Windows PowerShell Web erişimi çalıştırmak için gerekli altyapıyı oluşturur `https://<server_name>/pswa`. Web uygulamasını farklı bir Web sitesine yüklemek için Web sitesi adı ekleyerek sağlayın `WebSiteName` parametresi. Web uygulamasının adını değiştirmek için (varsayılan değer `pswa`), ekleme `WebApplicationName` parametresi.

   Aşağıdaki ayarlar cmdlet çalıştırılarak yapılandırılır. Bu el ile IIS Yöneticisi konsolunda, isterseniz değiştirebilirsiniz.

   - Path: /pswa
   - ApplicationPool: pswa_pool
   - EnabledProtocols: http
   - PhysicalPath: %windir%/Web/PowerShellWebAccess/wwwroot

   **Örnek**: `Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate`

   Bu örnekte, sonuçta elde edilen Web sitesi için Windows PowerShell Web erişimi olan `https://<server_name>/myWebApp`.

   > [!NOTE]
   > Yetkilendirme kuralları ekleyerek, kullanıcıların Web sitesi erişimi verilinceye kadar oturum açamazsınız. Daha fazla bilgi için [kısıtlayıcı yetkilendirme kuralı yapılandırma](#configure-a-restrictive-authorization-rule) ve [yetkilendirme kuralları ve güvenlik özellikleri, Windows PowerShell Web erişimi](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a>Windows PowerShell Web erişimi ağ geçidini Install-PswaWebApplication ve IIS Yöneticisi kullanarak orijinal bir sertifika ile yapılandırmak için

1. Bir Windows PowerShell oturumu açmak için aşağıdakilerden birini yapın.

   - Windows masaüstünde, sağ **Windows PowerShell** görev.
   - Windows üzerinde **Başlat** ekranında **Windows PowerShell**.

2. Aşağıdaki komutu yazın ve ardından basın **Enter**.

   `Install-PswaWebApplication`

   Aşağıdaki ağ geçidi ayarları cmdlet çalıştırılarak yapılandırılır. Bu el ile IIS Yöneticisi konsolunda, isterseniz değiştirebilirsiniz. İçin değerler belirtebilirsiniz `WebsiteName` ve `WebApplicationName` parametrelerinin `Install-PswaWebApplication` cmdlet'i.

   - Path: /pswa
   - ApplicationPool: pswa_pool
   - EnabledProtocols: http
   - PhysicalPath: %windir%/Web/PowerShellWebAccess/wwwroot

3. Aşağıdakilerden birini yaparak IIS Yöneticisi konsolunu açın.

   - Tıklayarak Windows masaüstünde, Sunucu Yöneticisi'ni başlatın **Sunucu Yöneticisi'ni** Windows görev çubuğunda. Üzerinde **Araçları** Sunucu Yöneticisi ' nde menüsünü **Internet Information Services (IIS) Yöneticisi'ni**.
   - Windows üzerinde **Başlat** ekranında **Sunucu Yöneticisi**.

4. IIS Yöneticisi ağaç bölmesinde, Windows PowerShell Web Erişimi'nın yüklendiği kadar sunucu düğümünü genişletin **siteleri** klasördür görünür. Genişletin **siteleri** klasör.

5. Windows PowerShell Web erişimi web uygulamasını yüklediğiniz Web sitesini seçin.
   İçinde **eylemleri** bölmesinde tıklayın **bağlamaları**.

6. İçinde **Site bağlamasını** iletişim kutusu, tıklayın **Ekle**.

7. İçinde **Site bağlaması Ekle** iletişim kutusundaki **türü** alanın, Seç **https**.

8. İçinde **SSL sertifikası** alanında, aşağı açılan menüden imzalı sertifikanızı seçin.
   **Tamam**’a tıklayın. Bkz: [IIS Yöneticisi'nde bir SSL sertifikası yapılandırma](#to-configure-an-ssl-certificate-in-iis-manager) bir sertifikanın nasıl alınacağı hakkında daha fazla bilgi için bu konuda.

   Windows PowerShell Web erişimi web uygulaması, imzalanmış bir SSL sertifikası kullanmak üzere yapılandırılmıştır.

   Windows PowerShell Web erişimi açarak erişebileceğiniz `https://<server_name>/pswa` bir tarayıcı penceresinde.

   > [!NOTE]
   > Yetkilendirme kuralları ekleyerek, kullanıcıların Web sitesi erişimi verilinceye kadar oturum açamazsınız. Daha fazla bilgi için [kısıtlayıcı yetkilendirme kuralı yapılandırma](#configure-a-restrictive-authorization-rule), bu konuda, ve [yetkilendirme kuralları ve güvenlik özellikleri, Windows PowerShell Web erişimi](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>Kısıtlayıcı yetkilendirme kuralı yapılandırma

Windows PowerShell Web erişimi yüklendikten ve ağ geçidi yapılandırıldıktan sonra kullanıcılar oturum açma sayfasını bir tarayıcıda açabilir, ancak açıkça erişim Windows PowerShell Web erişimi yönetici kullanıcılar verene kadar oturum olamaz. Windows PowerShell Web erişimi erişim denetimi aşağıdaki tabloda açıklanan Windows PowerShell cmdlet'leri kümesi kullanılarak yönetilir. Ekleme veya yetkilendirme kuralları yönetmek için karşılaştırılabilir GUI yoktur. Windows PowerShell Web erişimi cmdlet'leri hakkında daha ayrıntılı bilgi için cmdlet başvuru konularına bakın [Windows PowerShell Web erişimi cmdlet'leri](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Windows PowerShell Web Erişimi yetkilendirme kuralları ve güvenlik hakkında daha fazla ayrıntı için [yetkilendirme kuralları ve güvenlik özellikleri, Windows PowerShell Web erişimi](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>Kısıtlayıcı yetkilendirme kuralı eklemek için

1. Bir Windows PowerShell oturumu yükseltilmiş kullanıcı haklarıyla açmak için aşağıdakilerden birini yapın.

   - Windows masaüstünde, sağ **Windows PowerShell** görev ve ardından **yönetici olarak çalıştır**.
   - Windows üzerinde **Başlat** ekranında, sağ **Windows PowerShell**ve ardından **yönetici olarak çalıştır**.

2. Kullanıcı erişimini oturum yapılandırmaları kullanarak kısıtlamak için isteğe bağlı adım: Kullanmak istediğiniz kurallarınızda zaten oturum yapılandırmaları mevcut olduğunu doğrulayın. Bunlar henüz oluşturulmadı, içindeki oturum yapılandırmaları oluşturmak için yönergeleri kullanın [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Aşağıdaki komutu yazın ve ardından basın **Enter**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Bu yetkilendirme kuralı genellikle, kullanıcının tipik komut dosyası için kapsamı belirli bir oturum yapılandırması erişimi ile erişimleri ve cmdlet gereksinimlerine ağ üzerinde bir bilgisayara bir kullanıcıya erişim sağlar.

   Aşağıdaki örnekte adlı bir kullanıcıya `JSmith` içinde `Contoso` etki alanı bilgisayarı yönetmek için erişim verildi `Contoso_214`ve adlı bir oturum yapılandırması kullanmak `NewAdminsOnly`.

   `Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

4. Kural çalıştırılarak oluşturulduğunu doğrulayın `Get-PswaAuthorizationRule` cmdlet'ini veya `Test-PswaAuthorizationRule -UserName <domain\user> -ComputerName <computer-name>`

   Örneğin, `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

Bir yetkilendirme kuralını yapılandırdıktan sonra yetkili kullanıcıların web tabanlı konsolda oturum açması ve Windows PowerShell Web Erişimi'ı kullanmaya başlamak için hazır olursunuz.

## <a name="custom-deployment"></a>Özel dağıtım

Windows PowerShell Web erişimi ağ geçidini, Sunucu Yöneticisi'nde rol ve Özellik Ekleme Sihirbazı'nı kullanarak Windows Server 2012 veya Windows Server 2012 R2 çalıştıran bir sunucuya yükleyebilirsiniz.
Windows PowerShell Web erişimi yüklendikten sonra IIS Yöneticisi'nde ağ geçidi yapılandırmasını özelleştirebilirsiniz.

### <a name="install-windows-powershell-web-access-using-the-add-roles-and-features-wizard"></a>Windows PowerShell Web Erişimi rol ve Özellik Ekleme Sihirbazı'nı kullanarak yükleme

1. Sunucu Yöneticisi zaten açıksa sonraki adıma geçin. Sunucu Yöneticisi'ni zaten açık değilse aşağıdakilerden birini yaparak açın.

   - Tıklayarak Windows masaüstünde, Sunucu Yöneticisi'ni başlatın **Sunucu Yöneticisi'ni** Windows görev çubuğunda.
   - Windows üzerinde **Başlat** ekranında **Sunucu Yöneticisi**.

2. Üzerinde **Yönet** menüsünü tıklatın **rol ve Özellik Ekle**.

3. **Yükleme türünü seçin** sayfasında **Rol tabanlı veya özellik tabanlı yükleme**’yi seçin.
   **İleri**’ye tıklayın.

4. Üzerinde **hedef sunucuyu seçin** sayfasında, sunucu havuzundan bir sunucu seçin ya da çevrimdışı bir VHD seçin. Çevrimdışı bir VHD'yi hedef sunucunuz olarak seçmek için önce VHD'nin bağlanacağı sunucuyu seçin ve ardından VHD dosyasını seçin. Sunucuları sunucu havuzunuza ekleme hakkında daha fazla bilgi için Sunucu Yöneticisi Yardım'a bakın. Hedef sunucuyu seçtikten sonra tıklayın **sonraki**.

5. Üzerinde **özellikleri seçin** sayfasında sihirbazın genişletin **Windows PowerShell**ve ardından **Windows PowerShell Web erişimi**.

6. .NET Framework 4.5 ve Web sunucusu (IIS) rol hizmetleri gibi gerekli özellikleri eklemeniz istenir unutmayın. Gerekli özellikleri ekleyin ve devam edin.

   > [!NOTE]
   > Rol ve Özellik Ekleme Sihirbazı'nı kullanarak Windows PowerShell Web erişimi yükleme, Web sunucusu (IIS Yöneticisi ek bileşeniyle birlikte IIS), yükler. Rol ve Özellik Ekleme Sihirbazı kullanıyorsanız ek bileşenini ve diğer IIS Yönetim Araçları varsayılan olarak yüklenir. Aşağıdaki yordamda açıklandığı gibi Windows PowerShell cmdlet'lerini kullanarak Windows PowerShell Web erişimi yükleme yapıyorsanız, Yönetim Araçları varsayılan olarak eklenmez.

7. Üzerinde **yükleme seçimlerini onaylayın** sayfasında, özellik dosyaları adım 4 ' te seçtiğiniz hedef sunucuda Windows PowerShell Web erişimi depolanmamış için tıklarsanız **alternatifkaynakyolbelirtme**ve özellik dosyalarının yolunu belirtin. ' A tıklayıp **yükleme**.

8. Tıkladıktan sonra **yükleme**, **yükleme ilerleme durumu** sayfası, yükleme ilerleme durumunu, sonuçları ve uyarılar, hatalar veya yükleme sonrası yapılandırma adımları gibi iletileri görüntüler Windows PowerShell Web erişimi için gereklidir. Windows PowerShell Web erişimi yüklendikten sonra ağ geçidi için temel, gerekli kurulum yönergelerini içeren Benioku dosyasını gözden istenir. Bu konu başlığında bu yönergeleri de dahil edilir. Benioku dosyası yolu `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>Ağ geçidini yapılandırma

Bu bölümdeki yönergeler, Windows PowerShell Web erişimi web uygulamasını yüklemek için bir alt dizinde ve değil, Web sitesinin kök dizininde içindir. Bu yordamı tarafından gerçekleştirilen eylemlerin GUI tabanlı eşdeğeridir `Install-PswaWebApplication` cmdlet'i. Bu bölümde, Windows PowerShell Web erişimi ağ geçidini bir kök Web sitesi yapılandırmak için IIS Yöneticisi'ni kullanmak için yönergeleri de içerir.

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a>IIS Yöneticisi kullanarak mevcut bir Web sitesinde ağ geçidini yapılandırmak için

1. Aşağıdakilerden birini yaparak IIS Yöneticisi konsolunu açın.

   - Tıklayarak Windows masaüstünde, Sunucu Yöneticisi'ni başlatın **Sunucu Yöneticisi'ni** Windows görev çubuğunda. Üzerinde **Araçları** Sunucu Yöneticisi ' nde menüsünü **Internet Information Services (IIS) Yöneticisi'ni**.
   - Windows üzerinde **Başlat** ekranında, adının bir kısmını **Internet Information Services (IIS) Yöneticisi'ni**. İçinde gösterildiğinde kısayola tıklayın **uygulamaları** sonuçları.

2. Windows PowerShell Web erişimi için yeni bir uygulama havuzu oluşturun. IIS Yöneticisi ağaç bölmesinde, Ağ Geçidi sunucusunun düğümünü genişletin **uygulama havuzları**, tıklatıp **uygulama havuzu Ekle** içinde **eylemleri** bölmesi.

3. Adlı yeni bir uygulama havuzu Ekle **pswa_pool**, veya başka bir ad belirtin. **Tamam**’a tıklayın.

4. IIS Yöneticisi ağaç bölmesinde, Windows PowerShell Web Erişimi'nın yüklendiği kadar sunucu düğümünü genişletin **siteleri** klasördür görünür. Seçin **siteleri** klasör.

5. Web sitesini sağ tıklayın (örneğin, **varsayılan Web sitesi**) için Windows PowerShell Web Erişimi Web sitesini ekleyin ve ardından istediğiniz **uygulama Ekle**.

6. İçinde **diğer** alanına pswa yazın ya da başka bir diğer ad belirtin. Diğer sanal dizin adı olur. Örneğin, **pswa** Bu adımda belirtilen diğer adı aşağıdaki URL'yi temsil eder: `https://<server-name>/pswa`.

7. İçinde **uygulama havuzu** alanında, adım 3'te oluşturduğunuz uygulama havuzunu seçin.

8. İçinde **fiziksel yolu** alan, için uygulamanın konumuna göz atın. Varsayılan konumu kullanabileceğiniz `$env:windir/Web/PowerShellWebAccess/wwwroot`. **Tamam**’a tıklayın.

9. Yordamdaki adımları [IIS Yöneticisi'nde bir SSL sertifikası yapılandırma](#to-configure-an-ssl-certificate-in-iis-manager) bu konuda.

10. ![](images/SecurityNote.jpeg) İsteğe bağlı güvenlik adımı:

    Ağaç bölmesinde seçilen Web sitesi çift **SSL ayarları** içerik bölmesinde.
    Seçin **SSL iste**ve ardından **eylemleri** bölmesinde tıklayın **Uygula**. İsteğe bağlı olarak **SSL ayarları** bölmesinde, Windows PowerShell Web Erişimi Web sitesine bağlanan kullanıcıların istemci sertifikaları olmasını isteyebilir. İstemci sertifikaları bir istemci cihaz kullanıcısının kimliğini doğrulamaya yardımcı olur. İstemci sertifika istemenin Windows PowerShell Web erişimi güvenliğini nasıl artırabilir hakkında daha fazla bilgi için bkz. [yetkilendirme kuralları ve güvenlik özellikleri, Windows PowerShell Web erişimi](authorization-rules-and-security-features-of-windows-powershell-web-access.md) bu kılavuzdaki.

11. Bir istemci cihazda tarayıcı oturumu açın. Desteklenen tarayıcılar ve cihazlar hakkında daha fazla bilgi için bkz: [tarayıcı ve istemci cihaz desteği](#browser-and-client-device-support) bu konuda.

12. Yeni Windows PowerShell Web Erişimi Web sitesini açın **https://\<*Ağ Geçidi sunucu adını*\>/pswa**.

    Tarayıcı, Windows PowerShell Web erişimi konsol oturum açma sayfası görüntülemelidir.

    > [!NOTE]
    > Yetkilendirme kuralları ekleyerek, kullanıcıların Web sitesi erişimi verilinceye kadar oturum açamazsınız. Daha fazla bilgi için [kısıtlayıcı yetkilendirme kuralı yapılandırma](#configure-a-restrictive-authorization-rule), bu konuda, ve [yetkilendirme kuralları ve güvenlik özellikleri, Windows PowerShell Web erişimi](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

13. Yükseltilmiş kullanıcı haklarıyla (yönetici olarak çalıştır) ile açılmış bir Windows PowerShell oturumunda, aşağıdaki betiği çalıştırarak *application_pool_name* 3. adımda oluşturduğunuz uygulama havuzu adını temsil eder Uygulama havuzu yetkilendirme dosyasına erişim hakları vermek için.

    ```powershell
    $applicationPoolName = "<application_pool_name>"
    $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
    c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
    ```

    Yetkilendirme dosyasındaki mevcut erişim haklarını görüntülemek için aşağıdaki komutu çalıştırın:

    ```powershell
    c:\windows\system32\icacls.exe $authorizationFile
    ```

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a>IIS Yöneticisi kullanarak ağ geçidini bir test sertifikası ile bir kök Web sitesi olarak yapılandırmak için

1. Aşağıdakilerden birini yaparak IIS Yöneticisi konsolunu açın.

   - Tıklayarak Windows masaüstünde, Sunucu Yöneticisi'ni başlatın **Sunucu Yöneticisi'ni** Windows görev çubuğunda. Üzerinde **Araçları** Sunucu Yöneticisi ' nde menüsünü **Internet Information Services (IIS) Yöneticisi'ni**.
   - Windows üzerinde **Başlat** ekranında, adının bir kısmını **Internet Information Services (IIS) Yöneticisi'ni**. İçinde gösterildiğinde kısayola tıklayın **uygulamaları** sonuçları.

1. IIS Yöneticisi ağaç bölmesinde, Windows PowerShell Web Erişimi'nın yüklendiği kadar sunucu düğümünü genişletin **siteleri** klasördür görünür. Seçin **siteleri** klasör.

1. İçinde **eylemleri** bölmesinde tıklayın **Web sitesi Ekle**.

1. Web sitesi için bir ad yazın **Windows PowerShell Web erişimi**.

1. Bir uygulama havuzu için yeni Web sitesi otomatik olarak oluşturulur. Farklı bir uygulama havuzu kullanmak için **seçin** yeni Web sitesiyle ilişkilendirilecek bir uygulama havuzu seçin. Diğer uygulama havuzunu seçin **uygulama havuzu Seç** iletişim kutusunu ve ardından **Tamam**.

1. İçinde **fiziksel yolu** metin kutusunda, Windir%/Web/PowerShellWebAccess/Wwwroot için gidin.

1. İçinde **türü** alanını **bağlama** alanında **https**.

1. Zaten başka bir site veya uygulama tarafından kullanılmadığından ve Web sitesi bağlantı noktası numarası atayın.
   Açık bağlantı noktalarını bulmak için çalıştırabilirsiniz **netstat** bir komut istemi penceresinde komutu. Varsayılan bağlantı noktası numarası 443 ' dir.

   Varsayılan bağlantı noktası 443 başka bir Web sitesi zaten kullanılıyorsa veya bağlantı noktası numarasını değiştirmek için başka güvenlik nedenleriniz varsa değiştirin. Ağ geçidi sunucunuzda çalışan başka bir Web sitesi seçtiğiniz bağlantı noktasını kullanıyorsa,'a tıkladığınızda bir uyarı görüntülenir **Tamam** içinde **Web sitesi Ekle** iletişim kutusu. Windows PowerShell Web Erişimi'ni çalıştırmak için kullanılmayan bir bağlantı noktası kullanmanız gerekir.

1. İsteğe bağlı olarak, kuruluşunuz için gerekirse, kuruluş ve kullanıcılar gibi anlamlı bir konak adı belirtin **`www.contoso.com`**. **Tamam**’a tıklayın.

1. Daha güvenli bir üretim ortamı için CA tarafından imzalanmış geçerli bir sertifikanın belirtilmesi önerilir. Kullanıcılar yalnızca Windows PowerShell Web erişimi için bir HTTPS Web sitesi kurabildiğinden bir SSL sertifikası sağlamanız gerekir. Bkz: [IIS Yöneticisi'nde bir SSL sertifikası yapılandırma](#to-configure-an-ssl-certificate-in-iis-manager) bir sertifikanın nasıl alınacağı hakkında daha fazla bilgi için bu konuda.

1. Tıklayın **Tamam** kapatmak için **Web sitesi Ekle** iletişim kutusu.

1. Yükseltilmiş kullanıcı haklarıyla (yönetici olarak çalıştır) ile açılmış bir Windows PowerShell oturumunda, aşağıdaki betiği çalıştırarak _application_pool_name_ adım 4 ' te oluşturduğunuz uygulama havuzu adını temsil eder Uygulama havuzu yetkilendirme dosyasına erişim hakları vermek için.

   ```powershell
   $applicationPoolName = "<application_pool_name>"
   $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
   c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
   ```

   Yetkilendirme dosyasındaki mevcut erişim haklarını görüntülemek için aşağıdaki komutu çalıştırın:

   ```powershell
   c:\windows\system32\icacls.exe $authorizationFile
   ```

1. IIS Yöneticisi ağaç bölmesinde seçili yeni Web sitesi ile tıklayın **Başlat** içinde **eylemleri** bölmesinde Web sitesini başlatmak için.

1. Bir istemci cihazda tarayıcı oturumu açın. Desteklenen tarayıcılar ve cihazlar hakkında daha fazla bilgi için bkz: [tarayıcı ve istemci cihaz desteği](#browser-and-client-device-support) bu belgedeki.

1. Yeni Windows PowerShell Web Erişimi Web sitesini açın.

   Kök Web sitesi için Windows PowerShell Web erişimi klasörünü işaret ettiğinden, açtığınızda tarayıcı Windows PowerShell Web erişimi oturum açma sayfası görüntülemelidir `https://<gateway_server_name>`. Ekleme gerekmez **/pswa** URL'si.

   > [!NOTE]
   > Yetkilendirme kuralları ekleyerek, kullanıcıların Web sitesi erişimi verilinceye kadar oturum açamazsınız. Daha fazla bilgi için [kısıtlayıcı yetkilendirme kuralı yapılandırma](#configure-a-restrictive-authorization-rule), bu konuda, ve [yetkilendirme kuralları ve güvenlik özellikleri, Windows PowerShell Web erişimi](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configuring-a-restrictive-authorization-rule"></a>Kısıtlayıcı yetkilendirme kuralı yapılandırma

Windows PowerShell Web erişimi yüklendikten ve ağ geçidi yapılandırıldıktan sonra kullanıcılar oturum açma sayfasını bir tarayıcıda açabilir, ancak açıkça erişim Windows PowerShell Web erişimi yönetici kullanıcılar verene kadar oturum olamaz. Windows PowerShell Web erişimi erişim denetimi aşağıdaki tabloda açıklanan Windows PowerShell cmdlet'leri kümesi kullanılarak yönetilir. Ekleme veya yetkilendirme kuralları yönetmek için karşılaştırılabilir GUI yoktur. Windows PowerShell Web erişimi cmdlet'leri hakkında daha ayrıntılı bilgi için cmdlet başvuru konularına bakın [Windows PowerShell Web erişimi cmdlet'leri](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Windows PowerShell Web Erişimi yetkilendirme kuralları ve güvenlik hakkında daha fazla ayrıntı için [yetkilendirme kuralları ve güvenlik özellikleri, Windows PowerShell Web erişimi](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="adding-a-restrictive-authorization-rule"></a>Kısıtlayıcı yetkilendirme kuralı ekleme

1. Bir Windows PowerShell oturumu yükseltilmiş kullanıcı haklarıyla açmak için aşağıdakilerden birini yapın.

   - Windows masaüstünde, sağ **Windows PowerShell** görev ve ardından **yönetici olarak çalıştır**.
   - Windows üzerinde **Başlat** ekranında, sağ **Windows PowerShell**ve ardından **yönetici olarak çalıştır**.

1. ![Güvenlik Notu](images/SecurityNote.jpeg) Kullanıcı erişimini oturum yapılandırmaları kullanarak kısıtlamak için isteğe bağlı adım:

   Kullanmak istediğiniz kurallarınızda zaten oturum yapılandırmaları mevcut olduğunu doğrulayın. Bunlar henüz oluşturulmadı, içindeki oturum yapılandırmaları oluşturmak için yönergeleri kullanın [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Aşağıdaki komutu yazın ve ardından basın **Enter**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Bu yetkilendirme kuralı belirli bir bilgisayar erişmesine izin verir, genellikle sahip oldukları erişimi kullanıcıya kapsayan belirli bir oturum yapılandırması erişimi ile ağ '™ s tipik komut dosyası ve cmdlet gereksinimlerine.

   Aşağıdaki örnekte adlı bir kullanıcıya `JSmith` içinde `Contoso` etki alanı bilgisayarı yönetmek için erişim verildi `Contoso_214`ve adlı bir oturum yapılandırması kullanmak `NewAdminsOnly`.

   `Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

1. Kural çalıştırılarak oluşturulduğunu doğrulayın `Get-PswaAuthorizationRule` cmdlet'ini veya `Test-PswaAuthorizationRule -UserName '<domain\user>' -ComputerName <computer-name>`.

   Örneğin, `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

   Bir yetkilendirme kuralını yapılandırdıktan sonra yetkili kullanıcıların web tabanlı konsolda oturum açması ve Windows PowerShell Web Erişimi'ı kullanmaya başlamak için hazır olursunuz.

## <a name="configure-a-genuine-certificate"></a>Orijinal sertifika yapılandırma

Güvenli bir üretim ortamı için her zaman bir sertifika yetkilisi (CA) tarafından imzalanmış geçerli bir SSL sertifikası kullanın. Bu bölümdeki yordamı, almak ve bir CA'dan geçerli bir SSL sertifikası geçerli açıklar.

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a>IIS Yöneticisi'nde bir SSL sertifikası yapılandırma

1. IIS Yöneticisi ağaç bölmesinde, Windows PowerShell Web erişimi yüklü olduğu sunucuyu seçin.

1. İçerik bölmesinde çift tıklayarak **sunucu sertifikaları**.

1. İçinde **eylemleri** bölmesi, aşağıdakilerden birini yapın. IIS'de sunucu sertifikalarını yapılandırma hakkında daha fazla bilgi için bkz. [IIS 7'de sunucu sertifikalarını yapılandırma](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).

   - Tıklayın **alma** ağınızdaki bir konumdan mevcut, geçerli bir sertifikayı içeri aktarmak için.
   - Tıklayın **sertifika isteği oluştur** gibi bir CA'dan bir sertifika istemeniz [VeriSign](https://www.verisign.com/), [Thawte](https://www.thawte.com/), veya [GeoTrust](https://www.geotrust.com/). Sertifikanın ortak adı, istekteki konak üst bilgisi eşleşmesi gerekir.

     Örneğin, istemci tarayıcısı isterse `http://www.contoso.com/`, ortak ad ayrıca olmalıdır `http://www.contoso.com/`. Windows PowerShell Web erişimi ağ geçidini bir sertifikasıyla sağlamak için en güvenli ve önerilen seçenek budur.

   - Tıklayın **otomatik olarak imzalanan sertifika oluşturma** hemen kullanabilirsiniz ve daha sonra bir CA tarafından istenirse, oturum açmış olan bir sertifika oluşturmak için. Otomatik olarak imzalanan sertifika için bir kolay ad belirtin **Windows PowerShell Web erişimi**. Bu seçenek güvenli olarak kabul edilmez ve yalnızca özel bir test ortamı için önerilir.

1. Oluşturma veya bir sertifikayı aldıktan sonra sertifikayı uygulandığı Web sitesini seçin (örneğin, **varsayılan Web sitesi**) IIS Yöneticisi ağaç bölmesinde ve ardından **bağlamaları** içinde**Eylemleri** bölmesi.

1. İçinde **Site bağlaması Ekle** iletişim kutusunda bir **https** biri zaten görüntülenmiyorsa, site için bağlama. Kendinden imzalı bir sertifika kullanmıyorsanız, bu yordamın 3. adımındaki konak adı belirtin. Kendinden imzalı bir sertifika kullanıyorsanız, bu adım gerekli değildir.

1. Elde edilen veya bu yordamın 3. adımında oluşturulan sertifikayı seçin ve ardından **Tamam**.

## <a name="using-the-web-based-windows-powershell-console"></a>Web tabanlı Windows PowerShell konsolunu kullanma

Windows PowerShell Web erişimi yüklendikten ve ağ geçidi yapılandırması, bu konuda anlatıldığı gibi tamamlandıktan sonra web tabanlı Windows PowerShell konsolunu kullanmak hazırdır. Web tabanlı konsolda alma hakkında daha fazla bilgi için bkz [Web tabanlı Windows PowerShell Konsolu](use-the-web-based-windows-powershell-console.md).

## <a name="see-also"></a>Ayrıca bkz:

[Internet Information Services (IIS) 7.0 belgeleri](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753433(v=ws.10))

[IIS Yöneticisi 7.0 Yardımı](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732664(v=ws.11))

[Web sunucunuzun güvenliğini (IIS 7) yapılandırma](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731278(v=ws.10))

[IPSec dağıtım kaynakları](/previous-versions/windows/it-pro/windows-server-2003/cc776369(v=ws.10))
