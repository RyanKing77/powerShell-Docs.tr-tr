---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Kaynak yazma denetim listesi
ms.openlocfilehash: 91942a174bc6f38fa77c1925dc3c690ecf2ab34b
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893564"
---
# <a name="resource-authoring-checklist"></a>Kaynak yazma denetim listesi

Bu denetim yeni bir DSC kaynağı yazma en iyi bir listedir.

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a>Kaynak modülü .psd1 dosya ve her kaynak için schema.mof içerir.

Kaynağınızı doğru yapıya sahiptir ve tüm gerekli dosyaları içeren denetleyin. Her kaynak modülü .psd1 dosya içermelidir ve her bileşik olmayan kaynak schema.mof dosyanız olmalıdır. Şema içermeyen kaynaklar tarafından listelenmez `Get-DscResource` ve kullanıcıların ISE'de modüller karşı kod yazarken IntelliSense kullanmanız mümkün olmayacaktır.
Parçası olan xRemoteFile kaynak dizin yapısı, [xPSDesiredStateConfiguration resource Modülü](https://github.com/PowerShell/xPSDesiredStateConfiguration), şu şekilde görünür:

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

## <a name="resource-and-schema-are-correct"></a>Kaynak ve şema doğru

Kaynak şemayı doğrulayın (*. schema.mof) dosyası. Kullanabileceğiniz [DSC kaynak Tasarımcısı](https://www.powershellgallery.com/packages/xDSCResourceDesigner) geliştirip test şemanızı yardımcı olmak için.
Emin olun:

- Özellik türleri doğru (dize, sayısal değerleri kabul etmek için özellikleri örn kullanmayın, bunun yerine UInt32 ya da diğer sayısal türleri kullanmalısınız)
- Özellik öznitelikleri doğru olarak belirtilir: ([anahtarı] [gerekli], [yazma], [okuma])
- Şema en az bir parametresi [anahtar] olarak işaretlenmesi gerekir
- [özelliği olmayan bir arada herhangi biri ile birlikte okuyun]: [gerekli], [key] [yazma]
- Birden çok niteleyicileri dışında [oku] belirtilirse, [key] öncelik kazanır
- Varsa [yazma] ve [gerekli] belirtilen sonra [gerekli] önceliğe
- ValueMap belirtilen örnek uygun olduğunda:

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- Kolay ad belirtilir ve DSC adlandırma kurallarına onaylar

  Örnek: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`

- Her alan anlamlı bir açıklama bulunur. PowerShell GitHub deposunu iyi örnekler vardır [. schema.mof xRemoteFile için](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)

Ayrıca, kullanmanız gereken **Test xDscResource** ve **Test xDscSchema** cmdlet'lerinden [DSC kaynak Tasarımcısı](https://www.powershellgallery.com/packages/xDSCResourceDesigner) kaynak ve şema otomatik olarak doğrulamak için:

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

Örneğin:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a>Kaynak hatasız yükler.

Kaynak modülü başarıyla yüklenmiş olup olmadığını denetleyin.
Bu el ile çalıştırarak ulaşılabilecek `Import-Module <resource_module> -force` ve herhangi bir hata oluştuğunu onayladıktan veya göre test Otomasyonu yazma. İkinci olması durumunda, bu yapı, test çalışmasında izleyebilirsiniz:

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a>Kaynak etkilidir pozitif durumda

DSC kaynakları temel özelliklerini Eşkuvvetlilik olması biridir. Bu, birden çok kez bu kaynağı içeren bir DSC yapılandırması uygulama her zaman aynı sonucu elde edecek, anlamına gelir. Örneğin aşağıdaki dosya kaynağı içeren bir yapılandırma oluşturacağız:

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

İlk kez uyguladıktan sonra dosya test.txt gözükeceğini `C:\test` klasör. Ancak, aynı yapılandırmayı sonraki çalışmaları makinenin durumunu değiştirmemesi gerekir (örneğin hiçbir kopyalarını `test.txt` dosya oluşturulmalıdır).
Bir kaynağa tekrar tekrar çağırmak bir kez etkili olduğundan emin olmak için `Set-TargetResource` kaynak doğrudan test veya çağrı `Start-DscConfiguration` birden çok kez baştan sona test yaparken. Her sonrasında çalıştırma sonucu aynı olması gerekir.

## <a name="test-user-modification-scenario"></a>Test kullanıcı değişiklik senaryosu

Makinenin durumunu değiştirme ve DSC artırarak algoritmanın yeniden çalıştırılması doğrulayabilirsiniz `Set-TargetResource` ve `Test-TargetResource` düzgün. Uygulamanız gereken adımlar şunlardır:

1. İstenen durumda değil kaynakla başlayın.
2. Kaynağınız ile çalıştırma yapılandırma
3. Doğrulama `Test-DscConfiguration` True döndürür
4. İstenen durum dışında olacak şekilde yapılandırılmış öğesini değiştirin
5. Doğrulama `Test-DscConfiguration` false döndürür

Registry kaynağı kullanarak daha somut bir örnek aşağıda verilmiştir:

1. Kayıt defteri anahtarı istenen durumda değil başlayın
2. Çalıştırma `Start-DscConfiguration` istenen durumda yerleştirin ve doğrulamak için bir yapılandırmayla geçirir.
3. Çalıştırma `Test-DscConfiguration` ve doğrulayın, true döndürür
4. İstenen durumda değil anahtarının değerini değiştirin
5. Çalıştırma `Test-DscConfiguration` ve false döndürür doğrulayın
6. `Get-TargetResource` işlevleri kullanılarak doğrulandı `Get-DscConfiguration`

`Get-TargetResource` Kaynağın geçerli durumu ayrıntıları döndürmelidir. Çağırarak sınayın `Get-DscConfiguration` sonra yapılandırmayı uygulamak ve çıktısını almak için doğru Bu doğrulama makinenin geçerli durumunu yansıtır. Bu alandaki tüm sorunları çağırırken görünmez olduğundan ayrı ayrı test etmek önemlidir `Start-DscConfiguration`.

## <a name="call-getsettest-targetresource-functions-directly"></a>Çağrı **Get/Set/Test-TargetResource** doğrudan işlevleri

Test emin **Get/Set/Test-TargetResource** kaynağınızda doğrudan çağırmak ve beklendiği gibi çalıştığını doğrulama uygulanan işlevleri.

## <a name="verify-end-to-end-using-start-dscconfiguration"></a>Uçtan uca kullanarak doğrulama **Başlat-DscConfiguration**

Test **Get/Set/Test-TargetResource** işlevlerini doğrudan çağırma tarafından önemlidir, ancak bu şekilde tüm sorunları bulunacaktır. Testinizin kullanma ile ilgili önemli bir bölümü durmalısınız `Start-DscConfiguration` veya çekme sunucusu. Aslında, bu kullanıcılar bu tür testler önemini düşük gösterdiğini olmayan şekilde kaynak nasıl kullanacağınız değerdir.
Olası sorunları türleri:

- DSC aracı bir hizmet olarak çalıştığı için kimlik bilgisi/oturum farklı davranabilir.  Burada herhangi bir özellik baştan sona test etmeyi unutmayın.
- Hataları çıktı tarafından `Start-DscConfiguration` çağırırken görüntülenen alınanlardan farklı olabilir `Set-TargetResource` doğrudan işlev.

## <a name="test-compatability-on-all-dsc-supported-platforms"></a>Test uyumluluk tüm DSC üzerinde desteklenen platformlar

Kaynak DSC desteklenen tüm platformlarda iş (Windows Server 2008 R2 ve üzeri). DSC en son sürümünü almak için işletim sisteminize en son WMF (Windows Management Framework) yükleyin. Kaynağınızı bu platformları bazılarında tasarım gereği çalışmazsa, belirli bir hata iletisi döndürülmelidir. Ayrıca kaynağınızın aradığınız cmdlet'leri belirli makinede mevcut olup olmadığını denetler emin olun. Windows Server 2012, çok sayıda bile WMF yüklü Windows Server 2008R2 üzerinde mevcut olmayan yeni cmdlet'ler eklendi.

## <a name="verify-on-windows-client-if-applicable"></a>(Eğer varsa) Windows istemcide doğrulayın

Çok yaygın bir test boşluk kaynağın yalnızca Windows server sürümlerini doğruluyor. Çok sayıda kaynağı da istemci SKU'ları üzerinde çalışacak şekilde tasarlanmıştır, sizin durumunuzda true ise, bu platformlarda test unutmamak.

## <a name="get-dscresource-lists-the-resource"></a>Get-DSCResource kaynak listeler

Modül dağıttıktan sonra çağırma `Get-DscResource` kaynağınızı diğerlerinin yanı sıra sonucunda listelemelisiniz. Kaynağınızı listede bulamazsanız, bu kaynağın mevcut için schema.mof osyanın emin olun.

## <a name="resource-module-contains-examples"></a>Kaynak modülü örnekler içerir.

Başkalarının yardımcı olacak oluşturma kalite örnekleri nasıl kullanılacağını anlamak. Özellikle çok sayıda kullanıcı belgeleri örnek kod işle olduğundan bu, çok önemlidir.

- İlk olarak, en azından – modülüyle dahil edilecek örnekler belirlemelisiniz, kaynağınız için en önemli kullanım örneklerini kapsamalıdır:
- Temel uçtan uca örnek ideal olarak, modül bir uçtan uca senaryo için birlikte çalışmak için gereken çeşitli kaynaklar varsa, ilk olacaktır.
- İlk örnek çok basit--nasıl (örneğin yeni bir VHD oluşturma) küçük yönetilebilir yığınlar kaynaklarınızı kullanmaya başlama
- Sonraki örneklerde (örneğin VM VM değiştirme, kaldırma, bir VHD'den VM oluşturma) Bu örnekleri oluşturmak ve gelişmiş işlevleri (örneğin dinamik bellek ile VM oluşturma) göster
- Örnek yapılandırma parametreli (tüm değerler için yapılandırma parametreleri olarak geçirilmelidir ve sabit kodlanmış değer olması gerekir):

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

- Yapılandırmanın sonunda örnek betik, gerçek değerlerle çağırmak nasıl (out açıklamalı) örneği eklemek iyi bir uygulamadır.
  Örneğin, yukarıdaki yapılandırmada UserAgent belirtmek için en iyi yolu olduğunu mutlaka belirgin değildir:

  `UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` Bu durumda bir açıklama yapılandırmasının hedeflenen yürütme açıklık getirebilirsiniz:

  ```powershell
  <#
  Sample use (parameter values need to be changed according to your scenario):

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
  -userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
  #>
  ```

- Her örneğin ne yaptığını açıklayan kısa bir açıklama ve parametreleri anlamını yazın.
- Örnekler kaynağınızın birçok önemli senaryoyu kapsar ve şey eksik, yoksa tüm yürütün ve istenen durumda makine yerleştirebilir doğrulayın emin olun.

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a>Anlama ve kullanıcılar sorunları çözmesine yardımcı olmak hata iletileri kolaydır

İyi hata iletileri olmalıdır:

- : Hata iletileri en büyük sorun yoktur genellikle yoksa, bu nedenle bunlar olmadığından emin olun.
- Kolay anlaşılır: insan tarafından okunabilir, Hayır belirsiz hata kodları
- Kesin: tam olarak sorunun ne olduğunu açıklamak
- Yapıcı: Öneri sorunun nasıl çözüleceğini
- Yumuşak: Kullanıcı sorumlu veya yoksa onları hatalı gönderebilirsiniz

Uçtan uca senaryolar Hataları Doğrula emin olun (kullanarak `Start-DscConfiguration`), kaynak işlevleri doğrudan çalıştırılırken döndürülen olanlardan farklı olabilir.

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a>Kolay anlaşılır ve bilgilendirici günlük iletisi (dahil-verbose,-hata ayıklama ve ETW günlükleri)

Kaynak tarafından yüzdelik günlükleri anlama ve kullanıcıya değeri sağlamak kolay olduğundan emin olun. Kaynakları, kullanıcıya yardımcı olabilecek tüm bilgileri oluşturmalıdır, ancak daha fazla günlükleri değil her zaman daha iyi. Yedeklilik önlemek ve gerekir içermeyen veri çıktısı ek değer sağlayın: birisi aradıklarını bulmak amacıyla günlük girişlerini yüzlerce Git yapmayın. Elbette, günlük değil Bu sorun için kabul edilebilir bir çözüm ya da.

Test ederken de ayrıntılı analiz etmek ve hata ayıklama günlüklerini (çalıştırarak `Start-DscConfiguration` ile `–Verbose` ve `–Debug` uygun şekilde geçer) da ETW günlükleri olarak. DSC ETW günlükleri görmek için Olay Görüntüleyicisi'ne gidin ve şu klasörü açın: uygulama ve Hizmetleri - Microsoft - Windows - Desired State Configuration.  Varsayılan olarak yok işlevsel kanal olabilir, ancak analitik etkinleştirdiğinizden emin olun ve yapılandırmayı çalıştırmadan önce kanalları hata ayıklama.
Analitik/Debug kanalları etkinleştirmek için aşağıdaki betiği yürütebilirsiniz:

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

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a>Kaynak uygulama, sabit kodlanmış yollar içermiyor

Özellikle dil varsayarsanız kaynak uygulamasında, sabit kodlanmış yol olmadığından emin olun (en-us), veya kullanılabilir sistem değişkenlerini olduğunda.
Kaynağınızı belirli yollar erişmeniz gerekiyorsa, diğer makinelere değişebilir gibi ortam değişkenleri yerine runbook'a kod yolu kullanın.

Örnek:

Onun yerine:

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

Şunu yazabilirsiniz:

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a>Kaynak uygulaması kullanıcı bilgisi içermiyor

E-posta adları, hesap bilgileri veya kod kişilerin adları yok emin olun.

## <a name="resource-was-tested-with-validinvalid-credentials"></a>Kaynak geçerli/geçersiz kimlik bilgileri ile test edilmiştir

Kaynağınızı parametre olarak bir kimlik bilgisi sürerse:

- Yerel Sistem (veya uzak kaynaklara yönelik bilgisayar hesabının) erişimi olmadığında, kaynak çalıştığını doğrulayın.
- Bir kimlik bilgisi için belirtilen kaynak çalışır Al Ayarla ve Test doğrulayın
- Kaynak paylaşımları erişirse, desteği, aşağıdaki gibi ihtiyacınız olan tüm çeşitleri test edin:
  - Standart windows paylaşımları.
  - DFS paylaşımları.
  - SAMBA paylaşımları (Linux desteklemek isterseniz.)

## <a name="resource-does-not-require-interactive-input"></a>Kaynak etkileşimli giriş gerektirmez

**Get/Set/Test-TargetResource** işlevleri otomatik olarak yürütülüp ve kullanıcının herhangi bir yürütme aşamasında girişinin için beklemeyip gerekir (örneğin kullanmamalısınız `Get-Credential` bu işlevler içinde). Kullanıcının giriş sağlamanız gerekiyorsa, yapılandırma için parametre olarak derleme aşaması sırasında geçirdiğiniz.

## <a name="resource-functionality-was-thoroughly-tested"></a>Kaynak işlevselliği kapsamlı olarak test edildi

Bu denetim, test edilecek önemlidir ve/veya genellikle eksik öğeleri içerir. Testler, test ve burada belirtilmeyen kaynak belirli olacağı çoğunlukla işlevsel olanları sürü olacaktır. Negatif test çalışmaları hakkında unutmayın.

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a>En iyi yöntem: kaynak modülünde ResourceDesignerTests.ps1 betiğiyle test klasörü

Kaynak modülü içinde "testleri" klasör oluşturma, için iyi bir uygulamadır `ResourceDesignerTests.ps1` kullanarak testleri ekleyin ve dosya **Test xDscResource** ve **Test xDscSchema** içinde tüm kaynaklar için verilen modülü.
Bu şekilde tüm kaynakların bir sağlamlık denetleyin yayımlanmadan önce belirtilen modülleri ve şemaları hızlı bir şekilde doğrulayabilirsiniz.
XRemoteFile için `ResourceTests.ps1` kadar basit görünebilir:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a>En iyi yöntem: kaynak klasörünü içeren şema oluşturmak için kaynak Tasarımcı betiği

Her kaynak bir kaynağın mof şema oluşturur bir kaynak Tasarımcı betiği içermelidir. Bu dosya yerleştirilmelidir `<ResourceName>\ResourceDesignerScripts` ve Oluştur adlandırılması `<ResourceName>Schema.ps1` xRemoteFile kaynağı için bu dosyayı çağırılan `GenerateXRemoteFileSchema.ps1` ve içerir:

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

## <a name="best-practice-resource-supports--whatif"></a>En iyi yöntem: kaynak - WhatIf destekler

Kaynağınızı "tehlikeli" işlemleri gerçekleştiriliyorsa, uygulamak için iyi bir uygulamadır `-WhatIf` işlevselliği. Bunu yaptıktan sonra emin olun `-WhatIf` çıkış doğru olmadan komut yürütülürse olacağını işlemleri açıklar `-WhatIf` geçin.
Ayrıca, operations yürütülmez doğrulayın (düğümün durumu için hiçbir değişiklik yapılmaz) olduğunda `–WhatIf` anahtar.
Örneğin, şu dosya kaynak test varsayalım. Aşağıdaki dosya oluşturan basit yapılandırmadır `test.txt` "test" içeriğiyle:

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

Derleme ve sonra yapılandırmasıyla yürütün `-WhatIf` anahtarı, çıkış unsurdur bize yapılandırma çalıştırıyoruz, tam olarak ne olacağını. Yapılandırma ancak yürütülmedi (`test.txt` dosyası oluşturulmadı).

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```output
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

Bu liste kapsamlı değildir, ancak tasarlama, geliştirme ve test etme DSC kaynakları hatayla karşılaşıldı, birçok önemli sorunları kapsamaktadır.