---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: Kaynak yazma denetim listesi
ms.openlocfilehash: 76d9fecca8618fcc178975465f45cda0d0e04064
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="resource-authoring-checklist"></a>Kaynak yazma denetim listesi
Bu denetim listesini yeni bir DSC kaynağı yazarken en iyi yöntemler bir listedir.
## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a>.Psd1 dosya ve schema.mof her kaynak için kaynak modülü içerir
Kaynağınız doğru yapısına sahip ve tüm gerekli dosyaları içeren denetleyin. Her kaynak modül .psd1 dosyası içermelidir ve her bileşik olmayan kaynak schema.mof dosya sahip olmalıdır. Şema içermeyen kaynaklar tarafından listelenmez **Get-DscResource** ve kullanıcıların IntelliSense kodu bu modüller karşı ISE'de yazarken kullanmak mümkün olmayacak.
Parçasıdır xRemoteFile kaynak dizin yapısı, [xPSDesiredStateConfiguration kaynak Modülü](https://github.com/PowerShell/xPSDesiredStateConfiguration), aşağıdaki gibi görünür:


```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a>Kaynak ve şema doğru ##
Kaynak şemasını doğrulayın (*. schema.mof) dosyası. Kullanabileceğiniz [DSC kaynak Tasarımcısı](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) geliştirmenizi ve test şemanızı yardımcı olacak.
Olduğundan emin olun:
- Özellik türleri doğru (dize, sayısal değerleri kabul özelliklerini örn kullanmayın, bunun yerine uint32 diğer sayısal türler kullanmalısınız)
- Özellik öznitelikleri doğru olarak belirtilir: ([anahtarı], [gerekli], [yazma], [okuma])
- [Anahtar] olarak işaretlenecek şemasında en az bir parametre içeriyor
- özelliği olmayan bir arada herhangi biri ile birlikte [okuma]: [gerekli], [anahtarı], [yazma]
- Birden çok niteleyicileri [dışında oku] belirtilmişse [anahtarı] öncelik kazanır
- Varsa [yazma] ve [gerekli] belirtilen sonra [gerekli] önceliğe
- ValueMap uygun yerlerde belirtilmiştir

Örnek:
```
[Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
```

- Kolay ad belirtilir ve DSC adlandırma kurallarına onaylar

Örnek: ```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```

- Her alanı anlamlı bir açıklama içeriyor. PowerShell GitHub deposuna iyi örnek, aşağıdaki gibi olan [. xRemoteFile schema.mof](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)

Ayrıca, kullanmanız gereken **Test xDscResource** ve **Test xDscSchema** cmdlet'leri [DSC kaynak Tasarımcısı](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) kaynak ve şema otomatik olarak doğrulanamadı:
```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```
Örneğin:
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a>Kaynak hatasız yükler ##
Kaynak modülü başarıyla yüklü olup olmadığını denetleyin.
Bu el ile çalıştırarak elde edilebilir `Import-Module <resource_module> -force ` ve hiçbir hata oluştuğunu onaylayarak veya göre test Otomasyonu yazma. İkinci durumunda, bu yapıyı test durumunuzda izleyebilirsiniz:
```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```
## <a name="resource-is-idempotent-in-the-positive-case"></a>Idempotent pozitif durumda kaynaktır
DSC kaynakları temel özelliklerini idempotence olması biridir. Bu, birden çok kez bu kaynak içeren bir DSC yapılandırma uygulama her zaman aynı sonucu elde edecek olduğunu anlamına gelir. Örneğin, aşağıdaki dosya kaynağı içeren bir yapılandırma oluşturuyoruz varsa:
```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```
İlk kez uyguladıktan sonra dosya sınama.txt C:\test klasöründeki görüntülenmelidir. Ancak, aynı yapılandırmaya sahip sonraki çalıştırır (örn. hiçbir kopya sınama.txt dosyasının oluşturulmalıdır) makinenin durumunu değiştirmemelisiniz.
Bir kaynak art arda çağırabilir ıdempotent olduğundan emin olmak için **kümesi TargetResource** kaynak doğrudan test veya çağrı **başlangıç DscConfiguration** birden çok kez uçtan uca test yaparken. Sonuç sonra her çalıştırılışında aynı olması gerekir.


## <a name="test-user-modification-scenario"></a>Test kullanıcı değişiklik senaryosu ##
Makinenin durumunu değiştirme ve DSC yeniden çalıştırma olduğunu doğrulayabilirsiniz **kümesi TargetResource** ve **Test TargetResource** düzgün. Almanız gereken adımlar şunlardır:
1.  İstenilen durumda değil kaynak başlayın.
2.  Kaynağınız ile çalışma yapılandırması
3.  Doğrulama **Test DscConfiguration** True değerini döndürür
4.  İstenen durumdan yapılandırılmış öğeyi değiştirin
5.  Doğrulama **Test DscConfiguration** döndürür yanlış kayıt defteri kaynak kullanımına daha somut bir örnek şudur:
1.  Kayıt defteri anahtarı istenilen durumda değil başlayın
2.  Çalıştırma **başlangıç DscConfiguration** istenilen durumda koyun ve doğrulamak için bir yapılandırmayla geçirir.
3.  Çalıştırma **Test DscConfiguration** ve doğru döndürdüğü doğrulayın
4.  İstenilen durumda olmaması anahtarının değerini değiştirme
5.  Çalıştırma **Test DscConfiguration** ve false döndürdüğü doğrulayın
6.  Get-TargetResource işlevselliği Get-DscConfiguration kullanılarak doğrulandı

Get-TargetResource kaynağın geçerli durumuyla ayrıntılarını döndürmelidir. Get-DscConfiguration yapılandırmayı uyguladıktan sonra arama ve çıkış doğru makinenin geçerli durumunu yansıtır doğrulama testi emin olun. Bu alandaki sorunları başlangıç DscConfiguration çağrılırken görünmez beri ayrı ayrı test etmek önemlidir.

## <a name="call-getsettest-targetresource-functions-directly"></a>Çağrı **Get/Set/Test-TargetResource** doğrudan işlevleri ##

Test emin olun **Get/Set/Test-TargetResource** , kaynak doğrudan çağırma ve beklendiği gibi çalıştığını doğrulama uygulanan işlevler.

## <a name="verify-end-to-end-using-start-dscconfiguration"></a>Uçtan uca kullanarak doğrulayın **başlangıç DscConfiguration** ##

Sınama **Get/Set/Test-TargetResource** işlevlerini doğrudan çağırma tarafından önemlidir, ancak bu şekilde tüm sorunları bulunacaktır. Testinizin kullanarak önemli bir bölümü durmalısınız **başlangıç DscConfiguration** veya çekme sunucusunda. Aslında, kullanıcıların bu tür testleri önemini daha düşük olmayan şekilde kaynak nasıl kullanacağını budur.
Olası sorunlar türleri:
- DSC Aracısı hizmeti olarak çalıştığından kimlik bilgisi/oturum farklı davranabilir.  Burada herhangi bir özellik uçtan uca mutlaka test edin.
- Hataları çıktı tarafından **başlangıç DscConfiguration** çağrılırken görüntülenen olanlar farklı olabilir **kümesi TargetResource** doğrudan işlev.

## <a name="test-compatability-on-all-dsc-supported-platforms"></a>Test uyumluluk tüm DSC üzerinde desteklenen platformlar ##
Kaynak tüm DSC desteklenen platformlarda çalışmalıdır (Windows Server 2008 R2 ve daha yeni). En son WMF (Windows Management Framework) DSC en son sürümünü almak için işletim sistemine yükleyebilir. Kaynağınız bazı bu platformlar tarafından tasarım çalışmazsa, belirli bir hata iletisi döndürülmelidir. Ayrıca, kaynak, aradığınız cmdlet'leri belirli makinede mevcut olup olmadığını denetler emin olun. Windows Server 2012, çok sayıda bile WMF yüklü Windows Server 2008R2 üzerinde kullanılabilir değil yeni cmdlet'ler eklenmiştir.

## <a name="verify-on-windows-client-if-applicable"></a>Windows istemcisinde (varsa) doğrulayın ##
Yaygın bir test boşluk yalnızca, Windows server sürümlerinde kaynak doğruluyor. Birçok kaynağa ayrıca istemci SKU'larında çalışması için tasarlanmış, sizin durumunuzda true ise, bu platformlarda test unutmayın şekilde.
## <a name="get-dscresource-lists-the-resource"></a>Get-DSCResource kaynak listeleri ##
Modül dağıttıktan sonra Get-DscResource çağırma diğerlerinin yanı sıra, kaynak sonucunda listelenmelidir. Kaynağınız listede bulamazsanız, bu kaynak mevcut için o schema.mof dosya emin olun.
## <a name="resource-module-contains-examples"></a>Kaynak modülü örnekleri içerir ##
Başkalarının yardımcı olacak oluşturma nitelikli örnekler nasıl kullanılacağını anlayın. Özellikle çok sayıda kullanıcı örnek kod belgeleri davran beri bu, çok önemlidir.
- İlk olarak, en az – modülüyle eklenecek örnekler belirlemeniz gerekir, kaynak için en önemli kullanım örneklerini kapsamalıdır:
- Temel uçtan uca örnek ideal olarak, modül bir uçtan uca senaryo için birlikte çalışmak için gereken çeşitli kaynaklar içeriyorsa, ilk olacaktır.
- İlk örnek çok basit--nasıl kaynaklarınızı (örn. yeni bir VHD oluşturma) küçük yönetilebilir yığınlar kullanmaya başlama
- Sonraki örnekleri (örn. bir VM VM değiştirme VM kaldırma bir VHD'den oluşturma) Bu örnekleri oluşturmak ve gerekir (örn. bir VM ile dinamik bellek oluşturma) gelişmiş işlevselliği Göster
- Örnek yapılandırmaları parametreli (tüm değerleri yapılandırmaya parametre olarak geçirilen ve sabit kodlanmış değerler olmalıdır):
```powershell
configuration Sample_xRemoteFile_DownloadFile
{
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
}
```
- Örnek komut dosyası sonunda gerçek değerlerle yapılandırma çağırmak nasıl (out açıklamalı) örneği dahil etmek için iyi bir uygulamadır.
Örneğin, yukarıdaki yapılandırmada UserAgent belirtmek için en iyi yolu olduğunu mutlaka açık değil:

`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` Bu durumda bir yorum yapılandırmasının hedeflenen yürütme açıklık getirebilir:
```
<#
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>
```
- Her örneğin ne yaptığını açıklayan kısa bir açıklama ve parametreleri anlamını yazma.
- Örnekler, kaynak için en önemli senaryolarını kapsamak ve varsa eksik, hiçbir şey Tümünü Yürüt ve makine istenilen durumda put doğrulayın emin olun.

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a>Hata iletileri anlamak ve kullanıcıların sorunlarını gidermenize yardımcı olmak kolay ##
İyi hata iletileri olmalıdır:
- : Hata iletileri büyük sorun yoktur genellikle yoksa, bu nedenle bunlar bulunmadığından emin olun.
- Kolay anlaşılır: İnsan okunabilir, Hayır belirsiz hata kodları
- Kesin: tam olarak sorunun ne olduğunu açıklar
- Yapıcı: Öneri sorunu gidermeye yönelik
- Yumuşak: nedenlerle kullanıcı ya da bunları eşitleyerek hatalı yapma uçtan uca senaryolarda hataları doğrulayın emin yok (kullanarak **başlangıç DscConfiguration**), kaynak işlevlerini doğrudan çalıştırırken döndürülen olanlardan farklı olabilir.

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a>Günlük iletilerini kolay anlaşılır ve bilgilendirici (dahil – ayrıntılı, – hata ayıklama hem de ETW günlükleri) ##
Kaynak tarafından yüzdelik günlükleri anlama ve kullanıcıya değeri sağlamak kolay olduğundan emin olun. Kaynakları kullanıcı için yararlı olabilecek tüm bilgileri çıkış, ancak daha fazla günlükleri değil her zaman daha iyi. Artıklık önlemek ve gerekir içermeyen veri çıktısı ek değer sağlamanız – birisi aradıklarını bulmak için günlük girişlerini yüzlerce Git yapmayın. Elbette, hiçbir günlük değil Bu sorun için kabul edilebilir bir çözüm ya da.

Test edilirken de ayrıntılı çözümleyebilir ve hata ayıklama günlüklerini (çalıştırarak **başlangıç DscConfiguration** ile – ayrıntılı ve – anahtarları uygun şekilde hata ayıklama), yanı ETW günlükleri olarak. DSC ETW günlükleri görmek için Olay Görüntüleyici'ye gidin ve şu klasörü açın: uygulamaları ve Hizmetleri - Microsoft - Windows - istenen durum yapılandırması.  Varsayılan olarak var. işletimsel kanal olabilir, ancak analitik etkinleştirdiğinizden emin olun ve kanallar yapılandırma çalıştırmadan önce hata ayıklama.
Analitik/Debug kanalları etkinleştirmek için aşağıdaki komut dosyası çalıştırabilirsiniz:
```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```
## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a>Kaynak uygulama sabit kodlanmış yolları içermiyor ##
Özellikle bu bunlar dil olduğunu varsayarsak kaynak uygulamasında hiçbir sabit kodlanmış yol olmadığından emin olun (en-us), veya kullanılabilir sistem değişkenleri olduğunda.
Kaynağınız belirli yollar erişmesi gerekirse, ortam değişkenleri diğer makinelerde farklı olabileceği yerine cmdlet'e kod yolu kullanın.

Örnek:

Onun yerine:
```
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
 ```
Şunu yazabilirsiniz:
```
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```
## <a name="resource-implementation-does-not-contain-user-information"></a>Kaynak uygulaması kullanıcı bilgisi içermiyor ##
E-posta adlarını, hesap bilgilerini ya kodda kişilerin adlarını olmadığından emin olun.
## <a name="resource-was-tested-with-validinvalid-credentials"></a>Kaynağın geçerli/geçersiz kimlik bilgileri ile test edilmiştir ##
Kaynağınız parametre olarak bir kimlik bilgisi sürerse:
- Yerel Sistem (veya uzak kaynaklar için bilgisayar hesabı) erişimi olmadığında kaynak çalıştığını doğrulayın.
- Belirtilen kimlik bilgileriyle kaynak works Al ayarlayın ve sınayın doğrulayın
- Kaynağınız paylaşımları erişirse, gibi desteklemeniz gereken tüm çeşitleri test edin:
  - Standart windows paylaşımları.
  - DFS paylaşımları.
  - SAMBA paylaşımları (Linux desteklemek istiyorsanız,.)

## <a name="resource-does-not-require-interactive-input"></a>Kaynak etkileşimli giriş gerektirmez ##
**Get/Set/Test-TargetResource** işlevleri otomatik olarak yürütülüp ve kullanıcının herhangi bir yürütme aşamasında giriş için beklemesi gereken değil (örneğin kullanılamaz **Get-Credential** bu işlevler içinde). Kullanıcının giriş sağlamak ihtiyacınız varsa, bu yapılandırmaya parametre olarak derleme aşamasında geçirmelisiniz.
## <a name="resource-functionality-was-thoroughly-tested"></a>Kaynak işlevselliği baştan sona test edilmiştir ##
Bu denetim, sınanacak önemlidir ve/veya genellikle eksik öğeleri içerir. Testleri, test ve burada belirtilmeyen kaynak belirli olacağı çoğunlukla işlevsel olanları demet olacaktır. Negatif test çalışmaları hakkında unutmayın.
## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a>Açısından en iyisi: kaynak modülü ResourceDesignerTests.ps1 betik klasörle testleri içerir ##
İçinde kaynak modül klasörü "testleri" oluşturun, ResourceDesignerTests.ps1 dosyası oluşturun ve kullanarak testleri eklemek için iyi bir uygulamadır **Test xDscResource** ve **Test xDscSchema** belirtilen tüm kaynakların ilişkin Modül.
Bu şekilde tüm kaynakların bir sağlamlık denetleyin yayımlanmadan önce belirtilen modülleri ve şemaları hızla doğrulayabilirsiniz.
XRemoteFile için ResourceTests.ps1 kadar basit görünebilir:
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```
##<a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a>Açısından en iyisi: kaynak klasörünü içeren kaynak Tasarımcı betik şema ## oluşturmak için
Her bir kaynağın kaynak mof şeması oluşturan bir kaynak Tasarımcı betik içermelidir. Bu dosya yerleştirilmelidir <ResourceName>\ResourceDesignerScripts ve Generate adlandırılması<ResourceName>xRemoteFile kaynak Schema.ps1 için bu dosyayı GenerateXRemoteFileSchema.ps1 çağrılır ve içerir:
```powershell
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.'
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile
```
## <a name="best-practice-resource-supports--whatif"></a>Açısından en iyisi: kaynak - whatIf destekler ##
Kaynağınız "tehlikeli" işlemleri çalışıyorsa, - whatIf işlevselliği uygulamak için iyi bir uygulamadır. Bunu yaptıktan sonra whatIf çıkış doğru whatIf anahtarı olmadan komut yürütülürse olacağını işlemleri açıklayan emin olun.
Ayrıca, operations yürütülmez doğrulayın (düğümün durumuna değişiklik yapılmaz) – whatIf anahtar olduğunda mevcut.
Örneğin, dosya kaynağı test ettiğiniz varsayalım. "Test" dosyası "sınama.txt" içeriğiyle oluşturan basit yapılandırma aşağıdadır:
```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```
Derleme ve yapılandırma – whatIf anahtarıyla yürütmek, çıktı bize biz yapılandırma çalıştırdığınızda tam olarak ne olacağını belirtiyor. Yapılandırma ancak yürütülmedi (sınama.txt dosyası oluşturulmadı).
```powershell
Start-DscConfiguration -path .\config -ComputerName localhost -wait -verbose -whatif
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

Bu liste geniş kapsamlı değildir, ancak tasarlama, geliştirme ve test etme DSC kaynakları hatayla karşılaştı birçok önemli sorunlar ele alınmaktadır.