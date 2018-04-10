---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: DSC’de sorun giderme
ms.openlocfilehash: 6bb639febc3f413e909c3e61559059adb5c96389
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="troubleshooting-dsc"></a>DSC’de sorun giderme

>İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Bu konuda ortaya sorun çıktığında DSC gidermenin yolları açıklanmaktadır.

## <a name="winrm-dependency"></a>WinRM bağımlılık

Windows PowerShell istenen durum yapılandırması (DSC) üzerinde WinRM bağlıdır. WinRM Windows Server 2008 R2 ve Windows 7 varsayılan olarak etkin değildir. Çalıştırma ```Set-WSManQuickConfig```, Windows PowerShell'de yükseltilmiş WinRM etkinleştirmek için oturumu.

## <a name="using-get-dscconfigurationstatus"></a>Get-DscConfigurationStatus kullanma

[Get-DscConfigurationStatus](https://technet.microsoft.com/library/mt517868.aspx) cmdlet'i, hedef düğüm yapılandırması durumu hakkındaki bilgileri alır.
Yapılandırma çalıştırma veya desteklemediğini başarılı hakkında üst düzey bilgileri içeren zengin bir nesne döndürdü. Gibi çalıştırmak yapılandırması hakkında ayrıntıları keşfetmek için nesnesine derinliklerine:

* Tüm başarısız kaynakları
* Bir sistem yeniden başlatması herhangi bir kaynak
* Çalışma zamanında yapılandırmasının meta yapılandırma ayarları
* VS.

Aşağıdaki parametre kümesi çalıştırmak son yapılandırma durum bilgilerini döndürür:

```powershell
Get-DscConfigurationStatus  [-CimSession <CimSession[]>]
                            [-ThrottleLimit <int>]
                            [-AsJob]
                            [<CommonParameters>]
```
Aşağıdaki parametre kümesi önceki tüm yapılandırma çalışmaları için durum bilgilerini döndürür:

```powershell
Get-DscConfigurationStatus  -All
                            [-CimSession <CimSession[]>]
                            [-ThrottleLimit <int>]
                            [-AsJob]
                            [<CommonParameters>]
```

## <a name="example"></a>Örnek

```powershell
PS C:\> $Status = Get-DscConfigurationStatus

PS C:\> $Status

Status      StartDate               Type            Mode    RebootRequested     NumberOfResources
------      ---------               ----            ----    ---------------     -----------------
Failure     11/24/2015  3:44:56     Consistency     Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName       :   MyService
DependsOn               :
ModuleName              :   PSDesiredStateConfiguration
ModuleVersion           :   1.1
PsDscRunAsCredential    :
ResourceID              :   [File]ServiceDll
SourceInfo              :   c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds       :   0.19
Error                   :   SourcePath must be accessible for current configuration. The related file/directory is:
                            \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState              :
InDesiredState          :   False
InitialState            :
InstanceName            :   ServiceDll
RebootRequested         :   False
ReosurceName            :   File
StartDate               :   11/24/2015  3:44:56
PSComputerName          :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a>My komut çalışmaz: kullanarak DSC günlüklerini komut dosyası hataları tanılamak için

Tüm Windows yazılımı gibi DSC hatalarını ve olaylarını kaydeder [günlükleri](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) alanından görüntülenebilir [Olay Görüntüleyicisi'ni](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer). Bu günlükler inceleyerek neden belirli bir işlem başarısız oldu, hata gelecekte oluşmasını engellemek nasıl anlamanıza yardımcı olabilir. Yapılandırma komut dosyası yazma bu nedenle, yazar olarak izleme hataları kolaylaştırmak, DSC günlük kaynak yapılandırmanızı DSC analitik olay günlüğünde ilerlemesini izlemek için kullanın zor olabilir.

## <a name="where-are-dsc-event-logs"></a>DSC olay günlüklerini nerede?

DSC olayları bulunan Olay Görüntüleyicisi'nde: **uygulamalar ve hizmetler günlükleri/Microsoft/Windows/istenen durum yapılandırması**

Karşılık gelen PowerShell cmdlet'ini [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), olay günlüklerini görüntülemek için da çalıştırılabilir:

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

Yukarıda gösterildiği gibi DSC'SİNİN birincil günlük adıdır **Microsoft -> Windows DSC ->** (diğer günlük adları Windows altında burada okumanızdır gösterilmez). Birincil adı tam günlük adını oluşturmak için kanal ada eklenir. DSC altyapısı genellikle üç tür günlükleri Yazar: [işlemsel Analitik ve hata ayıklama günlüklerini](https://technet.microsoft.com/library/cc722404.aspx). Bu yana Analitik ve hata ayıklama günlükleri devre dışı bırakma varsayılan olarak, Olay Görüntüleyicisi'nde etkinleştirmeniz gerekir. Bunu yapmak için Windows PowerShell'de Göster olay günlüğüne yazarak Olay Görüntüleyicisi'ni açın; veya tıklatın **Başlat** düğmesini tıklatın, **Denetim Masası**, tıklatın **Yönetimsel Araçlar**ve ardından **Olay Görüntüleyicisi'ni**. Üzerinde **Görünüm** Olay Görüntüleyicisi'nde menüsünü **Analitik ve hata ayıklama günlüklerini göster**. Günlük adı analitik kanalı **Microsoft-Windows-Dsc/analitik**, ve hata ayıklama kanalıdır **Microsoft-Windows-Dsc/Debug**. De kullanabilirsiniz [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) yardımcı programını kullanarak aşağıdaki örnekte gösterildiği gibi günlüklerini etkinleştirin.

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a>DSC günlükleri neler içerir?

DSC günlükleri ileti önemini dayalı üç günlük kanalları üzerinden bölünür. DSC işlem günlüğünde tüm hata iletilerini içerir ve bir sorunu tanımlamak için kullanılır. Analitik günlük olaylarının daha yüksek bir birimin vardır ve hatalarla oluştuğu tanımlayabilirsiniz. Bu kanal, ayrıca (varsa) ayrıntılı iletiler içerir. Hata ayıklama günlüğü nasıl hataları oluştu anlamanıza yardımcı olacak günlükleri içerir. Her olay iletisi benzersiz olarak DSC işlemini temsil eden bir iş kimliği ile başlar, DSC olay iletileri yapılandırılmıştır. Aşağıdaki örnek işletimsel DSC günlüğüne kaydedilmiş ilk olayı ileti almak çalışır.

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

DSC olaylar kullanıcının bir DSC işten toplama olaylarına sağlayan belirli bir yapı günlüğe kaydedilir. Yapısı aşağıdaki gibidir:

**İş Kimliği: <Guid>**
**<Event Message>**

## <a name="gathering-events-from-a-single-dsc-operation"></a>Tek bir DSC işlem toplama olayları

DSC olay günlüklerini çeşitli DSC işlemleri tarafından oluşturulan olayları içerir. Ancak, genellikle ayrıntılarla tek belirli işlemi hakkında endişe olmanız. Tüm DSC günlükler, her DSC işlem için benzersiz olan iş kimliği özelliği tarafından gruplandırılabilir. İş kimliği, tüm DSC olayları ilk özellik değeri olarak görüntülenir. Aşağıdaki adımları gruplandırılmış dizi yapısındaki tüm olayları birikmesini açıklanmaktadır.

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>

wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
wevtutil.exe set-log “Microsoft-Windows-Dsc/Debug” /q:True /e:true

<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>

Get-DscLocalConfigurationManager

<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>

$DscEvents=[System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Debug" -Oldest)


<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations = $DscEvents | Group {$_.Properties[0].value}
```

Burada, değişkeni `$SeparateDscOperations` kimlikleri iş tarafından gruplandırılmış günlükleri içerir. Her dizi öğesi, bu değişkenin günlükleri hakkında daha fazla bilgi için erişim farklı bir DSC işlem tarafından günlüğe kaydedilen olayları grubunu temsil eder.

```
PS C:\> $SeparateDscOperations

Count Name                      Group
----- ----                      -----
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
PS C:\> $SeparateDscOperations[0].Group
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
```

Değişkeni verilerde ayıklayabilirsiniz `$SeparateDscOperations` kullanarak [Where-Object](https://technet.microsoft.com/library/ee177028.aspx). DSC sorun giderme için verileri ayıklamak isteyeceğiniz beş senaryolar şunlardır:

### <a name="1-operations-failures"></a>1: işlemleri hataları

Tüm olayları sahip [önem düzeyleri](https://msdn.microsoft.com/library/dd996917(v=vs.85)). Bu bilgiler, hata olayları tanımlamak için kullanılabilir:

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a>2: işlem ayrıntılarını son bir yarım saatte çalıştırın

`TimeCreated`, her Windows olay özelliği durumları olayın oluşturulduğu saat. Bu özellik belirli bir tarih/saat nesnesi ile karşılaştırma tüm olayları filtrelemek için kullanılabilir:

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a>3: en son işlem iletileri

Son işlemi dizi grubuna ilk dizininde depolanan `$SeparateDscOperations`. Dizin 0 için grubun iletileri sorgulama son işlemi için tüm iletileri döndürür:

```powershelll
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Consistency check completed.
```

### <a name="4-error-messages-logged-for-recent-failed-operations"></a>4: en son başarısız işlemler için günlüğe hata iletileri

`$SeparateDscOperations[0].Group` Son işlemi olayları kümesini içerir. Çalıştırma `Where-Object` olayları filtrelemek için cmdlet tabanlı kullanıcıların düzeyi görünen adı. Sonuçları depolanır `$myFailedEvent` değişkenine olabilen başka olay iletisini almak için dissected:

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a>5: belirli iş kimliği için oluşturulan tüm olayları

`$SeparateDscOperations` her biri benzersiz iş kimliği ada sahip bir dizi gruplarının Çalıştırarak `Where-Object` cmdlet'ini gruplarıyla belirli iş kimliği olan olayları ayıklamak:

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
```

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a>Günlüklerini DSC çözümlemek için xDscDiagnostics kullanma

**xDscDiagnostics** DSC hataları makinenizde çözümlemenize yardımcı olabilecek birçok işlevleri oluşan bir PowerShell modülüdür. Bu işlevler geçmiş DSC Operations tüm yerel olayları veya uzak bilgisayarlarda DSC olayları (geçerli kimlik bilgileriyle) belirlemenize yardımcı olabilir. Burada, DSC işlemi terimi, bir tek benzersiz DSC yürütülmesine onun başlangıçtan sonunu tanımlamak için kullanılır. Örneğin, `Test-DscConfiguration` ayrı bir DSC işlemi olacaktır. Benzer şekilde, her diğer cmdlet'ini DSC (gibi `Get-DscConfiguration`, `Start-DscConfiguration`, vs.) her ayrı DSC işlemleri olarak tanımlanamadı. İşlevler en açıklanacak [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).
Yardım kullanılabilir çalıştırarak `Get-Help <cmdlet name>`.

### <a name="getting-details-of-dsc-operations"></a>DSC işlemlerinin ayrıntıları alınıyor

`Get-xDscOperation` İşlevi bir veya birden çok bilgisayar üzerinde çalışacak DSC işlemlerinin sonuçlarını bulmanıza sağlar ve her DSC işlemi tarafından üretilen olayları koleksiyonunu içeren bir nesne döndürür.
Örneğin, aşağıdaki çıktıda üç komutları çalıştırılmadı. Birinci geçirilen ve diğer iki başarısız oldu. Bu sonuçları çıktısında özetlenir `Get-xDscOperation`.

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...

```

Kullanarak, en son işlemleri için yalnızca sonuçları istemediğinizi de belirtebilirsiniz `Newest` parametre:

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation -Newest 5
ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   2          6/23/2016 4:36:54 PM  Success  5c06402b-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   3          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   4          6/23/2016 4:36:54 PM  Success  5c06402a-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   5          6/23/2016 4:36:51 PM  Success                                        {@{Message=; TimeC...
```

### <a name="getting-details-of-dsc-events"></a>DSC olaylarının ayrıntılarını alma

`Trace-xDscOperation` Cmdlet'i olaylar, kendi olay türleri koleksiyonunu içeren bir nesne döndürür ve çıktı mesajı oluşturulan belirli bir DSC işlemi. Genellikle, ne zaman bulduğunuz hata kullanarak işlemleri hiçbirinde `Get-xDscOperation`, hangi olayların bir hata neden olduğunu bulmak için bu işlemi izleme.

Kullanım `SequenceID` belirli bir bilgisayar için belirli bir işlemi olayları almak için parametre. Örneğin, belirttiğiniz bir `SequenceID` 9, `Trace-xDscOperaion` son işlem 9 edildi DSC işlemi için izleme alın:

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -SequenceID 9

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Running consistency engine.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM The local configuration manager is updating the PSModulePath to WindowsPowerShell\Modules;C:\Prog...
SRV1   OPERATIONAL  6/24/2016 10:51:53 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Operation Consistency Check or Pull completed successfully.
```

Geçirmek **GUID** belirli bir DSC işlemi atanan (tarafından döndürülen `Get-xDscOperation` cmldet) bu DSC işlemi için olay ayrıntıları almak için:

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -JobID 9e0bfb6b-3a3a-11e6-9165-00155d390509

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Starting consistency engine.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Current.mof.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with resource name [WindowsFeature]DSC...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCServiceFeature] True in 0.3130 sec...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with resource name [xDSCWebService]P...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Ensure
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Port
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Physical Path ...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check State
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Get Full Path for We...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCPullServer] True in 0.0160 seconds.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Consistency check completed.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
```

Unutmayın, beri `Trace-xDscOperation` analitik, hata ayıklama, olayları toplayan ve işlemsel günlükleri, bunu yukarıda açıklandığı gibi bu günlükleri etkinleştirmek isteyip istemediğinizi sorar.

Olaylar üzerinde çıktısını kaydederek bilgiler alternatif olarak, toplayabilirsiniz `Trace-xDscOperation` bir değişkenin içine. Belirli bir DSC işlem için tüm olayları görüntülemek için aşağıdaki komutları kullanabilirsiniz.

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

Bu aynı sonuçları görüntüler `Get-WinEvent` çıkış olduğu gibi cmdlet:

```powershell
   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
6/23/2016 1:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 1:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:07:00 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:07:01 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:36:56 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:06:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:06:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:36:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:06:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:36:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:36:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:36:56 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:36:57 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 8:06:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
```

İdeal olarak, ilk kullanacağınız `Get-xDscOperation` en son birkaç DSC listelemek için yapılandırma makinelerinizi üzerinde çalışır. Bu (SequenceId: veya JobId kullanarak) herhangi bir tek işlem ile inceleyebilirsiniz `Trace-xDscOperation` ne arka planda yaptığını bulmak için.

### <a name="getting-events-for-a-remote-computer"></a>Bir uzak bilgisayara olayları alma

Kullanım `ComputerName` parametresinin `Trace-xDscOperation` uzak bir bilgisayarda olay ayrıntıları almak için cmdlet. Bunu yapmak için önce uzak bilgisayarda Uzaktan yönetime izin vermek için bir güvenlik duvarı kuralı oluşturmanız gerekir:

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```
Aramanız için o bilgisayarın belirtebilirsiniz artık `Trace-xDscOperation`:

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -ComputerName SRV2 -Credential Get-Credential -SequenceID 5

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 f...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Starting consistency...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Curr...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature,...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCSer...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with re...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCP...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with ...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Consistency check co...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
```

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a>Kaynaklarım güncelleştirme olmaz: önbellek sıfırlama

DSC altyapısı verimliliği amaçlar için bir PowerShell modülü olarak uygulanan kaynakları önbelleğe alır. Ancak, bir kaynak yazma ve işlemi yeniden başlatılana kadar DSC önbelleğe alınan sürüm yükler için aynı anda sınama bu sorunlara neden olabilir. Daha yeni sürümü yüklemek DSC yapmak için tek açıkça DSC altyapısı barındırma işlemi sonlandırmak için yoludur.

Benzer şekilde, çalıştırdığınızda `Start-DscConfiguration`ekleme ve özel bir kaynak değiştirildikten sonra değişikliğin sürece yürütülmeyebilir veya bilgisayar yeniden başlatılana kadar. DSC WMI sağlayıcısı ana bilgisayar işlemi (WmiPrvSE) çalışır ve genellikle birçok WmiPrvSE aynı anda çalışan örneklerini vardır nedeni budur. Bilgisayarı yeniden başlattığınızda, ana bilgisayar işlemi yeniden ve önbellek temizlenir.

Başarıyla yapılandırmasını geri dönüşüm ve başlatmadan önbelleğini temizlemek için durdurun ve ana bilgisayar işlemi yeniden başlatın. Bu yapabildiği işlemi tanımlamak, durdurmak ve yeniden başlatmak için tek başına örnek temelinde, yapılabilir. Veya, kullanabileceğiniz `DebugMode`, PowerShell DSC kaynağı yeniden yüklemek için aşağıda gösterildiği gibi.

DSC altyapısı barındırma hangi işlemi tanımlamak ve tek başına örnek temelinde durdurmak için DSC altyapısı barındırma WmiPrvSE işlem kimliği listeleyebilirsiniz. Ardından, sağlayıcı güncelleştirmek için aşağıdaki komutları kullanarak WmiPrvSE işlemi ve çalıştırın Durdur **başlangıç DscConfiguration** yeniden.

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers |
Where-Object {$_.provider -like 'dsccore'} |
Select-Object -ExpandProperty HostProcessIdentifier

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## <a name="using-debugmode"></a>DebugMode kullanma

DSC yerel Configuration Manager (kullanmak için LCM'yi) yapılandırabilirsiniz `DebugMode` her zaman ana bilgisayar işlemi başlatıldığında önbelleğini temizlemek için. Ayarlandığında **doğru**, PowerShell DSC kaynağı her zaman yeniden altyapısı neden olur. Tamamladıktan sonra kaynak yazma, onu ayarlayabilirsiniz geri **FALSE** ve altyapı modülleri önbelleğe alma davranışını döner.

Aşağıdaki olduğunu göstermek için bir tanıtım nasıl `DebugMode` önbellek otomatik olarak yenileyebilirsiniz. İlk olarak, varsayılan yapılandırmasını bakalım:

```
PS C:\> Get-DscLocalConfigurationManager


AllowModuleOverwrite           : False
CertificateID                  :
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     :
DebugMode                      : False
DownloadManagerCustomData      :
DownloadManagerName            :
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :
```

Görebilirsiniz `DebugMode` ayarlanır **FALSE**.

Ayarlamak için `DebugMode` gösterimi, aşağıdaki PowerShell kaynağı kullanın:

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1" | Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
}
```

Şimdi, denilen yukarıdaki kaynağı kullanarak yapılandırma Yazar `TestProviderDebugMode`:

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

Göreceksiniz dosyasının içeriğini: "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" olan **1**.

Şimdi, aşağıdaki komut dosyası kullanarak sağlayıcı kodunu güncelleştirin:

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput" | Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

Bu komut dosyası rastgele bir sayı oluşturur ve sağlayıcı kodu buna göre güncelleştirir. İle `DebugMode` dosyasının içeriğini false olarak ayarlayın "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" hiçbir zaman değiştirilir.

Şimdi, `DebugMode` için **TRUE** yapılandırma komut:

```powershell
LocalConfigurationManager
{
    DebugMode = $true
}
```

Yukarıdaki komut dosyasını yeniden çalıştırdığınızda, dosyanın içeriği her zaman farklı olduğunu göreceksiniz. (Çalıştırabilirsiniz `Get-DscConfiguration` bunu denetlemek için). (Komut dosyasını çalıştırdığınızda sonuçlarınızı farklı olabilir) iki ek çalıştırmaları sonucu aşağıdadır:

```powershell
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
20                                      localhost

PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
14                                      localhost
```

## <a name="see-also"></a>Ayrıca bkz:

### <a name="reference"></a>Başvuru
* [DSC günlük kaynak](logResource.md)

### <a name="concepts"></a>Kavramlar
* [Özel Windows PowerShell istenen durum yapılandırması kaynakları oluşturma](authoringResource.md)

### <a name="other-resources"></a>Diğer Kaynaklar
* [Windows PowerShell istenen durum yapılandırma cmdlet'leri](https://technet.microsoft.com/library/dn521624(v=wps.630).aspx)