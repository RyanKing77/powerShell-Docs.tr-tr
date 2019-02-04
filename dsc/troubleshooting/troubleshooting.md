---
ms.date: 10/30/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC’de sorun giderme
ms.openlocfilehash: e1f36bbc97569ac0d65f003ee08f52ec174a4520
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684958"
---
# <a name="troubleshooting-dsc"></a>DSC’de sorun giderme

_Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0_

Bu konuda, sorunları ortaya çıktığında DSC gidermenin yolları açıklanmaktadır.

## <a name="winrm-dependency"></a>WinRM bağımlılık

WinRM üzerinde Windows PowerShell Desired State Configuration (DSC) bağlıdır. WinRM üzerinde Windows Server 2008 R2 ve Windows 7 varsayılan olarak etkin değil. Çalıştırma `Set-WSManQuickConfig`, Windows PowerShell'de yükseltilmiş oturumu WinRM'yi etkinleştirin.

## <a name="using-get-dscconfigurationstatus"></a>Get-DscConfigurationStatus kullanma

[Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet'i, hedef düğüm yapılandırma durumu hakkında bilgi alır. Yapılandırma çalıştırma veya olup olmadığını başarılı hakkında üst düzey bilgileri içeren zengin bir nesne döndürülür. Nesnesine gibi yapılandırma ayrıntılarını bulmak için incelemek:

- Başarısız olan tüm kaynakları
- Bir sistem yeniden başlatması herhangi bir kaynağa
- Çalıştırma zaman yapılandırmasının meta-yapılandırma ayarları
- VS.

Aşağıdaki parametre kümesi son yapılandırma Çalıştır durum bilgilerini döndürür:

```
Get-DscConfigurationStatus [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```
Aşağıdaki parametre kümesi, önceki tüm yapılandırma çalıştırmalar için durum bilgileri döndürür:

```
Get-DscConfigurationStatus -All
                           [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

## <a name="example"></a>Örnek

```powershell
PS C:\> $Status = Get-DscConfigurationStatus

PS C:\> $Status

Status         StartDate                Type            Mode    RebootRequested        NumberOfResources
------        ---------                ----            ----    ---------------        -----------------
Failure        11/24/2015  3:44:56     Consistency        Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName     :    MyService
DependsOn             :
ModuleName            :    PSDesiredStateConfiguration
ModuleVersion         :    1.1
PsDscRunAsCredential  :
ResourceID            :    [File]ServiceDll
SourceInfo            :    c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds     :    0.19
Error                 :    SourcePath must be accessible for current configuration. The related file/directory is:
                           \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState            :
InDesiredState        :    False
InitialState          :
InstanceName          :    ServiceDll
RebootRequested       :    False
ReosurceName          :    File
StartDate             :    11/24/2015  3:44:56
PSComputerName        :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a>Betiğimde çalışmaz: DSC kullanarak betik hatalarını tanılamak için günlükleri

Tüm Windows yazılım gibi DSC hatalarını ve olaylarını kaydeder [günlükleri](/windows/desktop/EventLog/about-event-logging) alanından görüntülenebilir [Olay Görüntüleyicisi'ni](https://support.microsoft.com/hub/4338813/windows-help).
Bu günlükleri İnceleme neden belirli bir işlem başarısız oldu ve hata gelecekte önlemek nasıl anlamanıza yardımcı olabilir. Yapılandırma komut dosyası yazma, bu nedenle, yazar olarak izleme hataları kolaylaştırmak, DSC günlük kaynak yapılandırmanızı ve DSC analitik olay günlüğüne ilerlemesini izlemek için kullanın zor olabilir.

## <a name="where-are-dsc-event-logs"></a>DSC olay günlükleri nerededir?

Olay Görüntüleyicisi'nde DSC olayları dahildir. **Uygulamalar ve hizmetler günlükleri/Microsoft/Windows/Desired State Configuration**

Karşılık gelen PowerShell cmdlet [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent), olay günlükleri görüntülemek için de çalıştırılabilir:

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

Yukarıda gösterildiği gibi DSC'ın birincil günlük adı olan **Microsoft -> Windows -> DSC** (Windows diğer günlük adlarla burada konuyu uzatmamak amacıyla gösterilmez). Birincil ad tam günlük adı oluşturmak için kanal adına eklenir. DSC altyapısını esas olarak üç tür günlükleri Yazar: [İşlemsel, Analitik ve hata ayıklama günlükleri](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)). Bu yana Analitik ve hata ayıklama günlükleri devre dışı bırakma varsayılan olarak, Olay Görüntüleyicisi'nde etkinleştirmeniz gerekir. Bunu yapmak için Windows PowerShell'de Show-EventLog yazarak Olay Görüntüleyicisi'ni açın; veya tıklayın **Başlat** düğmesini tıklatın, **Denetim Masası**, tıklayın **Yönetimsel Araçlar**ve ardından **Olay Görüntüleyicisi'ni**.
Üzerinde **görünümü** Olay Görüntüleyicisi'nde menüsünü **Analitik ve hata ayıklama günlüklerini göster**. Günlük adı analitik kanalı **Microsoft-Windows-Dsc/analitik**, ve hata ayıklama kanal **Microsoft-Windows-Dsc/Debug**. Ayrıca kullanabileceğinizi [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) yardımcı programını kullanarak aşağıdaki örnekte gösterildiği gibi günlüklerini etkinleştirin.

```powershell
wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a>DSC günlükleri ne içerir?

DSC günlükleri iletinin önem derecesine göre üç günlük kanalları üzerinden bölünür. DSC işlem günlüğünde tüm hata iletilerini içerir ve bir sorunu tanımlamak için kullanılabilir. Analitik günlüğünü daha yüksek bir olayların hacmine sahip ve hata oluştuğu belirleyebilirsiniz. Bu kanal, ayrıntılı iletileri de (varsa) içerir. Hata ayıklama günlüğünü nasıl hataları oluştu anlamanıza yardımcı olacak günlükleri içerir. DSC olay iletileri, her olay iletisi benzersiz bir DSC işlemini temsil eden bir iş kimliği ile başlayan şekilde yapılandırılmıştır. Aşağıdaki örnekte, ilk olay işletimsel DSC oturum günlüğüne ileti almak çalışır.

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

Kullanıcının bir DSC projeden toplama olayları sağlar. belirli bir yapı DSC olayları günlüğe kaydedilir. Yapı aşağıdaki gibidir:

```
Job ID : <Guid>
<Event Message>
```

## <a name="gathering-events-from-a-single-dsc-operation"></a>Tek bir DSC işlemi toplama olayları

DSC olay günlükleri, çeşitli DSC işlemleri tarafından oluşturulan olayları içerir. Ancak, genellikle yalnızca tek bir belirli işlem hakkında endişe ayrıntılarla olacaktır. Tüm DSC günlükler her DSC işlem için benzersiz iş kimliği özelliği göre gruplandırılabilir. İş kimliği, tüm DSC olayları ilk özellik değeri olarak görüntülenir. Aşağıdaki adımlarda, gruplandırılmış dizi yapıdaki tüm olayları ulaşıncaya kadar açıklanmaktadır.

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>

wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
wevtutil.exe set-log "Microsoft-Windows-Dsc/Debug" /q:True /e:true

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

Burada, değişken `$SeparateDscOperations` kimlikleri işi tarafından gruplandırılmış günlükleri içerir. Her dizi öğesi bu değişken grubunu erişimine günlükleri hakkında daha fazla bilgi için farklı bir DSC işlemi tarafından günlüğe kaydedilen olayları temsil eder.

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

Veri değişkeni içinde ayıklayabilir `$SeparateDscOperations` kullanarak [Where-Object](/powershell/module/microsoft.powershell.core/where-object). DSC sorun giderme için verileri ayıklamak isteyebilirsiniz beş senaryolar aşağıda verilmiştir:

### <a name="1-operations-failures"></a>1: İşlem hataları

Tüm olaylar sahiptir [önem düzeyleri](/windows/desktop/WES/defining-severity-levels). Bu bilgiler hata olayları tanımlamak için kullanılabilir:

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}

Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a>2: Son yarım saat içinde çalıştırma işlemlerinin ayrıntıları

`TimeCreated`, her Windows olay özelliği durumları olayın oluşturulduğu zaman. Bu özellik belirli bir tarih/saat nesnesi ile karşılaştırma tüm olayları filtrelemek için kullanılabilir:

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}

Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a>3: En son işlem iletileri

En son işlemi dizi grubunun ilk dizininde depolanan `$SeparateDscOperations`.
Dizin 0 için grubun iletileri sorgulama en son işlem için tüm iletileri döndürür:

```powershell
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

### <a name="4-error-messages-logged-for-recent-failed-operations"></a>4: Son Başarısız işlemler için günlüğe hata iletileri

`$SeparateDscOperations[0].Group` en son işlemi için olaylar kümesini içerir. Çalıştırma `Where-Object` olayları filtrelemek için cmdlet tabanlı üzerinde kullanıcıların düzeyi görünen adı. Sonuçlar depolanır `$myFailedEvent` değişken olabilen daha fazla olay iletisi almayı dissected:

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message

Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a>5: Belirli bir proje kimliği için oluşturulan tüm olaylar

`$SeparateDscOperations` grupları, her biri benzersiz iş kimliği ada sahip bir dizisi Çalıştırarak `Where-Object` cmdlet'i, bu gruplara belirli iş Kimliğine sahip olayı ayıklamak:

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

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a>DSC çözümlemek için xDscDiagnostics kullanarak günlükleri

**xDscDiagnostics** DSC hataları makinenizde çözümlemenize yardımcı olabilecek çeşitli işlevler içeren bir PowerShell modülüdür. Bu işlevler, tüm yerel olayları son DSC işlemlerden veya uzak bilgisayarlarda DSC olayları (geçerli kimlik bilgileriyle) belirlemenize yardımcı olabilir. Burada, DSC işlemi terimi, bir tek benzersiz DSC yürütmeyi, başlangıçtan sonuna tanımlamak için kullanılır. Örneğin, `Test-DscConfiguration` ayrı bir DSC işlemi olacaktır. Benzer şekilde, her diğer cmdlet DSC (gibi `Get-DscConfiguration`, `Start-DscConfiguration`, vs.) her ayrı DSC işlem olarak tanımlanamadı. İşlevler, açıklanmıştır [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics). Yardım kullanılabilir çalıştırarak `Get-Help <cmdlet name>`.

### <a name="getting-details-of-dsc-operations"></a>DSC işlemlerinin ayrıntıları alınıyor

`Get-xDscOperation` İşlevi bir veya birden çok bilgisayarda çalıştırma DSC işlemlerinin sonuçlarını bulmanıza olanak tanır ve olayları koleksiyonu içeren bir nesne her DSC işlemiyle oluşturulan döndürür. Örneğin, aşağıdaki çıktı, üç komutu çalıştırılamadı. İlk geçirilen ve diğer iki başarısız oldu. Bu sonuçları çıktısında özetlenir `Get-xDscOperation`.

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

Yalnızca sonuçları kullanarak en son işlemler için istediğiniz belirtebilirsiniz `Newest` parametresi:

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

### <a name="getting-details-of-dsc-events"></a>DSC olayların ayrıntıları alınıyor

`Trace-xDscOperation` Cmdlet, olaylar, olay türlerini koleksiyonu içeren bir nesne döndürür ve ileti çıkış oluşturulan belirli bir DSC işlemi. Genellikle, ne zaman bulduğunuz hata kullanarak işlemleri hiçbirinde `Get-xDscOperation`, hangi olayların hata neden olduğunu bulmak için bu işlemi izleme.

Kullanım `SequenceID` belirli bir bilgisayar için belirli bir işlemi için olaylar almak için parametre.
Örneğin, belirttiğiniz bir `SequenceID` 9, `Trace-xDscOperaion` son işlemden 9 olan DSC işlemi için izleme alın:

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

Geçirmek **GUID** belirli bir DSC işlemi için atanan (tarafından döndürülen `Get-xDscOperation` cmdlet'i) bu DSC işlem için olay ayrıntılarını almak için:

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

Unutmayın, beri `Trace-xDscOperation` analitik, hata ayıklama olaylarını toplar ve işlemsel günlükleri, yukarıda açıklandığı gibi bu günlükleri etkinleştirmenizi ister.

Olaylar üzerinde çıkışını kaydederek bilgileri alternatif olarak, toplayabilirsiniz `Trace-xDscOperation` bir değişkenin içine. Belirli bir DSC işlem için tüm olayları görüntülemek için aşağıdaki komutları kullanabilirsiniz.

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

Bu aynı sonuçları görüntüler `Get-WinEvent` gibi aşağıdaki çıktıyı cmdlet'inin:

```output
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

İdeal olarak, ilk kullanacağınız `Get-xDscOperation` yapılandırma makinelerinizde çalışan en son birkaç DSC listesi. Aşağıdaki (kendi SequenceId: veya JobId kullanılarak) herhangi tek bir işlem ile inceleyebilirsiniz `Trace-xDscOperation` perde arkasında neler kişiselleştirmeden bulunacak.

### <a name="getting-events-for-a-remote-computer"></a>Uzak bir bilgisayar için olayları alma

Kullanım `ComputerName` parametresinin `Trace-xDscOperation` uzak bir bilgisayarda olay ayrıntılarını almak için cmdlet. Bunu yapmak için önce uzak bilgisayarda Uzaktan yönetime izin vermek için bir güvenlik duvarı kuralı oluşturmak sahip:

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```

Bu bilgisayar çağrınız belirtebilirsiniz artık `Trace-xDscOperation`:

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

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a>Kaynaklarım güncelleştirme olmaz: Önbelleğini sıfırlama

DSC altyapısını verimliliği amaçlar için bir PowerShell modülü olarak uygulanan kaynakları önbelleğe alır.
Ancak, bir kaynak yazma ve işlemi yeniden başlatılana kadar DSC önbelleğe alınmış sürümünü yükler için aynı anda test bu sorunlara neden olabilir. DSC daha yeni sürümünü yükleme yapmak için tek açıkça DSC altyapısını barındıran işlemi sonlandırmak için yoludur.

Benzer şekilde, çalıştırdığınızda `Start-DscConfiguration`, ekleme ve özel bir kaynağı değiştirme sonra değişiklik sürece yürütülmeyebilir veya bilgisayar yeniden başlatılana kadar. DSC WMI sağlayıcısı ana bilgisayar işlemi (WmiPrvSE) çalışır ve genellikle aynı anda çalışan WmiPrvSE birçok örneği mevcuttur nedeni budur. Bilgisayarı yeniden başlattığınızda ana bilgisayar işlemi başlatılır ve önbellek temizlenir.

Başarılı bir şekilde yapılandırmayı geri dönüşüm ve yeniden başlatmaya gerek kalmadan önbelleği temizlemek için durdurun ve ana bilgisayar işlemi yeniden gerekir. Bu yapabildiği işlemi tanımlamak, durdurmak ve yeniden tek başına örnek temelinde, yapılabilir. Veya, kullanabileceğiniz `DebugMode`PowerShell DSC kaynağı yeniden yüklemek için aşağıda gösterildiği gibi.

DSC altyapısını barındıran işlemi tanımlamak ve tek başına örnek temelinde durdurmak için DSC altyapısını barındıran WmiPrvSE işlem Kimliğini listeleyebilirsiniz. Ardından, sağlayıcı güncelleştirmek için çalıştırın ve aşağıdaki komutları kullanarak WmiPrvSE işlemi durdurmak **Başlat-DscConfiguration** yeniden.

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

DSC yerel Configuration Manager (kullanılacak LCM) yapılandırabileceğiniz `DebugMode` her zaman, ana bilgisayar işlemi başlatıldığında önbelleği temizlemek için. Ayarlandığında **TRUE**, PowerShell DSC kaynağı her zaman yeniden yüklemek altyapı sağlar. İşiniz bittiğinde, kaynak yazma, bunu ayarlayabilirsiniz geri **FALSE** ve altyapısı, modülleri önbelleğe alma davranışını geri döner.

Gösterilecek bir örnek aşağıdadır nasıl `DebugMode` önbellek otomatik olarak yenileyebilirsiniz. İlk olarak, varsayılan yapılandırmayı göz atalım:

```powershell
PS C:\> Get-DscLocalConfigurationManager
```

```output
AllowModuleOverwrite           : False
CertificateID                  :
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     :
DebugMode                      : {None}
DownloadManagerCustomData      :
DownloadManagerName            :
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :
```

Gördüğünüz gibi `DebugMode` ayarlanır **"None"**.

Ayarlamak için `DebugMode` gösterim, aşağıdaki PowerShell kaynağı kullanın:

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

Şimdi, adlı yukarıdaki kaynak kullanarak yapılandırma Yazar `TestProviderDebugMode`:

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

Göreceksiniz dosyasının içeriğini: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` olduğu **1**.

Artık, aşağıdaki betiği kullanarak sağlayıcı kodu güncelleştirin:

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

Bu betik, rastgele bir sayı oluşturur ve sağlayıcı kodu uygun şekilde güncelleştirir. İle `DebugMode` dosyasının içeriğini false olarak ayarlayın "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" hiçbir zaman değiştirilir.

Şimdi, `DebugMode` için **"ForceModuleImport"** yapılandırma betiğinizde:

```powershell
LocalConfigurationManager
{
    DebugMode = "ForceModuleImport"
}
```

Yukarıdaki komut dosyasını yeniden çalıştırdığınızda, dosyanın içeriğini her seferinde farklı olduğunu görürsünüz. (Çalıştırabileceğiniz `Get-DscConfiguration` bunu kontrol etmek için). (Komut dosyasını çalıştırırken sonuçlarınızı farklı olabilir) iki ek çalıştırma sonucunu aşağıdadır:

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

### <a name="concepts"></a>Kavramlar

- [Derleme özel Windows PowerShell Desired State Configuration kaynakları](../resources/authoringResource.md)

### <a name="other-resources"></a>Diğer Kaynaklar

- [Windows PowerShell cmdlet'leri Desired State Configuration](/powershell/module/psdesiredstateconfiguration/)
