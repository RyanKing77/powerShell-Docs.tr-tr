---
ms.date: 07/10/2019
keywords: Jea, PowerShell, güvenlik
title: JEA rol özellikleri
ms.openlocfilehash: 7191b90e198ffb539da6870a8ddc3e449ad9e8ae
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017961"
---
# <a name="jea-role-capabilities"></a>JEA rol özellikleri

Bir JEA uç noktası oluştururken, bir JEA oturumunda ne yapabileceğini tanımlayan bir veya daha fazla rol özelliği tanımlamanız gerekir. Rol yeteneği, Kullanıcı bağlamak için kullanılabilir hale getirilen tüm `.psrc` cmdlet 'leri, işlevleri, sağlayıcıları ve dış programları listeleyen uzantıya sahip bir PowerShell veri dosyasıdır.

## <a name="determine-which-commands-to-allow"></a>Hangi komutların izin olacağını belirle

Rol yetenek dosyası oluşturmanın ilk adımı, kullanıcıların hangi kullanıcılara erişmesi gerektiğini düşünmelidir. Gereksinim toplama işlemi biraz zaman alabilir, ancak önemli bir işlemdir. Kullanıcılara çok az cmdlet ve işleve erişim verilmesi, bunların işlerini almasını engelleyebilir. Çok fazla cmdlet ve işleve erişime izin verilmesi, kullanıcıların hedeflediğiniz ve güvenlik desteklemeyle yumuşyorundan daha fazla çalışmasına izin verebilir.

Bu işlem hakkında nasıl gittiğiniz, kuruluşunuza ve hedeflerinize göre değişir. Aşağıdaki ipuçları doğru yolda olduğunuzdan emin olmanıza yardımcı olabilir.

1. Kullanıcılarının işlerini yapmak için kullandığı komutları **belirler** . Bu, BT personelini incelemek, Otomasyon betikleri denetlemek ya da PowerShell oturum dökümünü ve günlüklerini çözümlemek içerebilir.
2. En iyi denetim ve JEA özelleştirme deneyimi için mümkün olduğunca, komut satırı araçlarının kullanımını PowerShell eşdeğerlerine **güncelleştirin** . Dış programlar yerel PowerShell cmdlet 'leri ve JEA işlevleri olarak kısıtlanmış olarak kısıtlanamaz.
3. Cmdlet 'lerin kapsamını yalnızca belirli parametrelere veya parametre değerlerine izin verecek şekilde **kısıtlayın** . Bu özellikle, kullanıcıların bir sistemin yalnızca bir bölümünü yönetmesi gereken durumlarda önemlidir.
4. JEA 'da kısıtlamak zor olan karmaşık komutları veya komutları değiştirmek için özel işlevler **oluşturun** . Karmaşık bir komutu sarmalayan veya ek doğrulama mantığı uygulayan basit bir işlev, Yöneticiler ve Son Kullanıcı basitliği için ek denetim sunabilir.
5. Kullanıcılarınızın veya Otomasyon hizmetlerinize sahip izin verilen komutların kapsamlı listesini **Test** edin ve gereken şekilde ayarlayın.

### <a name="examples-of-potentially-dangerous-commands"></a>Tehlikeli olabilecek komutların örnekleri

JEA uç noktasının, kullanıcının izinlerini yükseltmesine izin vermediğinden emin olmak için komutların dikkatli seçimi önemlidir.

> [!IMPORTANT]
> Bir JEA oturumunda Kullanıcı başarılı komutları için gereken önemli bilgiler genellikle yükseltilmiş ayrıcalıklarla çalıştırılır.

Aşağıdaki tabloda, kısıtlanmış olmayan bir durumda izin verildiğinde kötü amaçlı olarak kullanılabilecek komutların örnekleri verilmiştir. Bu kapsamlı bir liste değildir ve yalnızca bir uyarı başlangıç noktası olarak kullanılmalıdır.

|                                            Risk                                            |                                Örnek                                |                                                                              İlgili komutlar                                                                              |
| ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| JEA 'yı atlamak için bağlama Kullanıcı Yöneticisi ayrıcalıkları verme                                | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`                                                                                                        |
| Korumaları atlamak için kötü amaçlı yazılım, güvenlik açıkları veya özel betikler gibi rastgele kod çalıştırma | `Start-Process -FilePath '\\san\share\malware.exe'`                   | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob` |

## <a name="create-a-role-capability-file"></a>Rol yetenek dosyası oluşturma

[New-PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-6) cmdlet 'ini kullanarak yeni bir PowerShell rol yetenek dosyası oluşturabilirsiniz.

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

Rol için gerekli olan komutlara izin vermek için ortaya çıkan rol yetenek dosyası düzenlenmelidir. PowerShell yardım belgeleri, dosyayı nasıl yapılandırabilmeniz için birkaç örnek içerir.

### <a name="allowing-powershell-cmdlets-and-functions"></a>PowerShell cmdlet 'leri ve işlevlerine izin verme

Kullanıcıların PowerShell cmdlet 'lerini veya işlevlerini çalıştırmasını yetkilendirmek için, cmdlet 'ini veya işlev adını Visiblecmdlet 'Ler veya VisibleFunctions alanlarına ekleyin. Bir komutun bir cmdlet veya işlev olup olmadığından emin değilseniz, çıkışta `Get-Command <name>` **CommandType** özelliğini çalıştırabilir ve kontrol edebilirsiniz.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Bazen belirli bir cmdlet veya işlevin kapsamı kullanıcılarınızın ihtiyaçlarına göre çok geniş olabilir. Örneğin, bir DNS Yöneticisi, genellikle DNS hizmetini yeniden başlatmak için erişime ihtiyaç duyuyor. Çok kiracılı ortamlarda kiracıların self servis yönetim araçlarına erişimi vardır. Kiracılar kendi kaynaklarını yönetmeye sınırlı olmalıdır. Bu gibi durumlarda, cmdlet veya işlevden hangi parametrelerin açığa çıkarılabileceğini kısıtlayabilirsiniz.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}
```

Daha Gelişmiş senaryolarda, bir kullanıcının bu parametrelerle kullanabileceği değerleri de kısıtlamanız gerekebilir. Rol özellikleri, hangi girişe izin verileceğini belirleyen bir değer kümesi veya bir normal ifade deseninin tanımlamanızı sağlar.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> Kullanılabilir parametreleri kısıtlasanız bile [ortak PowerShell parametrelerine](/powershell/module/microsoft.powershell.core/about/about_commonparameters) her zaman izin verilir.
> Parametreleri Parametreler alanında açıkça listememelisiniz.

Aşağıdaki tabloda, görünür bir cmdlet veya işlevi özelleştirmek için kullanabileceğiniz çeşitli yollar açıklanmaktadır.
**Visiblecmdlet 'ler** alanında aşağıdan birini karıştırarak ve eşleştirebilirsiniz.

|                                           Örnek                                           |                                                             Kullanım örneği                                                              |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `'My-Func'` veya `@{ Name = 'My-Func' }`                                                      | Kullanıcının parametreler üzerinde herhangi bir `My-Func` kısıtlama olmadan çalışmasına izin verir.                                                      |
| `'MyModule\My-Func'`                                                                        | Kullanıcının parametrelerde kısıtlama olmadan modülden `My-Func` `MyModule` çalışmasına izin verir.                           |
| `'My-*'`                                                                                    | Kullanıcının fiil `My`ile herhangi bir cmdlet veya işlev çalıştırmasına izin verir.                                                                 |
| `'*-Func'`                                                                                  | Kullanıcının ad `Func`ile herhangi bir cmdlet veya işlev çalıştırmasına izin verir.                                                               |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`              | Kullanıcının `My-Func` `Param1` ve parametreleriyle`Param2` çalışmasına izin verir. Parametrelere herhangi bir değer sağlanabilir.          |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}` | Kullanıcının `My-Func` `Param1` parametresiyle çalışmasına izin verir. Parametreye yalnızca "değer1" ve "değer2" sağlanabilir.        |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`    | Kullanıcının `My-Func` `Param1` parametresiyle çalışmasına izin verir. "Contoso" ile başlayan herhangi bir değer parametreye sağlanabilir. |

> [!WARNING]
> En iyi güvenlik uygulamaları için, görünür cmdlet 'leri veya işlevleri tanımlarken joker karakter kullanılması önerilmez. Bunun yerine, her bir güvenilir komutu, aynı adlandırma şemasını paylaşan başka komutların istenmeden yetkilendirilmesini sağlamak için açıkça listelemelidir.

Aynı cmdlet veya işleve hem **ValidateModel** hem de **validateset** uygulayamazsınız.

Bunu yaparsanız, **ValidateModel** **validateset**'i geçersiz kılar.

**ValidateModel**hakkında daha fazla bilgi Için [Bu Hey göz atın *, komut dosyası* ](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/) işleme ve [PowerShell normal ifadeleri](/powershell/module/microsoft.powershell.core/about/about_regular_expressions) başvuru içeriği ' ne bakın.

### <a name="allowing-external-commands-and-powershell-scripts"></a>Dış komutlara ve PowerShell betiklerine izin verme

Kullanıcıların bir JEA oturumunda yürütülebilir dosyaları ve PowerShell betikleri (. ps1) çalıştırmasına izin vermek için, **Visibleexternalcommands** alanındaki her bir programa tam yolu eklemeniz gerekir.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Mümkün olduğunda, PowerShell cmdlet 'leri ve işlevleriyle izin verilen parametrelerin üzerinde denetiminiz olduğundan, yetkilendirdiğiniz herhangi bir dış yürütülebilir dosya için PowerShell cmdlet 'ini veya işlev eşlerini kullanmak için.

Birçok yürütülebilir dosya, geçerli durumu okumanızı ve sonra farklı parametreler sağlayarak değiştirmenizi sağlar.

Örneğin, bir sistemde barındırılan ağ paylaşımlarını yöneten bir dosya sunucusu yöneticisinin rolünü göz önünde bulundurun. Paylaşımları yönetmenin bir yolu kullanmaktır `net share`. Ancak, Kullanıcı ile `net group Administrators unprivilegedjeauser /add`yönetici ayrıcalıkları kazanmak için komutunu kullanabilmesi nedeniyle **net. exe** ' ye izin veriliyor. Daha güvenli bir seçenek, [Get-SmbShare](/powershell/module/smbshare/get-smbshare)öğesine izin vermek, aynı sonucu elde etmek, ancak daha sınırlı bir kapsama sahiptir.

Dış komutları bir JEA oturumunda kullanıcılara kullanılabilir hale getirmek için her zaman yürütülebilir dosyanın tüm yolunu belirtin. Bu, sistemde başka bir yerde bulunan benzer adlandırılmış ve olası kötü amaçlı programların yürütülmesini önler.

### <a name="allowing-access-to-powershell-providers"></a>PowerShell sağlayıcılarına erişime izin verme

Varsayılan olarak, JEA oturumlarında kullanılabilir PowerShell sağlayıcısı yoktur. Bu, bağlanan kullanıcıya bildirilen hassas bilgiler ve yapılandırma ayarları riskini azaltır.

Gerektiğinde, `VisibleProviders` komutunu kullanarak PowerShell sağlayıcılarına erişime izin verebilirsiniz. Sağlayıcıların tam listesi için çalıştırın `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

Dosya sistemine, kayıt defterine, sertifika deposuna veya diğer hassas sağlayıcılara erişim gerektiren basit görevler için Kullanıcı adına sağlayıcıyla birlikte çalışarak özel bir işlev yazmayı düşünün. JEA oturumunda bulunan işlevler, cmdlet 'ler ve dış programlar, JEA ile aynı kısıtlamalara tabi değildir. Varsayılan olarak herhangi bir sağlayıcıya erişebilirler. Ayrıca, bir JEA uç noktasından veya bu uç noktadan dosya kopyalarken [Kullanıcı sürücüsünü](session-configurations.md#user-drive) kullanmayı göz önünde bulundurun.

### <a name="creating-custom-functions"></a>Özel işlevler oluşturma

Son kullanıcılarınız için karmaşık görevleri basitleştirecek bir rol yetenek dosyasında özel işlevler yazabilirsiniz. Cmdlet parametre değerleri için gelişmiş doğrulama mantığına ihtiyacınız olduğunda özel işlevler de kullanışlıdır. **FunctionDefinitions** alanında basit işlevler yazabilirsiniz:

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
> Özel işlevlerinizin adını, JEA kullanıcıları tarafından çalıştırılabilmeleri için **visiblefunctions** alanına eklemeyi unutmayın.

Özel işlevlerin gövdesi (betik bloğu) sistem için varsayılan dil modunda çalışır ve JEA 'nın dil kısıtlamalarına tabi değildir. Bu, işlevlerin dosya sistemine ve kayıt defterine erişebileceği ve rol yetenek dosyasında görünür olmayan komutları çalıştırabileceği anlamına gelir. Parametreleri kullanırken rastgele kod çalıştırmadan kaçınmak için dikkatli olmanız. Kullanıcı girişini, gibi `Invoke-Expression`cmdlet 'lere doğrudan yönelmekten kaçının.

Yukarıdaki örnekte, tam modül adının (FQMN) `Microsoft.PowerShell.Utility\Select-Object` toplu `Select-Object`değer yerine kullanıldığını fark edersiniz.
Rol yetenek dosyalarında tanımlanan işlevler, var olan komutları kısıtlamak için JEA tarafından oluşturulan ara sunucu işlevlerini de içeren JEA oturumlarının kapsamına tabidir.

Varsayılan olarak, `Select-Object` nesneleri üzerinde rastgele Özellikler seçimine izin veren tüm Jea oturumlarında kısıtlanmış bir cmdlet 'dir. Kısıtlanmış `Select-Object` olmayan işlevleri kullanmak için, FQMN kullanarak tam uygulamayı açıkça istemeniz gerekir. Bir JEA oturumunda kısıtlanmış cmdlet, bir işlevden çağrıldığında aynı kısıtlamalara sahiptir. Daha fazla bilgi için bkz. [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence).

Birkaç özel işlev yazıyorsanız, bunları bir PowerShell betik modülüne koymak daha uygundur. Bu işlevleri, yerleşik ve üçüncü taraf modülleriyle yaptığınız gibi **visiblefunctions** alanını kullanarak Jea oturumunda görünür hale getirebilirsiniz.

Sekme tamamlama işleminin Jea oturumlarında düzgün çalışması için, `tabexpansion2` **visiblefunctions** listesine yerleşik işlevi eklemeniz gerekir.

## <a name="place-role-capabilities-in-a-module"></a>Rol yeteneklerini bir modüle yerleştirme

PowerShell 'in bir rol yetenek dosyası bulması için, PowerShell modülündeki bir **Rolecapabilities** klasöründe depolanması gerekir. Modül, `$env:PSModulePath` ortam değişkeninde yer alan herhangi bir klasörde depolanabilir, ancak bunu system32 içine veya güvenilmeyen, bağlanan kullanıcıların dosyaları değiştirebilecekleri bir klasöre yerleştirmemeniz gerekir. Aşağıda, `$env:ProgramFiles` yolda **contosojea** adlı temel bir PowerShell betik modülünün oluşturulmasına ilişkin bir örnek verilmiştir.

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

PowerShell modülleri hakkında daha fazla bilgi için bkz. [PowerShell modülünü anlama](/powershell/developer/windows-powershell).

## <a name="updating-role-capabilities"></a>Rol özellikleri güncelleştiriliyor

Ayarları dilediğiniz zaman güncelleştirmek için rol yetenek dosyasını düzenleyebilirsiniz. Rol özelliği güncelleştirildikten sonra başlatılan yeni JEA oturumları, düzeltilen özellikleri yansıtır.

Bu, rol yetenekleri klasörüne erişimin denetlenmesi için önemlidir. Rol yetenek dosyalarını yalnızca son derece güvenilen yöneticilerin değiştirmesine izin verilmelidir. Güvenilmeyen bir Kullanıcı rol yetenek dosyalarını değiştirebiliyorsanız, kendilerine kendi ayrıcalıklarını yükseltmesine izin veren cmdlet 'lere kolayca erişim izni verebilir.

Rol yeteneklerine erişimi kilitlemek isteyen yöneticiler için, yerel sistemin rol yetenek dosyalarına ve modülleri içeren okuma erişimine sahip olduğundan emin olun.

## <a name="how-role-capabilities-are-merged"></a>Rol özellikleri nasıl birleştirilir

Kullanıcılara bir JEA oturumu girdiklerinde [oturum yapılandırma dosyasındaki](session-configurations.md) tüm eşleşen rol özelliklerine erişim verilir. JEA, kullanıcıya rollerden herhangi biri tarafından izin verilen en fazla sayıda komuta izin vermesini sağlamaya çalışır.

### <a name="visiblecmdlets-and-visiblefunctions"></a>Visiblecmdlet 'ler ve VisibleFunctions

En karmaşık birleştirme mantığı, parametreleri ve parametre değerlerini JEA 'da sınırlı olabilecek cmdlet 'leri ve işlevleri etkiler.

Kurallar aşağıdaki gibidir:

1. Bir cmdlet yalnızca bir rolde görünür durumdaysa, geçerli parametre kısıtlamalarına sahip kullanıcı tarafından görülebilir.
2. Bir cmdlet birden fazla rolde görünür hale getiril, ve her rolün Cmdlet 'inde aynı kısıtlamalara sahip olması durumunda, cmdlet bu kısıtlamalara sahip kullanıcı tarafından görülebilir.
3. Bir cmdlet birden fazla rolde görünür hale getirilme ve her bir rol farklı bir parametre kümesine izin veriyorsa, cmdlet ve her rol için tanımlanan tüm parametreler kullanıcıya görünür.
   Bir rolün parametreler üzerinde kısıtlamaları yoksa, tüm parametrelere izin verilir.
4. Bir rol bir cmdlet parametresi için bir doğrulama kümesi veya doğrulama modelini tanımlıyorsa ve diğer rol parametreye izin veriyorsa ancak parametre değerlerini kısıtlamaz, doğrulama kümesi veya kalıp yok sayılır.
5. Bir doğrulama kümesi birden fazla rolde aynı cmdlet parametresi için tanımlandıysa, tüm doğrulama kümelerindeki tüm değerlere izin verilir.
6. Bir doğrulama deseni birden fazla rolde aynı cmdlet parametresi için tanımlanmışsa, desenlerden biriyle eşleşen herhangi bir değere izin verilir.
7. Doğrulama kümesi bir veya daha fazla rolde tanımlanmışsa ve bir doğrulama deseni aynı cmdlet parametresi için başka bir rolde tanımlanmışsa, doğrulama kümesi yok sayılır ve kural (6) kalan doğrulama desenleri için geçerlidir.

Rollerin bu kurallara göre nasıl birleştirildiğini gösteren bir örnek aşağıda verilmiştir:

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

### <a name="visibleexternalcommands-visiblealiases-visibleproviders-scriptstoprocess"></a>VisibleExternalCommands, Visibleadlarla, VisibleProviders, ScriptsToProcess

Rol yetenek dosyasındaki diğer tüm alanlar, bir dizi izin verilen dış komutlara, diğer adlara, sağlayıcılara ve başlangıç betiklerine eklenir. Tek bir rol özelliği ile kullanılabilen herhangi bir komut, diğer ad, sağlayıcı veya komut dosyası JEA kullanıcısı tarafından kullanılabilir.

Bir rol yeteneğinin ve cmdlet 'lerden/işlevlerden/komutlardan oluşan Birleşik sağlayıcıların sistem kaynaklarına yanlışlıkla erişmesini izin vermediği konusunda dikkatli olun.
Örneğin, bir rol `Remove-Item` cmdlet 'e izin veriyorsa ve başka bir `FileSystem` sağlayıcıya izin veriyorsa, bilgisayarınızda rastgele dosyaları silen bir Jea kullanıcısı riski vardır. Kullanıcıların etkili izinlerini tanımlama hakkında ek bilgi, [JEA makalesinde denetim](audit-and-report.md) altında bulunabilir.

## <a name="next-steps"></a>Sonraki adımlar

[Oturum yapılandırma dosyası oluşturma](session-configurations.md)
