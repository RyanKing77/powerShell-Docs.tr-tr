---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea, powershell, güvenlik"
title: "JEA oturum yapılandırmaları"
ms.openlocfilehash: 0a8931ae15caf04a3639ab46f130e5f5b0498d8c
ms.sourcegitcommit: 0733db9a05e89e6a23f6b52b9edd784fcbe8beec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2017
---
# <a name="jea-session-configurations"></a>JEA oturum yapılandırmaları

> Uygulandığı öğe: Windows PowerShell 5.0

JEA uç noktası oluşturarak ve belirli bir şekilde bir PowerShell oturumu yapılandırma dosyası kaydediliyor bir sistemde kayıtlı.
Oturum yapılandırmaları belirlemek *kimin* JEA endpoint kullanabilirsiniz ve hangi rollere erişime sahip.
Bunlar aynı zamanda JEA oturumunda herhangi bir rolü kullanıcılar için geçerli genel ayarlarını tanımlar.

Bu konuda, bir PowerShell oturumu yapılandırma dosyası oluşturun ve JEA uç noktasını kaydetme açıklar.

## <a name="create-a-session-configuration-file"></a>Oturum yapılandırma dosyası oluşturma

JEA uç noktasını kaydetmek için bu uç nasıl yapılandırılmalıdır belirtmeniz gerekir.
Burada, en önemli hangi kimin JEA uç noktası erişimi olması gereken olmaya biri, hangi rollerin olacak bunlar dikkate alınması gereken birçok seçenek atanabilir, hangi kimlik JEA perde arkasında kullanacağı vardır ve ne JEA uç noktanın adı olacaktır.
Bunlar tüm tanımlanmış bir PowerShell oturumu yapılandırma dosyasında hangi .pssc uzantısı ile bir PowerShell veri dosyasını sonlandırıyor.

JEA uç noktaları için bir iskelet oturum yapılandırma dosyası oluşturmak için aşağıdaki komutu çalıştırın.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Yalnızca en yaygın yapılandırma seçenekleri varsayılan olarak iskelet dosyasına dahil edilir.
> Kullanım `-Full` anahtar içinde oluşturulan PSSC tüm ilgili ayarları içerir.

Herhangi bir metin düzenleyicisinde oturum yapılandırma dosyası açabilirsiniz.
`-SessionType RestrictedRemoteServer` Alan, oturum yapılandırması için güvenli yönetim JEA tarafından kullanılacak gösterir.
Bu şekilde yapılandırılan oturumları çalışacağı [NoLanguage modu](https://technet.microsoft.com/en-us/library/dn433292.aspx) ve yalnızca aşağıdaki 8 varsayılan komutları (ve diğer adlar) kullanılabilir:

- Clear-Host (cls, Temizle)
- Çıkış-PSSession (exsn, çıkış)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Ölçü nesnesi (ölçüm)
- Dışarı varsayılan
- Select-Object (seçin)

Herhangi bir PowerShell sağlayıcısı kullanılabilir veya tüm dış (yürütülebilir dosyaları, komut dosyaları, vb.) programlardır.

JEA oturumu için yapılandırmak istediğiniz bazı alanlar vardır.
Bunlar aşağıdaki bölümlerde ele alınmıştır.

### <a name="choose-the-jea-identity"></a>JEA kimliğini seçin

Arka planda JEA bağlı kullanıcının komutlarını çalıştırırken kullanılacak bir kimliği (hesap) gerekir.
JEA oturum yapılandırma dosyasında kullanacağı hangi kimlik karar verin.

#### <a name="local-virtual-account"></a>Yerel sanal hesap

Bu JEA bitiş noktası tarafından desteklenen roller tüm yerel makine yönetmek için kullanılır ve yerel yönetici hesabı komutları başarıyla çalıştırmak yeterli ise, yerel sanal hesap kullanmak için JEA yapılandırmanız gerekir.
Sanal hesap belirli bir kullanıcı için benzersiz ve kendi PowerShell oturumu süresince yalnızca son geçici hesaplardır.
Üye sunucusu veya iş istasyonu sanal hesaplar yerel bilgisayarın ait **Yöneticiler** grup ve çoğu sistem kaynaklarına erişimi vardır.
Bir Active Directory etki alanı denetleyicisinde sanal hesaplar etki alanına ait ait **Domain Admins** grubu.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Oturum yapılandırması tarafından desteklenen roller gibi geniş ayrıcalıklarına gerek duymuyorsanız, isteğe bağlı olarak sanal hesap ait olacağı güvenlik gruplarını belirtebilirsiniz.
Üye sunucusu veya iş istasyonu belirtilen güvenlik grupları yerel gruplar, olmayan bir etki alanından grupları olması gerekir.

Bir veya daha fazla güvenlik grubu belirtilirse, sanal hesap artık yerel veya etki alanı yöneticileri grubuna ait.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a>Grup Yönetilen Hizmet Hesabı


Diğer makinelerin veya web Hizmetleri gibi ağ kaynaklarına erişmek için JEA kullanıcının gerektiren senaryolar için bir grup yönetilen hizmet hesabı (gMSA) kullanmak için bir daha uygun kimliğidir.
gMSA hesapları etki alanındaki herhangi bir makinede kaynaklarına karşı kimlik doğrulaması için kullanılan bir etki alanı kimlik sağlayabilirsiniz.
Erişmeye çalıştığınız hakları kaynaklar tarafından belirlenir. gMSA hesabı sağlar.
Makine/Hizmet Yöneticisi Yönetici ayrıcalıkları gMSA hesabını açıkça verildi sürece tüm makineler veya hizmetler üzerinde yönetici hakları otomatik olarak olmayacaktır.

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

gMSA hesapları yalnızca kullanılmalıdır ağ kaynaklarına erişim olduğunda gereken birkaç nedeni:

- Her kullanıcı aynı Çalıştır kimlik paylaşır beri gMSA hesabı kullanırken, bir kullanıcıya eylemleri geri izlemek için daha zor olduğu. PowerShell oturumu dökümleri ve kullanıcılar kendi eylemleri ile ilişkilendirmek için günlükleri danışmanız gerekir.

- GMSA hesabı bağlanan kullanıcı erişimi gerekmez birçok ağ kaynaklarına erişim olabilir. En az ayrıcalık ilkesini izlemek için bir JEA oturumunda etkili izinleri sınırlamak her zaman deneyin.

> [!NOTE]
> Grup yönetilen hizmet hesapları yalnızca Windows PowerShell 5.1 kullanılabilir veya daha yeni ve etki alanına katılmış makinelerde.


#### <a name="more-information-about-run-as-users"></a>Hakkında daha fazla bilgi kullanıcı olarak çalıştırın

Kimlikleri ve bunlar JEA oturumu güvenlik nasıl faktör olarak çalıştır hakkında ek bilgiler bulunabilir [güvenlik konuları](security-considerations.md) makalesi.

### <a name="session-transcripts"></a>Oturum dökümleri

Kullanıcıların oturumunu otomatik olarak kayıt dökümleri JEA oturum yapılandırma dosyasına yapılandırmanız önerilir.
PowerShell oturumu dökümleri, atanmış kimlik Çalıştır bağlanan kullanıcı hakkındaki bilgileri içerir ve kullanıcı tarafından komutları çalıştırın.
Bunlar, bir sistem için belirli bir değişiklik gerçekleştiren anlamak için gereken bir denetim ekibi için yararlı olabilir.

Oturum yapılandırma dosyasında otomatik transcription yapılandırmak için dökümleri depolanacağı klasörün yolunu girin.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

Belirtilen klasör, değiştirme veya silme içindeki tüm veriler kullanıcıların önlemek için yapılandırılmalıdır.
Dökümleri, okuma ve yazma erişimi dizinine gerektiren yerel sistem hesabı tarafından klasörüne yazılır.
Standart kullanıcılar klasörüne erişimi olmalıdır ve güvenlik yöneticileri sınırlı sayıda dökümleri denetim erişimi olması gerekir.

### <a name="user-drive"></a>Kullanıcı sürücü

Bağlanan kullanıcıların dosyaları için/JEA uç noktası bir komut çalıştırmak için kopyalamak gerekiyorsa oturum yapılandırma dosyasındaki kullanıcı sürücü etkinleştirebilirsiniz.
Kullanıcı sürücü bir [PSDrive](https://msdn.microsoft.com/en-us/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) bağlanan her kullanıcı için benzersiz bir klasör için eşlenmedi.
Bu klasör, bunları bunları tam dosya sistemine erişim veren veya dosya sistemi sağlayıcısı gösterme denetleyicisinden sistem dosyaları kopyalamak bir alan olarak görev yapar.
Kullanıcı disk içeriği ağ bağlantısı nerede kesintiye durumlarda oturumlarında kalıcıdır.

```powershell
MountUserDrive = $true
```

Varsayılan olarak, kullanıcı sürücüsünde en fazla kullanıcı başına veri 50 MB depolamanıza olanak sağlar.
Bir kullanıcı ile tüketebileceği veri miktarını sınırlamak *UserDriveMaximumSize* alan.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Kalıcı olması için kullanıcı sürücüde veri istemiyorsanız, zamanlanmış bir görev klasörü her gece otomatik olarak temizlemek için sistemde yapılandırabilirsiniz.

> [!NOTE]
> Kullanıcı yalnızca Windows PowerShell 5.1 bulunan ya da daha yeni sürücüdür.

### <a name="role-definitions"></a>Rol tanımları

Rol tanımları oturum yapılandırma dosyasında tanımlayın eşleme *kullanıcılar* için *rolleri*.
Otomatik olarak onu kaydedildikten sonra her bir kullanıcı veya grup bu alana dahil JEA endpoint izni verilecektir.
Her bir kullanıcı veya grup yalnızca bir kez anahtar hashtable olarak dahil edilebilir, ancak birden çok rol atanabilir.
Rol özelliğin adına .psrc uzantısı olmadan Rol Yetenek dosyasının adı olmalıdır.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Bir kullanıcı birden fazla rol tanımı grubuna aitse, her rol için erişim elde.
İki rolleri aynı cmdlet'leri erişim izni, en fazla izne sahip parametre kümesi kullanıcıya verilecektir.

Yerel kullanıcılar veya gruplar rol tanımları alanı belirtirken, bilgisayar adı kullandığınızdan emin olun (değil *localhost* veya *.*) ters eğik çizgi önce.
Bilgisayar adı inceleyerek denetleyebilirsiniz `$env:computername` değişkeni.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Rol Yetenek arama sırası
Yukarıdaki örnekte gösterildiği gibi rol özellikleri Rol Yetenek dosya düz adıyla (dosya adı uzantısı olmadan) başvurulur.
Birden çok rol özellikleri varsa düz adında sisteminde PowerShell etkili Rol Yetenek dosyasını seçmek için kendi örtük arama sırası kullanacaksınız.
İçinde **değil** aynı ada sahip tüm Rol Yetenek dosyaları erişim verin.

JEA kullanan `$env:PSModulePath` Rol Yetenek dosyaları taramak için hangi yolları belirlemek için ortam değişkeni.
Her bu yollar içinde bir "RoleCapabilities" alt klasör içeren geçerli PowerShell modülleri için JEA arar.
Modülleri gibi içeri aktarma ile aynı ada sahip özel rol özellikleri için Windows ile birlikte rol özellikleri JEA tercih eder.
Tüm diğer adlandırma çakışmaları için öncelik Windows (alfabetik olması garanti değil) dizindeki dosyaların numaralandırır sıraya göre belirlenir.
İstenen eşleşen ilk Rol Yetenek dosyası bulundu adı bağlanan kullanıcı için kullanılır.

Rol Yetenek arama sırası iki belirleyici değil veya daha fazla rol özellikleri aynı adı paylaşan beri olan **önemle tavsiye** rol özellikleri makinenize benzersiz adlara sahip olun.

### <a name="conditional-access-rules"></a>Koşullu erişim kuralları

Otomatik olarak tüm kullanıcılar ve gruplar RoleDefinitions alanında bulunan JEA Uç noktalara erişimi verilir.
Koşullu erişim kuralları, bu erişim daraltın ve kullanıcıların, bunlar atanan rollerden etkilemeyen ek güvenlik gruplarına ait zorunlu olanak tanır.
Bu bir "biraz zaman" ayrıcalıklı tümleştirmek istediğiniz durumlarda yararlı olabilir erişim yönetimi çözümü, akıllı kart kimlik doğrulaması veya başka bir çok faktörlü kimlik doğrulama çözümü JEA ile.

Koşullu erişim kuralları, bir oturum yapılandırma dosyası RequiredGroups alanında tanımlanır.
Burada, kullanır (isteğe bağlı olarak iç içe) bir hashtable sağlayabilir 'Ve' ve 'Veya' anahtarları kurallarınızı oluşturmak için.
Bu alan yararlanmak nasıl bazı örnekleri şunlardır:

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
> Koşullu erişim kuralları yalnızca Windows PowerShell 5.1 bulunan ya da daha yeni.

### <a name="other-properties"></a>Diğer özellikler
Oturum yapılandırma dosyalarını bir rol özelliği dosyası yalnızca farklı komutları bağlanan kullanıcılara erişim vermek özelliği olmadan yapabilirsiniz her şeyi da yapabilirsiniz.
Tüm kullanıcıların belirli cmdlet'ler, İşlevler veya sağlayıcıları erişmesine izin vermek istiyorsanız, bunu yapabilirsiniz sağ oturum yapılandırma dosyası.
Desteklenen özellikler oturum yapılandırma dosyasında tam listesi için çalıştırın `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Bir oturum yapılandırma dosyası test etme

Bir oturum Yapılandırması kullanılarak test [Test PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet'i.
El ile sözdizimi doğru olduğundan emin olmak için bir metin düzenleyicisi kullanarak pssc dosyayı düzenlerseniz, oturum yapılandırma dosyanızı test önerilir.
Bir oturum yapılandırma dosyası bu test geçemezse, sistemde başarıyla kaydedilmesi mümkün olmaz.

## <a name="sample-session-configuration-file"></a>Örnek oturum yapılandırma dosyası

Aşağıda nasıl oluşturulacağı ve bir oturum yapılandırması doğrulamak için JEA gösteren tam bir örnek verilmiştir.
Rol tanımları oluşturulur ve depolanır Not `$roles` kolaylık sağlamak ve Okunabilirlik için değişken.
Bunu yapmak için zorunlu değildir.

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

Rolleri, kullanıcılara eşleme dahil olmak üzere bir JEA oturum yapılandırmasının özelliklerini değiştirmeniz gerekiyorsa, gerekir [kaydı](register-jea.md#unregistering-jea-configurations) ve [yeniden kaydettirin](register-jea.md) JEA oturum yapılandırması.
JEA oturum yapılandırmasını yeniden kaydettiğinizde, istediğiniz değişiklikleri içeren güncelleştirilmiş bir PowerShell oturumu yapılandırma dosyası kullanın.

## <a name="next-steps"></a>Sonraki adımlar

- [JEA yapılandırma kaydetme](register-jea.md)
- [Yazar JEA rolleri](role-capabilities.md)

