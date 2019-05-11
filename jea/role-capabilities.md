---
ms.date: 06/12/2017
keywords: jea, powershell, güvenlik
title: JEA rol özellikleri
ms.openlocfilehash: 528b41c0e2ffdcfed3251fb0f714c649e7290761
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229557"
---
# <a name="jea-role-capabilities"></a>JEA rol özellikleri

> Şunun için geçerlidir: Windows PowerShell 5.0

Bir JEA uç noktası oluştururken, "tanımlayan bir veya daha fazla rol özellikleri" tanımlamanız gerekir *ne* birisi bir JEA oturumda yapabilirsiniz.
Bir rol özelliği, tüm cmdlet'ler, İşlevler, sağlayıcıları ve kullanıcıları bağlamak için kullanılabilir hale dış programlarda listeleyen .psrc uzantısına sahip bir PowerShell veri dosyasıdır.

Bu konuda JEA kullanıcılarınız için bir PowerShell rol özellik dosyası oluşturmayı açıklar.

## <a name="determine-which-commands-to-allow"></a>İzin vermek için hangi komutları belirleme

Bir rol özelliği dosyası oluştururken ilk adım, hangi rolü atanmış kullanıcılar erişmesi göz önünde bulundurun sağlamaktır.
Bu gereksinimleri toplama işlemi biraz zaman alabilir, ancak çok önemli bir işlemdir.
Çok az sayıda cmdlet'ler ve İşlevler kullanıcılara erişim verme bunları işin yapılması olmanızı engelleyebilir.
Çok fazla cmdlet'ler ve İşlevler için erişime izin verme, güvenlik tutum sergilemek zayıflatmanın örtük yönetici ayrıcalıklarını istenenden daha yapılması kullanıcılara yol açabilir.

Aşağıdaki ipuçları, doğru yolda olduğunuzu sağlamaya yardımcı olabilir ancak bu işlem hakkında nasıl gittiğiniz, kuruluş ve hedefleri bağlıdır.

1. **Tanımlamak** komutları kullanıcıların işlerini halletmek için kullanıyorsunuz. Bu, BT personeliniz araştırma, Otomasyon betikleri denetimi veya PowerShell oturumu dökümleri ya da günlükleri çözümleme gerektirebilir.
2. **Güncelleştirme** PowerShell eşdeğerlerine komut satırı araçları, mümkün olduğunda, en iyi denetleme ve JEA özelleştirme deneyimini kullanın. Dış programlarda, yerel PowerShell cmdlet'leri ve jea işlevlerle hedefle olarak kısıtlayamaz.
3. **Kısıtlama** cmdlet'ler belirli bir parametre veya parametre değerleri için yalnızca gerekli izin kapsamı. Kullanıcılar yalnızca bir sistemin parçası yönetmek gerekiyorsa bu özellikle önemlidir.
4. **Oluşturma** karmaşık komutlar ya da JEA içinde kısıtlamak zor olan komutları değiştirmek için özel işlevler. Karmaşık bir komut sarmalar veya ek doğrulama mantığını uygular, basit bir işlevi yöneticileri ve son kullanıcı kolaylık olması için ek denetim sunabilir.
5. **Test** kapsamlı kullanıcılara ve/veya Otomasyon ile verilen komutların listesini Hizmetleri ve gerektiği gibi ayarlayın.

Bir JEA oturumunda komutları genellikle yönetici (veya başka türlü yükseltilmiş) ile çalışma ayrıcalıkları olduğunu unutmamak önemlidir.
Kullanılabilir komutları dikkatli seçimi JEA uç noktası bağlanan kullanıcının izinlerini yükseltmesine izin vermiyor sağlamak önemlidir.
Aşağıda bazı örnekler izin veriliyorsa sınırlandırılmamış bir durumda kötü amaçla kullanılabilecek komutlar verilmektedir.
Bu kapsamlı bir liste değildir ve yalnızca bir uyarı başlangıç noktası olarak kullanılması gerektiğini unutmayın.

### <a name="examples-of-potentially-dangerous-commands"></a>Potansiyel olarak tehlikeli olabilecek komutlar örnekleri

Risk | Örnek | İlgili komutları
-----|---------|-----------------
Bağlanan kullanıcının JEA atlamak için yönetici ayrıcalıkları verme | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`
Kötü amaçlı yazılım, saldırılara veya korumaları atlamak için özel betikler gibi rastgele kod çalıştırma | `Start-Process -FilePath '\\san\share\malware.exe'` | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`

## <a name="create-a-role-capability-file"></a>Bir rol özelliği dosyası oluşturma

Yeni bir PowerShell rolü özelliği dosyasıyla oluşturabilirsiniz [yeni PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet'i.

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

Sonuçta elde edilen rol özelliği dosyasını bir metin Düzenleyicisi'nde açılır ve rolü için istenen komutlarına izin vermek için değiştirilebilir.
PowerShell Yardım belgeleri dosyanın nasıl yapılandırabileceğiniz çeşitli örnekler içerir.

### <a name="allowing-powershell-cmdlets-and-functions"></a>PowerShell cmdlet'leri ve işlevleri izin verme

PowerShell cmdlet'lerini veya işlevleri çalıştırmak için Kullanıcıları yetkilendirmek için cmdlet veya işlev adı VisibleCmdlets veya VisibleFunctions alanları ekleyin.
Bir cmdlet veya işlevi bir komut olup emin değilseniz, çalıştırabileceğiniz `Get-Command <name>` ve çıktıda "CommandType" özelliğini denetleyin.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Bazen belirli bir cmdlet veya işlev kapsamı için kullanıcılarınızın ihtiyaçlarını çok geniş olabilir.
Bir DNS Yöneticisi, örneğin, DNS hizmetini yeniden başlatmak için büyük olasılıkla yalnızca gereksinimlerini erişin.
Burada, kiracılar Self Servis Yönetimi Araçları erişim izni verilen çok kiracılı ortam kiracılar ile kendi kaynaklarını yönetmek için sınırlı olmalıdır.
Bu durumlarda cmdlet ya da işlev hangi parametreler sunulur kısıtlayabilirsiniz.

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

Daha gelişmiş senaryolarda, birisi sağlayabilirsiniz hangi değerlerin bu parametrelere sınırlamak gerekebilir.
Rol işlevleri izin verilen değerler ya da belirli bir giriş izin verilip verilmeyeceğini belirlemek için değerlendirilen bir normal ifade deseni kümesi tanımlamanıza olanak sağlar.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> [Ortak PowerShell parametrelerini](https://technet.microsoft.com/library/hh847884.aspx) kullanılabilir parametrelerin kısıtlama olsa bile her zaman izin verilir.
> Siz açıkça bunları parametreler alanında listelenmemesi gerekir.

Aşağıdaki tabloda görünür cmdlet'ini veya işlev özelleştirebilirsiniz çeşitli yolları açıklar.
Karışık ve hiçbiriyle aşağıda VisibleCmdlets alan.

Örnek                                                                                      | Kullanım örneği
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
`'My-Func'` veya `@{ Name = 'My-Func' }`                                                       | Çalıştırılacak verir `My-Func` parametreler üzerinde herhangi bir kısıtlama olmadan.
`'MyModule\My-Func'`                                                                         | Çalıştırılacak verir `My-Func` modülünden `MyModule` parametreler üzerinde herhangi bir kısıtlama olmadan.
`'My-*'`                                                                                     | Herhangi bir cmdlet veya işlevi için fiili ile çalıştırmak kullanıcının `My`.
`'*-Func'`                                                                                   | Herhangi bir cmdlet veya işlev isim ile çalıştırmak kullanıcının `Func`.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | Çalıştırılacak verir `My-Func` ile `Param1` ve/veya `Param2` parametreleri. Parametreleri herhangi bir değer sağlanabilir.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | Çalıştırılacak verir `My-Func` ile `Param1` parametresi. Yalnızca "Value1" ve "Value2" parametresi sağlanabilir.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | Çalıştırılacak verir `My-Func` ile `Param1` parametresi. "Contoso" ile başlayan herhangi bir değer parametresi sağlanabilir.

> [!WARNING]
> En iyi güvenlik uygulamaları bu joker karakterler görünür cmdlet'leri veya işlevlerini tanımlarken kullanmak için önerilmez.
> Bunun yerine, aynı adlandırma şeması paylaşan başka hiçbir komut istemeden yetkinizin olduğundan emin olmak için güvenilen her komut açıkça listelemelidir.

Aynı cmdlet veya işlevi bir ValidatePattern ve ValidateSet uygulanamıyor.

Bunu yaparsanız, ValidatePattern ValidateSet geçersiz kılar.

ValidatePattern hakkında daha fazla bilgi için kullanıma [bu *Hey, Scripting Guy!* sonrası](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) ve [PowerShell normal ifadeler](https://technet.microsoft.com/library/hh847880.aspx) başvuru içeriği.

### <a name="allowing-external-commands-and-powershell-scripts"></a>Dış komutları ve PowerShell betiklerini izin verme

Bir JEA oturumda yürütülebilir dosyaları ve PowerShell betikleri (.ps1) çalıştırmak kullanıcılara izin vermek için VisibleExternalCommands alandaki her bir program için tam yolu eklemeniz gerekir.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Mümkünse, PowerShell cmdlet/işlevi eşdeğerleri parametreleri PowerShell cmdlet'leri/olan işlevlere izin üzerinde denetime sahip olduğundan, yetkilendirme dış yürütülebilir dosyaları kullanmak önerilir.

Birçok yürütülebilir dosyaları, hem geçerli durumu okuyun ve ardından farklı parametreler sağlayarak değiştirin olanak tanır.

Örneğin, hangi ağ paylaşımlara yerel makine tarafından barındırılan denetlemek isteyen bir dosya sunucusu yöneticisi rolünü göz önünde bulundurun.
Denetlenecek tek bir yolu `net share`.
Ancak, yönetici, yönetici ayrıcalıklarıyla elde etmek için komut kolayca kullanabilir olduğundan net.exe çok tehlikeli izin vererek `net group Administrators unprivilegedjeauser /add`.
İzin vermek için daha iyi bir yaklaşım olan [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) aynı sonucu veren, ancak çok daha sınırlı kapsamı vardır.

Dış komutları kullanılabilir kullanıcılara bir JEA oturumda yaparken, her zaman başka bir sistem üzerinde yerleştirilen benzer ada (ve kötü amaçlı olabilecek) bir program yerine Yürütülmeyen emin olmak için yürütülebilir dosyanın tam yolunu belirtin.

### <a name="allowing-access-to-powershell-providers"></a>PowerShell sağlayıcıları için erişime izin verme

Varsayılan olarak, PowerShell yok sağlayıcıları JEA oturumlarında kullanılabilir.

Bu hassas bilgiler ve yapılandırma ayarları için bağlanan kullanıcı ifşa riskini azaltmak için öncelikli olarak yapılır.

Gerekli olduğunda kullanarak PowerShell sağlayıcılarının erişime izin verebilir `VisibleProviders` komutu.
Sağlayıcıları tam listesi için çalıştırma `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

Dosya sistemi, kayıt defteri, sertifika deposu veya diğer hassas sağlayıcıları erişmesi Basit görevler için kullanıcı adına sağlayıcısı ile çalıştığından, özel bir işlev yazarken düşünebilirsiniz.
İşlevler, cmdlet'leri ve JEA oturumunda kullanılabilir olan dış programları JEA olarak aynı kısıtlamalara tabi değildir; varsayılan olarak herhangi bir sağlayıcı erişebilir.
Ayrıca kullanmayı [kullanıcı sürücü](session-configurations.md#user-drive) zaman dosyaları kopyalamak için buralardan bir JEA uç noktası gereklidir.

### <a name="creating-custom-functions"></a>Özel bir işlev oluşturma

Karmaşık görevleri, son kullanıcılarınız için basitleştirmek için bir rol özelliği dosyasındaki özel işlevler yazabilirsiniz.
Gelişmiş Doğrulama mantığı cmdlet'i parametre değerlerini gerektirdiğinde özel işlevler de yararlıdır.
Basit işlevler yazabilirsiniz **FunctionDefinitions** alan:

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> Özel işlevlerinizi adını eklemek unutmayın **VisibleFunctions** JEA kullanıcılar tarafından çalışma alanı.

Özel işlev gövdesi (betik bloğu) sistemi için varsayılan dil modda çalışır ve JEA'ın dil kısıtlamalarına tabi değildir.
Bu işlevler dosya sistemi ve kayıt defteri erişebilir ve rol özelliği dosyasında görünür oluşturulmayan komutları çalıştırın, anlamına gelir.
Rastgele kod parametrelerini kullanırken çalıştırılmasına izin vererek kaçınmak için dikkatli ve cmdlet'ler gibi doğrudan yöneltme kullanıcı girişini engellemek `Invoke-Expression`.

Yukarıdaki örnekte, görürsünüz (FQMN) tam modül adı `Microsoft.PowerShell.Utility\Select-Object` toplu yerine kullanılan `Select-Object`.
Rol özelliği dosyalarında tanımlanan işlevleri proxy işlevleri içeren hala kapsamını JEA oturumları tabi olan mevcut komutları sınırlamak için JEA oluşturur.

Select-Object nesneler üzerinde isteğe bağlı özellikler seçmenizi izin vermeyen kısıtlanmış cmdlet'i tüm JEA oturumlarda bir varsayılan davranıştır.
Sınırlandırılmamış Select-Object işlevleri kullanmak için açıkça FQMN belirterek tam uygulamayı istemeniz gerekir.
Bir JEA oturumda kısıtlanmış herhangi bir cmdlet'i PowerShell'in ayarlarına uygun olarak bir işlev çağrıldığında aynı davranışı sergiler [komut öncelik](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).

Birçok özel işlev yazıyorsanız, bunları yerleştirmek daha kolay olabilir bir [PowerShell betik modülündeki](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx).
Daha sonra bu işlevleri yerleşik ve üçüncü taraf modülleriyle gibi VisibleFunctions alanını kullanarak JEA oturumdaki görünür yapabilirsiniz.

İçin sekmesinde tamamlama JEA oturumlarında, düzgün çalışması için yerleşik işlev içermelidir `tabexpansion2` içinde **VisibleFunctions** listesi.

## <a name="place-role-capabilities-in-a-module"></a>Rol işlevleri bir modülde yerleştirin

Bir rol özelliği dosyayı bulmak PowerShell sırada bir PowerShell modülü "RoleCapabilities" klasöründe depolanmalıdır.
Modül içindeki herhangi bir klasörde depolanan `$env:PSModulePath` ortam değişkeni, ancak System32 (yerleşik modülleri için ayrılmıştır) veya bir klasöre yerleştirmelisiniz değil burada güvenilmeyen, kullanıcıların bağlanma dosyaları değiştirebilir.
Adlı temel bir PowerShell Betiği modülü oluşturma örneği aşağıda verilmiştir *ContosoJEA* "Program Files" yolda.

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

Bkz: [bir PowerShell modülü anlama](https://msdn.microsoft.com/library/dd878324.aspx) PowerShell modülleri, modül bildirimleri ve PSModulePath ortam değişkeni hakkında daha fazla bilgi.

## <a name="updating-role-capabilities"></a>Rol özellikleri güncelleştiriliyor

Değişiklikleri yalnızca Rol özelliği dosyasına kaydederek, bir rol özelliği dosyası herhangi bir zamanda güncelleştirebilirsiniz.
Rol özelliği güncelleştirildikten sonra kullanmaya yeni herhangi JEA oturumları düzeltilmiş özellikleri yansıtır.

Rol özellikleri klasörüne erişimi denetleme bu kadar önemlidir nedeni budur.
Yalnızca yüksek oranda güvenilir Yöneticiler rolü dosyaları değiştirmek mümkün olması gerekir.
Güvenilmeyen bir kullanıcının rol özellik dosyaları değiştirebilirsiniz, bunlar kolayca kendilerini erişim cmdlet'leri için bunları ayrıcalıklarını yükseltmek izin verebilirsiniz.

Rol işlevleri erişimi kilitleme isteyen yöneticiler için yerel sistem içeren modüller ve rol özellik dosyaları okuma erişimi olduğundan emin olun.

## <a name="how-role-capabilities-are-merged"></a>Rol işlevleri nasıl birleştirilir

Kullanıcı rolü eşlemelerin bağlı olarak bir JEA oturumu girdikleri zaman birden çok rol özelliklere erişim verilebilir [oturum yapılandırma dosyası](session-configurations.md).
Bu durumda kullanıcıya vermek JEA çalışır *en esnek* herhangi bir rol tarafından izin verilen komutları kümesi.

**VisibleCmdlets ve VisibleFunctions**

En karmaşık birleştirme mantığı, cmdlet'ler ve İşlevler, kendi parametreleri ve parametre değerlerini JEA içinde sınırlı olabilir etkiler.

Kurallar aşağıdaki gibidir:

1. Bir cmdlet yalnızca tek bir role görünür duruma getirildiyse, tüm geçerli parametresi kısıtlamalarıyla kullanıcıya görünür olacaktır.
2. Bir cmdlet birden fazla rolde görünür hale gelir ve her bir rolü cmdlet aynı kısıtlamalar varsa, cmdlet bu kısıtlamaları olan kullanıcıya görünür olacaktır.
3. Bir cmdlet birden fazla rolde görünür hale gelir ve farklı bir dizi parametrenin her rolü sağlar, cmdlet ve her rol arasında tanımlanan parametrelerin tümü kullanıcıya görünür olacaktır. Bir rol parametreler üzerinde kısıtlama yoksa, tüm parametreleri izin verilir.
4. Bir rol bir doğrulama kümesi veya bir cmdlet parametresi doğrulama desenini tanımlar ve diğer rol parametresi izin verir, ancak parametre değerlerini kısıtlamaz, doğrulama kümesi veya deseni yoksayılacak.
5. Doğrulama kümesi aynı cmdlet parametresi birden fazla rol için tanımlanmış olması durumunda, tüm doğrulama kümelerinden tüm değerleri izin verilir.
6. Doğrulama düzeni için birden fazla rol aynı cmdlet parametresinde tanımlanmazsa, desenleri hiçbiriyle tüm değerlere izin verilir.
7. Doğrulama kümesi bir veya daha fazla rollerinde tanımlanır ve başka bir rol aynı cmdlet parametresi için bir doğrulama deseni tanımlanır, doğrulama kümesi göz ardı edilir ve kalan doğrulama desenleri için kural (6) uygular.

Rolleri bu kurallara göre nasıl birleştirilmiş bir örnek aşağıdadır:

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**

Diğer rol özellik dosyası tüm alanlar yalnızca izin verilen dış komutları, diğer adlar, sağlayıcıları ve başlatma komut dosyaları toplu kümesine eklenir.
Komutu, diğer adı, sağlayıcı veya betik bir rol özelliği kullanılabilir JEA kullanıcılar için uygun olacaktır.

Bir sağlayıcıdan birleştirilmiş bir dizi emin olmak dikkatli olun rol özellik ve işlevleri/cmdlet'leri/komutları başka bir izin verme bağlanan kullanıcıların yanlışlıkla sistem kaynaklarına erişim.
Örneğin, bir rol izin veriyorsa `Remove-Item` cmdlet ve diğer sağlar `FileSystem` sağlayıcısı olan bilgisayarınızda rastgele dosyalar silinirken bir JEA kullanıcının risk altında.
Kullanıcıların geçerli izinler tanımlama hakkında daha fazla bilgi bulunabilir [JEA konu denetim](audit-and-report.md).

## <a name="next-steps"></a>Sonraki adımlar

- [Oturum yapılandırma dosyası oluşturma](session-configurations.md)
