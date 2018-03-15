---
ms.date: 2017-06-27
keywords: PowerShell cmdlet'i
title: "Windows PowerShell Web Erişimi Yetkilendirme Kuralları ve Güvenlik Özellikleri"
ms.openlocfilehash: 19e4aa1bb55178ec2634af0771afe2db5db3423c
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a>Windows PowerShell Web Erişimi Yetkilendirme Kuralları ve Güvenlik Özellikleri

Güncelleştirilmiş: 24 Haziran 2013

İçin geçerlidir: Windows Server 2012 R2, Windows Server 2012

Windows Server 2012 R2 ve Windows Server 2012, Windows PowerShell Web erişimi kısıtlayıcı güvenlik modeli vardır.
Windows PowerShell Web erişimi ağ geçidine oturum açın ve web tabanlı Windows PowerShell Konsolu önce kullanıcılara açıkça erişim verilmesi gerekir.

## <a name="configuring-authorization-rules-and-site-security"></a>Yetkilendirme kuralları ve site güvenliği yapılandırma

Windows PowerShell Web erişimi yüklendikten ve ağ geçidi yapılandırıldıktan sonra kullanıcılar oturum açma sayfasını bir tarayıcıda açabilir, ancak açıkça erişim Windows PowerShell Web erişimi yönetici kullanıcılar verene kadar kullanıcılar oturum açamaz.
'Windows PowerShell Web Erişimi' erişim denetimi, aşağıdaki tabloda açıklanan Windows PowerShell cmdlet'leri kümesi kullanılarak yönetilir.
Yetkilendirme kuralları eklemek veya yönetmek için karşılaştırılabilir GUI yoktur.
Bkz: [Windows PowerShell Web erişim cmdlet'leri](cmdlets/web-access-cmdlets.md).

Yöneticiler tanımlayabilirsiniz 0 -*n* Windows PowerShell Web erişimi için kimlik doğrulama kuralları.
Varsayılan güvenlik esnek değil kısıtlayıcıdır; sıfır kimlik doğrulama kuralı, hiçbir kullanıcının herhangi bir şeye erişimi olmadığı anlamına gelir.

[Add-PswaAuthorizationRule](cmdlets/add-pswaauthorizationrule.md) ve [Test-PswaAuthorizationRule](cmdlets/test-pswaauthorizationrule.md) Windows Server 2012 R2'de ekleyin ve uzak bir Windows PowerShell Web Erişimi yetkilendirme kuralları test olanak tanıyan bir kimlik bilgisi parametresi içerir bilgisayar veya etkin bir Windows PowerShell Web erişimi oturumu içinde.
Farklı bir kimlik bilgisi parametresi olan diğer Windows PowerShell cmdlet'leri ile bir PSCredential nesnesi parametre değeri olarak belirtebilirsiniz.
Uzak bir bilgisayara geçirmek istediğiniz kimlik bilgilerini içeren bir PSCredential nesnesi oluşturmak için çalıştırın [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet'i.

Windows PowerShell Web erişimi kimlik doğrulama kuralları beyaz liste kurallarıdır.
Her kural kullanıcılar, hedef bilgisayarlar ve belirli Windows PowerShellÂ arasında izin verilen bir bağlantının tanımıdır [oturum yapılandırmaları](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) (uç noktalar olarak da adlandırılan veya _çalışma alanlarını_) üzerinde Belirtilen hedef bilgisayarlar.
Üzerinde bir açıklama için **çalışma alanlarını** görmek [başına kullanım, PowerShell çalışma alanları](https://blogs.technet.microsoft.com/heyscriptingguy/2015/11/26/beginning-use-of-powershell-runspaces-part-1/)

> **Güvenlik Notu**
>
> Bir kullanıcının, erişim elde etmek için yalnızca bir kuralın doğru olmasına ihtiyacı vardır.
Bir kullanıcı bir bilgisayara tam dil erişimi veya yalnızca erişim Windows PowerShell uzaktan yönetim cmdlet'leri, web tabanlı konsoldan ile erişim verilirse, kullanıcı oturum açın (veya atlama) ilk hedef bilgisayara bağlı diğer bilgisayarlara.
Kullanıcılar, normalde uzaktan yapmak için gereksinim duydukları belirli görevleri gerçekleştirmek imkan kısıtlı oturum yapılandırmalarına erişmesine izin vermek için Windows PowerShell Web erişimi yapılandırmak için en güvenli yolu değil.

Başvurulan cmdlet'leri [Windows PowerShell Web erişimi cmdlet'leri](cmdlets/web-access-cmdlets.md) bir kullanıcı Windows PowerShell Web erişimi ağ geçidinde yetkilendirmek için kullanılan erişim kuralları kümesi oluşturmak için izin verin.
Kurallar, hedef bilgisayardaki erişim denetimi listelerinden (ACL) farklıdır ve web erişimi için ek bir güvenlik katmanı sağlar.
Güvenlik hakkında daha fazla ayrıntı, aşağıdaki bölümde açıklanmıştır.

Kullanıcıların herhangi bir önceki güvenlik katmanını geçemezse, Tarayıcı pencerelerinde bir genel erişim reddedildi' iletisi alırsınız.
Güvenlik ayrıntıları, ağ geçidi sunucusunda günlüğe kaydedilmiş olsa da, son kullanıcılara, kaç adet güvenlik katmanı geçtikleri ya da oturum açma ya da kimlik doğrulama hatasının hangi katmanda gerçekleştiğine dair bilgi gösterilmez.

Yetkilendirme kuralları yapılandırma hakkında daha fazla bilgi için bkz: [yetkilendirme kuralları yapılandırma](#configuring-authorization-rules-and-site-security) bu konuda.

### <a name="security"></a>Güvenlik

Windows PowerShell Web erişimi güvenlik modeli web tabanlı konsolun son kullanıcısı ve bir hedef bilgisayar arasında dört katmanı vardır.
Windows PowerShell Web erişimi Yöneticiler IIS Yöneticisi konsolunda ek yapılandırmayla ilave güvenlik katmanları ekleyebilir.
IIS Yöneticisi konsolunda Web sitelerinin güvenliğini sağlama hakkında daha fazla bilgi için bkz: [Web sunucusu güvenlik yapılandırması (IIS 7)](https://technet.microsoft.com/library/cc731278).
IIS hakkında daha fazla bilgi için en iyi uygulamalar ve hizmet reddi saldırılarını önleme, bkz: [en iyi uygulamalar için engelleme DoS/hizmet reddi saldırılarını](https://technet.microsoft.com/library/cc750213).
Yönetici ayrıca satın alın ve ek perakende yetkilendirme yazılımı yükleyin.

Aşağıdaki tabloda, son kullanıcılar ve hedef bilgisayar arasındaki dört güvenlik katmanı açıklanmaktadır.

|Düzey|Katman|
|-|-|
|1|[IIS web sunucusu güvenlik özellikleri](#iis-web-server-security-features)|
|2|[Windows powershell web erişimi ağ geçidi form tabanlı kimlik doğrulaması](#windows-powershell-web-access-forms-based-gateway-authentication)|
|3|[Windows powershell web erişimi yetkilendirme kuralları](#windows-powershell-web-access-authorization-rules)|
|4|[Hedef kimlik doğrulama ve yetkilendirme kuralları](#target-authentication-and-authorization-rules)|

Her katman hakkında ayrıntılı bilgi aşağıdaki başlıklar altında bulunabilir:

#### <a name="iis-web-server-security-features"></a>IIS Web sunucusu güvenlik özellikleri

Windows PowerShell Web erişimi kullanıcılar, bir kullanıcı adı ve parola geçidinde hesaplarının kimliğini doğrulamak için her zaman sağlamanız gerekir.
Ancak, Windows PowerShell Web erişimi yöneticileri Ayrıca isteğe bağlı istemci sertifikası kimlik doğrulaması üzerinde veya, bkz: kapatabilirsiniz [yükleyin ve windows powershell web erişimi](install-and-use-windows-powershell-web-access.md) bir test sertifikası etkinleştirmek için ve daha sonra nasıl yapılandırılacağı bir Orijinal sertifika).

İsteğe bağlı istemci sertifikası özelliği, son kullanıcıların, kullanıcı adlarına ve parolalarına ek olarak, geçerli bir istemci sertifikasına sahip olmasını gerektirir ve Web Sunucusu (IIS) yapılandırmasının bir parçasıdır.
İstemci sertifikası katmanı etkinleştirildiğinde, Windows PowerShell Web erişimi oturum açma sayfasında oturum açma kimlik bilgilerini değerlendirilmeden önce geçerli sertifikalar sağlaması için kullanıcıya sorar.
İstemci sertifikası kimlik doğrulaması, istemci sertifikasını otomatik olarak denetler.
Geçerli bir sertifika bulunmazsa, Windows PowerShell Web erişimi kullanıcıları bilgilendirir, böylelikle sertifikayı sağlayabilirler.
Geçerli bir istemci sertifikası bulunursa, Windows PowerShell Web erişimi kullanıcı adlarını ve parolaları sağlamak için kullanıcıların oturum açma sayfasını açar.

Bu IIS Web sunucusu tarafından sunulan ek güvenlik ayarlarının bir örnektir.
Diğer IIS güvenlik özellikleri hakkında daha fazla bilgi için bkz: [Web sunucusu güvenlik yapılandırması (IIS 7)](https://technet.microsoft.com/library/cc731278)

#### <a name="windows-powershell-web-access-forms-based-gateway-authentication"></a>Windows PowerShell Web erişimi ağ geçidi form tabanlı kimlik doğrulaması

Windows PowerShell Web erişimi oturum açma sayfasında bir dizi kimlik bilgisi (kullanıcı adı ve parola) gerektirir ve kullanıcılara hedef bilgisayar için farklı kimlik bilgileri sağlama seçeneği sunar.
Kullanıcı, alternatif kimlik bilgileri sağlamazsa, ağ geçidine bağlanmak için kullanılan birincil kullanıcı adı ve parola, hedef bilgisayara bağlanmak için de kullanılır.

Gerekli kimlik bilgilerinin Windows PowerShell Web erişimi ağ geçidini doğrulanır.
Bu kimlik bilgileri, geçerli bir kullanıcı hesapları ya da yerel sunucuda Windows PowerShell Web erişimi ağ geçidi ya da Active Directory içinde olmalıdır.

#### <a name="windows-powershell-web-access-authorization-rules"></a>Windows PowerShell Web Erişimi yetkilendirme kuralları

Bir kullanıcı geçidinde doğrulandıktan sonra Windows PowerShell Web erişimi kullanıcının istenen hedef bilgisayara erişimi olup olmadığını doğrulamak için yetkilendirme kurallarını denetler.
Başarılı yetkilendirme sonrasında, kullanıcının kimlik bilgileri boyunca hedef bilgisayara aktarılır.

Bu kurallar yalnızca, bir kullanıcı kimliği ağ geçidi tarafından doğrulandıktan sonra ve bir kullanıcının kimliğinin hedef bilgisayarda doğrulanabilmesinden önce değerlendirilir.

#### <a name="target-authentication-and-authorization-rules"></a>Hedef kimlik doğrulama ve yetkilendirme kuralları

Windows PowerShell Web erişimi için güvenliğin son katmanı hedef bilgisayarın kendi güvenlik yapılandırmasıdır.
Kullanıcıların Windows PowerShell Web erişimi aracılığıyla bir hedef bilgisayarı etkileyen bir Windows PowerShell web tabanlı konsol çalıştırmak için hedef bilgisayarda ve Windows PowerShell Web Erişimi yetkilendirme kurallarında, yapılandırılmış uygun erişim hakları olmalıdır.

Bu katman kullanıcılar çalıştırarak Windows PowerShell içinde bir hedef bilgisayara uzak bir Windows PowerShell oturumu oluşturmaya çalıştılarsa bağlantı denemelerini değerlendirecek güvenlik mekanizmalarının aynısını sunar [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Enter-PSSession) veya [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/new-pssession) cmdlet'leri.

Varsayılan olarak, Windows PowerShell Web erişimi, ağ geçidi ve hedef bilgisayar kimlik doğrulaması için birincil kullanıcı adı ve parola kullanır.
Web tabanlı oturum açma sayfasında, başlıklı bir bölümde **isteğe bağlı bağlantı ayarlarını**, gerekli olduğunda kullanıcılar hedef bilgisayar için farklı kimlik bilgileri sağlama seçeneği sunar.
Kullanıcı alternatif kimlik bilgileri sağlamazsa, birincil kullanıcı adı ve ağ geçidine bağlanmak için kullanılan parola ayrıca hedef bilgisayara bağlanmak için kullanılır.

Yetkilendirme kuralları, kullanıcıların belirli bir oturum yapılandırmasına erişmesine izin vermek için kullanılabilir.
Oluşturabileceğiniz _sınırlı çalışma alanlarını_ veya Windows PowerShell Web erişimi, oturum yapılandırmaları ve belirli kullanıcıların bunlar Windows PowerShell Web erişimi için oturum açtığında yalnızca belirli oturum yapılandırmalarına bağlanmasına izin verin.
Daha fazla belirli bir kullanıcı kümesi için uç noktaya Bu bölümde açıklanan yetkilendirme kurallarını kullanarak kısıtlayın ve hangi kullanıcıların belirli Uç noktalara erişimi olduğunu belirlemek için erişim denetim listelerini (ACL'ler) kullanın.
Sınırlı çalışma alanlarını hakkında daha fazla bilgi için bkz: [kısıtlı bir çalışma alanı oluşturma](https://msdn.microsoft.com/en-us/library/dn614668).

### <a name="configuring-authorization-rules"></a>Yetkilendirme kuralları yapılandırma

Yöneticiler olasılıkla ortamlarında Windows PowerShell uzaktan yönetimi için zaten tanımlı Windows PowerShell Web erişimi kullanıcılar için Yetkilendirme kuralının aynısını istiyor.
Bu bölümdeki ilk yordam tek bir oturum yapılandırması içinde ve bir bilgisayarı yönetmek için oturum açan bir kullanıcıya erişim veren bir güvenli Yetkilendirme kuralının nasıl ekleneceği açıklanmaktadır.
İkinci yordamda, artık gerekli olmayan bir yetkilendirme kuralının nasıl kaldırılacağı açıklanmaktadır.

Yalnızca Windows PowerShell Web Erişimi'nde sınırlı çalışma alanlarını içinde çalışmak belirli kullanıcılara izin vermek için özel oturum yapılandırmaları kullanmayı planlıyorsanız, özel oturum yapılandırmalarınızı, onları belirten yetkilendirme kuralları eklemeden önce oluşturun.
Özel oturum yapılandırmaları oluşturmak için Windows PowerShell Web erişimi cmdlet'leri kullanamazsınız.
Özel oturum yapılandırmaları oluşturma hakkında daha fazla bilgi için bkz: [about_Session_Configuration_Files](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configuration_files).

Windows PowerShell Web erişimi cmdlet'leri destekleyen bir joker karakter, bir yıldız işareti ( \* ).
Dizeler içindeki joker karakterler desteklenmez; özellik başına (kullanıcılar, bilgisayarlar veya oturum yapılandırmaları) tek bir yıldız işareti kullanın.

> **Not**
>
> Yetkilendirme kuralları kullanıcılara erişim vermek ve Windows PowerShell Web erişimi ortamı güvenliğinin sağlanmasına yardımcı olmak için kullanabileceğiniz diğer yolları görmek için [diğer yetkilendirme kuralı senaryo örnekleri](#other-authorization-rule-scenario-examples) bu konuda.

#### <a name="to-add-a-restrictive-authorization-rule"></a>Kısıtlayıcı yetkilendirme kuralı ekleme

1. Yükseltilmiş kullanıcı haklarıyla bir Windows PowerShell oturumu açmak için aşağıdakilerden birini yapın.

    - Windows masaüstünde, sağ **Windows PowerShell** görev ve ardından **yönetici olarak çalıştır**.

    - Windows **Başlat** ekranında, sağ **Windows PowerShell** ve ardından **yönetici olarak çalıştır**.

2. **İsteğe bağlı adım** kullanıcı erişimini oturum yapılandırmaları kullanarak kısıtlamak için:

    Kullanmak istediğiniz oturum yapılandırmalarının zaten var olduğundan, kurallarınızı doğrulayın.
Bunlar henüz oluşturulmadı, içindeki oturum yapılandırmaları oluşturmak için yönergeleri kullanın [about_Session_Configuration_Files](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configuration_files).

3. Bu yetkilendirme kuralı genelde sahip oldukları kullanıcı için kapsamlı bir özel oturum yapılandırması erişimi ile erişim ağınızdaki bir bilgisayara belirli kullanıcı erişimi sağlar '™ s tipik komut dosyası ve cmdlet gereksinimlerine. Aşağıdaki komutu yazın ve sonra basın **Enter**.

```powershell
Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>
```

  - Aşağıdaki örnekte, bir kullanıcı adlı _JSmith_ içinde _Contoso_ etki alanı bilgisayarı yönetmek için erişim izni _Contoso_214_ve adlı bir oturum yapılandırması kullanmak _NewAdminsOnly_.

```powershell
Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly
```

4. Kural ya da çalıştırarak oluşturulduğunu doğrulayın **Get-PswaAuthorizationRule** cmdlet'ini veya **Test-PswaAuthorizationRule - UserName &lt;etki alanı\\kullanıcı | bilgisayar\\ Kullanıcı&gt; - ComputerName** &lt;bilgisayar_adı&gt;. Örneğin, **Test-PswaAuthorizationRule - UserName Contoso\\JSmith - ComputerName Contoso_214**.

#### <a name="to-remove-an-authorization-rule"></a>Yetkilendirme kuralı kaldırma

1. Bir Windows PowerShell oturumu açık değilse, adım 1 / bkz [kısıtlayıcı yetkilendirme kuralı eklemek için](#to-add-a-restrictive-authorization-rule) bu bölümdeki.

2. Aşağıdaki komutu yazın ve sonra basın **Enter**, burada *kimliği kural* kaldırmak istediğiniz kuralın benzersiz kimlik numarasını temsil eder.

```powershell
Remove-PswaAuthorizationRule -ID <rule ID>
```

Alternatif olarak, kimlik numarasını bilmiyorsanız, ancak kaldırmak istediğiniz kuralın kolay adını biliyorsanız yaparsanız, kuralın adını almak ve kendisine kanal `Remove-PswaAuthorizationRule` aşağıdaki örnekte gösterildiği gibi kuralı kaldırmak için cmdlet: `Get-PswaAuthorizationRule -RuleName <rule-name> | Remove-PswaAuthorizationRule`.

>**Not**:
>
>Belirtilen yetkilendirme kuralını silmek isteyip istemediğinizi onaylamanız istenmez; Kural bastığınızda silinir **Enter**. `Remove-PswaAuthorizationRule` cmdlet’ini çalıştırmadan önce, yetkilendirme kuralını kaldırmak istediğinizden emin olun.

#### <a name="other-authorization-rule-scenario-examples"></a>Diğer yetkilendirme kuralı senaryo örnekleri

Her Windows PowerShell oturumu bir oturum yapılandırması kullanır; bir oturum açmak için belirtilmezse, Windows PowerShell varsayılan, Microsoft.PowerShell adlı yerleşik Windows PowerShell oturum yapılandırmasını kullanır. Varsayılan oturum yapılandırması, bir bilgisayarda mevcut tüm cmdlet'leri içerir. Yöneticiler, sınırlı bir çalışma alanı olan bir oturum yapılandırması tanımlayarak tüm bilgisayarlara erişimi kısıtlayabilir (son kullanıcılarının gerçekleştirebileceği sınırlı bir cmdlet'ler ve görevler aralığı). Tam dil erişimi veya yalnızca Windows PowerShell uzak yönetim cmdlet'leriyle bir bilgisayara erişim verilen bir kullanıcı, ilk bilgisayara bağlı diğer bilgisayarlara bağlanabilir. Sınırlı bir çalışma tanımlama kullanıcılar kendi izin verilen bir Windows PowerShell çalışma alanından diğer bilgisayarlara erişmesini engelleyebilir ve Windows PowerShell Web erişimi ortamınızın güvenliğini artırır. Oturum yapılandırması (Grup İlkesi kullanarak) Yöneticiler Windows PowerShell Web erişimi aracılığıyla erişilebilir olmasını istediğiniz tüm bilgisayarlara dağıtılabilir. Oturum yapılandırmaları hakkında daha fazla bilgi için bkz: [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx).
Aşağıda bu senaryonun bazı örnekleri verilmiştir.

- Adlı bir uç nokta, bir yöneticinin oluşturduğu **PswaEndpoint**, sınırlı bir çalışma alanıyla. Yönetici bir kural oluşturur sonra  **\*,\*, PswaEndpoint**ve uç noktayı diğer bilgisayarlara dağıtır. Kuralı tüm kullanıcıların uç noktası olan tüm bilgisayarlara erişmesine izin verdiği **PswaEndpoint**. Bu, kural kümesinde tanımlanan tek yetkilendirme kuralı ise, o uç noktası olmayan bilgisayarlara erişilemez.

- Bir uç nokta sınırlı bir çalışma alanıyla oluşturulan yönetici adında **PswaEndpoint**ve belirli kullanıcılar için erişimi sınırlandırmak istemektedir. Yönetici bir kullanıcı grubuna adlı oluşturur **Level1Support**ve şu kuralı tanımlıyor: **Level1Support,\*, PswaEndpoint**. Kural gruptaki tüm kullanıcılar verir **Level1Support** olan tüm bilgisayarlara erişim **PswaEndpoint** yapılandırma. Benzer şekilde, erişim belirli bir bilgisayar kümesine sınırlanabilir.

- Bazı yöneticiler, bazı kullanıcılara diğerlerinden daha fazla erişim sağlar. Örneğin, bir yönetici iki kullanıcı grubu oluşturuyor **Admins** ve **BasicSupport**. Yönetici bir uç nokta adı verilen sınırlı bir çalışma alanıyla da oluşturur. **PswaEndpoint**ve şu iki kuralı tanımlıyor: **yöneticileri,\*,\***  ve  **BasicSupport,\*, PswaEndpoint**. Tüm kullanıcılar ilk kural sağlar **yönetici** tüm bilgisayarlar ve ikinci kural grubu erişim sağlayan tüm kullanıcılar **BasicSupport** Grup yalnızca olan bilgisayarlara erişim  **PswaEndpoint**.

- Bir yönetici bir özel test ortamı ayarlamış ve tüm yetkilendirilmiş ağ kullanıcılarına, tipik olarak erişime sahip oldukları ağdaki tüm bilgisayarlar için, tipik olarak erişime sahip olukları tüm oturum yapılandırmalarıyla erişim izni vermek istiyor. Bu özel bir test ortamı olduğundan, yönetici güvenli olmayan bir yetkilendirme kuralı oluşturuyor.
  - Cmdlet'i yönetici çalıştırır `Add-PswaAuthorizationRule * * *`, joker karakterini kullanan  **\***  tüm kullanıcılar, tüm bilgisayarlar ve tüm yapılandırmaları belirtmek için.
  - Bu kural şuna eşdeğerdir: `Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *`.

  >**Not**:
  >
  >Bu kural, güvenli bir ortamda önerilmez ve Windows PowerShell Web erişimi tarafından sağlanan güvenlik yetkilendirme kuralı katmanını atlar.

- Bir yönetici, kullanıcıların, hem çalışma grupları hem de etki alanları içeren, çalışma grubu bilgisayarların ara sıra etki alanlarındaki hedef bilgisayarlara bağlanmak için kullanıldığı ve etki alanlarındaki bilgisayarların ara sıra çalışma alanlarındaki hedef bilgisayarlara bağlanmak için kullanıldığı bir ortamdaki hedef bilgisayarlara bağlanmasına izin vermek istiyor. Yönetici olan bir ağ geçidi sunucusu *PswaServer*, bir çalışma grubunda; ve hedef bilgisayar *srv1.contoso.com* bir etki alanında. Kullanıcı *Chris* hem çalışma grubu Ağ Geçidi sunucusunda hem de hedef bilgisayara yetkili bir yerel kullanıcı. Çalışma grubu sunucusundaki kullanıcı adı olan *chrisLocal*; ve kendi kullanıcı adı hedef bilgisayarda *contoso\\chris*. Chris’e srv1.contoso.com erişimini yetkilendirmek için, yönetici aşağıdaki kuralı ekler.

```powershell
Add-PswaAuthorizationRule -userName PswaServer\chrisLocal -computerName srv1.contoso.com -configurationName Microsoft.PowerShell
```

Önceki kural örneği Chris Ağ Geçidi sunucusunda kimliğini doğrular ve kendi erişimini yetkilendirir *srv1*. Oturum açma sayfasında, Chris ikinci bir kimlik bilgileri kümesi sağlamalıdır **isteğe bağlı bağlantı ayarlarını** alan (*contoso\\chris*). Ağ Geçidi sunucusu ona hedef bilgisayarda kimlik doğrulaması için ek kimlik bilgileri kümesini kullanır *srv1.contoso.com*.

Yalnızca aşağıdakiler başarılı olduktan ve en az bir yetkilendirme kuralı tarafından izin verilen eklendikten sonra önceki senaryoda, Windows PowerShell Web erişimi hedef bilgisayara başarılı bir bağlantı kurar.

1. Bir kullanıcı adı biçiminde ekleyerek çalışma grubu Ağ Geçidi sunucusunda kimlik doğrulaması *sunucu_adı*\\*user_name* yetkilendirme kuralı için

2. Kimlik doğrulaması oturum açma sayfasında sağlanan alternatif kimlik bilgileri kullanarak hedef bilgisayarda **isteğe bağlı bağlantı ayarlarını** alanı

  >**Not**:
  >
  >Ağ geçidi ve hedef bilgisayarlar farklı çalışma gruplarında veya etki alanlarında ise, iki çalışma grubu bilgisayarı arasında, iki etki alanı arasında veya çalışma grubu ile etki alanı arasında bir güven ilişkisi oluşturulmalıdır. Bu ilişki, Windows PowerShell Web Erişimi yetkilendirme kuralı cmdlet'leri kullanılarak yapılandırılamaz. Yetkilendirme kuralları, bilgisayarlar arasında bir güven ilişkisi tanımlamaz; yalnızca kullanıcıları, belirli hedef bilgisayarlara ve oturum yapılandırmalarına bağlanmaya yetkilendirebilir. Farklı etki alanları arasında bir güven ilişkisi yapılandırma hakkında daha fazla bilgi için bkz: [oluşturma etki alanı ve orman güvenleri](https://technet.microsoft.com/library/cc794775.aspx"). Bir güvenilir konaklar listesine çalışma grubu bilgisayarları ekleme hakkında daha fazla bilgi için bkz: [Sunucu Yöneticisi ile uzaktan yönetim](https://technet.microsoft.com/library/dd759202.aspx)

### <a name="using-a-single-set-of-authorization-rules-for-multiple-sites"></a>Birden çok site için tek bir yetkilendirme kuralları kümesi kullanma

Yetkilendirme kuralları, bir XML dosyasında depolanır. Varsayılan olarak, XML dosyasının yolu adıdır _% windir %\\Web\\PowershellWebAccess\\veri\\AuthorizationRules.xml_.

Yetkilendirme kurallarının XML dosyası yolu depolanan **powwa.config** içinde bulunan dosya _% windir %\\Web\\PowershellWebAccess\\veri_. Yönetici içinde varsayılan yol referansını değiştirme esnekliğine sahiptir **powwa.config** tercihlerine veya gereksinimlerine uyacak şekilde. Bu tür bir yapılandırma istenirse dosyanın konumunu değiştirmek yönetici izin vererek aynı yetkilendirme kurallarını kullanmak birden çok Windows PowerShell Web erişimi ağ geçidi olanak sağlar.

## <a name="session-management"></a>Oturum yönetimi

Varsayılan olarak, Windows PowerShell Web erişimi bir kullanıcı aynı anda üç oturumla sınırlar. Web uygulamasının düzenleyebilirsiniz **web.config** dosyasını farklı bir kullanıcı başına oturum sayısı desteklemek için IIS Yöneticisi'nde.
Yolu **web.config** dosyası _$Env: Windir\\Web\\PowerShellWebAccess\\wwwroot\\Web.config_.

Varsayılan olarak, IIS Web sunucusu herhangi bir ayar düzenlendiğinde uygulama havuzunu yeniden başlatmak üzere yapılandırılır. Örneğin, değişiklikler yapılırsa uygulama havuzu yeniden başlatılır **web.config** dosya.
>Çünkü **Windows PowerShell Web erişimi** kullandığı bellek içi oturum durumları, açan kullanıcılar **Windows PowerShell Web erişimi** oturumları zaman uygulama havuzunu yeniden başlatıldığında oturumlarını kaybeder.

### <a name="setting-default-parameters-on-the-sign-in-page"></a>Oturum açma sayfasında varsayılan parametreleri ayarlama

Windows PowerShell Web erişimi ağ geçidiniz Windows Server 2012 R2'de çalışıyorsa, Windows PowerShell Web erişimi oturum açma sayfasında görüntülenen ayarlar için varsayılan değerleri yapılandırabilirsiniz. Değerleri yapılandırabilirsiniz **web.config** önceki paragrafta açıklanan dosya. Oturum açma sayfası ayarları için varsayılan değerleri içinde bulunan **appSettings** web.config dosyasının; aşağıdaki örneğidir **appSettings** bölümü. Bu ayarların çoğu için geçerli değerler: ilgili parametreleri için aynı [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) Windows PowerShell cmdlet'i.
Örneğin, `defaultApplicationName` , aşağıdaki kod bloğunda gösterildiği gibi anahtarıdır değerini **$PSSessionApplicationName** hedef bilgisayarda tercih değişkeni.

```xml
    <appSettings>
            <add key="maxSessionsAllowedPerUser" value="3"/>
            <add key="defaultPortNumber" value="5985"/>
            <add key="defaultSSLPortNumber" value="5986"/>
            <add key="defaultApplicationName" value="WSMAN"/>
            <add key="defaultUseSslSelection" value="0"/>
            <add key="defaultAuthenticationType" value="0"/>
            <add key="defaultAllowRedirection" value="0"/>
            <add key="defaultConfigurationName" value="Microsoft.PowerShell"/>
    </appSettings>
```

### <a name="time-outs-and-unplanned-disconnections"></a>Zaman aşımları ve planlanmamış bağlantı kesilmeleri

Windows PowerShell Web erişimi oturumları zaman aşımına uğradı. Windows PowerShell Web Windows Server 2012'de çalışan erişimi'nde, oturum kaldıktan sonra 15 dakika oturum açmış kullanıcılar için bir zaman aşımı iletisi görüntülenir. Zaman aşımı iletisi görüntülendikten sonra, kullanıcı beş dakika içinde yanıt vermezse, oturum sonlandırılır ve kullanıcı oturumu kapatılır. IIS Yöneticisi'nde web sitesi ayarlarında oturumlar için zaman aşımı sürelerini değiştirebilirsiniz.

Windows PowerShell Web oturum zaman aşımı, Windows Server 2012 R2 üzerinde varsayılan olarak, 20 dakika işlem yapılmadığında çalıştıran Access'te. Kullanıcıların web tabanlı konsolda oturum ağ hataları veya diğer planlanmamış kapatmalar veya hatalar nedeniyle bağlantısı kesilen ve bunlar oturumları kendileri kapatmadıkları için Windows PowerShell Web erişimi oturumları çalıştırmak, bağlı devam zaman aşımı süresi istemci tarafı geçene kadar hedef bilgisayarlar. Oturum bağlantısı, hangisi daha kısaysa, varsayılan 20 dakikadan sonra veya ağ geçidi yöneticisi tarafından belirtilen zaman aşımı süresi sonrasında kesilir.

Ağ Geçidi sunucusu Windows Server 2012 R2 çalıştırıyorsa, kullanıcılar için yeniden Windows PowerShell Web erişimi sağlar oturumları sonraki bir zamanda kaydedildi ancak ağ hataları, planlanmamış kapatmalar veya diğer hatalar nedeniyle oturumların bağlantısı kesildiğinde, kullanıcılar bakın veya kaydedilmiş yeniden bağlanma Ağ Geçidi tarafından belirtilen zaman aşımı süresinden sonra yönetici dolduğundan kadar oturumları.

## <a name="see-also"></a>Ayrıca bkz:

- [Yükleme ve Windows PowerShell Web erişimini kullanma](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
- [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)
- [Windows PowerShell Web erişim cmdlet'leri](cmdlets/web-access-cmdlets.md)
