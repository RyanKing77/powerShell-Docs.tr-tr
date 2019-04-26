---
ms.date: 06/12/2017
keywords: jea, powershell, güvenlik
title: JEA güvenlik konuları
ms.openlocfilehash: 9526e141517601ae3b6d6932cd3536fdf49aa9a6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084785"
---
# <a name="jea-security-considerations"></a>JEA güvenlik konuları

> Şunun için geçerlidir: Windows PowerShell 5.0

JEA makinelerinizde kalıcı yönetici sayısını azaltarak güvenliğini geliştirmenize yardımcı olur.
Bunu sıkı bir şekilde kötüye kullanımı önlemek için varsayılan olarak kilitlenmiştir (bir PowerShell oturumu yapılandırması) sistemi yönetmek kullanıcılar için yeni bir giriş noktası oluşturarak yapar.
Ancak, bazı ihtiyaç duyan kullanıcılar sınırsız erişim yönetim görevlerini gerçekleştirmek için makineye JEA uç noktasına erişim verilebilir.
JEA bunları doğrudan yönetici erişimine gerek kalmadan yönetici komutlarını çalıştırmak izin verdiğinden, söz konusu kullanıcıların yüksek ayrıcalıklı güvenlik gruplarındaki (standart kullanıcılar olacak) sonra kaldırabilirsiniz.

Bu konu başlığı altında daha ayrıntılı bir şekilde en iyi yöntemler ve JEA güvenlik modeli açıklanır.

## <a name="run-as-account"></a>Farklı Çalıştır hesabı

Bağlanan kullanıcının eylemleri gerçekleştirildiği hesabı olan bir atanmış "run as" hesabını, her JEA uç noktası vardır.
Bu hesap yapılandırılabilirdir [oturum yapılandırma dosyası](session-configurations.md), ve seçtiğiniz hesabın bir önemli güvenlik uç noktanızın ilgisi.

**Sanal hesaplar** farklı çalıştır hesabı olarak yapılandırılması için önerilen yoldur.
JEA oturumun süresi sırasında kullanılacak bağlanan kullanıcı için oluşturulan tek seferlik, geçici yerel hesaplar sanal hesaplarıdır.
Oturumun sona hemen sonra sanal hesap yok edileceği ve artık kullanılamaz.
Bağlanan kullanıcının sanal hesabının kimlik bilgilerini kullanmayı bilmeyen ve sanal hesap üzerinden uzak masaüstü veya bir sınırlandırılmamış PowerShell uç nokta gibi başka bir yolla sisteme erişmek için kullanamazsınız.

Varsayılan olarak, sanal hesaplar makinede yerel Yöneticiler grubuna ait.
Bu bunları sistemdeki her şeyi yönetme hakkı tam, ancak ağ kaynaklarını yönetme hakkı verir.
Diğer makinelerle kimlik doğrulamasını yaparken, kullanıcı bağlamı, yerel bilgisayar hesabının, sanal hesap olacaktır.

Etki alanı denetleyicileri, yerel Yöneticiler grubuna kavramı olmadığından bir özel durum olan.
Bunun yerine, sanal hesaplar için etki alanı yöneticileri yerine ait ve Dizin Hizmetleri etki alanı denetleyicisinde yönetebilirsiniz.
Etki alanı kimliği burada JEA oturumu örneği oluşturulduktan ve bunun yerine etki alanı denetleyicisi bilgisayar nesnesinden gelen herhangi bir ağ erişim görünür etki alanı denetleyicisinde kullanmak için hala sınırlıdır.

Her iki durumda da açıkça sanal hesap ait olması gereken güvenlik grupları tanımlayabilirsiniz.
Gerçekleştirdiğiniz göreve yerel/etki alanı yönetici ayrıcalıklarına gerek kalmadan yapılabilir, iyi bir uygulamadır.
Yöneticilerinizin için tanımlı bir güvenlik grubu zaten varsa, yalnızca gerekli izinleri vermek için bu gruba sanal hesap için üyelik verebilirsiniz.
Sanal Hesap Grup üyeliği, iş istasyonu ve üye sunucu üzerinde yerel güvenlik gruplarına sınırlıdır, ancak bir etki alanı denetleyicisinde bunlar yalnızca etki alanı güvenlik gruplarının üyesi olabilir.
Ait bir veya daha fazla güvenlik grupları için sanal hesap belirttiğinizde, artık varsayılan gruplara (yerel yönetici veya etki alanı yöneticisi) ait olur.

Aşağıdaki tabloda olası yapılandırma seçeneklerini ve sonuçta elde edilen sanal hesaplar izinleri özetler.

Bilgisayar türü                | Sanal hesap grubu yapılandırması | Yerel kullanıcı bağlamı                                      | Ağ kullanıcı bağlamı
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
Etki alanı denetleyicisi            | Varsayılan                             | Etki alanı kullanıcısı, üyesi '*etki alanı*\Domain yöneticileri         | Bilgisayar hesabı
Etki alanı denetleyicisi            | A ve B etki alanı grupları               | Etki alanı kullanıcısı, üyesi '*etki alanı*\A ','*etki alanı*\B'       | Bilgisayar hesabı
Üye sunucu veya iş istasyonu | Varsayılan                             | Yerel bir kullanıcı, üyesi '*YERLEŞİK*\Administrators'        | Bilgisayar hesabı
Üye sunucu veya iş istasyonu | Yerel gruplar C ve D                | Yerel bir kullanıcı, üyesi '*bilgisayar*\C' ve '*bilgisayar*\D' | Bilgisayar hesabı

Güvenlik denetim olaylarını ve uygulama olay günlüklerini baktığınızda, her JEA kullanıcı oturumunu benzersiz sanal hesap olduğunu görürsünüz.
Bu komutun çalıştığını geri özgün kullanıcıya bir JEA uç noktası kullanıcı eylemleri izlemenize yardımcı olur.
Sanal hesap adları izleyen biçimi "WinRM sanal kullanıcıların\\WinRM\_VA\_*ACCOUNTNUMBER*\_*etki alanı* \_ *sAMAccountName*"Örneğin, etki alanı"Contoso"," Gamze "adlı kullanıcı, bir hizmet bir JEA uç noktası yeniden başlatılırsa, tüm hizmet denetimi yöneticisi olaylarını ile ilişkili kullanıcı adını olması" WinRM sanal kullanıcıların\\WinRM\_ VA\_1\_contoso\_alice ".


**Grup yönetilen hizmet hesapları (gmsa'ları)** üye sunucu JEA oturumda ağ kaynaklarına erişim sağlamak gerektiğinde yararlıdır.
Bu bir örnek kullanım örneği farklı bir makinede barındırılan bir REST API erişimi denetlemek için kullanılan bir JEA uç noktadır.
Ağ kimliği işlevleri REST API ile ilgili istenen çağrıları yapmak için ancak API ile kimliğinizi doğrulamak için gereken yazmak kolaydır.
Bir grup yönetilen hizmet hesabı kullanarak "ikinci atlama" denetim üzerinde bilgisayar hesabı kullanabilir yaparken hala mümkün kılar.
GMSA etkin izinleri gMSA hesabını ait olduğu güvenlik grupları (yerel veya etki alanı) tarafından tanımlanır.

Bir JEA uç noktası, bir gMSA hesabı kullanmak üzere yapılandırıldığında, yönetilen hizmet hesabı aynı grubundan gelen tüm JEA kullanıcıların eylemlerini görünür.
Belirli bir kullanıcıya geri eylemleri izleyebilirsiniz tek yolu, bir PowerShell oturumu transkripti çalıştırma komutları kümesini belirlemektir.

**Kimlik bilgileri, geçişi izlenecek** etmez bir farklı çalıştır hesabı olarak belirtin ve istediğiniz bağlanan kullanıcının kimlik bilgileri uzak sunucuda komutları çalıştırmak için PowerShell kullanılır.
Bu yapılandırma *değil* ayrıcalıklı yönetim gruplarına bağlantı kullanıcı doğrudan erişim vermek için gerektirecek şekilde JEA için önerilir.
Bağlanan kullanıcının yönetici ayrıcalıkları varsa, bunlar JEA tamamen önlemek ve diğer, sınırlandırılmamış yollar üzerinden sisteme yönetme.
Aşağıdaki bölüme bakın [JEA yöneticileri karşı korumaz](#jea-does-not-protect-against-admins) daha fazla bilgi için.

**Standart farklı çalıştır hesapları** tüm PowerShell oturumu altında çalışacağı herhangi bir kullanıcı hesabı belirtmenizi sağlar.
Sabit bir farklı çalıştır hesabı olarak kullanılacak bir oturum yapılandırması ayarlama önemli bir ayrımdır olmasıdır (ile `-RunAsCredential` parametresi) JEA uyumlu değil.
Bu rol tanımları artık beklendiği gibi çalışmaz ve her kullanıcı uç noktasına erişmek için yetkili aynı role atanması anlamına gelir.

Bir RunAsCredential bir JEA uç noktasında zorluk izleme eylemleri geri belirli kullanıcılara ve rollere kullanıcılar eşleme desteği eksikliği nedeniyle kullanmamanız gerekir.

## <a name="winrm-endpoint-acl"></a>WinRM uç noktası ACL'sini

Normal PowerShell uzaktan iletişim uç noktaları ile her bir JEA uç noktasının denetleyen WinRM yapılandırmasında bir ayrı bir erişim denetim listesi (ACL) sahip olduğundan kimin JEA uç noktası ile kimlik doğrulaması yapabilir.
Yanlış yapılandırılırsa, güvenilen kullanıcıların JEA uç noktasına erişmek mümkün olmayabilir ve/veya güvenilmeyen kullanıcıların erişim elde edebilirsiniz.
WinRM ACL ancak JEA rollerine kullanıcı eşleme etkilemez.
Tarafından denetlenen *RoleDefinitions* sistemde kaydedilen oturum yapılandırma dosyasında alan.

Bir oturum yapılandırma dosyası ve bir veya daha fazla rol işlevleri kullanarak bir JEA uç noktasını kaydetme, varsayılan olarak, tüm kullanıcıların bir veya daha fazla rol erişim uç noktasına eşleme WinRM ACL yapılandırılır.
Örneğin, aşağıdaki komutlar kullanılarak yapılandırılmış bir JEA oturumu tam erişim izni verir *CONTOSO\JEA\_Lev1* ve *CONTOSO\JEA\_Lev2*.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

Kullanıcı izinleriyle denetleyebilirsiniz [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet'i.

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Hangi kullanıcıların erişimi değiştirmek için ya da çalıştırın `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` için etkileşimli bir istemi veya `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` izinlerini güncelleştirmek için.
Kullanıcıların gereken en az *Invoke* JEA uç nokta erişim hakları.

Ek kullanıcılar JEA uç noktası için erişim verilir, ancak oturum yapılandırma dosyasında tanımlanmış rollere hiçbirine denk olmayan bir JEA oturumu başlatın, ancak yalnızca varsayılan cmdlet'leri erişiminiz olacaktır.
Bir JEA uç noktası kullanıcı izinlerini çalıştırarak denetleyebilirsiniz `Get-PSSessionCapability`.
Kullanıma [denetim ve JEA'da raporlama](audit-and-report.md) denetimi hakkında daha fazla bilgi için bir kullanıcı komutları makale bir JEA uç noktası için erişimine sahiptir.

## <a name="least-privilege-roles"></a>En az ayrıcalıklı rolleri

JEA rolleri tasarlarken, sanal veya grup yönetilen hizmet hesabı çalışan arka planda genellikle yerel makine yönetmek için erişim varmazlar unutmamak önemlidir.
JEA rol işlevleri yardımcı kısıtlamak için bu hesabı ne kullanılabilir komutları ve ayrıcalıklı bu bağlamı kullanarak çalışan uygulamaları sınırlandırırsınız.
Hatalı şekilde tasarlanmış roller JEA sınırları dışında sonu veya hassas bilgilere erişim elde etmek bir kullanıcı izin verebilecek için tehlikeli komutları izin verebilirsiniz.

Örneğin, aşağıdaki rol özelliği girişi göz önünde bulundurun:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Bu rolü özelliği kullanıcıların herhangi bir PowerShell cmdlet'i Microsoft.PowerShell.Management modülünden "İşlem" isim ile çalıştırmasına izin verir.
Kullanıcılar cmdlet'leri gibi erişim gerekebilir `Get-Process` hangi uygulamaları sistemde çalışan anlamak için ve `Stop-Process` , yanıt vermeyen tüm uygulamaları sonlandırılır.
Ancak bu girdi de tanır `Start-Process`, tam yönetici izinlerine sahip rastgele bir programı başlatmak için kullanılabilir.
Program, saldırganın yalnızca bir program bağlanan kullanıcı yerel yönetici ayrıcalıkları, çalıştırmalar kötü amaçlı yazılım ve diğer sağlayan bir dosya paylaşımında başlayabilmesi sistemde yerel olarak yüklü olması gerekmez.'

Bu rol aynısını daha güvenli bir sürümü gibi görünür:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Rolü özelliklerinde joker karakterleri kullanmaktan kaçının ve mutlaka [denetim etkin kullanıcı izinleri](audit-and-report.md#check-effective-rights-for-a-specific-user) düzenli olarak, bir kullanıcı komutları anlamak için erişebilir.

## <a name="jea-does-not-protect-against-admins"></a>JEA yöneticileri karşı korumaz

JEA çekirdek prensipleri biri yönetici olmayanlar gerçekleştirmeyi sağlayan *bazı* yönetim görevleri.
JEA zaten yönetici ayrıcalıklarına sahip olanlar karşı koruma sağlamaz.
Kullanıcılar "domain admins", "yerel Yöneticiler," ait ya da yüksek ayrıcalıklı diğer grupları, ortamınızdaki makine başka bir yöntem aracılığıyla oturum açarak JEA'ın korumaları almaya devam edebilir.
Bunlar Örneğin, oturum RDP oturumu, uzak konsolları veya sınırlandırılmamış PowerShell Uç noktalara bağlanmak.
Yerel yöneticiler sistem üzerindeki sistem yönetin veya bir kullanıcı kendi JEA oturumunda neler yapabileceğinizi kapsamını genişletmek için bir rol özelliği değiştirmek ek kullanıcıların JEA yapılandırmaları de değiştirebilirsiniz.
Bu nedenle, JEA kullanıcılarınızın genişletilmiş izinleri sisteme ayrıcalıklı erişim elde edebilir diğer yolları olup olmadığını değerlendirmek önemlidir.

Bir sık kullanılan normal günlük bakım için JEA kullanın ve bir "tam zamanında" ayrıcalıklı bir yöntemdir erişim yönetimi çözümü, kullanıcıların geçici olarak yerel Yöneticiler acil durumlarda duruma olanak tanır.
Bu, kullanıcıların sistemde kalıcı yönetici değildir, ancak bu hakları varsa ve yalnızca bunlar bu izinleri kullanımları belgeleri bir iş akışı tamamlandıktan sonra alabilirsiniz olun yardımcı olur.