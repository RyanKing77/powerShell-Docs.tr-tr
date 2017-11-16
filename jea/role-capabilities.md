---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea, powershell, güvenlik"
title: "JEA rol özellikleri"
ms.openlocfilehash: 10f5f390daccbb012be6ee7272041e777810ee12
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="jea-role-capabilities"></a>JEA rol özellikleri

> Uygulandığı öğe: Windows PowerShell 5.0

JEA uç noktası oluştururken, "tanımlayan bir veya daha fazla rol özellikleri" tanımlamanız gerekir *ne* birisi JEA oturumda yapabilirsiniz.
Bir rol özelliği bir uzantıya sahip olan tüm cmdlet'ler, İşlevler, sağlayıcıları ve kullanıcıları bağlamak için kullanılabilir hale getirmek dış programları listeler .psrc PowerShell veri dosyasıdır.

Bu konuda JEA kullanıcılarınız için bir PowerShell Rol Yetenek dosyasının nasıl oluşturulacağı açıklanmaktadır.

## <a name="determine-which-commands-to-allow"></a>İzin vermek için hangi komutların belirleme

Bir rol özelliği dosyası oluştururken, ilk adım ne rolüne atanan kullanıcıların erişmesi ise.
Bu gereksinimleri toplama işlemi biraz zaman alabilir, ancak çok önemli bir işlemdir.
Çok az cmdlet'ler ve İşlevler kullanıcıların erişim verip bunları işlerinin yapılmasını alma engelleyebilir.
Çok fazla cmdlet'ler ve İşlevler izin veren güvenlik tutum sergilemek zayıflatmanın örtük yönetici ayrıcalıklarını amaçlanan birden fazla yapılması kullanıcılara yol açabilir.

Aşağıdaki ipuçları doğru yolda olduğunuz sağlamaya yardımcı olabilir ancak bu işlem hakkında nasıl gidin, kuruluş ve hedeflerini bağlıdır.

1. **Tanımlamak** komutları kullanıcıların işlerini halletmek için kullanıyorsunuz. Bu, BT personeliniz araştırma, Otomasyon betikleri denetleme veya PowerShell oturumu dökümleri veya günlüklerini çözümleme gerektirebilir.
2. **Güncelleştirme** PowerShell eşdeğerlerine komut satırı araçlarını, mümkün olduğunda, en iyi denetim ve JEA özelleştirme deneyimini kullanın. Dış programları yerel PowerShell cmdlet'leri ve JEA işlevleri olarak granularly olarak kısıtlaması olamaz.
3. **Kısıtlama** yalnızca gereken belirli parametreleri veya parametre değerlerini izin verirseniz cmdlet'leri kapsamı. Kullanıcıların yalnızca bir sistem parçası yönetebileceği olacaksa, bu özellikle önemlidir.
4. **Oluşturma** karmaşık komutları ya da JEA içinde sınırlamak zor olan komutları değiştirmek için özel işlevler. Karmaşık bir komut sarmalar veya ek doğrulama mantığını uygular basit bir işlev yöneticileri ve son kullanıcı basitleştirmek için ek denetim sunabilir.
5. **Test** izin verilen komutları kullanıcılara ve/veya Otomasyon ile kapsamlı listesi Hizmetleri ve gerektiği gibi ayarlayın.

JEA oturumunda komutları genellikle yönetici (veya tersi durumda yükseltilmiş) ile çalışma ayrıcalıkları olduğunu unutmamak önemlidir.
Kullanılabilir komutları dikkatli seçimi JEA endpoint bağlanan kullanıcının izinlerini yükseltmesine izin verme sağlamak önemlidir.
Aşağıda izin veriyorsa kısıtlanmamış bir durumda amaçla kullanılabilir komutlar, bazı örnekler verilmiştir.
Bu kapsamlı bir liste değil ve dikkat gerektiren bir başlangıç noktası olarak kullanılması unutmayın.

### <a name="examples-of-potentially-dangerous-commands"></a>Potansiyel olarak tehlikeli olabilecek komutları örnekleri

Riski | Örnek | İlgili komutları
-----|---------|-----------------
Bağlanan kullanıcının JEA atlamak için yönetici ayrıcalıkları verme | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`
Kötü amaçlı yazılım, açıkları veya korumaları atlamak için özel betikler gibi rastgele bir kodu çalıştırma | `Start-Process -FilePath '\\san\share\malware.exe'` | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`

## <a name="create-a-role-capability-file"></a>Bir rol özelliği dosyası oluşturma

Yeni bir PowerShell Rol Yetenek dosya ile oluşturabileceğiniz [yeni PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet'i.

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

Sonuçta elde edilen Rol Yetenek dosyasını bir metin Düzenleyicisi'nde açılır ve rolü için istenen komutlarına izin vermek için değiştirilebilir.
PowerShell Yardım belgelerine dosya nasıl yapılandırabileceğiniz çeşitli örnekler içerir.

### <a name="allowing-powershell-cmdlets-and-functions"></a>PowerShell cmdlet'leri ve işlevleri izin verme

PowerShell cmdlet'lerini veya İşlevler çalıştırmak için Kullanıcıları yetkilendirmek için cmdlet veya işlev adı VisbibleCmdlets veya VisibleFunctions alanları ekleyin.
Bir cmdlet veya işlevi bir komut olup emin değilseniz, çalıştırabilirsiniz `Get-Command <name>` ve çıkışı "CommandType" özelliğini denetleyin.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Bazen belirli cmdlet veya işlevi kapsamını kullanıcılarınızın ihtiyaçları için çok geniş.
DNS Yöneticisi Örneğin, büyük olasılıkla yalnızca gereksinimlerini DNS hizmetini yeniden erişim sağlar.
Kiracılar Self Servis Yönetim Araçları erişimi burada verilen bir çok kiracılı ortamında, kiracılar kendi kaynakları ile yönetme için sınırlı olmalıdır.
Bu durumlarda, cmdlet veya işlevi hangi parametreler sunulur kısıtlayabilirsiniz.

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

Daha gelişmiş senaryolarda, bu parametrelerden biri sağlayabilir hangi değerlerin kısıtlamak gerekebilir.
Rol özellikleri, izin verilen değerler ya da belirli bir giriş izin verilip verilmediğini belirlemek için değerlendirilen bir normal ifade deseni tanımlamanıza olanak sağlar.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> [Ortak PowerShell parametrelerini](https://technet.microsoft.com/en-us/library/hh847884.aspx) kullanılabilir parametrelerin kısıtlıyor olsa bile her zaman izin verilir.
> Siz açıkça bunları parametreler alanında listelenmemesi gerekir.

Aşağıdaki tablo görünür cmdlet veya işlevi özelleştirebilirsiniz çeşitli yolları açıklanmaktadır.
Karışık ve herhangi biriyle eşleşen aşağıda VisibleCmdlets alan.

Örnek                                                                                      | Kullanım örneği
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
`'My-Func'` veya `@{ Name = 'My-Func' }`                                                       | Kullanıcının çalıştırmasına izin verir `My-Func` parametreleri herhangi bir kısıtlamanın olmadığı.
`'MyModule\My-Func'`                                                                         | Kullanıcının çalıştırmasına izin verir `My-Func` modülden `MyModule` parametreleri herhangi bir kısıtlamanın olmadığı.
`'My-*'`                                                                                     | Kullanıcının herhangi bir cmdlet veya işlevi ile fiili çalıştırmasına izin verir `My`.
`'*-Func'`                                                                                   | Kullanıcının herhangi bir cmdlet veya işlevi ile isim çalıştırmasına izin verir `Func`.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | Kullanıcının çalıştırmasına izin verir `My-Func` ile `Param1` ve/veya `Param2` parametreleri. Herhangi bir değer parametreleri sağlanabilir.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | Kullanıcının çalıştırmasına izin verir `My-Func` ile `Param1` parametresi. Yalnızca "Değer1" ve "Değer2" parametresi sağlanabilir.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | Kullanıcının çalıştırmasına izin verir `My-Func` ile `Param1` parametresi. "Contoso" ile başlayan herhangi bir değer parametresi sağlanabilir.


> [!WARNING]
> İçin en iyi güvenlik uygulamaları, onu görünen cmdlet'lerini veya İşlevler tanımlarken joker karakterler kullanmak için önerilmez.
> Bunun yerine, aynı adlandırma şeması paylaşan başka hiçbir komut istemeden yetkili olduğundan emin olmak için güvenilen her komutun açık olarak listelenmelidir.

Aynı cmdlet veya işlevi bir ValidatePattern ve ValidateSet uygulanamıyor.

Bunu yaparsanız, ValidatePattern ValidateSet geçersiz kılar.

ValidatePattern hakkında daha fazla bilgi için kullanıma [bu *Hey, Scripting Guy!* sonrası](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) ve [PowerShell normal ifadeler](https://technet.microsoft.com/en-us/library/hh847880.aspx) başvuru içeriği.

### <a name="allowing-external-commands-and-powershell-scripts"></a>Dış komutları ve PowerShell betikleri izin verme

Yürütülebilir dosyalar ve PowerShell betiklerini (.ps1) JEA oturumunda çalıştırmak kullanıcılara izin vermek için tam yolunu VisibleExternalCommands alandaki her bir program eklemeniz gerekir.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Mümkünse, PowerShell cmdlet ya da işlevin eşdeğerlerini parametreleri PowerShell cmdlet'leri/olan işlevlere izin üzerinde denetime sahip olduğundan, yetki dış yürütülebilir dosyaları kullanmak önerilir.

Birçok yürütülebilir dosyaları, geçerli durumu okuma ve yalnızca farklı parametreler sağlayarak değiştirmek olanak tanır.

Örneğin, hangi ağ paylaşımlarına yerel makine tarafından barındırılan denetlemek isteyen bir dosya sunucu yöneticisi rol göz önünde bulundurun.
Kontrol etmenin bir yolu kullanmaktır `net share`.
Ancak, yönetici, yönetici ayrıcalıklarıyla kazanmak için komutunu kolayca kullanabilirsiniz çünkü net.exe çok tehlikeli izin vererek `net group Administrators unprivilegedjeauser /add`.
Daha iyi bir yaklaşım izin vermektir [Get-SmbShare](https://technet.microsoft.com/en-us/library/jj635704.aspx) aynı sonucu veren ancak çok daha kısıtlı kapsama sahip.

Dış komutları kullanılabilir kullanıcılara JEA oturumda yaparken, her zaman başka bir yerde sistemine yerleştirilmiş bir benzer ada (ve büyük olasılıkla malicous) programı yerine yürütülmedi sağlamak için yürütülebilir dosyanın tam yolunu belirtin.

### <a name="allowing-access-to-powershell-providers"></a>PowerShell sağlayıcıları erişmesine izin verme

Varsayılan olarak, hiçbir PowerShell sağlayıcıları JEA oturumlarında kullanılabilir.

Öncelikle hassas bilgileri ve bağlanan kullanıcının duyurulmuş yapılandırma ayarları riskini azaltmak için budur.

Gerekli olduğunda kullanarak PowerShell sağlayıcılarının erişmesine izin vermek `VisibleProviders` komutu.
Sağlayıcıları tam listesi için çalıştırın `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

Dosya sistemi, kayıt defteri, sertifika deposu veya diğer hassas sağlayıcıları erişim gerektiren Basit görevler için kullanıcı adına sağlayıcı ile çalışır, özel bir işlev yazma düşünebilirsiniz.
İşlevler, cmdlet'ler ve JEA oturumunda kullanılabilir dış programları JEA olarak aynı kısıtlamalara tabi değildir – varsayılan olarak herhangi bir sağlayıcıyı erişebilir.
Ayrıca, kullanmayı [kullanıcı sürücü](session-configurations.md#user-drive) zaman dosyaları kopyalanıyor/JEA uç noktasından gereklidir.

### <a name="creating-custom-functions"></a>Özel işlevler oluşturma

Karmaşık görevleri, son kullanıcılarınız için basitleştirmek için bir rol özelliği dosyasındaki özel işlevler yazabilirsiniz.
Gelişmiş doğrulama mantığını cmdlet parametre değerleri için gerektiğinde özel işlevler de yararlıdır.
Basit işlevleri yazabilirsiniz **FunctionDefinitions** alan:

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


Özel işlevler gövdesi (betik bloğu) sistemi için varsayılan dili modunda çalışır ve JEA'ın dil kısıtlamaları tabi değildir.
Bu işlevler dosya sistemini ve kayıt defteri erişebilir ve Rol Yetenek dosyasında görünür oluşturulmayan komutları çalıştırmak, anlamına gelir.
Parametreleri kullanarak çalıştırmak için rastgele kod izin vererek kaçınmak için dikkatli olun ve yöneltme kullanıcı girişi cmdlet'leri gibi doğrudan kaçının `Invoke-Expression`.

Yukarıdaki örnekte göreceksiniz tam modül adı (FQMN) `Microsoft.PowerShell.Utility\Select-Object` yerine kestirme kullanılan `Select-Object`.
Rol Yetenek dosyalarında tanımlanan proxy işlevleri içeren hala kapsamını JEA oturumları tabi işlevlerdir mevcut komutları sınırlamak için JEA oluşturur.

Select-Object varsayılan olarak, tüm JEA oturumlarda nesneler üzerinde isteğe bağlı özellikler seçmenizi izin vermeyen kısıtlanmış cmdlet ' dir.
Kısıtlanmamış Select-Object işlevlerini kullanmak için açıkça FQMN belirterek tam uygulamayı istemeniz gerekir.
Herhangi bir kısıtlanmış cmdlet'i JEA oturumunda PowerShell'in uygun olarak bir işlevden çağrıldığında aynı davranışı sergiler [komut öncelik](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).

Çok sayıda özel işlevler yazıyorsanız, bunları yerleştirmek daha kolay olabilir bir [PowerShell betik modülündeki](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).
Daha sonra bu işlevler yerleşik ve üçüncü taraf modüllerle gibi VisibleFunctions alanını kullanarak JEA oturumunda görünür yapabilirsiniz.

## <a name="place-role-capabilities-in-a-module"></a>Bir modüle rol özellikleri yerleştirin

Bir rol özelliği dosyayı bulmak PowerShell sırada bir PowerShell modülü "RoleCapabilities" klasöründe depolanmalıdır.
Modül dahil herhangi bir klasör depolanabilir `$env:PSModulePath` ortam değişkeni, ancak bu System32 (yerleşik modülleri için ayrılmış) veya bir klasöre yerleştirdiğiniz değil burada güvenilmeyen, kullanıcılara bağlanan dosyaları değiştirebilir.
Adlı basit bir PowerShell komut dosyası modülü oluşturma örneği aşağıdadır *ContosoJEA* "Program Files" yolunda.

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

Bkz: [bir PowerShell modülü anlama](https://msdn.microsoft.com/en-us/library/dd878324.aspx) PowerShell modülleri, modül bildirimleri ve PSModulePath ortam değişkeni hakkında daha fazla bilgi.

## <a name="updating-role-capabilities"></a>Rol özellikleri güncelleştiriliyor


Yalnızca Rol Yetenek dosyasına değişiklikleri kaydederek herhangi bir anda bir rol özelliği dosya güncelleştirebilirsiniz.
Rol Yetenek güncelleştirildikten sonra başlatılan tüm yeni JEA oturumların yeniden düzenlenen özellikleri yansıtır.

Rol özellikleri klasörüne erişimi denetleme çok önemli nedeni budur.
Yalnızca yüksek oranda güvenilir Yöneticiler rolü yetenek dosyaları değiştirmek mümkün olması gerekir.
Güvenilmeyen bir kullanıcı rolü yetenek dosyaları değiştirirseniz bunlar kolayca kendilerini erişim bunları ayrıcalıklarını yükseltmek izin veren cmdlet'leri verebilirsiniz.


Rol özellikleri erişimi kilitleme isteyen yöneticiler için yerel sistem içeren modüller ve Rol Yetenek dosya okuma erişimi olduğundan emin olun.

## <a name="how-role-capabilities-are-merged"></a>Rol özellikleri nasıl birleştirilir

Kullanıcıların olanağı verilir birden çok rol özellikleri erişimi rolü eşlemelerin bağlı olarak bir JEA oturumu girdiğinizde [oturum yapılandırma dosyası](session-configurations.md).
Bu gerçekleştiğinde, kullanıcıya vermek JEA çalışır *en fazla izne sahip* herhangi bir rol tarafından izin verilen komutlar kümesi.

**VisibleCmdlets ve VisibleFunctions**

Cmdlet'leri ve bunların parametrelerini ve parametre değerlerini JEA içinde sınırlı olabilir İşlevler, en karmaşık birleştirme mantığı etkiler.

Kurallar aşağıdaki gibidir:

1. Bir cmdlet yalnızca bir rol görünür duruma getirildiyse, tüm geçerli parametre kısıtlamalarına sahip kullanıcıya görünür olacaktır.
2. Bir cmdlet birden fazla rolünde görünür hale gelir ve her bir rolü cmdlet aynı kısıtlamalar varsa, cmdlet bu kısıtlamalarına sahip kullanıcıya görünür olacaktır.
3. Bir cmdlet birden fazla rolünde görünür hale gelir ve farklı bir parametre kümesi her rolü sağlar, cmdlet ve her rolünde tanımlanan parametrelerin tümüne kullanıcıya görünür. Bir rol parametrelerindeki kısıtlamalar yoksa, tüm parametreleri izin verilir.
4. Doğrulama kümesi veya doğrulama düzeni bir cmdlet parametresi için bir rol tanımlar ve diğer rol parametresi verir, ancak parametre değerlerini sınırlamalarına değil, doğrulama kümesi veya desen yoksayılacak.
5. Doğrulama kümesi aynı cmdlet parametresi birden çok rolü için tanımlanmış olması durumunda, tüm doğrulama kümelerinden tüm değerleri izin verilir.
6. Birden fazla rol aynı cmdlet parametresinde için bir doğrulama düzeni tanımlanmışsa desenleri hiçbiriyle herhangi bir değere izin verilir.
7. Doğrulama kümesi bir veya daha fazla rollerinde tanımlandı ve başka bir rol aynı cmdlet parametresi için bir doğrulama düzeni tanımlanan doğrulama kümesi gözardı edilir ve kural (6) için kalan doğrulama modelleri uygular.

Roller bu kurallara göre nasıl birleştirilir örneği aşağıdadır:

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

# Resulting permisisons for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored becuase of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```



**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**

Rol Yetenek dosyasındaki diğer tüm alanlar yalnızca toplu bir izin verilen dış komutları, diğer adlar, sağlayıcıları ve başlatma komut dosyaları kümesine eklenir.
Komut, diğer ad, sağlayıcı veya komut dosyası bir rol özelliği de kullanılabilir JEA kullanıcı için kullanılabilir.

Bir sağlayıcılardan birleştirilmiş bir dizi emin olmak dikkatli olun rol özellik ve işlevleri/cmdlet'leri/komutları başka bir izin verme bağlanan kullanıcıların istenmeyen sistem kaynaklarına erişim.
Örneğin, bir rol izin veriyorsa `Remove-Item` cmdlet ve diğer izin veren `FileSystem` sağlayıcısı olduğunuz risk rastgele dosyaları bilgisayarınıza silme JEA kullanıcı.
Kullanıcıların etkili izinleri tanımlama hakkında ek bilgiler bulunabilir [JEA konu denetim](audit-and-report.md).

## <a name="next-steps"></a>Sonraki adımlar

- [Oturum yapılandırma dosyası oluşturma](session-configurations.md)

