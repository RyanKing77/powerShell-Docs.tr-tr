---
ms.date: 08/23/2017
keywords: PowerShell cmdlet'i
title: windows powershell web erişiminde erişim sorunlarını giderme
ms.openlocfilehash: c9b98c7a1685679eb88b718de0351154cb84e92e
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52321001"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a>Windows PowerShell Web Erişimi’nde Erişim Sorunlarını Giderme

Güncelleştirme: Haziran 24 (23 Ağustos 2017 düzenlendi) 2013

Uygulama hedefi: Windows Server 2012 R2, Windows Server 2012

Aşağıdaki bölümlerde, Windows PowerShell Web Erişimi'ni kullanarak bir uzak bilgisayara bağlanmaya çalışırken bazı yaygın sorunlar belirlemek ve sorunları çözmek için öneriler içerir.

## <a name="sign-in-failure"></a>Oturum açma hatası

Hata, aşağıdakilerden biri nedeniyle oluşabilir.

- Bilgisayara kullanıcı erişimine izin veren bir yetkilendirme kuralı ya da uzak bilgisayarda belirli bir oturum yapılandırması yok.

  Windows PowerShell Web erişimi güvenliği kısıtlayıcıdır; Yetkilendirme kuralları kullanarak, kullanıcılar uzak bilgisayarlara açık erişim verilmesi gerekir.

  Yetkilendirme kuralları oluşturma hakkında daha fazla bilgi için bkz. [yetkilendirme kuralları ve güvenlik özellikleri, Windows PowerShell Web erişimi](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

- Kullanıcının, hedef bilgisayara yetkili erişimi yok. Bu, erişim denetim listeleri (ACL’ler) ile belirlenir.

  Daha fazla bilgi için [Windows PowerShell Web erişimi için oturum açarken](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), veya Windows PowerShell ekibi blogu.

- Windows PowerShell uzaktan yönetimi hedef bilgisayarda etkinleştirilmemiş olabilir.

  Uzaktan Yönetim, kullanıcının bağlanmaya çalıştığı bilgisayarda etkin olup olmadığını doğrulayın.

  Daha fazla bilgi için [bilgisayarınızı uzaktan yapılandırmak için nasıl](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).

## <a name="internal-server-error"></a>İç sunucu hatası

Kullanıcılar Windows PowerShell Web Erişimi'nde bir Internet Explorer penceresi oturum açmayı denediğinde gösterilen bir **iç sunucu hatası** sayfasında veya *Internet Explorer* yanıt vermiyor.

Bu sorun, Internet Explorer’a özeldir.

### <a name="possible-cause"></a>Olası neden

Bu, Çince karakterler içeren bir etki alanı adı ile oturum açmış kullanıcılar için veya bir veya daha fazla Çince karakter ağ geçidi sunucusunun parçası ise oluşabilir.

#### <a name="workaround"></a>Geçici çözüm

1. [Yükleme ve Internet Explorer 10 çalıştırma](https://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. Internet Explorer değiştirme **belge modu** ayarını *ıe10* standartları.
   1. Tuşuna **F12** geliştirici araçları konsolunu açmak için
   1. Internet Explorer 10'da tıklayın **tarayıcı modu**ve ardından *Internet Explorer 10*.
   1. Tıklayın **belge modu**ve ardından *ıe10* standartları.
   1. Tuşuna **F12** geliştirici araçları konsolunu kapatın.
1. Internet Explorer 10 otomatik proxy yapılandırmasını devre dışı bırakın.
   1. Tıklayın **Araçları**ve ardından **Internet Seçenekleri**.
   1. İçinde **Internet Seçenekleri** iletişim kutusundaki **bağlantıları** sekmesinde **LAN Ayarları**.
   1. NET **ayarlarını otomatik olarak algıla** onay kutusu. Tıklayın **Tamam**ve ardından **Tamam** kapatmak için tekrar *Internet Seçenekleri* iletişim kutusu.

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a>Bir uzak çalışma grubu bilgisayarına bağlanılamıyor

Hedef bilgisayarın bir çalışma grubunun bir üyesi ise, kullanıcı adınızı sağlamak ve bilgisayara oturum açmak için aşağıdaki sözdizimini kullanın: `<workgroup_name>\<user_name>`

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a>Rol yüklenmiş olsa dahi, Web Sunucusu (IIS) yönetim araçları bulunamıyor

Windows PowerShell Web erişimi kullanarak yüklediyseniz `Install-WindowsFeature` cmdlet'i, Yönetim Araçları yüklü değil sürece `-IncludeManagementTools` parametresi için cmdlet eklendi.

Bir örnek için bkz. [Windows PowerShell cmdlet'lerini kullanarak Windows PowerShell Web erişimi yüklemek için](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).

IIS Yöneticisi konsolunu ekleyebilir ve diğer IIS Yönetim Araçları'nı seçerek ihtiyacınız olduğunu araçları bir **Ekle roller ve Özellikler Sihirbazı** Ağ Geçidi sunucusuna hedeflenmiş oturumu.
Rol ve Özellik Ekleme Sihirbazı açılır gelen Sunucu Yöneticisi içinde.

## <a name="windows-powershell-web-access-website-is-not-accessible"></a>Windows PowerShell Web Erişimi Web sitesi erişilebilir değil

Internet Explorer (IE ESC) Artırılmış Güvenlik Yapılandırması etkinse, Windows PowerShell Web Erişimi Web sitesi Güvenilen siteler listesine ekleyebilirsiniz.

Güvenlik riskleri nedeniyle daha az önerilen bir yaklaşım, IE ESC'yi devre dışı bırakmaktır.
Üzerinde Sunucu Yöneticisi'nde yerel sunucu sayfası özellikler kutucuğundaki IE ESC'yi devre dışı bırakabilirsiniz.

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a>Bir Yetkilendirme hatası oluştu. Hedef bilgisayara bağlanmak için yetkilendirilmiş olduğunuzu doğrulayın.

Ağ Geçidi sunucusu hedef bilgisayar ve ayrıca bir çalışma grubunda olduğunda, bağlantı kurulmaya çalışılırken yukarıdaki hata iletisi görüntülenir.

Ağ Geçidi sunucusu hedef sunucu da olduğunda ve bir çalışma grubundaysa, kullanıcı adı, bilgisayar adı ve kullanıcı grubu adı belirtin.
Bir nokta (.) kendisi tarafından bilgisayar adını temsil etmek için kullanmayın.

### <a name="scenarios-and-proper-values"></a>Senaryolar ve uygun değerleri

#### <a name="all-cases"></a>Tüm durumlarda

Parametre | Değer
-- | --
UserName | Sunucu\_adı\\kullanıcı\_adı<br/>Localhost\\kullanıcı\_adı<br/>. \\kullanıcı\_adı
UserGroup | Sunucu\_adı\\kullanıcı\_grubu<br/>Localhost\\kullanıcı\_grubu<br/>. \\kullanıcı\_grubu
ComputerGroup | Sunucu\_adı\\bilgisayar\_grubu<br/>Localhost\\bilgisayar\_grubu<br/>. \\bilgisayar\_grubu

#### <a name="gateway-server-is-in-a-domain"></a>Ağ geçidi sunucu bir etki alanında

Parametre | Değer
-- | --
ComputerName | Ağ geçidi sunucusunun tam adı veya Localhost

#### <a name="gateway-server-is-in-a-workgroup"></a>Ağ geçidi sunucusu bir çalışma alanında

Parametre | Değer
-- | --
ComputerName | Sunucu adı

### <a name="gateway-credentials"></a>Ağ Geçidi kimlik bilgileri

Bir ağ geçidi sunucusuna, aşağıdakilerden biri olarak biçimlendirilmiş kimlik bilgilerini kullanarak, hedef bilgisayar olarak oturum açın.

- Sunucu\_adı\\kullanıcı\_adı
- Localhost\\kullanıcı\_adı
- . \\kullanıcı\_adı

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a>Güvenlik tanımlayıcısı (SID) bir yetkilendirme kuralında görüntüleniyor

Güvenlik tanımlayıcısı (SID) söz dizimi kullanıcı yerine bir yetkilendirme kuralı görüntülenen\_adı/bilgisayar\_adı.

Kural artık geçerli değil veya Active Directory Etki Alanı Hizmetleri sorgusu başarısız olmuş.
Bir yetkilendirme kuralı genelde burada ağ geçidi sunucusu aynı anda bir çalışma grubunda olan, ancak daha sonra bir etki alanına katılmış senaryolarda geçerli değil

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a>Kural ile bir etki alanıyla IPv6 adresi olarak imzalanamıyor

Bir etki alanıyla IPv6 adresi olarak yetkilendirme kurallarında belirtilmiş bir hedef bilgisayara oturum açılamıyor.

Yetkilendirme kuralları, bir etki alanı adı biçiminde bir IPv6 adresini desteklemez.

Bir IPv6 adresi kullanarak bir hedef bilgisayar belirtmek için, yetkilendirme kuralında özgün IPv6 adresini kullanın (iki nokta üst üste içeren).
Hem etki alanı hem de sayısal (iki nokta üst üste ile) IPv6 adresleri, yetkilendirme kurallarında değil ancak, Windows PowerShell Web erişimi oturum açma sayfasında hedef bilgisayar adı olarak desteklenir.

IPv6 adresleri hakkında daha fazla bilgi için bkz. [IPv6 nasıl çalışır](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).

## <a name="see-also"></a>Ayrıca bkz:

- [Yetkilendirme kuralları ve güvenlik özellikleri Windows PowerShell Web erişimi](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
- [Web tabanlı Windows PowerShell konsolunu kullanma](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
- [about_Remote_Requirements](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements)