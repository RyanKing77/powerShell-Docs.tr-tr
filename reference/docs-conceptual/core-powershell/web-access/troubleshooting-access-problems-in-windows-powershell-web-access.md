---
ms.date: 08/23/2017
keywords: PowerShell cmdlet'i
title: windows powershell web erişimi'nde erişim sorunlarını giderme
ms.openlocfilehash: ef476d8e386e5380cb2c9dda69180dfce8748bf4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953455"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a>Windows PowerShell Web Erişimi’nde Erişim Sorunlarını Giderme

Güncelleştirme: 24 Haziran (23 Ağustos 2017 düzenlendi) 2013

İçin geçerlidir: Windows Server 2012 R2, Windows Server 2012

Aşağıdaki bölümlerde, Windows PowerShell Web erişimi kullanarak bir uzak bilgisayara bağlanmaya çalışılırken bazı yaygın sorunlar belirlemek ve sorunların çözümü için öneriler içermektedir.

## <a name="sign-in-failure"></a>Oturum açma hatası

Hata, aşağıdakilerden biri nedeniyle oluşabilir.

- Bilgisayara kullanıcı erişimine izin veren bir yetkilendirme kuralı ya da uzak bilgisayarda belirli bir oturum yapılandırması yok.

  Windows PowerShell Web erişimi güvenliği kısıtlayıcıdır; Yetkilendirme kuralları kullanılarak, kullanıcılara uzak bilgisayarlara açık erişim verilmesi gerekir.

  Yetkilendirme kuralları oluşturma hakkında daha fazla bilgi için bkz: [yetkilendirme kuralları ve güvenlik özellikleri, Windows PowerShell Web erişimi](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

- Kullanıcının, hedef bilgisayara yetkili erişimi yok. Bu, erişim denetim listeleri (ACL’ler) ile belirlenir.

  Daha fazla bilgi için bkz: [Windows PowerShell Web erişimi için oturum açma](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), veya Windows PowerShell ekip blogu.

- Windows PowerShell uzaktan yönetimi hedef bilgisayarda etkinleştirilmemiş olabilir.

  Uzaktan Yönetim için kullanıcının bağlanmaya çalıştığı bilgisayarda etkin doğrulayın.

  Daha fazla bilgi için bkz: [bilgisayarınızı yapılandırma uzaktan iletişim için nasıl](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).

## <a name="internal-server-error"></a>İç sunucu hatası

Kullanıcılar Windows PowerShell Web erişimi bir Internet Explorer penceresinde oturum açmaya çalıştığında, bunlar gösterilir bir **iç sunucu hatası** sayfasında veya *Internet Explorer* yanıt vermiyor.

Bu sorun, Internet Explorer’a özeldir.

### <a name="possible-cause"></a>Olası neden

Bu, Çince karakterler içeren bir etki alanı adı ile oturum açmış kullanıcılar için veya bir veya daha fazla Çince karakter ağ geçidi sunucusunun parçası ise oluşabilir.

#### <a name="workaround"></a>Geçici çözüm

1. [Internet Explorer 10 yüklemesi ve çalıştırması](http://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. Internet Explorer değiştirme **belge modu** ayarını *ıe10* standartları.
   1. Tuşuna **F12** geliştirici araçları konsolunu açmak için
   1. Internet Explorer 10'a tıklayın **tarayıcı modu**ve ardından *Internet Explorer 10*.
   1. Tıklatın **belge modu**ve ardından *ıe10* standartları.
   1. Tuşuna **F12** geliştirici araçları konsolunu kapatın.
1. Internet Explorer 10'daki otomatik proxy yapılandırmasını devre dışı bırakın.
   1. Tıklatın **Araçları**ve ardından **Internet Seçenekleri**.
   1. İçinde **Internet Seçenekleri** iletişim kutusundaki **bağlantıları** sekmesini tıklatın, **LAN Ayarları**.
   1. Clear **ayarları otomatik olarak algıla** onay kutusu. Tıklatın **Tamam**ve ardından **Tamam** kapatmak için tekrar *Internet Seçenekleri* iletişim kutusu.

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a>Bir uzak çalışma grubu bilgisayarına bağlanılamıyor

Hedef bilgisayar bir çalışma grubunun üyesi ise, kullanıcı adınızı sağlamak ve bilgisayara oturum açmak için aşağıdaki sözdizimini kullanın: `<workgroup_name>\<user_name>`

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a>Rol yüklenmiş olsa dahi, Web Sunucusu (IIS) yönetim araçları bulunamıyor

Windows PowerShell Web erişimi kullanarak yüklediyseniz `Install-WindowsFeature` cmdlet'i, Yönetim Araçları yüklü değil. sürece `-IncludeManagementTools` parametresini cmdlet'e eklenir.

Bir örnek için bkz: [Windows PowerShell cmdlet'lerini kullanarak Windows PowerShell Web erişimi yükleme](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).

IIS Yöneticisi konsolunu ekleyebilir ve gerektiğini bildiren araçları seçerek diğer IIS Yönetim Araçları bir **Ekle roller ve Özellikler Sihirbazı** Ağ Geçidi sunucusuna hedeflenmiş oturumu.
Ekle roller ve Özellikler Sihirbazı açıldığında gelen Sunucu Yöneticisi içinde.

## <a name="windows-powershell-web-access-website-is-not-accessible"></a>Windows PowerShell Web Erişimi Web sitesi erişilebilir değil

Internet Explorer (IE ESC) Artırılmış Güvenlik Yapılandırması etkinse, Windows PowerShell Web Erişimi Web sitesini güvenilir siteler listesine ekleyebilirsiniz.

Güvenlik riskleri nedeniyle daha az önerilen bir yaklaşım, IE ESC'yi devre dışı bırakmaktır.
Yerel Sunucu Sayfası Sunucu Yöneticisi'nde bulunan özellikler kutucuğunda IE ESC'yi devre dışı bırakabilirsiniz.

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a>Bir Yetkilendirme hatası oluştu. Hedef bilgisayara bağlanmak için yetkilendirilmiş olduğunuzu doğrulayın.

Ağ Geçidi sunucusu hedef bilgisayar ve ayrıca bir çalışma grubu içinde olduğunda bağlanmaya çalışıldığında yukarıdaki hata iletisi görüntülenir.

Ağ Geçidi sunucusu hedef sunucu da olduğunda ve bir çalışma grubunda olduğunda kullanıcı adı, bilgisayar adı ve kullanıcı grubu adını belirtin.
Bir nokta (.) kendisi tarafından bilgisayar adını temsil etmek için kullanmayın.

### <a name="scenarios-and-proper-values"></a>Senaryolar ve uygun değerleri

#### <a name="all-cases"></a>Tüm durumları

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

Güvenlik tanımlayıcısı (SID) sözdizimi kullanıcı yerine bir yetkilendirme kuralında görüntülenir\_bilgisayarı adlandırma\_adı.

Kural artık geçerli değil veya Active Directory Etki Alanı Hizmetleri sorgusu başarısız olmuş.
Bir yetkilendirme kuralı genelde, Ağ Geçidi sunucusunun bir zamanda bir çalışma grubunda olsa da, daha sonra bir etki alanına katılmış senaryolarda geçerli değildir

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a>Kural ile bir etki alanıyla IPv6 adresi olarak oturum açamaz

Bir etki alanıyla IPv6 adresi olarak yetkilendirme kurallarında belirtilmiş bir hedef bilgisayara oturum açılamıyor.

Yetkilendirme kuralları, bir etki alanı adı biçiminde bir IPv6 adresini desteklemez.

Bir IPv6 adresi kullanarak bir hedef bilgisayar belirtmek için, yetkilendirme kuralında özgün IPv6 adresini kullanın (iki nokta üst üste içeren).
Hem etki alanı hem de sayısal (iki nokta üst üste) olan IPv6 adresleri, yetkilendirme kurallarında değil ancak, Windows PowerShell Web erişimi oturum açma sayfasında hedef bilgisayar adı olarak desteklenir.

IPv6 adresleri hakkında daha fazla bilgi için bkz: [IPv6 nasıl çalışır](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).

## <a name="see-also"></a>Ayrıca bkz:

- [Yetkilendirme kuralları ve Windows PowerShell Web Erişimi'nın güvenlik özellikleri](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
- [Web tabanlı Windows PowerShell konsolunu kullanma](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
- [about_Remote_Requirements](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements)