---
ms.date: 07/10/2019
keywords: Jea, PowerShell, güvenlik
title: JEA oturum yapılandırması
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017884"
---
# <a name="jea-session-configurations"></a>JEA oturum yapılandırması

Bir JEA uç noktası, bir PowerShell oturum yapılandırma dosyası oluşturup kaydederek sisteme kaydedilir. Oturum yapılandırmalarının, JEA uç noktasını ve hangi rollerin erişebileceğini tanımlar. Ayrıca, JEA oturumunun tüm kullanıcıları için uygulanan genel ayarları tanımlar.

## <a name="create-a-session-configuration-file"></a>Oturum yapılandırma dosyası oluşturma

JEA uç noktasını kaydetmek için, bu uç noktanın nasıl yapılandırıldığını belirtmeniz gerekir. Göz önünde bulundurulması gereken birçok seçenek vardır. En önemli seçenekler şunlardır:

- JEA uç noktasına kimlerin erişimi vardır
- Atandıkları roller
- JEA 'nın, kapakları altında kullandığı kimlik
- JEA uç noktasının adı

Bu seçenekler, PowerShell oturum yapılandırma dosyası olarak bilinen bir `.pssc` uzantıya sahip bir PowerShell veri dosyasında tanımlanmıştır. Oturum yapılandırma dosyası herhangi bir metin Düzenleyicisi kullanılarak düzenlenebilir.

Boş bir şablon yapılandırma dosyası oluşturmak için aşağıdaki komutu çalıştırın.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Varsayılan olarak şablon dosyasına yalnızca en yaygın yapılandırma seçenekleri dahil edilir. Oluşturulan pssc içindeki tüm geçerli ayarları dahil etmek için anahtarınıkullanın.`-Full`

Alanı `-SessionType RestrictedRemoteServer` , oturum yapılandırmasının güvenli yönetim için Jea tarafından kullanıldığını gösterir. Bu türün oturumları **Nolanguage** modunda çalışır ve yalnızca aşağıdaki varsayılan komutlara (ve diğer adlara) erişebilir:

- Temizle-Konak (CLS, net)
- Çıkış-PSSession (exsn, çıkış)
- Get-komutu (GCM)
- Get-FormatData
- Yardım alın
- Ölçü-nesne (ölçü)
- Dışarı-varsayılan
- Select-Object (Seç)

Kullanılabilir PowerShell sağlayıcısı yok veya hiçbir dış program (yürütülebilir dosyalar veya betikler) yok.

Dil modları hakkında daha fazla bilgi için bkz. [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).

### <a name="choose-the-jea-identity"></a>JEA kimliğini seçin

Arka planda, JEA, bağlı bir kullanıcının komutlarını çalıştırırken kullanılacak bir kimliğe (hesap) ihtiyaç duyuyor.
JEA 'nın oturum yapılandırma dosyasında hangi kimliğe kullandığını tanımlarsınız.

#### <a name="local-virtual-account"></a>Yerel sanal hesap

Yerel sanal hesaplar, JEA uç noktası için tanımlanan tüm roller yerel makineyi yönetmek için kullanıldığında ve bir yerel yönetici hesabı komutları başarıyla çalıştırmak için yeterli olduğunda yararlıdır.
Sanal hesaplar, belirli bir kullanıcı için benzersiz olan geçici hesaplardır ve yalnızca PowerShell oturumunun süresi için en son. Bir üye sunucusunda veya iş istasyonunda, sanal hesaplar yerel bilgisayarın **Yöneticiler** grubuna aittir. Active Directory Etki Alanı denetleyicisinde, sanal hesaplar etki alanının **etki alanı yöneticileri** grubuna aittir.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Oturum yapılandırması tarafından tanımlanan roller tam yönetici ayrıcalığı gerektirmiyorsa, sanal hesabın ait olacağı güvenlik gruplarını belirtebilirsiniz. Bir üye sunucusunda veya iş istasyonunda, belirtilen güvenlik grupları bir etki alanından gruplar değil yerel gruplar olmalıdır.

Bir veya daha fazla güvenlik grubu belirtildiğinde, sanal hesap yerel veya etki alanı yöneticileri grubuna atanmaz.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> Sanal hesaplara geçici olarak yerel sunucu güvenlik ilkesinde hizmet olarak oturum açma hakkı verilir. Belirtilen VirtualAccountGroups 'lerden biri zaten ilkede bu hak verildiyse, bireysel sanal hesap artık ilkeden eklenmez ve ilkeye kaldırılmaz. Bu, etki alanı denetleyicisi güvenlik ilkesi düzeltmelerinin yakından denetlenmesinde etki alanı denetleyicileri gibi senaryolarda yararlı olabilir. Bu, Windows Server 2016 ' de yalnızca Kasım 2018 veya sonraki bir toplu ve Windows Server 2019 ile Ocak 2019 veya üzeri bir toplu toplaması ile kullanılabilir.

#### <a name="group-managed-service-account"></a>Grup tarafından yönetilen hizmet hesabı

Grup tarafından yönetilen hizmet hesabı (GMSA), JEA kullanıcılarının dosya paylaşımları ve Web Hizmetleri gibi ağ kaynaklarına erişmesi gerektiğinde kullanılacak uygun bir kimliktir. GMSAs, etki alanındaki tüm makineler üzerinde kaynaklarla kimlik doğrulaması yapmak için kullanılan bir etki alanı kimliği sağlar. Bir GMSA 'nın sağladığı haklar, eriştiğiniz kaynaklara göre belirlenir. Makine veya hizmet yöneticisi bu hakları GMSA 'ya açıkça verilmemişse, hiçbir makine veya hizmette yönetici haklarına sahip değilsiniz.

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

GMSAs yalnızca gerektiğinde kullanılmalıdır:

- Bir GMSA kullanırken eylemleri kullanıcıya geri izlemek zordur. Her Kullanıcı aynı farklı çalıştır kimliğini paylaşır. Bireysel kullanıcıların eylemleriyle ilişkilendirilmesi için PowerShell oturum dökümünü ve günlüklerini gözden geçirmeniz gerekir.

- GMSA, bağlanan kullanıcının erişmesi gerekmeyen birçok ağ kaynağına erişebilir. En az ayrıcalık ilkesini izlemek için her zaman bir JEA oturumunda etkin izinleri sınırlamayı deneyin.

> [!NOTE]
> Grup tarafından yönetilen hizmet hesapları yalnızca PowerShell 5,1 veya daha yeni bir sürümü kullanan etki alanına katılmış makinelerde kullanılabilir.

JEA oturumunun güvenliğini sağlama hakkında daha fazla bilgi için bkz. [güvenlik konuları](security-considerations.md) makalesi.

### <a name="session-transcripts"></a>Oturum yazılı betikleri

Kullanıcıların oturumlarının dökümünü otomatik olarak kaydetmek için bir JEA uç noktası yapılandırmanız önerilir. PowerShell oturum dökümü, bağlanan Kullanıcı, bunlara atanan farklı çalıştır kimliği ve Kullanıcı tarafından çalıştırılan komutlar hakkında bilgiler içerir. Bir sistemde belirli bir değişikliği kimin yaptığını anlaması gereken bir denetim takımı için yararlı olabilir.

Oturum yapılandırma dosyasında otomatik dökümü yapılandırmak için, döküm dosyalarının depolanması gereken bir klasöre bir yol sağlayın.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

Transcripts, dizine okuma ve yazma erişimi gerektiren **yerel sistem** hesabı tarafından klasöre yazılır. Standart kullanıcıların klasöre erişimi olmamalıdır. Yazılı betikleri denetlemek için erişimi olan güvenlik yöneticileri sayısını sınırlayın.

### <a name="user-drive"></a>Kullanıcı sürücüsü

Bağlanan kullanıcılarınızın, JEA uç noktasına veya bu bilgisayardan dosya kopyalaması gerekiyorsa, oturum yapılandırma dosyasında Kullanıcı sürücüsünü etkinleştirebilirsiniz. Kullanıcı sürücüsü, her bağlanan kullanıcı için benzersiz bir klasöre eşlenmiş bir **PSDrive** ' dır. Bu klasör, kullanıcıların tam dosya sistemine erişim izni vermeden veya FileSystem sağlayıcısını açığa çıkarmadan sisteme dosya kopyalamasını sağlar. Kullanıcı sürücüsü içeriği, ağ bağlantısının kesintiye uğratılbileceği durumlara uyum sağlamak için oturumlar arasında kalıcıdır.

```powershell
MountUserDrive = $true
```

Varsayılan olarak, Kullanıcı Sürücüsü Kullanıcı başına en fazla 50 MB veri depolamanıza olanak sağlar. Bir kullanıcının kullanıcı sayısını *Userdrivemaximumsize* alanı ile sınırlayabilirsiniz.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Kullanıcı sürücüsündeki verilerin kalıcı olmasını istemiyorsanız, her gece klasörü otomatik olarak temizlemek için sistemde zamanlanmış bir görev yapılandırabilirsiniz.

> [!NOTE]
> Kullanıcı sürücüsü yalnızca PowerShell 5,1 veya daha yeni bir sürümde kullanılabilir.

PSDrives hakkında daha fazla bilgi için bkz. [PowerShell sürücüleri yönetme](/powershell/scripting/samples/managing-windows-powershell-drives).

### <a name="role-definitions"></a>Rol tanımları

Bir oturum yapılandırma dosyasındaki rol tanımları, **kullanıcıların** **rollere**eşlemesini tanımlar. Bu alana dahil edilen her kullanıcıya veya gruba, kayıt edildiğinde JEA uç noktası için izin verilir.
Her Kullanıcı veya Grup, Hashtable 'da yalnızca bir kez bir anahtar olarak dahil edilebilir, ancak birden çok rol atanabilir. Rol yeteneğinin adı, `.psrc` uzantısı olmadan rol yetenek dosyasının adı olmalıdır.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Kullanıcı, rol tanımında birden fazla gruba aitse, her birinin rollerine erişim sağlar. İki rol aynı cmdlet 'lere erişim izni verildiğinde, en çok izin verilen parametre kümesi kullanıcıya verilir.

Rol tanımları alanındaki yerel kullanıcıları veya grupları belirtirken, bilgisayar adını **localhost** veya joker karakterler değil kullandığınızdan emin olun. `$env:COMPUTERNAME` Değişkeni inceleyerek bilgisayar adını kontrol edebilirsiniz.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Rol yetenek arama sırası

Yukarıdaki örnekte gösterildiği gibi, rol özelliklerine rol yetenek dosyasının temel adı tarafından başvurulur. Bir dosyanın temel adı, uzantısı olmayan dosya adıdır. Sistemde aynı ada sahip birden çok rol özelliği varsa, PowerShell etkin rol yetenek dosyasını seçmek için örtük arama sırasını kullanır. JEA, aynı ada sahip tüm rol yetenek dosyalarına erişim vermez.

Jea, `$env:PSModulePath` rol yetenek dosyalarını hangi yolların tarayacağını öğrenmek için ortam değişkenini kullanır. Bu yolların her biri içinde JEA, "RoleCapabilities" alt klasörü içeren geçerli PowerShell modülleri arar. Modüller içeri aktarılırken olduğu gibi, JEA aynı ada sahip özel rol yeteneklerine Windows ile gönderilen rol yeteneklerini tercih eder.

Diğer tüm adlandırma çakışmaları için öncelik, Windows 'un dizindeki dosyaları numaralandırdığı sıraya göre belirlenir. Siparişin alfabetik olması garanti edilmez. Bağlanan kullanıcı için belirtilen adla eşleşen ilk rol yetenek dosyası bulundu. Rol yetenek arama sırası belirleyici olmadığından, rol özelliklerinin benzersiz dosya adlarına sahip olması **önemle tavsiye edilir** .

### <a name="conditional-access-rules"></a>Koşullu erişim kuralları

**Roledefinitions** alanına dahil edilen tüm kullanıcılara ve gruplara otomatik olarak Jea uç noktalarına erişim verilir. Koşullu erişim kuralları, bu erişimi iyileştirmenize ve kullanıcıların atandıkları rolleri etkilemeden ek güvenlik gruplarına ait olmasını gerektirmenize olanak tanır. Bu, bir tam zamanında ayrıcalıklı erişim yönetimi çözümünü, akıllı kart kimlik doğrulamasını veya JEA ile diğer çok faktörlü kimlik doğrulama çözümünü bütünleştirmek istediğinizde yararlıdır.

Koşullu erişim kuralları, bir oturum yapılandırma dosyasındaki RequiredGroups alanında tanımlanmıştır.
Burada, kurallarınızı oluşturmak için ' ve ' ve ' veya ' anahtarlarını kullanan bir Hashtable (isteğe bağlı olarak iç içe) sağlayabilirsiniz. Bu alanın nasıl kullanılacağına ilişkin bazı örnekler şunlardır:

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> Koşullu erişim kuralları yalnızca PowerShell 5,1 veya daha yeni sürümlerde kullanılabilir.

### <a name="other-properties"></a>Diğer özellikler

Oturum yapılandırma dosyaları bir rol yetenek dosyasının yapabileceği her şeyi de yapabilir, böylece kullanıcılara farklı komutlara erişme izni verebilirsiniz. Tüm kullanıcıların belirli cmdlet 'lere, işlevlere veya sağlayıcılara erişmesine izin vermek istiyorsanız, oturum yapılandırma dosyasında bu hakkı uygulayabilirsiniz.
Oturum yapılandırma dosyasında desteklenen özelliklerin tam listesi için, öğesini çalıştırın `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Oturum yapılandırma dosyasını test etme

[Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet 'ini kullanarak bir oturum yapılandırmasını test edebilirsiniz. `.pssc` Dosyayı el ile düzenlediyseniz, oturum yapılandırma dosyanızı test etmeniz önerilir. Test, sözdiziminin doğru olmasını sağlar. Bu testte bir oturum yapılandırma dosyası başarısız olursa, sistemde kayıtlı olamaz.

## <a name="sample-session-configuration-file"></a>Örnek oturum yapılandırma dosyası

Aşağıdaki örnek, JEA için bir oturum yapılandırmasının nasıl oluşturulacağını ve doğrulandığını gösterir. Rol tanımları, kolay ve okunabilir olmaları için oluşturulur `$roles` ve değişkeninde depolanır. Bunun için gerekli değildir.

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a>Oturum yapılandırma dosyaları güncelleştiriliyor

Kullanıcıları rollerle eşleme dahil bir JEA oturum yapılandırmasının özelliklerini değiştirmek için, [kaydını silmeniz](register-jea.md#unregistering-jea-configurations)gerekir. Ardından, güncelleştirilmiş bir oturum yapılandırma dosyası kullanarak JEA oturum yapılandırmasını [yeniden kaydedin](register-jea.md) .

## <a name="next-steps"></a>Sonraki adımlar

- [JEA yapılandırmasını kaydetme](register-jea.md)
- [JEA rollerini yazma](role-capabilities.md)
