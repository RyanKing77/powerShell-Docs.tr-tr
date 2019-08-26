---
ms.date: 07/10/2019
keywords: Jea, PowerShell, güvenlik
title: JEA güvenlik konuları
ms.openlocfilehash: befc24fec368c4f6d60477daf63bf17e9431133e
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017912"
---
# <a name="jea-security-considerations"></a>JEA güvenlik konuları

JEA, makinelerinizdeki kalıcı yöneticilerin sayısını azaltarak güvenlik duruşunuzu iyileştirmenize yardımcı olur. JEA, kullanıcıların sistemi yönetmesi için yeni bir giriş noktası oluşturmak üzere bir PowerShell oturum yapılandırması kullanır. Yönetici görevleri için yükseltilmiş, ancak sınırsız olmayan, makineye erişime ihtiyacı olan kullanıcılar JEA uç noktasına erişim izni verebilir. JEA, bu kullanıcıların tam yönetici erişimi olmadan yönetici komutları çalıştırmasına izin verdiğinden, bu kullanıcıları son derece ayrıcalıklı güvenlik gruplarından çıkarabilirsiniz.

## <a name="run-as-account"></a>Farklı Çalıştır hesabı

Her JEA uç noktasının belirlenmiş bir **Farklı Çalıştır** hesabı vardır. Bu, bağlanan Kullanıcı eylemlerinin çalıştırıldığı hesaptır. Bu hesap [oturum yapılandırma dosyasında](session-configurations.md)yapılandırılabilir ve seçtiğiniz hesap, uç noktanızın güvenliği üzerinde önemli bir değer içerir.

**Sanal hesaplar** , **Farklı Çalıştır** hesabını yapılandırmanın önerilen yoludur. Sanal hesaplar, bağlanan kullanıcının JEA oturumunun süresi boyunca kullanması için oluşturulan tek seferlik, geçici yerel hesaplardır. Oturumu sonlandırıldığı anda, sanal hesap yok edilir ve artık kullanılamaz. Bağlanan kullanıcı sanal hesap için kimlik bilgilerini bilmez. Sanal hesap, uzak masaüstü veya kısıtlanmış olmayan bir PowerShell uç noktası gibi diğer yollarla sisteme erişmek için kullanılamaz.

Varsayılan olarak, sanal hesaplar makinedeki yerel **Yöneticiler** grubuna aittir. Bu, sistemdeki her şeyi yönetmek için tam haklar verir, ancak ağdaki kaynakları yönetmek için hiçbir haklara sahip olmaz.
Diğer makinelerle kimlik doğrulanırken, Kullanıcı bağlamı sanal hesaba değil yerel bilgisayar hesabıdır.

Yerel bir **Yöneticiler** grubu olmadığından, etki alanı denetleyicileri özel bir durumdur. Bunun yerine, sanal hesaplar **etki alanı yöneticilerine** aittir ve etki alanı denetleyicisindeki dizin hizmetlerini yönetebilir. Etki alanı kimliği, JEA oturumunun örneği oluşturulan etki alanı denetleyicisinde kullanılmaya devam etmektedir. Bunun yerine etki alanı denetleyicisi bilgisayar nesnesinden gelen herhangi bir ağ erişimi görünür.

Her iki durumda da, sanal hesabın ait olduğu güvenlik gruplarını açıkça tanımlayabilirsiniz. Bu, görev yerel veya etki alanı yöneticisi ayrıcalıkları olmadan yapılalecede iyi bir uygulamadır. Yöneticileriniz için tanımlanmış bir güvenlik grubunuz zaten varsa, sanal hesap üyeliğini bu gruba verin. Sanal hesap grubu üyeliği, iş istasyonundaki ve üye sunuculardaki yerel güvenlik gruplarıyla sınırlıdır. Etki alanı denetleyicilerinde, sanal hesapların etki alanı güvenlik gruplarının üyesi olması gerekir.
Sanal hesap bir veya daha fazla güvenlik grubuna eklendikten sonra, artık varsayılan gruplara (yerel veya etki alanı yöneticileri) ait değildir.

Aşağıdaki tabloda, olası yapılandırma seçenekleri ve sanal hesaplar için ortaya çıkan izinler özetlenmektedir:

|        Bilgisayar türü         | Sanal hesap grubu yapılandırması |                   Yerel Kullanıcı bağlamı                    | Ağ Kullanıcı bağlamı |
| ---------------------------- | ----------------------------------- | ------------------------------------------------------- | -------------------- |
| Etki alanı denetleyicisi            | Varsayılan                             | Etki alanı kullanıcısı, '*etki alanı*\ etki alanı yöneticileri ' üyesi         | Bilgisayar hesabı     |
| Etki alanı denetleyicisi            | A ve B etki alanı grupları               | Etki alanı kullanıcısı, '*Domain*\a ' üyesi, '*Domain*\b '       | Bilgisayar hesabı     |
| Üye sunucu veya iş istasyonu | Varsayılan                             | Yerel Kullanıcı, '*BUILTIN*tın\administrators ' üyesi        | Bilgisayar hesabı     |
| Üye sunucu veya iş istasyonu | C ve D yerel grupları                | Yerel Kullanıcı, '*bilgisayar*\c ' üyesi ve '*bilgisayar*\d ' | Bilgisayar hesabı     |

Güvenlik denetim olayları ve uygulama olay günlüklerine baktığınızda, her JEA Kullanıcı oturumunun benzersiz bir sanal hesaba sahip olduğunu görürsünüz. Bu benzersiz hesap, bir JEA uç noktasındaki kullanıcı eylemlerini, komutu çalıştıran özgün kullanıcıya geri izlemenize yardımcı olur. Sanal hesap adları `WinRM Virtual Users\WinRM_VA_<ACCOUNTNUMBER>_<DOMAIN>_<sAMAccountName>` Örneğin, **contoso** etki alanı Kullanıcı adı bir Jea uç noktasında bir hizmeti yeniden başlatacaksa, herhangi bir hizmet denetimi Yöneticisi ile ilişkili Kullanıcı adı olacaktır. `WinRM Virtual Users\WinRM_VA_1_contoso_alice`

**Grup tarafından yönetilen hizmet hesapları (gMSAs)** , bir üye sunucunun Jea oturumunda ağ kaynaklarına erişmesi gerektiğinde faydalıdır. Örneğin, bir JEA uç noktası, farklı bir makinede barındırılan bir REST API hizmetine erişimi denetlemek için kullanılır. REST API 'Leri çağırmak için işlevleri yazmak kolaydır, ancak API ile kimlik doğrulamak için bir ağ kimliği gereklidir. Grup tarafından yönetilen bir hizmet hesabı kullanmak, bu, hesabı hangi bilgisayarların kullanabileceği konusunda tutarak ikinci atlamayı mümkün hale getirir. GMSA 'nın etkili izinleri, gMSA hesabının ait olduğu güvenlik grupları (yerel veya etki alanı) tarafından tanımlanır.

JEA uç noktası gMSA 'yı kullanacak şekilde yapılandırıldığında, tüm JEA kullanıcılarının eylemleri aynı gMSA 'dan geliyor gibi görünür. Eylemleri belirli bir kullanıcıya geri izlemenin tek yolu, bir PowerShell oturumunda çalıştırılan komut kümesini tanımlamaktır.

**Geçiş kimlik bilgileri** , bir **Farklı Çalıştır** hesabı belirtmezseniz kullanılır. PowerShell, uzak sunucuda komutları çalıştırmak için kullanıcının kimlik bilgilerini bağlamayı kullanır. Bunun yapılması, kullanıcıya ayrıcalıklı yönetim gruplarına doğrudan erişim izni vermenizi gerektirir. Bu yapılandırma JEA için önerilmez. Bağlanan kullanıcının yönetici ayrıcalıkları zaten varsa, bu kişiler JEA 'dan kaçınabilir ve sistemi başka, sınırlandırılmamış yollarla yönetemez. Daha fazla bilgi için bkz. [Jea 'nın yöneticilere karşı korumadığı](#jea-doesnt-protect-against-admins)bölüm.

**Standart farklı çalıştır hesapları** , altında tüm PowerShell oturumunun çalıştırıldığı Kullanıcı hesabını belirtmenize olanak tanır. Sabit **Farklı Çalıştır** hesaplarını kullanan oturum konfigürasyonları ( `-RunAsCredential` parametresiyle birlikte) Jea-Aware değildir. Rol tanımları artık beklenen şekilde çalışmaz. Uç noktaya erişim yetkisi olan her kullanıcıya aynı rol atanır.

Bir JEA uç noktası üzerinde **Runascredential** kullanmamanız gerekir, çünkü eylemleri belirli kullanıcılara geri izlemek zordur ve kullanıcıları rollerle eşlemek için destek yoktur.

## <a name="winrm-endpoint-acl"></a>WinRM uç noktası ACL 'SI

Normal PowerShell uzaktan iletişim uç noktalarında olduğu gibi, her JEA uç noktası, JEA uç noktası ile kimlik doğrulayabilecek olan ayrı bir erişim denetim listesine (ACL) sahiptir. Yanlış yapılandırılmamışsa, güvenilen kullanıcılar JEA uç noktasına erişemeyebilir ve güvenilmeyen kullanıcıların erişimi olabilir. WinRM ACL 'SI, kullanıcıların JEA rollerine eşlenmesini etkilemez. Eşleme, uç noktasını kaydetmek için kullanılan oturum yapılandırma dosyasındaki **Roledefinitions** alanı tarafından denetlenir.

Varsayılan olarak, bir JEA uç noktası birden çok rol özelliğine sahip olduğunda, WinRM ACL, tüm eşlenmiş kullanıcılara erişime izin verecek şekilde yapılandırılır. Örneğin, aşağıdaki komutlar kullanılarak yapılandırılan bir Jea oturumu ve `CONTOSO\JEA_Lev1` `CONTOSO\JEA_Lev2`için tam erişim verir.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

[Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet 'i ile Kullanıcı izinlerini denetleyebilirsiniz.

```powershell
Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission
```

```Output
Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Hangi kullanıcıların erişimi olduğunu değiştirmek için, etkileşimli bir `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` istem için ya da izinleri güncelleştirmek için öğesini çalıştırın. Kullanıcıların JEA uç noktasına erişmek için en az bir haklara sahip olması gerekir.

Erişimi olan her kullanıcıya tanımlı bir rol eşleştirmeyen bir JEA uç noktası oluşturmak mümkündür. Bu kullanıcılar bir JEA oturumu başlatabilir, ancak yalnızca varsayılan cmdlet 'lere erişim sahibi olabilir. Çalıştırarak `Get-PSSessionCapability`bir Jea uç noktasındaki Kullanıcı izinlerini denetleyebilirsiniz. Daha fazla bilgi için bkz. [JEA 'Da denetleme ve raporlama](audit-and-report.md).

## <a name="least-privilege-roles"></a>En az ayrıcalık rolleri

JEA rolleri tasarlarken, arka planda çalışan sanal ve grup tarafından yönetilen hizmet hesaplarının yerel makineye sınırsız erişimi olabileceğini unutmamak önemlidir. JEA rol özellikleri, bu ayrıcalıklı bağlamda çalıştırılabilen komutları ve uygulamaları sınırlamaya yardımcı olur.
Yanlış tasarlanmış roller, bir kullanıcının JEA sınırlarının dışına çıkmasına izin veren veya hassas bilgilere erişim sağlayan tehlikeli komutlara izin verebilir.

Örneğin, aşağıdaki rol yetenek girişini göz önünde bulundurun:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Bu rol özelliği, kullanıcıların, **Microsoft. PowerShell. Management** modülünden ad **Işlemiyle** herhangi bir PowerShell cmdlet 'i çalıştırmasına izin verir. Kullanıcıların sistemde hangi uygulamaların çalıştığını görmek ve `Get-Process` `Stop-Process` yanıt vermeyen uygulamaları sonlandırmak için gibi cmdlet 'lere erişmesi gerekebilir. Ancak, bu giriş Ayrıca `Start-Process`, tam yönetici izinleriyle rastgele bir program başlatmak için kullanılabilecek. Programın sisteme yerel olarak yüklenmesi gerekmez. Bağlı bir Kullanıcı, Kullanıcı yerel yönetici ayrıcalıklarına sahip bir dosya paylaşımından program başlatabilir, kötü amaçlı yazılım ve daha fazlasını yapar.

Aynı rol yeteneğinin daha güvenli bir sürümü şöyle görünür:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Rol özellikleri ' nde joker karakter kullanmaktan kaçının. Kullanıcı tarafından hangi komutların erişilebilir olduğunu anlamak için [etkili Kullanıcı izinlerini](audit-and-report.md#check-effective-rights-for-a-specific-user) düzenli olarak denetlediğinizden emin olun.

## <a name="jea-doesnt-protect-against-admins"></a>JEA, yöneticilere karşı korumaz

JEA 'nın temel ilkelerinin biri, yönetici olmayan yöneticilerin bazı yönetim görevlerini yapmasına izin verir. JEA, zaten yönetici ayrıcalıklarına sahip olan kullanıcılara karşı koruma vermez. **Etki alanı yöneticilerine**, yerel **yöneticilere**veya diğer yüksek ayrıcalıklı gruplara ait kullanıcılar, Jea korumalarının başka yollarla de atlayabilirler. Örneğin, RDP ile oturum açabilirler, uzak MMC konsolları kullanabilir veya kısıtlanmış PowerShell uç noktalarına bağlanabilir. Ayrıca, bir sistemdeki yerel Yöneticiler JEA yapılandırmalarının ek kullanıcılara izin verecek veya bir kullanıcı tarafından JEA oturumunda neler yapabileceğini genişletmek üzere bir rol yeteneğini değiştirebilecekleri şekilde değiştirebilir. Sisteme ayrıcalıklı erişim kazanmak için başka yollar olup olmadığını görmek için JEA kullanıcılarınızın genişletilmiş izinlerini değerlendirmek önemlidir.

Yaygın bir uygulama, JEA 'yı düzenli günlük bakım işlemleri için kullanmanın yanı sıra kullanıcıların acil durumlarda yerel Yöneticiler haline gelmesine izin veren tam zamanında ve ayrıcalıklı bir erişim yönetimi çözümüdür. Bu, kullanıcıların sistemde kalıcı yönetici olmamasını sağlamaya yardımcı olur, ancak bu hakları yalnızca bu haklara sahip olmaları durumunda ve yalnızca, bu izinlerin kullanımını belgeleyen bir iş akışını tamamlarlar.
