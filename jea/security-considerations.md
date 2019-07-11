---
ms.date: 07/10/2019
keywords: jea, powershell, güvenlik
title: JEA güvenlik konuları
ms.openlocfilehash: befc24fec368c4f6d60477daf63bf17e9431133e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726592"
---
# <a name="jea-security-considerations"></a>JEA güvenlik konuları

JEA makinelerinizde kalıcı yönetici sayısını azaltarak güvenliğini geliştirmenize yardımcı olur. Jea'yı bir PowerShell oturumu yapılandırma sistemi yönetmek kullanıcılar için yeni bir giriş noktası oluşturmak için kullanır. Yönetim görevleri gerçekleştirmek için makineye yükseltilmiş ancak değil sınırsız erişmesi gereken kullanıcılar JEA uç noktasına erişim verilebilir. JEA tam yönetici erişimi olmadan yönetici komutlarını çalıştırmak bu kullanıcılara olanak tanıdığından, yüksek ayrıcalıklı güvenlik gruplarındaki kullanıcılar daha sonra kaldırabilirsiniz.

## <a name="run-as-account"></a>Farklı çalıştırma hesabı

Her bir JEA uç noktasının bir atanmış olan **Çalıştır** hesabı. Bağlanan kullanıcının eylemleri yürütüldüğü hesabıdır. Bu hesap yapılandırılabilirdir [oturum yapılandırma dosyası](session-configurations.md), ve seçtiğiniz hesabın bir önemli güvenlik uç noktanızın ilgisi.

**Sanal hesaplar** yapılandırma için önerilen yoldur **Çalıştır** hesabı. JEA oturumun süresi sırasında kullanılacak bağlanan kullanıcı için oluşturulan tek seferlik, geçici yerel hesaplar sanal hesaplarıdır. Oturumun sona hemen sonra sanal hesap edildiğinde ve artık kullanılamaz. Bağlanan kullanıcı hesabının kimlik bilgilerini sanal bilmez. Sanal hesap, Uzak Masaüstü veya bir sınırlandırılmamış PowerShell uç nokta gibi başka bir yolla üzerinden sisteme erişmek için kullanılamaz.

Varsayılan olarak, yerel sanal hesaplar ait **Yöneticiler** makinede grubu. Bu bunları sistemdeki her şeyi yönetme hakkı tam, ancak ağ kaynaklarını yönetme hakkı verir.
Diğer makinelerle kimlik doğrulamasını yaparken, kullanıcı bağlamı sanal hesabı değil yerel bilgisayar hesabının olmasıdır.

Etki alanı denetleyicisi olan bir özel durum yok olduğundan yerel **Yöneticiler** grubu. Sanal hesaplar bunun yerine, ait **Domain Admins** ve Dizin Hizmetleri etki alanı denetleyicisinde yönetebilirsiniz. Etki alanı kimliği, burada JEA oturumu örneği oluşturulduktan etki alanı denetleyicisinde kullanmak için hala sınırlıdır. Herhangi bir ağ erişimi, bunun yerine etki alanı denetleyicisi bilgisayar nesnesinden gelen görünmektedir.

Her iki durumda da, açıkça sanal hesap ait olduğu güvenlik grupları tanımlayabilir. Görev yerel veya etki alanı yönetici ayrıcalıklarına gerek kalmadan yapılabilir, iyi bir uygulamadır. Yöneticilerinize için tanımlı bir güvenlik grubu zaten varsa, sanal hesap için üyelik, bu gruba atayın. Sanal Hesap Grup üyeliği, iş istasyonu ve üye sunucularında yerel güvenlik gruplarını sınırlıdır. Etki alanı denetleyicilerinde sanal hesaplar, etki alanı güvenlik gruplarının üyesi olması gerekir.
Sanal hesap için bir veya daha fazla güvenlik grubu eklendikten sonra artık varsayılan grupları'na (yerel veya etki alanı yöneticileri) ait.

Aşağıdaki tabloda, olası yapılandırma seçeneklerini ve sonuçta elde edilen sanal hesaplar izinlerini özetlenmektedir:

|        Bilgisayar türü         | Sanal hesap grubu yapılandırması |                   Yerel kullanıcı bağlamı                    | Ağ kullanıcı bağlamı |
| ---------------------------- | ----------------------------------- | ------------------------------------------------------- | -------------------- |
| Etki alanı denetleyicisi            | Varsayılan                             | Etki alanı kullanıcısı, üyesi '*etki alanı*\Domain yöneticileri         | Bilgisayar hesabı     |
| Etki alanı denetleyicisi            | A ve B etki alanı grupları               | Etki alanı kullanıcısı, üyesi '*etki alanı*\A ','*etki alanı*\B'       | Bilgisayar hesabı     |
| Üye sunucu veya iş istasyonu | Varsayılan                             | Yerel bir kullanıcı, üyesi '*YERLEŞİK*\Administrators'        | Bilgisayar hesabı     |
| Üye sunucu veya iş istasyonu | Yerel gruplar C ve D                | Yerel bir kullanıcı, üyesi '*bilgisayar*\C' ve '*bilgisayar*\D' | Bilgisayar hesabı     |

Güvenlik denetim olaylarını ve uygulama olay günlüklerini bakın her JEA kullanıcı oturumunu benzersiz sanal hesap olduğunu görürsünüz. Bu benzersiz bir hesap olarak bir JEA uç noktası kullanıcı eylemlerini komutun çalıştığını geri özgün kullanıcıya izlemenize yardımcı olur. Sanal hesap adları biçim izleyen `WinRM Virtual Users\WinRM_VA_<ACCOUNTNUMBER>_<DOMAIN>_<sAMAccountName>` gibi kullanıcı **Alice** etki alanındaki **Contoso** herhangi bir hizmet denetimi Yöneticisi ile ilişkili kullanıcı adını bir JEA uç noktasını bir hizmetini yeniden başlatır olayları olacak `WinRM Virtual Users\WinRM_VA_1_contoso_alice`.

**Grup yönetilen hizmet hesapları (gmsa'ları)** üye sunucu JEA oturumda ağ kaynaklarına erişim sağlamak gerektiğinde yararlıdır. Örneğin, ne zaman bir JEA uç noktası farklı bir makinede barındırılan bir REST API hizmetini erişimi denetlemek için kullanılır. REST API'leri çağırmak için işlevleri yazmak kolaydır, ancak API ile kimlik doğrulaması için bir ağ kimliği gerekir. Bir grup yönetilen hizmet hesabı'nı kullanarak ikinci atlama üzerinde bilgisayar hesabı kullanabilir denetimini elde tutarak mümkün kılar. GMSA etkin izinleri gMSA hesabını ait olduğu güvenlik grupları (yerel veya etki alanı) tarafından tanımlanır.

Bir JEA uç noktası, bir gmsa'yı kullanmak için yapılandırıldığında, aynı gMSA ' gelen tüm JEA kullanıcıların eylemlerini görünür. Belirli bir kullanıcı için geri izleme eylemlerini tek yolu, bir PowerShell oturumu transkripti çalıştırma komutları kümesini belirlemektir.

**Kimlik bilgileri, geçişi izlenecek** belirtmeyin kullanılan bir **Çalıştır** hesabı. PowerShell komutları uzak sunucuda çalıştırılacak bağlanan kullanıcının kimlik bilgilerini kullanır. Bu, ayrıcalıklı yönetim gruplarına bağlantı kullanıcı doğrudan erişim vermenizi gerektirir. Bu yapılandırma **değil** JEA için önerilir. Bağlanan kullanıcının yönetici ayrıcalıkları varsa, bunlar JEA önlemek ve diğer, sınırlandırılmamış yollar üzerinden sisteme yönetme. Daha fazla bilgi için aşağıdaki bölüme hakkında bkz [JEA yöneticileri karşı korumak değil](#jea-doesnt-protect-against-admins).

**Standart farklı çalıştırma hesapları** tüm PowerShell oturumu çalıştığı herhangi bir kullanıcı hesabı belirtmenizi sağlar. Oturum yapılandırmaları kullanarak sabit **Çalıştır** hesapları (ile `-RunAsCredential` parametresi) JEA farkında değildir. Rol Tanımları artık beklendiği gibi çalışmaz. Uç nokta erişim yetkisine sahip tüm kullanıcılar aynı role atanır.

Kullanmamalısınız bir **RunAsCredential** geri için belirli İzleme eylemlerini zor olduğundan bir JEA uç noktasında kullanıcılar ve oturumda Kullanıcıları rollerine eşlemek için destek.

## <a name="winrm-endpoint-acl"></a>WinRM uç noktası ACL'sini

Normal PowerShell uzaktan iletişim uç noktaları ile her bir JEA uç noktasının denetleyen bir ayrı bir erişim denetim listesi (ACL) sahip olduğundan kimin JEA uç noktası ile kimlik doğrulaması yapabilir. Yanlış yapılandırılırsa, güvenilen kullanıcıların JEA uç noktasına erişmek mümkün olmayabilir ve güvenilmeyen kullanıcıların erişimleri olabilir. WinRM ACL JEA rollerine kullanıcı eşleme etkilemez. Eşleme tarafından denetlenir **RoleDefinitions** alan oturum yapılandırma dosyasında kullanılan uç noktasını kaydetmek için.

Bir JEA uç noktası birden çok rol özellikleri, varsa varsayılan olarak, tüm eşlenen kullanıcılar erişime izin vermek için WinRM ACL yapılandırılır. Örneğin, aşağıdaki komutlar kullanılarak yapılandırılmış bir JEA oturumu tam erişim veren `CONTOSO\JEA_Lev1` ve `CONTOSO\JEA_Lev2`.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

Kullanıcı izinleriyle denetleyebilirsiniz [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet'i.

```powershell
Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission
```

```Output
Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Hangi kullanıcıların erişimi değiştirmek için ya da çalıştırın `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` için etkileşimli bir istemi veya `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` izinlerini güncelleştirmek için. Kullanıcıların gereken en az *Invoke* JEA uç nokta erişim hakları.

Tanımlı bir role erişimi olan her kullanıcıya eşlemiyor bir JEA uç noktası oluşturmak mümkündür. Bu kullanıcılar bir JEA oturumu başlatın, ancak yalnızca varsayılan cmdlet'leri erişimi. Bir JEA uç noktası kullanıcı izinlerini çalıştırarak denetleyebilirsiniz `Get-PSSessionCapability`. Daha fazla bilgi için [denetim ve JEA'da raporlama](audit-and-report.md).

## <a name="least-privilege-roles"></a>En az ayrıcalıklı rolleri

JEA rolleri tasarlarken, arka planda çalışan sanal ve Grup yönetilen hizmet hesapları için yerel makine sınırsız erişimi vardır olduğunu unutmamak önemlidir. JEA rol işlevleri, komutlar ve ayrıcalıklı bu bağlamda çalışan uygulamaları sınırlamaya Yardım.
Hatalı şekilde tasarlanmış roller JEA sınırları dışında sonu veya hassas bilgilere erişim elde etmek için bir kullanıcı olabiliyor tehlikeli komutları izin verebilirsiniz.

Örneğin, aşağıdaki rol özelliği girişi göz önünde bulundurun:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Bu rol özellik herhangi bir PowerShell cmdlet'i ile isim çalıştırmak kullanıcılara **işlem** gelen **Microsoft.PowerShell.Management** modülü. Kullanıcılar cmdlet'leri gibi erişim gerekebilir `Get-Process` sistemde hangi uygulamaların çalıştığını görmek için ve `Stop-Process` yanıt olmayan uygulamaları sonlandırılır. Ancak bu girdi de tanır `Start-Process`, tam yönetici izinlerine sahip rastgele bir programı başlatmak için kullanılabilir. Program, sistem üzerinde yerel olarak yüklü olması gerekmez. Bağlı olan bir kullanıcı bir program, kullanıcının yerel yönetici ayrıcalıkları sağlar, kötü amaçlı yazılım çalıştıran bir dosya paylaşımından başlayabilirsiniz.

Bu rol aynısını daha güvenli bir sürümü gibi görünür:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Rolü özelliklerinde joker karakterleri kullanmaktan kaçının. Düzenli olarak yaptığınızdan emin olun [denetim etkin kullanıcı izinleri](audit-and-report.md#check-effective-rights-for-a-specific-user) hangi komutların kullanıcı erişimine açık olduğunu anlamak için.

## <a name="jea-doesnt-protect-against-admins"></a>JEA yöneticileri karşı korumaz.

JEA'ın temel ilkeler Yöneticileri olmayan bazı yönetim görevleri gerçekleştirmek izin verdiğini biridir. JEA zaten yönetici ayrıcalıklarına sahip kullanıcılar karşı korumaz. Ait olan kullanıcılar **Domain Admins**, yerel **Yöneticiler**, veya diğer üst düzey ayrıcalıklı grup başka bir yöntem aracılığıyla JEA'ın korumaları atlayabilir. Örneğin, RDP oturum oturumunuzu açamadı uzaktaki konsolları veya sınırlandırılmamış PowerShell Uç noktalara bağlanmak. Ayrıca, bir sistemde yerel Yöneticiler ek kullanıcılara izin ver veya bir kullanıcı kendi JEA oturumunda neler yapabileceğinizi kapsamını genişletmek için bir rol özelliği değiştirmek için JEA yapılandırmaları değiştirebilirsiniz. JEA kullanıcılarınızın genişletilmiş izinleri sistem ayrıcalıklı erişim elde etmek için diğer yolları olup olmadığını değerlendirmek önemlidir.

Bir yaygın JEA için normal Günlük Bakım ve tam zamanında, geçici olarak acil durumlarda yerel yönetici olmak kullanıcılara ayrıcalıklı erişim yönetimi çözümü olan bir uygulamadır. Bu, kullanıcıların sistemde kalıcı yönetici olmayan, ancak bu hakları varsa ve yalnızca bunlar bu izinleri kullanımları belgeleri bir iş akışı tamamlandıktan sonra alabilirsiniz olun yardımcı olur.
