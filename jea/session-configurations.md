---
ms.date: 06/12/2017
keywords: jea, powershell, güvenlik
title: JEA oturum yapılandırmaları
ms.openlocfilehash: 1b598522d43b2c1a26a739a67cee5181b21a7c32
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655472"
---
# <a name="jea-session-configurations"></a>JEA oturum yapılandırmaları

> Şunun için geçerlidir: Windows PowerShell 5.0

Bir JEA uç noktası oluşturarak ve belirli bir şekilde bir PowerShell oturumu yapılandırma dosyası kaydedilirken bir sistemde kayıtlı.
Oturum yapılandırmaları belirlemek *kimin* JEA uç noktası kullanabilir ve hangi rolleri erişimleri.
JEA oturumda herhangi bir rol kullanıcıları için geçerli genel ayarlar da tanımlarlar.

Bu konuda, bir PowerShell oturumu yapılandırma dosyası oluşturun ve bir JEA uç noktasını kaydetme açıklar.

## <a name="create-a-session-configuration-file"></a>Oturum yapılandırma dosyası oluşturma

Bir JEA uç nokta kaydetmek için uç noktanın nasıl yapılandırılmalıdır belirtmeniz gerekir.
Burada, en önemli hangi JEA uç noktasına erişimi olması gereken olan biri, hangi rollerin bunlar dikkate alınır için birçok seçenek atanabilir, hangi kimlik perde JEA kullanacağı vardır ve hangi JEA uç noktası adı olacaktır.
Bu tüm tanımlanmış bir PowerShell oturumu yapılandırma dosyasında, bir PowerShell veri dosyası .pssc uzantısı ile sona eriyor.

Bir JEA uç noktalar için iskelet oturum yapılandırma dosyası oluşturmak için aşağıdaki komutu çalıştırın.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> En yaygın yapılandırma seçenekleri çatı dosyasında varsayılan olarak dahil edilir.
> Kullanım `-Full` geçme içinde oluşturulan PSSC tüm ilgili ayarları içerir.

Herhangi bir metin düzenleyicisinde oturum yapılandırma dosyasını açabilirsiniz.
`-SessionType RestrictedRemoteServer` Alan, oturum yapılandırması güvenli yönetimi için JEA tarafından kullanılacak gösterir.
Bu şekilde yapılandırılan oturumları çalışır [NoLanguage modu](https://technet.microsoft.com/library/dn433292.aspx) ve yalnızca aşağıdaki 8 varsayılan komutları (ve diğer adları) olan kullanılabilir:

- Clear-Host (cls, Temizle)
- Çıkış-PSSession (exsn, çıkış)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Ölçü nesnesi (ölçü)
- Varsayılan dışarı
- Select-Object (Seç)

PowerShell yok sağlayıcıları kullanılabilir ya da herhangi bir dış (yürütülebilir dosyaları, betikler, vb.) programlardır.

JEA oturumu için yapılandırmak da isteyeceksiniz bazı alanlar vardır.
Bunlar aşağıdaki bölümlerde ele alınmıştır.

### <a name="choose-the-jea-identity"></a>JEA kimliğini seçin

Arka planda JEA bağlı kullanıcının komutlarını çalıştırırken kullanılacak bir kimliği (hesap) gerekir.
JEA oturum yapılandırma dosyasında kullanacağınız kimliği karar sizin.

#### <a name="local-virtual-account"></a>Yerel sanal hesap

Rolleri bu JEA uç noktası tarafından desteklenen tüm yerel makine yönetmek için kullanılır ve yerel yönetici hesabı komutlar başarıyla çalıştırmak için yeterli ise JEA sanal yerel hesap kullanmak için yapılandırmanız gerekir.
Belirli bir kullanıcı için benzersiz ve kendi PowerShell oturumu süresi için yalnızca son geçici hesaplarının sanal hesaplarıdır.
Üye sunucu veya iş istasyonunun Sanal hesaplar yerel bilgisayarın ait **Yöneticiler** grup ve çoğu sistem kaynaklarına erişimi vardır.
Bir Active Directory etki alanı denetleyicisinde etki alanı için sanal hesaplar ait **Domain Admins** grubu.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Oturum yapılandırması tarafından desteklenen rolleri gibi geniş ayrıcalıkları gerektirmez, isteğe bağlı olarak sanal hesap ait olacak güvenlik gruplarını belirtebilirsiniz.
Üye sunucu veya iş istasyonunun belirli güvenlik grupları yerel gruplar, bir etki alanından grupları değil olmalıdır.

Belirtilen bir veya daha fazla güvenlik grubu, sanal hesap yerel veya etki alanı yöneticileri grubuna ait olur.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```
> [!NOTE]
> Sanal hesaplar, yerel sunucu güvenlik ilkesini içinde bir hizmet olarak oturum açma geçici olarak verilir.  Belirtilen VirtualAccountGroups birini zaten ilkesinde bu hak verilmemişse, tek tek sanal hesap artık eklendi ve ilkeden kaldırılır.  Bu, burada etki alanı denetleyicisi güvenlik ilkesi uyarlamaları yakından denetlendiği etki alanı denetleyicileri gibi senaryolarda yararlı olabilir.  Bu seçenek yalnızca Kasım 2018'den Windows Server 2016 veya sonraki toplama ve Windows Server 2019 Ocak 2019 ile'veya sonraki toplama kullanılabilir.

#### <a name="group-managed-service-account"></a>Grup Yönetilen Hizmet Hesabı


JEA kullanıcı diğer makineler veya web Hizmetleri gibi ağ kaynaklarına erişmek için gerektiren senaryolar için bir grup yönetilen hizmet hesabı (gMSA) kullanmak için daha uygun bir kimliği var.
gMSA hesabı etki alanı içinde herhangi bir makinede kaynaklarına karşı kimlik doğrulaması için kullanılabilecek bir etki alanı kimliği verir.
Erişmeye çalıştığınız hakları kaynaklara göre belirlenir gMSA hesabı sağlar.
Makine/Hizmet Yöneticisi açıkça gMSA hesabı yönetici ayrıcalıkları vermedikçe, otomatik olarak tüm makineler veya hizmetler üzerinde yönetici hakları yoktur.

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

gMSA hesabı yalnızca kullanılmalıdır ağ kaynaklarına erişimi olduğunda gerekli birkaç nedeni:

- Her kullanıcı Çalıştır aynı kimliği paylaşıyor beri gMSA hesabı kullanılırken bir kullanıcı için Eylemler geri izleme için daha zor olan. PowerShell oturumu dökümleri ve kullanıcıların eylemlerini ile ilişkilendirmek için günlükleri başvurmanız gerekir.

- Bağlanan kullanıcının erişim gerekmeyen birçok ağ kaynaklarına erişim gMSA hesabı olabilir. En düşük öncelik ilkesini izlemek için bir JEA oturumunda etkili izinleri sınırlamak her zaman deneyin.

> [!NOTE]
> Grup yönetilen hizmet hesapları, yalnızca Windows PowerShell 5.1 kullanılabilir veya daha yeni ve etki alanına katılmış makinelerde.


#### <a name="more-information-about-run-as-users"></a>Hakkında daha fazla bilgi kullanıcı olarak çalıştırın

Kimlikleri ve bunların bir JEA oturum güvenliğini nasıl faktörü olarak çalışma hakkında ek bilgiler bulunabilir [güvenlik konuları](security-considerations.md) makalesi.

### <a name="session-transcripts"></a>Oturum dökümleri

Bir JEA oturum yapılandırma dosyasına otomatik olarak kayıt dökümleri, kullanıcıların oturumlarının yapılandırma önerilir.
PowerShell oturumu dökümleri bağlanan kullanıcının, farklı çalıştır kimlik atanmamış hakkındaki bilgileri içerir ve kullanıcı tarafından komutları çalıştırın.
Bunlar, belirli bir değişiklik sisteme gerçekleştiren anlaşılması gereken bir denetim ekibine yararlı olabilir.

Oturum yapılandırma dosyasında otomatik döküm yapılandırmak için dökümleri nerede depolanması gereken bir klasöre bir yol sağlar.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

Belirtilen klasör değiştirmekten veya silmekten içindeki tüm veriler kullanıcıların önlemek için yapılandırılmalıdır.
Dökümler, okuma ve dizine yazma erişimi gerektiren yerel sistem hesabı tarafından klasörüne yazılır.
Standart kullanıcılar klasörüne erişimi olmalıdır ve güvenlik yöneticileri sınırlı sayıda dökümleri denetim erişimi olması gerekir.

### <a name="user-drive"></a>Kullanıcı sürücü

Bağlanan kullanıcıların bir komutu çalıştırmak için dosyaları JEA uç noktası kopyalamak istiyorsanız, oturum yapılandırma dosyasındaki kullanıcı sürücü etkinleştirebilirsiniz.
Kullanıcı sürücüdür bir [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) bağlanan her kullanıcı için benzersiz bir klasöre eşlendi.
Bu klasör, bunları tam dosya sistemine erişim vermeden veya dosya sistemi sağlayıcısı gösterme öğesine/öğesinden sistem dosyalarını kopyalamak için bir alan olarak görev yapar.
Kullanıcı sürücü içeriğini burada ağ bağlantısı kesilebilir durumlarda oturumları arasında kalıcıdır.

```powershell
MountUserDrive = $true
```

Varsayılan olarak, kullanıcı sürücüsünde en fazla kullanıcı başına veri 50 MB'ın depolamanıza olanak sağlar.
Bir kullanıcı ile kullanabileceği veri miktarını sınırlamak *UserDriveMaximumSize* alan.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Verilerin kalıcı olmasını kullanıcı sürücüsündeki istemiyorsanız, sistemde klasörü her gece otomatik olarak temizlemek için zamanlanmış bir görev yapılandırabilirsiniz.

> [!NOTE]
> Kullanıcı yalnızca Windows PowerShell 5.1 bulunan ya da daha yeni sürücüdür.

### <a name="role-definitions"></a>Rol tanımları

Rol tanımları oturum yapılandırma dosyasında tanımlama eşleme *kullanıcılar* için *rolleri*.
Otomatik olarak kaydedildiğinde her kullanıcı veya grup bu alanda bulunan JEA uç noktasına izin verilir.
Her bir kullanıcı veya grubu yalnızca bir kez anahtar karma tablosu olarak dahil edilebilir, ancak birden çok rol atanabilir.
Rol özelliğin adına .psrc uzantısı olmadan rolü özelliği dosyasının adı olmalıdır.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Bir kullanıcı birden fazla rol tanımı grubuna dahilse, her rol için erişim alırlar.
İki rol aynı cmdlet'lere erişim sağlıyorsa, en esnek parametre kümesi kullanıcıya verilir.

Yerel kullanıcı veya grup rol tanımları alanını belirtirken, bilgisayar adını kullandığınız emin olun (değil *localhost* veya *.*) önce ters eğik çizgi.
Bilgisayar adı inceleyerek denetleyebilirsiniz `$env:computername` değişkeni.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Rol özellik arama sırası
Yukarıdaki örnekte gösterildiği gibi rol işlevleri rol özellik dosyası düz adıyla (dosya adı uzantısı olmadan) olarak başvurulur.
Sistem düz aynı ada sahip birden çok rol özellikleri mevcuttur, etkin bir rol özelliği dosyayı seçmek için örtük arama sırası PowerShell kullanacaksınız.
Götürür **değil** aynı ada sahip tüm rol özellik dosyaları için erişim verin.

Jea'yı kullanan `$env:PSModulePath` rol özellik dosyaları taramak için hangi yolları belirlemek için ortam değişkeni.
Her bu yollar içinde bir "RoleCapabilities" alt klasör içeren geçerli PowerShell modülleri için JEA görünecektir.
JEA modülleri alma gibi Windows ile aynı ada sahip özel rol özellikleri için sağlanan rol işlevleri tercih eder.
Tüm diğer adlandırma çakışmaları için öncelik, Windows (alfabetik olması garanti edilmez) dizindeki dosyaları listeler sıraya göre belirlenir.
İstenen eşleşen ilk rol özellik dosyası bulunamadı. adı bağlanan kullanıcı için kullanılır.

Rol özellik arama sırası, iki belirleyici değil veya daha fazla rol işlevleri aynı adı paylaşan olduğu **önemle tavsiye** rol işlevleri makinenizde benzersiz adlara sahip olun.

### <a name="conditional-access-rules"></a>Koşullu erişim kuralları

Otomatik olarak tüm kullanıcılar ve gruplar RoleDefinitions alanında bulunan JEA uç noktalarına erişimi verilir.
Koşullu erişim kuralları, bu erişimi iyileştirin ve kullanıcıların, atanmış olan rolleri etkilemez ek güvenlik gruplarına ait zorunlu olanak tanır.
Bu bir "tam zamanında" ayrıcalıklı tümleştirmek istiyorsanız yararlı olabilir erişim yönetimi çözümü, akıllı kart kimlik doğrulaması veya diğer çok faktörlü kimlik doğrulaması çözümüyle JEA.

Koşullu erişim kuralları, bir oturum yapılandırması dosyasını RequiredGroups alanında tanımlanır.
Kullanan bir hashtable (iç içe isteğe bağlı olarak) sağlar, 'Ve' ve 'Veya' anahtarlar kurallarınızı oluşturmak için.
Bu alan kullanmayı bazı örnekleri aşağıda verilmiştir:

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
> Koşullu erişim kuralları yalnızca, Windows PowerShell 5.1 veya yeni kullanılabilir.

### <a name="other-properties"></a>Diğer özellikler
Oturum yapılandırma dosyalarını da rol özellik dosyası için farklı komutlar bağlantı kullanıcı erişimi vermek için yalnızca özelliği olmadan yapabileceği her şeyi yapabilirsiniz.
Erişimi belirli cmdlet'ler, İşlevler veya sağlayıcıları tüm kullanıcılara izin vermek istiyorsanız, bunu yapabilirsiniz oturum yapılandırma dosyasında sağ.
Oturum yapılandırma dosyasında desteklenen özellikler tam listesi için çalıştırma `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Test oturumu yapılandırma dosyası

Kullanarak bir oturum yapılandırması test [Test PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet'i.
El ile söz dizimi doğru olduğundan emin olmak için bir metin düzenleyicisi kullanarak pssc dosyasını düzenlediyseniz oturum yapılandırma dosyanızı test önemle tavsiye edilir.
Bu test oturumu yapılandırma dosyası geçemezse, başarıyla sistemde kayıtlı olması mümkün olmayacaktır.

## <a name="sample-session-configuration-file"></a>Örnek oturum yapılandırma dosyası

Oluşturma ve oturum yapılandırmasını doğrulamak için JEA gösteren tam bir örnek aşağıda verilmiştir.
Rol tanımları oluşturulur ve depolanır Not `$roles` convenience ve Okunabilirlik için değişken.
Bunu yapmak için bir gereksinim değildir.

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a>Oturum yapılandırma dosyalarını güncelleştirme

Kullanıcıların rollere, eşleme içeren bir JEA oturum yapılandırması özelliklerini değiştirmek gerekiyorsa, [kaydını](register-jea.md#unregistering-jea-configurations) ve [yeniden kaydettirin](register-jea.md) JEA oturum yapılandırması.
JEA oturum yapılandırması yeniden kaydettiğinizde, istediğiniz değişiklikleri içeren güncelleştirilmiş bir PowerShell oturumu yapılandırma dosyası kullanın.

## <a name="next-steps"></a>Sonraki adımlar

- [Bir JEA yapılandırmasını Kaydet](register-jea.md)
- [Yazar JEA rolleri](role-capabilities.md)
