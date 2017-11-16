---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea, powershell, güvenlik"
title: "JEA güvenlik konuları"
ms.openlocfilehash: 2dcce34113998a1c31709b6afe6d0a21c991e79d
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2017
---
# <a name="jea-security-considerations"></a>JEA güvenlik konuları

> Uygulandığı öğe: Windows PowerShell 5.0

JEA, güvenlikle ilgili tutumunuzu makinelerinizi kalıcı Yöneticiler sayısını azaltarak artırılmasına yardımcı olur.
Bunu kullanıcıların sıkı bir şekilde kötüye kullanımı önlemek için varsayılan olarak kilitlenmiştir (bir PowerShell oturum yapılandırması) sistemini yönetmek yeni bir giriş noktası oluşturarak yapar.
Bazı, gereken ancak kullanıcılar sınırsız, yönetim görevlerini gerçekleştirmek için makine erişim JEA uç noktasına erişim izni.
JEA bunları yönetici erişimi zorunda kalmadan doğrudan yönetim komutları çalıştırmak izin verdiğinden, sonra (standart kullanıcılar olmalarını) yüksek ayrıcalıklı güvenlik gruplarındaki kullanıcılar kaldırabilirsiniz.

Bu konuda daha ayrıntılı en iyi yöntemler ve JEA güvenlik modeli açıklanır.

## <a name="run-as-account"></a>Farklı Çalıştır hesabı

Her JEA bitiş altında bağlanan kullanıcının Eylemler gerçekleştirileceği hesabı olan bir belirlenen "Farklı Çalıştır" hesabı vardır.
Bu hesap olarak yapılandırılabilir, [oturum yapılandırma dosyası](session-configurations.md), ve seçtiğiniz hesap uç noktanızı güvenlik üzerinde önemli bir şifrelemeyle sahiptir.

**Sanal hesaplar** run hesabıyla yapılandırma için önerilen yoldur.
JEA oturumuna süresi sırasında kullanılacak bağlanan kullanıcı için oluşturulan tek seferlik, geçici yerel hesaplar sanal hesaplarıdır.
Kullanıcıların oturumlarını sona hemen sanal hesap yok edilmesi ve artık kullanılamaz.
Bağlanan kullanıcı hesabının kimlik bilgilerini sanal bilmez ve sanal hesap Uzak Masaüstü veya bir Kısıtlanmamış PowerShell uç nokta gibi diğer yollarla üzerinden erişmek için kullanılamaz.

Varsayılan olarak, sanal hesaplar makinede yerel Yöneticiler grubuna ait.
Bu bunları sistemde herhangi bir şey yönetmek için tüm haklara, ancak ağ kaynaklarını yönetme hakkı verir.
Diğer makinelerle kimlik doğrulamasını yaparken, kullanıcı bağlamı, yerel bilgisayar hesabının, sanal hesap olacaktır.

Yerel Yöneticiler grubunun kavramına olduğundan etki alanı denetleyicileri bir özel durum etkilenir.
Bunun yerine, sanal hesaplar etki alanı yöneticileri için bunun yerine ait ve etki alanı denetleyicisindeki Dizin Hizmetleri yönetebilir.
Etki alanı kimliği burada JEA oturum örneğinin başlatılmasından ve herhangi bir ağ erişim etki alanı denetleyicisi bilgisayar nesnesinden yerine gelen görünür etki alanı denetleyicisinde kullanmak için hala sınırlıdır.

Her iki durumda da, açıkça sanal ait olması hangi güvenlik gruplarının tanımlayabilirsiniz.
Gerçekleştirmekte olduğunuz görev yerel/etki alanı yönetici ayrıcalıklarına yapılabilir olduğunda iyi bir uygulamadır.
Yöneticiler için tanımlanmış bir güvenlik grubu zaten varsa, yalnızca gerekli izinleri vermek için bu gruba sanal hesap için üyelik verebilirsiniz.
Sanal Hesap Grup üyeliği iş istasyonu ve üye sunuculara yerel güvenlik grupları sınırlıdır, ancak bir etki alanı denetleyicisinde bunlar yalnızca etki alanı güvenlik gruplarının üyesi olabilir.
Ait bir veya daha fazla güvenlik grupları için sanal hesap belirttiğinizde, artık (yerel yönetici veya etki alanı yöneticisi) varsayılan gruplara ait.

Sonuçta elde edilen sanal hesapların izinlerini ve olası yapılandırma seçenekleri aşağıdaki tabloda özetlenmiştir

Bilgisayar türü                | Sanal hesap grubu yapılandırması | Yerel kullanıcı bağlamı                                      | Ağ kullanıcı bağlamı
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
Etki alanı denetleyicisi            | Varsayılan                             | Etki alanı kullanıcısı, üyesi '*etki alanı*\Domain Admins'         | Bilgisayar hesabı
Etki alanı denetleyicisi            | Etki alanı gruplarını A ve B               | Etki alanı kullanıcısı, üyesi '*etki alanı*\A ','*etki alanı*\B'       | Bilgisayar hesabı
Üye sunucusu veya iş istasyonu | Varsayılan                             | Yerel bir kullanıcı, üyesi '*YERLEŞİK*\Administrators'        | Bilgisayar hesabı
Üye sunucusu veya iş istasyonu | C ve D yerel gruplar                | Yerel bir kullanıcı, üyesi '*bilgisayar*\C' ve '*bilgisayar*\D' | Bilgisayar hesabı

Güvenlik denetim olaylarını ve uygulama olay günlüklerini baktığınızda, her JEA kullanıcı oturumunu benzersiz bir sanal hesabı olduğunu görürsünüz.
Bu kullanıcı eylemlerini JEA uç noktada komutu çalıştıran özgün kullanıcıya geri izlemenize yardımcı olur.
Sanal hesap adlarını izleyin biçimi "WinRM sanal kullanıcıların\\WinRM\_VA\_*ACCOUNTNUMBER*\_*etki alanı* \_ *sAMAccountName*"Örneğin, kullanıcı etki alanında"Contoso"" Alice"bir JEA uç hizmet yeniden başlarsa, tüm hizmet denetimi yöneticisi olaylarını ile ilişkili kullanıcı adını olması" WinRM sanal kullanıcıların\\WinRM\_ VA\_1\_contoso\_alice ".


**Grup yönetilen hizmet hesapları (gmsa'ları)** bir üye sunucuya ağ kaynaklarına erişim JEA oturumunuz gerektiğinde kullanışlıdır.
Bu bir örnek kullanım örneği farklı bir makinede barındırılan bir REST API erişimi denetlemek için kullanılan bir JEA uç noktadır.
Bir ağ kimliğini işlevleri REST API istenen çağrılarını yapmak için ancak API ile kimlik doğrulamak için gereken yazma kolaydır.
Grup yönetilen hizmet hesabı kullanarak "ikinci atlama" hala üzerinde bilgisayar hesabı kullanabilirsiniz denetim yaparken mümkün kılar.
GMSA etkili izinleri gMSA hesabının ait olduğu güvenlik grupları (yerel veya etki alanı) tarafından tanımlanır.

JEA uç noktası bir gMSA hesabı kullanmak üzere yapılandırıldığında, yönetilen hizmet hesabı aynı grubundan gelen tüm JEA kullanıcılar eylemler görüntülenir.
Belirli bir kullanıcıya geri eylemleri izleyebilirsiniz tek bir PowerShell oturumu dökümü çalıştırma komutları kümesini tanımlamak için yoludur.

**Geçişi aracılığı kimlik bilgilerini** , olmayan bir farklı çalıştır hesabı olarak belirttiğiniz ve uzak sunucuda komutları çalıştırmak için bağlanan kullanıcının kimlik bilgilerini kullanmak için PowerShell istediğinizde kullanılır.
Bu yapılandırma *değil* ayrıcalıklı yönetim gruplarına bağlanma kullanıcı doğrudan erişim vermek için gerektirecek şekilde JEA için önerilir.
Bağlanan kullanıcının yönetici ayrıcalıkları varsa, bunlar JEA tamamen önlemek ve diğer, Kısıtlanmamış yollar üzerinden yönetebilirsiniz.
Aşağıdaki bölüme bakın [JEA admins karşı korumaz](#jea-does-not-protect-against-admins) daha fazla bilgi için.

**Standart farklı çalıştır hesapları** tüm PowerShell oturumu altında çalışacağı herhangi bir kullanıcı hesabı belirtmenizi sağlar.
Bir oturum yapılandırması sabit farklı çalıştır hesabı olarak kullanmak üzere ayarlamak için önemli bir fark budur (ile `-RunAsCredential` parametresi) JEA uyumlu değil.
Rol Tanımları artık beklendiği gibi çalışmaz ve uç noktasına erişmek için yetkili her kullanıcı aynı role atanması anlamına gelir.

Bir RunAsCredential JEA noktadaki geri belirli kullanıcılar ve eylemleri Kullanıcıları rollerine eşlemek için destek eksikliği izleme zorluk nedeniyle kullanmamanız gerekir.

## <a name="winrm-endpoint-acl"></a>WinRM uç nokta ACL

Normal PowerShell uzaktan iletişim uç ile denetimleri WinRM yapılandırmasında bir ayrı bir erişim denetim listesi (ACL) her JEA bitiş taşıdığından kimin JEA bitiş noktası ile doğrulanabilir.
Hatalı biçimde yapılandırdıysanız, güvenilen kullanıcıların JEA uç noktasına erişmek mümkün olmayabilir ve/veya güvenilmeyen kullanıcıların erişim elde.
WinRM ACL ancak JEA roller kullanıcılara eşleme etkilemez.
Tarafından denetlenen *RoleDefinitions* sistemde kaydedildiği oturum yapılandırma dosyasında alan.

Bir oturum yapılandırma dosyası ve bir veya daha fazla rol özellikleri, kullanarak bir JEA uç noktasını kaydetme, varsayılan olarak, bir veya daha fazla rol erişim uç noktasına eşleme tüm kullanıcılara izin vermek için WinRM ACL yapılandırılır.
Örneğin, aşağıdaki komutları kullanarak yapılandırılmış bir JEA oturumu tam erişim izni verecek *CONTOSO\JEA\_Lev1* ve *CONTOSO\JEA\_Lev2*.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

Kullanıcı izinleri olan denetim [Get-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet'i.

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Hangi kullanıcıların erişimi değiştirmek için ya da çalıştırmak `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` etkileşimli bir istem için veya `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` izinlerini güncelleştirmek için.
Kullanıcıların gereken en az *Invoke* JEA uç noktasına erişmek için hakları.

Ek kullanıcılar JEA uç noktasına erişimi verilir, ancak oturum yapılandırma dosyasında tanımlanan rolleri hiçbirine kalan değil, JEA oturumu başlatmak, ancak yalnızca varsayılan cmdlet'leri erişimi mümkün olacaktır.
Kullanıcı izinleri JEA uç noktada çalıştırarak denetleyebilirsiniz `Get-PSSessionCapability`.
Kullanıma [denetim ve JEA üzerinde raporlama](audit-and-report.md) denetimi hakkında daha fazla bilgi için bir kullanıcı komutları makalesine bir JEA uç erişimi vardır.

## <a name="least-privilege-roles"></a>En az ayrıcalık rolleri

JEA rolleri tasarlarken, sanal veya grup yönetilen hizmet hesabı çalıştırılması arka planda genellikle yerel makine yönetmek için sınırsız erişimi olduğunu unutmamak önemlidir.
JEA rol özellikleri yardımcı olması için bu hesabı ne kullanılabilir kısıtlamak, ayrıcalıklı bağlamını kullanarak çalışan uygulamaları ve komutları sınırlandırırsınız.
Yanlış bir şekilde tasarlanmış roller JEA sınırları dışında bölün veya hassas bilgilere erişim elde etmek bir kullanıcı izin verebilir çalıştırmak tehlikeli komutları izin verebilirsiniz.

Örneğin, aşağıdaki Rol Yetenek giriş göz önünde bulundurun:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Bu rol özelliği kullanıcıların herhangi bir PowerShell cmdlet'i Microsoft.PowerShell.Management modülünden "İşlem" isim ile çalıştırmasını sağlar.
Kullanıcıların cmdlet'leri gibi erişim gerekebilir `Get-Process` ne uygulamaları sistem üzerinde çalışan anlamak için ve `Stop-Process` herhangi sonlandırmak için uygulamaları askıda kaldı.
Ancak, bu girdi ayrıca tanır `Start-Process`, tam yönetici izinlerine sahip bir rastgele programını başlatmak için kullanılabilir.
Program bir saldırganın yalnızca bağlanan kullanıcı yerel yönetici ayrıcalıkları, çalışır kötü amaçlı yazılım ve daha fazlasını sunan bir dosya paylaşımında bir programı başlatabileceği şekilde sistem üzerinde yerel olarak yüklü olması gerekmez.'

Bu aynı rol özellik daha güvenli bir sürümü gibi görünür:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Rol özellikleri joker karakterleri kullanmaktan kaçının ve emin olun [denetim etkin kullanıcı izinlerini](audit-and-report.md#check-effective-rights-for-a-specific-user) düzenli olarak, bir kullanıcı komutları anlamak için erişimi vardır.

## <a name="jea-does-not-protect-against-admins"></a>JEA admins karşı koruma sağlamaz

JEA çekirdek ilkeleri biri gerçekleştirmek yönetici olmayanlar izin verdiğini *bazı* yönetim görevleri.
JEA zaten yönetici ayrıcalıklarına sahip olanlar karşı koruma sağlamaz.
Kullanıcılar "domain admins", "Yerel yöneticileri," ait veya diğer üst düzey Ayrıcalıklı Grup ortamınızda başka bir yöntem aracılığıyla makinede imzalayarak JEA'ın korumaları alabilir olmaya devam edecektir.
Bunlar Örneğin, oturum RDP oturumu, uzak konsolları veya Kısıtlanmamış PowerShell Uç noktalara bağlanmak.
Sistemde yerel yöneticiler de JEA yapılandırmaları sistem yönetmek veya bir kullanıcı kendi JEA oturumunda neler yapabileceğinizi kapsamını genişletmek için bir rol özelliği değiştirmek ek kullanıcılara izin verecek şekilde değiştirebilirsiniz.
Bu nedenle, sistem ayrıcalıklı erişim elde edebilir diğer yolları olup olmadığını görmek için genişletilmiş izinleri JEA kullanıcılarınızın değerlendirmek önemlidir.

JEA düzenli günlük bakım kullanıyorsanız ve bir "biraz zaman" ayrıcalıklı için ortak bir uygulama olan erişim yönetimi çözümü kullanıcıların geçici olarak yerel Yöneticiler acil durumlarda duruma olanak tanır.
Bu, kullanıcıların sistemde kalıcı yönetici değildir, ancak bu hakları varsa ve yalnızca bunlar bu izinleri kullanımını belgeleri bir iş akışı tamamlandığında, alabilirsiniz sağlamaya yardımcı olur.

