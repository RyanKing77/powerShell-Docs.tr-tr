---
ms.date: 07/10/2019
keywords: jea, powershell, güvenlik
title: JEA oturum yapılandırmaları
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726556"
---
# <a name="jea-session-configurations"></a>JEA oturum yapılandırmaları

Bir JEA uç noktası oluşturma ve bir PowerShell oturumu yapılandırma dosyası kaydedilirken bir sistemde kayıtlı. JEA uç noktası kullanan ve hangi rollerin erişimleri oturum yapılandırmaları tanımlar. Bunlar ayrıca JEA oturumun tüm kullanıcılar için geçerli genel ayarlarını tanımlar.

## <a name="create-a-session-configuration-file"></a>Oturum yapılandırma dosyası oluşturma

Bir JEA uç noktasını kaydetmek için uç noktanın nasıl yapılandırıldığını belirtmeniz gerekir. Dikkate alınması gereken birçok seçenek vardır. En önemli Seçenekler şunlardır:

- JEA uç noktası erişimi kimler
- Hangi rollerin bunlar atanması
- Hangi kimlik JEA perde kullanır.
- JEA uç noktası adı

Bu seçenekler, bir PowerShell veri dosyasında tanımlanan bir `.pssc` uzantısı bir PowerShell oturumu yapılandırma dosyası bilinir. Oturum yapılandırma dosyası, herhangi bir metin düzenleyicisi kullanarak düzenlenebilir.

Boş şablon yapılandırma dosyasını oluşturmak için aşağıdaki komutu çalıştırın.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> En yaygın yapılandırma seçenekleri varsayılan olarak şablon dosyasına dahil edilir. Kullanım `-Full` geçme içinde oluşturulan PSSC tüm ilgili ayarları içerir.

`-SessionType RestrictedRemoteServer` Alanının oturum yapılandırması tarafından JEA güvenli yönetimi için kullanılır. Bu tür oturumları olarak çalışır **NoLanguage** modu ve yalnızca aşağıdaki varsayılan komutları (ve diğer adları) erişimi:

- Clear-Host (cls, Temizle)
- Çıkış-PSSession (exsn, çıkış)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Ölçü nesnesi (ölçü)
- Varsayılan dışarı
- Select-Object (Seç)

PowerShell yok sağlayıcıları kullanılabilir ya da herhangi bir dış (yürütülebilir dosyalar veya betikler) programlardır.

Dil modları hakkında daha fazla bilgi için bkz. [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).

### <a name="choose-the-jea-identity"></a>JEA kimliğini seçin

Arka planda JEA bağlı kullanıcının komutlarını çalıştırırken kullanılacak bir kimliği (hesap) gerekir.
JEA oturum yapılandırma dosyasında kullanan hangi kimlik tanımlarsınız.

#### <a name="local-virtual-account"></a>Yerel sanal hesap

JEA uç noktası için tanımlanan tüm rolleri yerel makine yönetmek için kullanılır ve yerel yönetici hesabı başarıyla komutları çalıştırmak yeterli yerel sanal hesaplar yararlı olur.
Belirli bir kullanıcı için benzersiz ve kendi PowerShell oturumu süresi için yalnızca son geçici hesaplarının sanal hesaplarıdır. Üye sunucu veya iş istasyonunun Sanal hesaplar yerel bilgisayarın ait **Yöneticiler** grubu. Bir Active Directory etki alanı denetleyicisinde etki alanı için sanal hesaplar ait **Domain Admins** grubu.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Oturum yapılandırması tarafından tanımlanan rolleri tam yönetici ayrıcalığı gerektirmeyen sanal hesap ait olacak güvenlik gruplarını belirtebilirsiniz. Üye sunucu veya iş istasyonunun belirli güvenlik grupları yerel gruplar, bir etki alanından grupları değil olmalıdır.

Bir veya daha fazla güvenlik grubu belirtildiğinde, sanal hesap yerel veya etki alanı yöneticileri grubuna atanmadı.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> Sanal hesaplar, yerel sunucu güvenlik ilkesini içinde bir hizmet olarak oturum açma geçici olarak verilir. Belirtilen VirtualAccountGroups birini zaten ilkesinde bu hak verilmemişse, tek tek sanal hesap artık eklendi ve ilkeden kaldırılır. Bu, burada etki alanı denetleyicisi güvenlik ilkesi uyarlamaları yakından denetlendiği etki alanı denetleyicileri gibi senaryolarda yararlı olabilir. Bu seçenek yalnızca Kasım 2018'den Windows Server 2016 veya sonraki toplama ve Windows Server 2019 Ocak 2019 ile'veya sonraki toplama kullanılabilir.

#### <a name="group-managed-service-account"></a>Grup yönetilen hizmet hesabı

Grup yönetilen hizmet hesabı (GMSA) JEA kullanıcıların dosya paylaşımları ve web Hizmetleri gibi ağ kaynaklarına erişmek gerektiğinde kullanmak için uygun bir kimliği var. Gmsa'lar etki alanındaki herhangi bir makinede kaynakları ile kimlik doğrulaması için kullanılan bir etki alanı kimliği verir. Kaynaklar tarafından belirlenen bir GMSA sağladığı hakları eriştiğiniz. Makine veya Hizmet Yöneticisi gmsa'nın bu hakları açıkça vermedikçe tüm makineler veya hizmetler üzerinde yönetici haklarına sahip değilsiniz.

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

Gmsa'lar yalnızca gerekli olduğunda kullanılmalıdır:

- Bir gmsa'yı kullanarak bir kullanıcıya eylemleri geri izleme zordur. Her kullanıcı Çalıştır aynı kimliği paylaşıyor. PowerShell oturumu dökümleri ve bireysel kullanıcıların eylemlerini ile ilişkilendirmek için günlükleri gözden geçirmeniz gerekir.

- GMSA bağlanan kullanıcının erişmesi gereken olmayan birçok ağ kaynaklarına erişiminiz olmayabilir. En düşük öncelik ilkesini izlemek için bir JEA oturumunda etkili izinleri sınırlamak her zaman deneyin.

> [!NOTE]
> Grup yönetilen hizmet hesapları yalnızca PowerShell 5.1 kullanarak etki alanına katılmış makinelerde veya yeni kullanılabilir.

Bir JEA oturum güvenliğini sağlama hakkında daha fazla bilgi için bkz. [güvenlik konuları](security-considerations.md) makalesi.

### <a name="session-transcripts"></a>Oturum dökümleri

Bir JEA uç noktası için kullanıcıların oturumu otomatik olarak kayıt dökümleri yapılandırma önerilir. PowerShell oturumu dökümleri bağlanan kullanıcının, farklı çalıştır kimlik atanmamış hakkındaki bilgileri içerir ve kullanıcı tarafından komutları çalıştırın. Bunlar, bir sistemde belirli bir değişikliği kimin yaptığını anlamak için gereken bir denetim takımı yararlı olabilir.

Oturum yapılandırma dosyasında otomatik döküm yapılandırmak için dökümleri nerede depolanması gereken bir klasöre bir yol sağlar.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

Dökümler tarafından belirtilen klasöre yazılır **yerel sistem** hesabı okuma ve dizine yazma erişimi gerektirir. Standart kullanıcılar klasörüne erişimi olmalıdır. Dökümler denetim erişimi güvenlik yöneticileri sayısını sınırlayın.

### <a name="user-drive"></a>Kullanıcı sürücü

Bağlanan kullanıcıların veya JEA uç noktasından dosyaları kopyalamak gerekiyorsa, oturum yapılandırma dosyasındaki kullanıcı sürücü etkinleştirebilirsiniz. Kullanıcı sürücüdür bir **PSDrive** bağlanan her kullanıcı için benzersiz bir klasöre eşlendi. Bu klasör, dosyaları ya da sistemden tam dosya sistemine erişim vermeden veya dosya sistemi sağlayıcısı gösterme kopyalamak kullanıcıların sağlar. Kullanıcı sürücü içeriğini burada ağ bağlantısı kesilebilir durumlarda oturumları arasında kalıcıdır.

```powershell
MountUserDrive = $true
```

Varsayılan olarak, kullanıcı sürücüsünde en fazla kullanıcı başına veri 50 MB'ın depolamanıza olanak sağlar. Bir kullanıcı ile kullanabileceği veri miktarını sınırlamak *UserDriveMaximumSize* alan.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Verilerin kalıcı olmasını kullanıcı sürücüsündeki istemiyorsanız, sistemde klasörü her gece otomatik olarak temizlemek için zamanlanmış bir görev yapılandırabilirsiniz.

> [!NOTE]
> Kullanıcı yalnızca PowerShell 5.1 bulunan ya da daha yeni sürücüdür.

PSDrives hakkında daha fazla bilgi için bkz: [yönetme PowerShell sürücüleri](/powershell/scripting/samples/managing-windows-powershell-drives).

### <a name="role-definitions"></a>Rol tanımları

Rol tanımları oturum yapılandırma dosyasında tanımlama eşleme **kullanıcılar** için **rolleri**. Kaydedildiğinde her kullanıcı veya grup bu alanda bulunan JEA uç noktasına izin verilir.
Her bir kullanıcı veya grubu yalnızca bir kez anahtar karma tablosu olarak dahil edilebilir, ancak birden çok rol atanabilir. Rol özelliğin adına rolü özelliği dosyasının adı olmadan olmalıdır `.psrc` uzantısı.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Bir kullanıcı birden fazla rol tanımı grubuna dahilse, her rol erişim elde edin. İki rol aynı cmdlet'lere izin verdiğinizde, en esnek parametre kümesi kullanıcıya verilir.

Yerel kullanıcı veya grup rol tanımları alanını belirtirken, bilgisayar adı kullanmadığınızdan emin olması **localhost** veya joker karakterler. Bilgisayar adı inceleyerek denetleyebilirsiniz `$env:COMPUTERNAME` değişkeni.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Rol özellik arama sırası

Yukarıdaki örnekte gösterildiği gibi rol işlevleri rolü özelliği dosyasının temel adı tarafından başvurulur. Temel dosya adı uzantısı olmadan dosya adıdır. PowerShell, örtük arama sırası sistem aynı ada sahip birden çok rol özellikleri mevcuttur, etkin bir rol özelliği dosyayı seçmek için kullanır. JEA mu **değil** aynı ada sahip tüm rol özellik dosyaları için erişim verin.

Jea'yı kullanan `$env:PSModulePath` rol özellik dosyaları taramak için hangi yolları belirlemek için ortam değişkeni. Her bu yollar içinde bir "RoleCapabilities" alt klasör içeren geçerli PowerShell modülleri için JEA arar. JEA modülleri alma gibi Windows ile aynı ada sahip özel rol özellikleri için sağlanan rol işlevleri tercih eder.

Tüm diğer adlandırma çakışmaları için öncelik, Windows dizinde dosyaları listeler sıraya göre belirlenir. Sipariş alfabetik olmasını garanti yoktur. Belirtilen eşleşen ilk rol özellik dosyası bulunamadı. adı bağlanan kullanıcı için kullanılır. Rol özellik arama beri sırası belirlenimci değildir, bu **önemle tavsiye** rol işlevleri benzersiz dosya adları vardır.

### <a name="conditional-access-rules"></a>Koşullu erişim kuralları

Tüm kullanıcıları ve grupları dahil **RoleDefinitions** alan JEA uç noktalarına erişimi otomatik olarak verilir. Koşullu erişim kuralları, bu erişimi iyileştirin ve kendisine atanmış oldukları roller etkisini ek güvenlik gruplarına ait gerektirmek olanak tanır. Just-ın-time ayrıcalıklı erişim yönetimi çözümü, akıllı kart kimlik doğrulaması veya diğer çok faktörlü kimlik doğrulama çözümü JEA ile tümleştirmek istediğiniz durumlarda kullanışlıdır.

Koşullu erişim kuralları, bir oturum yapılandırması dosyasını RequiredGroups alanında tanımlanır.
Kullanan bir hashtable (iç içe isteğe bağlı olarak) sağlar, 'Ve' ve 'Veya' anahtarlar kurallarınızı oluşturmak için. Bu alan ilişkin bazı örnekler şunlardır:

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
> Koşullu erişim kuralları yalnızca PowerShell 5.1 bulunan ya da daha yeni.

### <a name="other-properties"></a>Diğer özellikler

Oturum yapılandırma dosyalarını da rol özellik dosyası için farklı komutlar bağlantı kullanıcı erişimi vermek için yalnızca özelliği olmadan yapabileceği her şeyi yapabilirsiniz. Erişimi belirli cmdlet'ler, İşlevler veya sağlayıcıları tüm kullanıcılara izin vermek istiyorsanız, bunu yapabilirsiniz oturum yapılandırma dosyasında sağ.
Oturum yapılandırma dosyasında desteklenen özellikler tam listesi için çalıştırma `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Test oturumu yapılandırma dosyası

Kullanarak bir oturum yapılandırması test [Test PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet'i. El ile düzenlendi, oturum yapılandırma dosyanızı sınamanız önerilir `.pssc` dosya. Test, söz dizimi doğru olmasını sağlar. Bir oturum yapılandırma dosyası bu test başarısız olursa, sistemde kaydedilemez.

## <a name="sample-session-configuration-file"></a>Örnek oturum yapılandırma dosyası

Aşağıdaki örnek, oluşturma ve JEA için bir oturum yapılandırması doğrulama gösterilmektedir. Rol tanımları oluşturulur ve depolanır `$roles` convenience ve Okunabilirlik için değişken. Bu, bunu yapmak için bir gereksinim değildir.

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

Kullanıcıların rollere, eşleme içeren bir JEA oturum yapılandırması özelliklerini değiştirmek için şunları yapmalısınız [kaydını](register-jea.md#unregistering-jea-configurations). Ardından, [yeniden kaydettirin](register-jea.md) bir güncelleştirilmiş oturum yapılandırma dosyası kullanarak JEA oturum yapılandırması.

## <a name="next-steps"></a>Sonraki adımlar

- [Bir JEA yapılandırmasını Kaydet](register-jea.md)
- [Yazar JEA rolleri](role-capabilities.md)
