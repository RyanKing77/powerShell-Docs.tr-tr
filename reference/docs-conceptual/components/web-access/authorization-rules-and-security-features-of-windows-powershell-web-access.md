---
ms.date: 06/27/2017
keywords: PowerShell cmdlet'i
title: Yetkilendirme kuralları ve güvenlik özellikleri Windows PowerShell Web erişimi
ms.openlocfilehash: c426b8cfb10829241ba244a5d840c91e1de9f66e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058429"
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a>Yetkilendirme kuralları ve güvenlik özellikleri Windows PowerShell Web erişimi

Güncelleme tarihi: 24 Haziran 2013

Uygulama hedefi: Windows Server 2012 R2, Windows Server 2012

Windows Server 2012 R2 ve Windows Server 2012, Windows PowerShell Web erişimi, bir kısıtlayıcı güvenlik modeline sahiptir. Windows PowerShell Web erişimi ağ geçidini oturum açın ve web tabanlı Windows PowerShell Konsolu önce kullanıcılara açıkça erişim verilmesi gerekir.

## <a name="configuring-authorization-rules-and-site-security"></a>Yetkilendirme kuralları ve site güvenliği yapılandırma

Windows PowerShell Web erişimi yüklendikten ve ağ geçidi yapılandırıldıktan sonra kullanıcılar oturum açma sayfasını bir tarayıcıda açabilir, ancak açıkça erişim Windows PowerShell Web erişimi yönetici kullanıcılar verene kadar oturum olamaz. 'Windows PowerShell Web Erişimi' erişim denetimi aşağıdaki tabloda açıklanan Windows PowerShell cmdlet'leri kümesi kullanılarak yönetilir. Ekleme veya yetkilendirme kuralları yönetmek için karşılaştırılabilir GUI yoktur.
Bkz: [Windows PowerShell Web erişim cmdlet'leri](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Yöneticiler tanımlayabilirsiniz `{0-n}` Windows PowerShell Web erişimi için kimlik doğrulama kuralları. Varsayılan güvenliği kısıtlayıcıdır İhtiyari; yol sıfır kimlik doğrulama kuralları şeye erişimi kullanıcı yok.

[Ekle-PswaAuthorizationRule](/powershell/module/powershellwebaccess/add-pswaauthorizationrule?view=winserver2012r2-ps) ve [Test-PswaAuthorizationRule](/powershell/module/powershellwebaccess/test-pswaauthorizationrule?view=winserver2012r2-ps) Windows Server 2012 R2'de ekleyin ve bir uzak Windows PowerShell Web Erişimi yetkilendirme kuralları test etmenize olanak tanıyan bir kimlik bilgisi parametresi içerir bilgisayar veya etkin bir Windows PowerShell Web erişimi oturumu içinde. Olarak bir kimlik bilgisi parametresi olan diğer Windows PowerShell cmdlet'leriyle, bir PSCredential nesnesi parametresinin değeri belirtebilirsiniz. Uzak bir bilgisayara geçirmek istediğiniz kimlik bilgilerini içeren bir PSCredential nesnesi oluşturmak için çalıştırılması [Get-Credential](/powershell/module/microsoft.powershell.security/Get-Credential) cmdlet'i.

Windows PowerShell Web erişimi kimlik doğrulama kuralları beyaz liste kurallarıdır. Her kural, kullanıcılar ve hedef bilgisayarlar için belirli bir Windows PowerShell arasındaki izin verilen bir bağlantının tanımıdır [oturum yapılandırmaları](/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-5.1) (uç noktaları olarak da adlandırılan veya _çalışma alanları_) üzerinde Belirtilen hedef bilgisayarlar.
Açıklaması **çalışma alanları** bkz [başına kullanım, PowerShell çalışma alanları](https://blogs.technet.microsoft.com/heyscriptingguy/2015/11/26/beginning-use-of-powershell-runspaces-part-1/)

> [!IMPORTANT]
> Bir kullanıcının erişim elde etme true olması için yalnızca bir kural gerekir. Bir kullanıcı bir bilgisayara tam dil erişimi veya web tabanlı konsoldan, yalnızca için Windows PowerShell uzak yönetim Cmdlet'lerine erişimi ile erişim verilirse, kullanıcı oturum (veya atlama) ilk hedef bilgisayara bağlı diğer bilgisayarlara. Windows PowerShell Web erişimi yapılandırmak için en güvenli yolu, kullanıcılara normalde uzaktan yapmak için ihtiyaç duydukları belirli görevleri gerçekleştirmelerine olanak tanıyan kısıtlı oturum yapılandırmalarına erişim imkanı sağlamaktır.

Başvurulan cmdlet'leri [Windows PowerShell Web erişimi cmdlet'leri](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps) erişim kuralları, bir kullanıcı Windows PowerShell Web erişim ağ geçidinde yetkilendirmek için kullanılan bir dizi oluşturulmasına izin verin. Kurallar, hedef bilgisayardaki erişim denetim listeleri (ACL) farklıdır ve web erişimi için ek bir güvenlik katmanı sağlar. Güvenlik hakkında daha fazla ayrıntı, aşağıdaki bölümde açıklanmıştır.

Kullanıcılar herhangi bir önceki güvenlik katmanını geçemezse, Tarayıcı pencerelerinde bir genel erişim reddedildi' iletisi alırsınız. Güvenlik ayrıntıları Ağ Geçidi sunucusunda günlüğe kaydedilmiş olsa da, son kullanıcılar oturum açma veya kimlik doğrulama hatası oluştu veya hakkında bilgi geçirilen kaç güvenlik katmanları, hangi katmanda gösterilmez.

Yetkilendirme kuralları yapılandırma hakkında daha fazla bilgi için bkz. [yetkilendirme kuralları yapılandırma](#configuring-authorization-rules-and-site-security) bu konuda.

### <a name="security"></a>Güvenlik

Windows PowerShell Web erişimi güvenlik modeli, web tabanlı konsolun bir end user ve bir hedef bilgisayar arasında dört katmanı vardır. Windows PowerShell Web erişimi Yöneticiler IIS Yöneticisi konsolunda ek yapılandırmayla ilave güvenlik katmanları ekleyebilir. IIS Yöneticisi konsolunda Web sitelerinin güvenliğini sağlama hakkında daha fazla bilgi için bkz. [Web sunucusu güvenlik yapılandırması (IIS7)](https://technet.microsoft.com/library/cc731278).

IIS hakkında daha fazla bilgi için en iyi uygulamalar ve hizmet reddi saldırılarını önleme, bkz: [en iyi yöntemler için engelleme DoS/hizmet reddi saldırılarını](https://technet.microsoft.com/library/cc750213).
Yönetici ayrıca satın alın ve ek perakende yetkilendirme yazılımı yükleyin.

Aşağıdaki tabloda dört son kullanıcılar ve hedef bilgisayar arasında bir güvenlik katmanı açıklanmaktadır.

|Düzey|Katman|
|-|-|
|1|[IIS web sunucusu güvenlik özellikleri](#iis-web-server-security-features)|
|2|[Windows powershell web erişimi ağ geçidini form tabanlı kimlik doğrulaması](#windows-powershell-web-access-forms-based-gateway-authentication)|
|3|[Windows powershell web erişimi yetkilendirme kuralları](#windows-powershell-web-access-authorization-rules)|
|4|[Hedef kimlik doğrulama ve yetkilendirme kuralları](#target-authentication-and-authorization-rules)|

Aşağıdaki başlıklar altında her katman hakkında ayrıntılı bilgi bulunabilir:

#### <a name="iis-web-server-security-features"></a>IIS Web sunucusu güvenlik özellikleri

Windows PowerShell Web erişim kullanıcılarını, bir kullanıcı adı ve parola geçidinde kendi hesaplarının kimliğini doğrulamak için her zaman sağlamanız gerekir. Ancak, Windows PowerShell Web erişim yöneticileri Ayrıca isteğe bağlı istemci sertifikası kimlik doğrulaması veya kapat bakın kapatabilirsiniz [windows powershell web erişimi yükleme ve kullanma](install-and-use-windows-powershell-web-access.md) bir test sertifikası etkinleştirmek için ve daha sonra yapılandırmak nasıl bir Orijinal sertifika).

İsteğe bağlı istemci sertifikası özelliği, son kullanıcılar, kullanıcı adları ve parolalar, ek olarak bir geçerli istemci sertifikasına sahip olmasını gerektirir ve Web sunucusu (IIS) yapılandırmasının bir parçasıdır. İstemci sertifikası katmanı etkinleştirildiğinde, Windows PowerShell Web erişimi oturum açma sayfasında, oturum açma kimlik bilgilerini değerlendirilmeden önce geçerli sertifikalar sağlaması için kullanıcıya sorar. İstemci sertifikası kimlik doğrulaması için istemci sertifikasını otomatik olarak denetler. Geçerli bir sertifika bulunmazsa, Windows PowerShell Web erişimi kullanıcıları bilgilendirir, böylelikle sertifikayı sağlayabilirler. Geçerli bir istemci sertifikası bulunursa, Windows PowerShell Web erişimi, kullanıcıların kendi kullanıcı adlarını ve parolalarını sağlayabilmeleri oturum açma sayfası açılır.

Bu, IIS Web sunucusu tarafından sunulan ek güvenlik ayarlarına bir örnektir. Diğer IIS güvenlik özellikleri hakkında daha fazla bilgi için bkz. [Web sunucusu güvenlik yapılandırması (IIS 7)](https://technet.microsoft.com/library/cc731278).

#### <a name="windows-powershell-web-access-forms-based-gateway-authentication"></a>Windows PowerShell Web erişimi ağ geçidini form tabanlı kimlik doğrulaması

Windows PowerShell Web erişimi oturum açma sayfasında kimlik bilgileri (kullanıcı adı ve parola) gerektirir ve kullanıcılara hedef bilgisayar için farklı kimlik bilgileri sağlama seçeneği sunar.
Kullanıcı alternatif kimlik bilgileri sağlamazsa, birincil kullanıcı adını ve ağ geçidine bağlanmak için kullanılan parola ayrıca hedef bilgisayara bağlanmak için kullanılır.

Windows PowerShell Web erişimi ağ geçidini gerekli kimlik bilgilerinin doğrulanır. Bu kimlik bilgileri geçerli bir kullanıcı hesapları ya da yerel Windows PowerShell Web erişimi Ağ Geçidi sunucusunda veya Active Directory'de olması gerekir.

#### <a name="windows-powershell-web-access-authorization-rules"></a>Windows PowerShell Web Erişimi yetkilendirme kuralları

Bir kullanıcı geçidinde doğrulandıktan sonra Windows PowerShell Web Erişimi yetkilendirme kuralları, kullanıcının istenen hedef bilgisayara erişimi olup olmadığını doğrulamak için denetler. Başarılı yetkilendirme sonrasında, kullanıcının kimlik bilgilerini hedef bilgisayara birlikte geçirilir.

Bu kurallar, yalnızca bir kullanıcı ağ geçidi tarafından doğrulandıktan sonra ve bir kullanıcı hedef bilgisayarda doğrulanabilmesinden önce değerlendirilir.

#### <a name="target-authentication-and-authorization-rules"></a>Hedef kimlik doğrulama ve yetkilendirme kuralları

Windows PowerShell Web erişimi için güvenliğin son katmanı hedef bilgisayarın kendi güvenlik yapılandırmasıdır. Kullanıcılar, Windows PowerShell Web erişimi bir hedef bilgisayarı etkileyen bir Windows PowerShell web tabanlı konsol çalıştırmak için hedef bilgisayarda ve Windows PowerShell Web Erişimi yetkilendirme kurallarında, yapılandırılmış uygun erişim hakları olmalıdır.

Bu katman, kullanıcılar çalıştırarak Windows PowerShell içinde bir hedef bilgisayara bir uzak Windows PowerShell oturumu oluşturmaya çalıştılarsa bağlantı denemelerini değerlendirecek güvenlik mekanizmalarının aynısını sunar [Enter-PSSession](/powershell/module/microsoft.powershell.core/Enter-PSSession) veya [New-PSSession](/powershell/module/microsoft.powershell.core/new-pssession) cmdlet'leri.

Varsayılan olarak, Windows PowerShell Web erişimi, hem ağ geçidi hem de hedef bilgisayarda kimlik doğrulaması için birincil kullanıcı adı ve parola kullanır. Web tabanlı oturum açma sayfasında, başlıklı bir bölümde **isteğe bağlı bağlantı ayarları**, gerektirilirse kullanıcılar hedef bilgisayar için farklı kimlik bilgileri sağlama seçeneği sunar. Kullanıcı alternatif kimlik bilgileri sağlamazsa, birincil kullanıcı adını ve ağ geçidine bağlanmak için kullanılan parola ayrıca hedef bilgisayara bağlanmak için kullanılır.

Yetkilendirme kuralları, kullanıcıların belirli bir oturum yapılandırmasına erişmesine izin vermek için kullanılabilir. Oluşturabileceğiniz _kısıtlı çalışma alanları_ veya oturum yapılandırmaları için Windows PowerShell Web erişimi ve belirli kullanıcılar için Windows PowerShell Web erişimi oturum açtığında, yalnızca belirli oturum yapılandırmalarına bağlanmasına izin verir. Hangi kullanıcıların belirli Uç noktalara erişimi olduğunu belirlemek ve erişimi belirli bir kullanıcı kümesi için uç nokta için bu bölümde açıklanan yetkilendirme kurallarını kullanarak daha da kısıtlamanıza erişim denetim listeleri (ACL'ler) kullanabilirsiniz. Kısıtlı çalışma alanları hakkında daha fazla bilgi için bkz: [kısıtlı bir çalışma alanı oluşturma](https://msdn.microsoft.com/library/dn614668).

### <a name="configuring-authorization-rules"></a>Yetkilendirme kuralları yapılandırma

Yöneticiler olasılıkla, ortamlarında Windows PowerShell uzaktan yönetimi için zaten tanımlanmış olan Windows PowerShell Web erişimi kullanıcılar için Yetkilendirme kuralının aynısını istersiniz. Bu bölümdeki ilk yordam, bir kullanıcı, bir bilgisayarı yönetmek oturum açma ve tek bir oturum yapılandırması içinde erişim veren bir güvenli Yetkilendirme kuralının eklemeyi açıklar. İkinci yordam gerekli olmayan bir Yetkilendirme kuralının nasıl kaldırılacağı açıklanmaktadır.

Yalnızca kısıtlı çalışma alanları Windows PowerShell Web Erişimi'nde içinde çalışmak belirli kullanıcılara izin vermek için özel oturum yapılandırmaları kullanmayı planlıyorsanız, özel oturum yapılandırmalarınızı, onları belirten yetkilendirme kuralları eklemeden önce oluşturun. Windows PowerShell Web erişimi cmdlet'leri, özel oturum yapılandırmaları oluşturmak için kullanamazsınız. Özel oturum yapılandırmaları oluşturma hakkında daha fazla bilgi için bkz. [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

Windows PowerShell Web erişimi cmdlet'leri bir joker karakter, bir yıldız işareti destekler ( \* ). Dizeler içindeki joker karakterler desteklenmez; özellik (kullanıcılar, bilgisayarlar veya oturum yapılandırmaları) başına tek bir yıldız işareti kullanın.

> [!NOTE]
> Yetkilendirme kuralları kullanıcılara erişim izni ve Windows PowerShell Web erişimi ortam güvenliğini sağlamaya yardımcı olmak için kullanabileceğiniz diğer yolları için bkz [diğer yetkilendirme kuralı senaryo örnekleri](#other-authorization-rule-scenario-examples) bu konuda.

#### <a name="to-add-a-restrictive-authorization-rule"></a>Kısıtlayıcı yetkilendirme kuralı eklemek için

1. Bir Windows PowerShell oturumu yükseltilmiş kullanıcı haklarıyla açmak için aşağıdakilerden birini yapın.

   - Windows masaüstünde, sağ **Windows PowerShell** görev ve ardından **yönetici olarak çalıştır**.

   - Windows üzerinde **Başlat** ekranında, sağ **Windows PowerShell**ve ardından **yönetici olarak çalıştır**.

2. **İsteğe bağlı bir adım** kullanıcı erişimini oturum yapılandırmaları kullanarak kısıtlamak için:

   Kullanmak istediğiniz oturum yapılandırmalarının zaten mevcut kurallarınızda doğrulayın.

   Bunlar henüz oluşturulmadı, içindeki oturum yapılandırmaları oluşturmak için yönergeleri kullanın [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

3. Bu yetkilendirme kuralı belirli bir bilgisayar erişmesine izin verir, genellikle sahip oldukları erişimi kullanıcıya kapsayan belirli bir oturum yapılandırması erişimi ile ağ '™ s tipik komut dosyası ve cmdlet gereksinimlerine. Aşağıdaki komutu yazın ve ardından basın **Enter**.

   ```
   Add-PswaAuthorizationRule -UserName <domain\user | computer\user> `
      -ComputerName <computer_name> -ConfigurationName <session_configuration_name>
   ```

   - Aşağıdaki örnekte adlı bir kullanıcıya _JSmith_ içinde _Contoso_ etki alanı bilgisayarı yönetmek için erişim verildi _Contoso_214_ve adlı bir oturum yapılandırması kullanın _NewAdminsOnly_.

   ```powershell
   Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' `
      -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly
   ```

4. Kural çalıştırılarak oluşturulduğunu doğrulayın **Get-PswaAuthorizationRule** cmdlet'ini veya `Test-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName** <computer_name>`.
   Örneğin, `Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214`.

#### <a name="to-remove-an-authorization-rule"></a>Bir yetkilendirme kuralı kaldırmak için

1. 1. adımı bir Windows PowerShell oturumu zaten açık değilse bkz [kısıtlayıcı yetkilendirme kuralı eklemek için](#to-add-a-restrictive-authorization-rule) bu bölümdeki.

2. Aşağıdaki komutu yazın ve ardından basın **Enter**burada *kural kimliği* kaldırmak istediğiniz kuralın benzersiz kimlik numarasını temsil eder.

   ```
   Remove-PswaAuthorizationRule -ID <rule ID>
   ```

   Alternatif olarak, kimlik numarasını bilmiyorsanız, ancak kaldırmak istediğiniz kuralın kolay adını biliyorsanız yaparsanız, kural adını alın ve kendisine kanal `Remove-PswaAuthorizationRule` cmdlet'i aşağıdaki örnekte gösterildiği gibi kuralı kaldırmak için:

   ```
   Get-PswaAuthorizationRule `
      -RuleName <rule-name> | Remove-PswaAuthorizationRule
   ```

> [!NOTE]
> Belirtilen yetkilendirme kuralını silmek isteyip istemediğinizi onaylamanız istenmez; Kural bastığınızda silinir **Enter**. Çalıştırmadan önce yetkilendirme kuralını kaldırmak istediğinizden emin olmalısınız `Remove-PswaAuthorizationRule` cmdlet'i.

#### <a name="other-authorization-rule-scenario-examples"></a>Diğer yetkilendirme kuralı senaryo örnekleri

Her Windows PowerShell oturumunda bir oturum yapılandırması kullanır. bir oturum için belirtilmezse, Windows PowerShell varsayılan, Microsoft.PowerShell adlı yerleşik Windows PowerShell oturum yapılandırması kullanır. Varsayılan oturum yapılandırması, bir bilgisayarda mevcut tüm cmdlet'leri içerir. Yöneticiler sınırlı bir çalışma alanı (sınırlı cmdlet'leri ve son kullanıcıları gerçekleştirebilir görevleri bir aralık) ile bir oturum yapılandırması tanımlayarak tüm bilgisayarlara erişimi kısıtlayabilirsiniz. Tam dil erişimi veya yalnızca Windows PowerShell uzak yönetim cmdlet'leriyle bir bilgisayara erişim verilen bir kullanıcı, ilk bilgisayara bağlı diğer bilgisayarlara bağlanabilir. Sınırlı bir çalışma alanı tanımlanması kullanıcılar kendi izin verilen bir Windows PowerShell çalışma alanından diğer bilgisayarlara erişmesini engelleyebilir ve Windows PowerShell Web erişimi ortamınızın güvenliğini artırır. Oturum yapılandırması (Grup İlkesi kullanılarak) Yöneticiler, Windows PowerShell Web erişimi aracılığıyla erişilebilir olmasını istediğiniz tüm bilgisayarlara dağıtılabilir. Oturum yapılandırmaları hakkında daha fazla bilgi için bkz: [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx). Bu senaryonun bazı örnekleri aşağıda verilmiştir.

- Adlı bir uç nokta, bir yöneticinin oluşturduğu **PswaEndpoint**, sınırlı bir çalışma. Yönetici bir kural oluşturur sonra `*,*,PswaEndpoint`, uç noktayı diğer bilgisayarlara dağıtır. Kural tüm kullanıcıların uç noktası ile tüm bilgisayarlara erişmesine izin verdiği **PswaEndpoint**.
  Bu kural kümesinde tanımlanan tek yetkilendirme kuralı ise, o uç noktası olmayan bilgisayarlara erişilemez.

- Bir uç nokta ile sınırlı bir çalışma alanı oluşturan yönetici adlı **PswaEndpoint**ve belirli kullanıcılar için erişimi sınırlandırmak istemektedir. Yönetici adı verilen bir kullanıcı grubu oluşturuyor **Level1Support**ve şu kuralı tanımlıyor: **Level1Support,\*, PswaEndpoint**. Kural gruptaki tüm kullanıcılar verir **Level1Support** erişimi olan tüm bilgisayarlara **PswaEndpoint** yapılandırma. Benzer şekilde, erişim belirli bir bilgisayar kümesine sınırlanabilir.

- Bazı yöneticiler, belirli kullanıcılara diğerlerinden daha fazla erişim sağlar. Örneğin, bir yönetici iki kullanıcı grubu oluşturuyor **yöneticileri** ve **BasicSupport**. Yönetici bir uç nokta adı verilen sınırlı bir çalışma da oluşturur. **PswaEndpoint**ve şu iki kuralı tanımlıyor: **Yöneticiler,\*,\***  ve **BasicSupport,\*, PswaEndpoint**. İlk kural içindeki tüm kullanıcılar sağlar **yönetici** tüm bilgisayarlar ve ikinci kural grubu erişim sağlayan tüm kullanıcıların **BasicSupport** grubu yalnızca olan bilgisayarlara erişim  **PswaEndpoint**.

- Bir yönetici özel bir test ortamı ayarlamış ve tüm yetkilendirilmiş ağ kullanıcılarına, genellikle erişimi olan tüm oturum yapılandırmalarıyla için tipik olarak erişime sahip oldukları erişim ile sahip oldukları ağdaki tüm bilgisayarlara erişim izin vermek istiyor. Bu özel bir test ortamı olduğundan, yönetici güvenli olmayan bir yetkilendirme kuralı oluşturur. -Yönetici cmdlet'ini çalıştırır `Add-PswaAuthorizationRule * * *`, joker karakterini kullanan **\*** tüm kullanıcılar, tüm bilgisayarlar ve tüm yapılandırmaları belirtmek için. -Bu kural aşağıdaki eşdeğerdir: `Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *`.

  > [!NOTE]
  > Bu kural, güvenli bir ortamda önerilmez ve güvenlik Windows PowerShell Web erişimi tarafından sağlanan yetkilendirme kuralı katmanını atlar.

- Yönetici kullanıcıların hem çalışma grupları hem de burada çalışma grubu bilgisayarlarını ara sıra etki alanlarındaki hedef bilgisayarlara bağlanmak için kullanılır ve etki alanlarındaki bilgisayarların ara sıra kullanılan etki alanları, bir ortamda hedef bilgisayarlara bağlanmasına izin vermeniz gerekir alanlarındaki hedef bilgisayarlara bağlanmak için. Yönetici olan bir ağ geçidi sunucusu *PswaServer*, bir çalışma grubunda; ve hedef bilgisayar *srv1.contoso.com* bir etki alanında. Kullanıcı *Chris* hem çalışma grubu Ağ Geçidi sunucusunda hem de hedef bilgisayarda yetkili bir yerel kullanıcı. Çalışma grubu sunucusundaki kullanıcı adı olan *chrisLocal*; ve hedef bilgisayardaki kullanıcı adı *contoso\\chris*. Chris'e srv1.contoso.com erişimini yetkilendirmek için yönetici aşağıdaki kuralı ekler.

```powershell
Add-PswaAuthorizationRule -userName PswaServer\chrisLocal `
   -computerName srv1.contoso.com -configurationName Microsoft.PowerShell
```

Önceki kural örneği, Chris Ağ Geçidi sunucusunda kimliğini doğrular ve ardından kendi erişimini yetkilendirir *srv1*. Oturum açma sayfasında, Chris ikinci bir kimlik bilgilerini sağlamanız gerekir **isteğe bağlı bağlantı ayarları** alan (*contoso\\chris*). Ağ Geçidi sunucusu, ona hedef bilgisayarda kimlik doğrulaması için ek kimlik bilgileri kümesini kullanır. *srv1.contoso.com*.

Yalnızca aşağıdakiler başarılı olduktan ve en az bir yetkilendirme kuralı tarafından izin verilen eklendikten sonra önceki senaryoda, Windows PowerShell Web erişimi hedef bilgisayara başarılı bir bağlantı kurar.

1. Bir kullanıcı adı biçiminde ekleyerek çalışma grubu Ağ Geçidi sunucusunda kimlik doğrulaması *sunucu_adı*\\*user_name* yetkilendirme kuralı için

2. Kimlik doğrulaması oturum açma sayfasında sağlanan alternatif kimlik bilgileri kullanarak hedef bilgisayarda **isteğe bağlı bağlantı ayarları** alan

   > [!NOTE]
   > Ağ geçidi ve hedef bilgisayarlar farklı çalışma gruplarında veya etki alanlarında ise iki çalışma grubu bilgisayarları olan iki etki alanı veya çalışma grubu ve etki alanı arasında bir güven ilişkisi kurulmalıdır. Bu ilişki, Windows PowerShell Web Erişimi yetkilendirme kuralı cmdlet'leri kullanılarak yapılandırılamaz. Yetkilendirme kuralları bilgisayarlar arasında bir güven ilişkisi tanımlamaz; yalnızca belirli hedef bilgisayarlara ve oturum yapılandırmalarına bağlanmasına yetki verebilir. Farklı etki alanları arasında bir güven ilişkisi yapılandırma hakkında daha fazla bilgi için bkz. [oluşturma etki alanı ve orman güvenleri](https://technet.microsoft.com/library/cc794775.aspx).
   > Bir güvenilir konaklar listesine çalışma grubu bilgisayarları ekleme hakkında daha fazla bilgi için bkz. [Sunucu Yöneticisi ile uzaktan yönetim](https://technet.microsoft.com/library/dd759202.aspx).

### <a name="using-a-single-set-of-authorization-rules-for-multiple-sites"></a>Birden çok site için tek bir yetkilendirme kuralları kümesi kullanma

Yetkilendirme kuralları, bir XML dosyasında depolanır. Varsayılan olarak, XML dosyasının yol adı olan `$env:windir\Web\PowershellWebAccess\data\AuthorizationRules.xml`.

Yetkilendirme kurallarının XML dosyası yolu depolanan **powwa.config** içinde bulunan dosya `$env:windir\Web\PowershellWebAccess\data`. Yönetici içinde varsayılan yol referansını değiştirme esnekliğine sahiptir **powwa.config** tercihlerine veya gereksinimlerine uyacak şekilde. Bu tür bir yapılandırma istenirse dosyasının konumunu değiştirmek için yöneticiye izin verme, aynı yetkilendirme kurallarını birden fazla Windows PowerShell Web erişimi ağ geçidi olanak tanır.

## <a name="session-management"></a>Oturum yönetimi

Varsayılan olarak, Windows PowerShell Web erişimi bir kullanıcı aynı anda üç oturumla sınırlar. Web uygulamasının düzenleyebileceğiniz **web.config** farklı bir kullanıcı başına oturum sayısı desteklemek için IIS Yöneticisi'nde dosya. Yolu **web.config** dosyasıdır `$env:windir\Web\PowerShellWebAccess\wwwroot\Web.config`.

Varsayılan olarak, IIS Web sunucusu herhangi bir ayar düzenlendiğinde uygulama havuzunu yeniden başlatmak üzere yapılandırılır. Örneğin, değişiklikler yapılırsa uygulama havuzu yeniden başlatılır **web.config** dosya. > çünkü **Windows PowerShell Web erişimi** kullanan bellek içi oturum durumları > kullanıcıların oturumu **Windows PowerShell Web erişimi** oturumlarını uygulama havuzu başlatıldığında oturumlarını kaybeder.

### <a name="setting-default-parameters-on-the-sign-in-page"></a>Oturum açma sayfasında varsayılan parametreleri ayarlama

Windows PowerShell Web erişimi ağ geçidi Windows Server 2012 R2 üzerinde çalışıyorsa, Windows PowerShell Web erişimi oturum açma sayfasında görüntülenen ayarlar için varsayılan değerleri yapılandırabilirsiniz. Değerleri yapılandırabilirsiniz **web.config** önceki paragrafta açıklanan dosya. Oturum açma sayfası ayarları için varsayılan değerler bulunur **appSettings** web.config dosyasının; aşağıdaki örneğidir **appSettings** bölümü. Bu ayarların çoğu için geçerli değerler: ilgili parametreleri için aynı [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) Windows PowerShell cmdlet'i.

Örneğin, `defaultApplicationName` anahtarı, aşağıdaki kod bloğunda gösterildiği gibi değeri **$PSSessionApplicationName** hedef bilgisayarda tercih değişkeni.

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

Windows PowerShell Web erişimi oturumları zaman aşımına uğrar. Windows PowerShell Web Windows Server 2012'de çalışan erişimi'nde, 15 dakika işlem yapılmadığında oturum açmış kullanıcılara bir zaman aşımı iletisi görüntülenir. Kullanıcı zaman aşımı iletisi görüntülendikten sonra beş dakika içinde yanıt vermezse oturum sonlandırılır ve kullanıcı oturumunu kapatmadan. IIS Yöneticisi'nde Web sitesi ayarlarında oturumlar için zaman aşımı sürelerini değiştirebilirsiniz.

Windows PowerShell Web oturumların zaman aşımı, Windows Server 2012 R2 üzerinde varsayılan olarak 20 dakika işlem yapılmadığında çalıştırılan Access'te. Kullanıcıların web tabanlı konsolda oturum ağ hata veya diğer planlanmamış kapatma veya arıza nedeniyle kesildiyse ve oturumları kendileri kapatmadıkları Windows PowerShell Web erişimi oturumları çalıştırmak, bağlı devam edin istemci tarafı kesildiyse zaman aşımı süresi kadar hedef bilgisayarlar. Oturumu sonra ya da varsayılan 20 dakika kesildiğinde veya Ağ Geçidi Yöneticisi tarafından belirtilen zaman aşımı süresi sonrasında, hangisi daha kısaysa.

Ağ Geçidi sunucusu Windows Server 2012 R2 çalıştırıyorsa, sonraki bir zamanda oturumları için kullanıcıların yeniden Windows PowerShell Web erişimi sağlar kaydedildi, ancak ağ hataları, planlanmamış kapatmalar veya diğer hatalar oturumların bağlantısı kesildiğinde, kullanıcılar göremez veya kaydedilmiş yeniden Ağ Geçidi tarafından belirtilen zaman aşımı süresinden sonra yönetici geçene kadar oturumları.

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell Web erişimi yükleme ve kullanma](https://technet.microsoft.com/library/hh831611(v=ws.11).aspx)

[about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)

[Windows PowerShell Web erişim cmdlet'leri](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps)
