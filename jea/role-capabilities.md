---
ms.date: 07/10/2019
keywords: jea, powershell, güvenlik
title: JEA rol özellikleri
ms.openlocfilehash: 7191b90e198ffb539da6870a8ddc3e449ad9e8ae
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726593"
---
# <a name="jea-role-capabilities"></a>JEA rol özellikleri

Bir JEA uç noktası oluştururken, birisi bir JEA oturumda neler yapabileceğini açıklayın bir veya daha fazla rol işlevleri tanımlamak gerekir. Bir PowerShell veri dosyasıyla rol özelliktir `.psrc` tüm cmdlet'ler, İşlevler, sağlayıcıları ve kullanıcıları bağlamak için kullanılabilir hale getirilir, dış programlarda listeler uzantısı.

## <a name="determine-which-commands-to-allow"></a>İzin vermek için hangi komutları belirleme

Hangi kullanıcıların erişmesi gereken rol özellik dosyası oluşturmanın ilk adımı ise. Gereksinimleri toplama işlemi biraz zaman alabilir, ancak önemli bir işlemdir. Çok az sayıda cmdlet'ler ve İşlevler kullanıcılara erişim verme bunları işin yapılması olmanızı engelleyebilir. Çok fazla cmdlet'ler ve İşlevler için erişimine yönelik ve, güvenlik tutum sergilemek zayıflatabilir çok daha fazlasını yapmasını kullanıcılar izin verebilirsiniz.

Bu işlem hakkında nasıl gittiğiniz, kuruluş ve hedeflerine bağlıdır. Aşağıdaki ipuçları, doğru yolda olduğunuzu sağlanmasına yardımcı olur.

1. **Tanımlamak** komutları kullanıcıların işlerini halletmek için kullanıyorsunuz. Bu, BT personeliniz araştırma, Otomasyon betikleri denetimi veya PowerShell oturumu dökümleri ve günlükleri çözümleme gerektirebilir.
2. **Güncelleştirme** PowerShell eşdeğeri komut satırı araçları, mümkün olduğunda, en iyi denetleme ve JEA özelleştirme deneyimini kullanın. Dış programlarda, yerel PowerShell cmdlet'leri ve jea işlevlerle hedefle olarak kısıtlayamaz.
3. **Kısıtlama** kapsamı yalnızca belirli bir parametre veya parametre değerlerini izin vermek için cmdlet'ler. Kullanıcılar yalnızca bir sistem bölümü yönetiyorsanız, bu özellikle önemlidir.
4. **Oluşturma** karmaşık komutlar ya da JEA içinde kısıtlamak zor olan komutları değiştirmek için özel işlevler. Karmaşık bir komut sarmalar veya ek doğrulama mantığını uygular, basit bir işlevi yöneticileri ve son kullanıcı kolaylık olması için ek denetim sunabilir.
5. **Test** kapsamlı kullanıcılar veya Otomasyon Hizmetleri, izin verilen komutların listesini ve gerektiği gibi ayarlayın.

### <a name="examples-of-potentially-dangerous-commands"></a>Potansiyel olarak tehlikeli olabilecek komutlar örnekleri

Komutları dikkatli seçimi JEA uç noktası kullanıcı izinlerini yükseltmesine izin vermeyen sağlamak önemlidir.

> [!IMPORTANT]
> Bir JEA oturumda kullanıcı successCommands için gereken önemli bilgileri genellikle yükseltilmiş ayrıcalıklarla çalıştırın.

Aşağıdaki tabloda izin veriliyorsa sınırlandırılmamış bir durumda kötü amaçla kullanılabilecek komutlar, örnekleri verilmektedir. Bu kapsamlı bir liste değildir ve yalnızca bir uyarı başlangıç noktası olarak kullanılmalıdır.

|                                            Risk                                            |                                Örnek                                |                                                                              İlgili komutları                                                                              |
| ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Bağlanan kullanıcının JEA atlamak için yönetici ayrıcalıkları verme                                | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`                                                                                                        |
| Kötü amaçlı yazılım, saldırılara veya korumaları atlamak için özel betikler gibi rastgele kod çalıştırma | `Start-Process -FilePath '\\san\share\malware.exe'`                   | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob` |

## <a name="create-a-role-capability-file"></a>Bir rol özelliği dosyası oluşturma

Yeni bir PowerShell rolü özelliği dosyasıyla oluşturabilirsiniz [yeni PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-6) cmdlet'i.

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

Elde edilen rol özellik dosyası, rol için gerekli komutları izin verecek şekilde düzenlenmelidir. PowerShell Yardım belgeleri dosyanın nasıl yapılandırabileceğiniz çeşitli örnekler içerir.

### <a name="allowing-powershell-cmdlets-and-functions"></a>PowerShell cmdlet'leri ve işlevleri izin verme

PowerShell cmdlet'lerini veya işlevleri çalıştırmak için Kullanıcıları yetkilendirmek için cmdlet veya işlev adı VisibleCmdlets veya VisibleFunctions alanları ekleyin. Bir cmdlet veya işlevi bir komut olup emin değilseniz, çalıştırabileceğiniz `Get-Command <name>` ve **CommandType** çıktıda özelliği.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Bazen belirli bir cmdlet veya işlev kapsamı için kullanıcılarınızın ihtiyaçlarını çok geniş olabilir. Bir DNS Yöneticisi, örneğin, DNS hizmetini yeniden başlatmak için büyük olasılıkla yalnızca gereksinimlerini erişin. Çok kiracılı ortamlarda, kiracılar Self Servis yönetim araçlarına erişebilirsiniz. Kiracıların kendi kaynaklarını yönetmek için sınırlı olmalıdır. Bu durumlarda cmdlet ya da işlev hangi parametreler sunulur kısıtlayabilirsiniz.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}
```

Daha gelişmiş senaryolarda, bir kullanıcı bu parametrelerle kullanabilir değerleri kısıtlamak gerekebilir. Rol işlevleri değerleri veya hangi girişine izin belirleyen bir normal ifade deseni kümesi tanımlamanıza olanak sağlar.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> [Ortak PowerShell parametrelerini](/powershell/module/microsoft.powershell.core/about/about_commonparameters) kullanılabilir parametrelerin kısıtlama olsa bile her zaman izin verilir.
> Siz açıkça bunları parametreler alanında listelenmemesi gerekir.

Aşağıdaki tabloda görünür cmdlet'ini veya işlev özelleştirebilirsiniz çeşitli yolları açıklar.
Karışık ve hiçbiriyle aşağıda içinde **VisibleCmdlets** alan.

|                                           Örnek                                           |                                                             Kullanım örneği                                                              |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `'My-Func'` veya `@{ Name = 'My-Func' }`                                                      | Çalıştırılacak verir `My-Func` parametreler üzerinde herhangi bir kısıtlama olmadan.                                                      |
| `'MyModule\My-Func'`                                                                        | Çalıştırılacak verir `My-Func` modülünden `MyModule` parametreler üzerinde herhangi bir kısıtlama olmadan.                           |
| `'My-*'`                                                                                    | Herhangi bir cmdlet veya işlevi için fiili ile çalıştırmak kullanıcının `My`.                                                                 |
| `'*-Func'`                                                                                  | Herhangi bir cmdlet veya işlev isim ile çalıştırmak kullanıcının `Func`.                                                               |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`              | Çalıştırılacak verir `My-Func` ile `Param1` ve `Param2` parametreleri. Parametreleri herhangi bir değer sağlanabilir.          |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}` | Çalıştırılacak verir `My-Func` ile `Param1` parametresi. Yalnızca "Value1" ve "Value2" parametresi sağlanabilir.        |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`    | Çalıştırılacak verir `My-Func` ile `Param1` parametresi. "Contoso" ile başlayan herhangi bir değer parametresi sağlanabilir. |

> [!WARNING]
> En iyi güvenlik uygulamaları bu joker karakterler görünür cmdlet'leri veya işlevlerini tanımlarken kullanmak için önerilmez. Bunun yerine, aynı adlandırma şeması paylaşan başka hiçbir komut istemeden yetkinizin olduğundan emin olmak için güvenilen her komut açıkça listelemelidir.

Her ikisi de uygulanamıyor bir **ValidatePattern** ve **ValidateSet** aynı cmdlet'i veya işlev.

Bunu yaparsanız, **ValidatePattern** geçersiz kılmalar **ValidateSet**.

Hakkında daha fazla bilgi için **ValidatePattern**, kullanıma [bu *Hey, Scripting Guy!* sonrası](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/) ve [PowerShell normal ifadeler](/powershell/module/microsoft.powershell.core/about/about_regular_expressions)başvuru içeriği.

### <a name="allowing-external-commands-and-powershell-scripts"></a>Dış komutları ve PowerShell betiklerini izin verme

Bir JEA oturumda yürütülebilir dosyaları ve PowerShell betikleri (.ps1) çalıştırmak kullanıcılara izin vermek için tam yolu her programda eklemek zorunda **VisibleExternalCommands** alan.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Mümkünse, PowerShell kullanmak için cmdlet veya işlevi dış yürütülebilir dosyaları, bu yana yetkilendirmek için PowerShell cmdlet'leri ve işlevlerine izin parametreleri üzerinde denetim eşdeğerleri.

Birçok yürütülebilir dosyaları, geçerli durumu okuyun ve ardından farklı parametreler sağlayarak değiştirin olanak tanır.

Örneğin, bir sistemde barındırılan ağ paylaşımlara yöneten bir dosya sunucu yöneticisi rolünü göz önünde bulundurun. Paylaşımları yönetme tek bir yolu `net share`. Ancak, izin verme **net.exe** kullanıcı komutunu yönetici ayrıcalıklarıyla elde etmek için kullanabilirsiniz, çünkü tehlikelidir `net group Administrators unprivilegedjeauser /add`. Daha fazla güvenli seçenek sağlamaktır [Get-SmbShare](/powershell/module/smbshare/get-smbshare), aynı sonucu elde eder, ancak çok fazla kapsam sınırlıdır.

Her zaman dış komutları kullanılabilir kullanıcılara bir JEA oturumda yaparken, yürütülebilir dosyanın tam yolunu belirtin. Bu, başka bir yerde sistemde bulunan benzer şekilde adlandırılmış ve olası kötü amaçlı programlar yürütülmesini engeller.

### <a name="allowing-access-to-powershell-providers"></a>PowerShell sağlayıcıları için erişime izin verme

Varsayılan olarak, PowerShell yok sağlayıcıları JEA oturumlarında kullanılabilir. Bu, hassas bilgiler ve yapılandırma ayarları için bağlanan kullanıcı ifşa riskini azaltır.

Gerekli olduğunda kullanarak PowerShell sağlayıcılarının erişime izin verebilir `VisibleProviders` komutu. Sağlayıcıları tam listesi için çalıştırma `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

Dosya sistemine erişim gerektiren basit görevleri için kayıt defteri, sertifika deposuna ya da diğer hassas sağlayıcıları, sağlayıcı ile kullanıcı adına çalışan özel bir işlev yazarken göz önünde bulundurun. İşlevler, cmdlet'leri ve dış programlarda JEA oturumunda kullanılabilir JEA olarak aynı kısıtlamalara tabi değildir. Bunlar, varsayılan olarak herhangi bir sağlayıcı erişebilir. Ayrıca kullanmayı [kullanıcı sürücü](session-configurations.md#user-drive) ne zaman ya da bir JEA uç noktasından dosyaları kopyalama gereklidir.

### <a name="creating-custom-functions"></a>Özel bir işlev oluşturma

Karmaşık görevleri, son kullanıcılarınız için basitleştirmek için bir rol özelliği dosyasındaki özel işlevler yazabilirsiniz. Gelişmiş Doğrulama mantığı cmdlet'i parametre değerlerini gerektirdiğinde özel işlevler de yararlıdır. Basit işlevler yazabilirsiniz **FunctionDefinitions** alan:

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending |
            Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> Özel işlevlerinizi adını eklemek unutmayın **VisibleFunctions** JEA kullanıcılar tarafından çalışma alanı.

Özel işlev gövdesi (betik bloğu) sistemi için varsayılan dil modda çalışır ve JEA'ın dil kısıtlamalarına tabi değildir. Bu işlevler dosya sistemi ve kayıt defteri erişebilir ve rol özelliği dosyasında görünür hale olmayan komutları çalıştırın, anlamına gelir. Rastgele kod parametrelerini kullanırken çalıştırmaktan kaçınmak için dikkatli olun. Yöneltme kullanıcı girişi cmdlet'leri gibi doğrudan önlemek `Invoke-Expression`.

Yukarıdaki örnekte, dikkat tam modül adı (FQMN) `Microsoft.PowerShell.Utility\Select-Object` toplu yerine kullanılan `Select-Object`.
Rol özelliği dosyalarında tanımlanan işlevleri proxy işlevleri içeren hala kapsamını JEA oturumları tabi olan mevcut komutları sınırlamak için JEA oluşturur.

Varsayılan olarak, `Select-Object` rastgele özellik seçimi nesnelerde izin vermeyen bir kısıtlanmış cmdlet tüm JEA oturumlardaki. Sınırlandırılmamış kullanılacak `Select-Object` işlevleri, açıkça FQMN kullanarak tam uygulama istemelisiniz. Bir JEA oturumda kısıtlanmış herhangi bir cmdlet'i bir işlevden çağrıldığında aynı kısıtlamalara sahiptir. Daha fazla bilgi için [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence).

Bazı özel işlevler yazıyorsanız, bir PowerShell Betiği modülde koymak daha kolaydır. Bu işlevlerin görünür JEA oturumu kullanarak yaptığınız **VisibleFunctions** yerleşik ve üçüncü taraf modülleriyle gibi alan.

İçin sekmesinde tamamlama JEA oturumlarında, düzgün çalışması için yerleşik işlev içermelidir `tabexpansion2` içinde **VisibleFunctions** listesi.

## <a name="place-role-capabilities-in-a-module"></a>Rol işlevleri bir modülde yerleştirin

Bir rol özelliği dosyayı bulmak PowerShell için sırada bu saklanmalıdır bir **RoleCapabilities** klasörde bir PowerShell modülü. Modülü dahil herhangi bir klasörde depolanan `$env:PSModulePath` ortam değişkeni, ancak bunu System32 veya bir klasöre yerleştirdiğiniz olmamalıdır burada güvenilmeyen, kullanıcıların bağlanma dosyaları değiştirebilirsiniz. Adlı temel bir PowerShell Betiği modülü oluşturma örneği aşağıda verilmiştir **ContosoJEA** içinde `$env:ProgramFiles` yolu.

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest.
# At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

PowerShell modülleri hakkında daha fazla bilgi için bkz: [bir PowerShell modülü anlama](/powershell/developer/windows-powershell).

## <a name="updating-role-capabilities"></a>Rol özellikleri güncelleştiriliyor

Herhangi bir zamanda ayarları güncelleştirmek için bir rol özelliği dosyayı düzenleyebilirsiniz. Rol özelliği güncelleştirildikten sonra kullanmaya yeni herhangi JEA oturumları düzeltilmiş özellikleri yansıtır.

Rol özellikleri klasörüne erişimi denetleme bu kadar önemlidir nedeni budur. Yalnızca yüksek oranda güvenilir Yöneticiler rolü dosyaları değiştirmek için izin verilmelidir. Güvenilmeyen bir kullanıcının rol özellik dosyaları değiştirirseniz, kolayca kendilerini erişim kendi ayrıcalıklarını yükseltme olanak tanıyan cmdlet'lerinde verebilirsiniz.

Rol işlevleri erişimi kilitleme isteyen yöneticiler için yerel sistem içeren modüller ve rol özellik dosyaları okuma erişimi olduğundan emin olun.

## <a name="how-role-capabilities-are-merged"></a>Rol işlevleri nasıl birleştirilir

Kullanıcılar, tüm eşleşen rol özelliklere erişim verilir [oturum yapılandırma dosyası](session-configurations.md) JEA oturumu girdikleri zaman. JEA en esnek herhangi bir rol tarafından izin verilen komut kümesini kullanıcıya vermek çalışır.

### <a name="visiblecmdlets-and-visiblefunctions"></a>VisibleCmdlets ve VisibleFunctions

En karmaşık birleştirme mantığı, cmdlet'ler ve İşlevler, kendi parametreleri ve parametre değerlerini JEA içinde sınırlı olabilir etkiler.

Kurallar aşağıdaki gibidir:

1. Bir cmdlet yalnızca tek bir role görünür hale gelir, tüm geçerli parametresi kısıtlamalarıyla kullanıcıya görünür olur.
2. Bir cmdlet birden fazla rolde görünür hale gelir ve her bir rolü cmdlet aynı kısıtlamalar varsa, cmdlet bu kısıtlamaları olan kullanıcı tarafından görülebilir.
3. Bir cmdlet birden fazla rolde görünür hale gelir ve farklı bir dizi parametrenin her rolü sağlar, cmdlet ve her rol arasında tanımlanan tüm parametreleri kullanıcıya görünür.
   Bir rol parametreler üzerinde kısıtlama yoksa, tüm parametreleri izin verilir.
4. Bir rol bir doğrulama kümesi veya bir cmdlet parametresi doğrulama desenini tanımlar ve diğer rol parametresi izin verir, ancak parametre değerlerini kısıtlamaz, doğrulama kümesi veya deseni göz ardı edilir.
5. Doğrulama kümesi aynı cmdlet parametresi birden fazla rol için tanımlanmış olması durumunda, tüm doğrulama kümelerinden tüm değerlerine izin verilir.
6. Doğrulama düzeni için birden fazla rol aynı cmdlet parametresinde tanımlanır desenleri hiçbiriyle tüm değerlere izin verilir.
7. Doğrulama kümesi bir veya daha fazla rollerinde tanımlanır ve başka bir rol aynı cmdlet parametresi için bir doğrulama deseni tanımlanır, doğrulama kümesi göz ardı edilir ve kalan doğrulama desenleri için kural (6) uygular.

Rolleri bu kurallara göre nasıl birleştirilmiş bir örnek aşağıdadır:

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service
#   is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use
#   ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

### <a name="visibleexternalcommands-visiblealiases-visibleproviders-scriptstoprocess"></a>VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess

Diğer rol özellik dosyası tüm alanlar, izin verilen dış komutları, diğer adlar, sağlayıcıları ve başlatma komut dosyaları toplu kümesine eklenir. Komutu, diğer adı, sağlayıcı veya betik bir rol özelliği kullanılabilir JEA kullanıcı tarafından kullanılabilir.

Bir sağlayıcıdan birleştirilmiş bir dizi emin olmak dikkatli olun rol özellik ve işlevleri/cmdlet'leri/komutları başka bir izin verme kullanıcıların yanlışlıkla sistem kaynaklarına erişim.
Örneğin, bir rol izin veriyorsa `Remove-Item` cmdlet ve diğer sağlar `FileSystem` sağlayıcısı olan bilgisayarınızda rastgele dosyalar silinirken bir JEA kullanıcının risk altında. Kullanıcıların geçerli izinler tanımlama hakkında daha fazla bilgi bulunabilir [JEA denetim](audit-and-report.md) makalesi.

## <a name="next-steps"></a>Sonraki adımlar

[Oturum yapılandırma dosyası oluşturma](session-configurations.md)
