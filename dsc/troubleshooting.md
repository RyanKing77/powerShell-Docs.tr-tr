---
ms.date: 10/30/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC’de sorun giderme
ms.openlocfilehash: 04fb1e9016c508d0e514b51b3cfd6e6f6d5c4974
ms.sourcegitcommit: 9cabc119f4d59598e12d4a36238a311349082ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50410023"
---
# <a name="troubleshooting-dsc"></a><span data-ttu-id="5b950-103">DSC’de sorun giderme</span><span class="sxs-lookup"><span data-stu-id="5b950-103">Troubleshooting DSC</span></span>

<span data-ttu-id="5b950-104">_Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="5b950-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="5b950-105">Bu konuda, sorunları ortaya çıktığında DSC gidermenin yolları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b950-105">This topic describes ways to troubleshoot DSC when problems arise.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="5b950-106">WinRM bağımlılık</span><span class="sxs-lookup"><span data-stu-id="5b950-106">WinRM Dependency</span></span>

<span data-ttu-id="5b950-107">WinRM üzerinde Windows PowerShell Desired State Configuration (DSC) bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5b950-107">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="5b950-108">WinRM üzerinde Windows Server 2008 R2 ve Windows 7 varsayılan olarak etkin değil.</span><span class="sxs-lookup"><span data-stu-id="5b950-108">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="5b950-109">Çalıştırma `Set-WSManQuickConfig`, Windows PowerShell'de yükseltilmiş oturumu WinRM'yi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="5b950-109">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="using-get-dscconfigurationstatus"></a><span data-ttu-id="5b950-110">Get-DscConfigurationStatus kullanma</span><span class="sxs-lookup"><span data-stu-id="5b950-110">Using Get-DscConfigurationStatus</span></span>

<span data-ttu-id="5b950-111">[Get-DscConfigurationStatus](https://technet.microsoft.com/library/mt517868.aspx) cmdlet'i, hedef düğüm yapılandırma durumu hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="5b950-111">The [Get-DscConfigurationStatus](https://technet.microsoft.com/library/mt517868.aspx) cmdlet gets information about configuration status from a target node.</span></span> <span data-ttu-id="5b950-112">Yapılandırma çalıştırma veya olup olmadığını başarılı hakkında üst düzey bilgileri içeren zengin bir nesne döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5b950-112">A rich object is returned that includes high-level information about whether or not the configuration run was successful or not.</span></span> <span data-ttu-id="5b950-113">Nesnesine gibi yapılandırma ayrıntılarını bulmak için incelemek:</span><span class="sxs-lookup"><span data-stu-id="5b950-113">You can dig into the object to discover details about the configuration run such as:</span></span>

- <span data-ttu-id="5b950-114">Başarısız olan tüm kaynakları</span><span class="sxs-lookup"><span data-stu-id="5b950-114">All of the resources that failed</span></span>
- <span data-ttu-id="5b950-115">Bir sistem yeniden başlatması herhangi bir kaynağa</span><span class="sxs-lookup"><span data-stu-id="5b950-115">Any resource that requested a reboot</span></span>
- <span data-ttu-id="5b950-116">Çalıştırma zaman yapılandırmasının meta-yapılandırma ayarları</span><span class="sxs-lookup"><span data-stu-id="5b950-116">Meta-Configuration settings at time of configuration run</span></span>
- <span data-ttu-id="5b950-117">VS.</span><span class="sxs-lookup"><span data-stu-id="5b950-117">Etc.</span></span>

<span data-ttu-id="5b950-118">Aşağıdaki parametre kümesi son yapılandırma Çalıştır durum bilgilerini döndürür:</span><span class="sxs-lookup"><span data-stu-id="5b950-118">The following parameter set returns the status information for the last configuration run:</span></span>

```
Get-DscConfigurationStatus [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```
<span data-ttu-id="5b950-119">Aşağıdaki parametre kümesi, önceki tüm yapılandırma çalıştırmalar için durum bilgileri döndürür:</span><span class="sxs-lookup"><span data-stu-id="5b950-119">The following parameter set returns the status information for all previous configuration runs:</span></span>

```
Get-DscConfigurationStatus -All
                           [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

## <a name="example"></a><span data-ttu-id="5b950-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="5b950-120">Example</span></span>

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

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a><span data-ttu-id="5b950-121">Betiğimde çalışmaz: betik hatalarını tanılamak için DSC kullanarak günlükleri</span><span class="sxs-lookup"><span data-stu-id="5b950-121">My script won't run: Using DSC logs to diagnose script errors</span></span>

<span data-ttu-id="5b950-122">Tüm Windows yazılım gibi DSC hatalarını ve olaylarını kaydeder [günlükleri](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) alanından görüntülenebilir [Olay Görüntüleyicisi'ni](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer).</span><span class="sxs-lookup"><span data-stu-id="5b950-122">Like all Windows software, DSC records errors and events in [logs](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) that can be viewed from the [Event Viewer](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer).</span></span>
<span data-ttu-id="5b950-123">Bu günlükleri İnceleme neden belirli bir işlem başarısız oldu ve hata gelecekte önlemek nasıl anlamanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5b950-123">Examining these logs can help you understand why a particular operation failed, and how to prevent failure in the future.</span></span> <span data-ttu-id="5b950-124">Yapılandırma komut dosyası yazma, bu nedenle, yazar olarak izleme hataları kolaylaştırmak, DSC günlük kaynak yapılandırmanızı ve DSC analitik olay günlüğüne ilerlemesini izlemek için kullanın zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="5b950-124">Writing configuration scripts can be tricky, so to make tracking errors easier as you author, use the DSC Log resource to track the progress of your configuration in the DSC Analytic event log.</span></span>

## <a name="where-are-dsc-event-logs"></a><span data-ttu-id="5b950-125">DSC olay günlükleri nerededir?</span><span class="sxs-lookup"><span data-stu-id="5b950-125">Where are DSC event logs?</span></span>

<span data-ttu-id="5b950-126">DSC olayları bulunan Olay Görüntüleyicisi'nde: **uygulamalar ve hizmetler günlükleri/Microsoft/Windows/Desired State Configuration**</span><span class="sxs-lookup"><span data-stu-id="5b950-126">In Event Viewer, DSC events are in: **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span></span>

<span data-ttu-id="5b950-127">Karşılık gelen PowerShell cmdlet [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), olay günlükleri görüntülemek için de çalıştırılabilir:</span><span class="sxs-lookup"><span data-stu-id="5b950-127">The corresponding PowerShell cmdlet, [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), can also be run to view the event logs:</span></span>

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

<span data-ttu-id="5b950-128">Yukarıda gösterildiği gibi DSC'ın birincil günlük adı olan **Microsoft -> Windows -> DSC** (Windows diğer günlük adlarla burada konuyu uzatmamak amacıyla gösterilmez).</span><span class="sxs-lookup"><span data-stu-id="5b950-128">As shown above, DSC's primary log name is **Microsoft->Windows->DSC** (other log names under Windows are not shown here for brevity).</span></span> <span data-ttu-id="5b950-129">Birincil ad tam günlük adı oluşturmak için kanal adına eklenir.</span><span class="sxs-lookup"><span data-stu-id="5b950-129">The primary name is appended to the channel name to create the complete log name.</span></span> <span data-ttu-id="5b950-130">DSC altyapısını esas olarak üç tür günlükleri Yazar: [işlemsel, Analitik ve hata ayıklama günlükleri](https://technet.microsoft.com/library/cc722404.aspx).</span><span class="sxs-lookup"><span data-stu-id="5b950-130">The DSC engine writes mainly into three types of logs: [Operational, Analytic, and Debug logs](https://technet.microsoft.com/library/cc722404.aspx).</span></span> <span data-ttu-id="5b950-131">Bu yana Analitik ve hata ayıklama günlükleri devre dışı bırakma varsayılan olarak, Olay Görüntüleyicisi'nde etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b950-131">Since the analytic and debug logs are turned off by default, you should enable them in Event Viewer.</span></span> <span data-ttu-id="5b950-132">Bunu yapmak için Windows PowerShell'de Show-EventLog yazarak Olay Görüntüleyicisi'ni açın; veya tıklayın **Başlat** düğmesini tıklatın, **Denetim Masası**, tıklayın **Yönetimsel Araçlar**ve ardından **Olay Görüntüleyicisi'ni**.</span><span class="sxs-lookup"><span data-stu-id="5b950-132">To do this, open Event Viewer by typing Show-EventLog in Windows PowerShell; or, click the **Start** button, click **Control Panel**, click **Administrative Tools**, and then click **Event Viewer**.</span></span>
<span data-ttu-id="5b950-133">Üzerinde **görünümü** Olay Görüntüleyicisi'nde menüsünü **Analitik ve hata ayıklama günlüklerini göster**.</span><span class="sxs-lookup"><span data-stu-id="5b950-133">On the **View** menu in Event viewer, click **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="5b950-134">Günlük adı analitik kanalı **Microsoft-Windows-Dsc/analitik**, ve hata ayıklama kanal **Microsoft-Windows-Dsc/Debug**.</span><span class="sxs-lookup"><span data-stu-id="5b950-134">The log name for the analytic channel is **Microsoft-Windows-Dsc/Analytic**, and the debug channel is **Microsoft-Windows-Dsc/Debug**.</span></span> <span data-ttu-id="5b950-135">Ayrıca kullanabileceğinizi [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) yardımcı programını kullanarak aşağıdaki örnekte gösterildiği gibi günlüklerini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="5b950-135">You could also use the [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) utility to enable the logs, as shown in the following example.</span></span>

```powershell
wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a><span data-ttu-id="5b950-136">DSC günlükleri ne içerir?</span><span class="sxs-lookup"><span data-stu-id="5b950-136">What do DSC logs contain?</span></span>

<span data-ttu-id="5b950-137">DSC günlükleri iletinin önem derecesine göre üç günlük kanalları üzerinden bölünür.</span><span class="sxs-lookup"><span data-stu-id="5b950-137">DSC logs are split over the three log channels based on the importance of the message.</span></span> <span data-ttu-id="5b950-138">DSC işlem günlüğünde tüm hata iletilerini içerir ve bir sorunu tanımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5b950-138">The operational log in DSC contains all error messages, and can be used to identify a problem.</span></span> <span data-ttu-id="5b950-139">Analitik günlüğünü daha yüksek bir olayların hacmine sahip ve hata oluştuğu belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b950-139">The analytic log has a higher volume of events, and can identify where error(s) occurred.</span></span> <span data-ttu-id="5b950-140">Bu kanal, ayrıntılı iletileri de (varsa) içerir.</span><span class="sxs-lookup"><span data-stu-id="5b950-140">This channel also contains verbose messages (if any).</span></span> <span data-ttu-id="5b950-141">Hata ayıklama günlüğünü nasıl hataları oluştu anlamanıza yardımcı olacak günlükleri içerir.</span><span class="sxs-lookup"><span data-stu-id="5b950-141">The debug log contains logs that can help you understand how the errors occurred.</span></span> <span data-ttu-id="5b950-142">DSC olay iletileri, her olay iletisi benzersiz bir DSC işlemini temsil eden bir iş kimliği ile başlayan şekilde yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5b950-142">DSC event messages are structured such that every event message begins with a job ID that uniquely represents a DSC operation.</span></span> <span data-ttu-id="5b950-143">Aşağıdaki örnekte, ilk olay işletimsel DSC oturum günlüğüne ileti almak çalışır.</span><span class="sxs-lookup"><span data-stu-id="5b950-143">The example below attempts to obtain the message from the first event logged into the operational DSC log.</span></span>

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

<span data-ttu-id="5b950-144">Kullanıcının bir DSC projeden toplama olayları sağlar. belirli bir yapı DSC olayları günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="5b950-144">DSC events are logged in a particular structure that enables the user to aggregate events from one DSC job.</span></span> <span data-ttu-id="5b950-145">Yapı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="5b950-145">The structure is as follows:</span></span>

```
Job ID : <Guid>
<Event Message>
```

## <a name="gathering-events-from-a-single-dsc-operation"></a><span data-ttu-id="5b950-146">Tek bir DSC işlemi toplama olayları</span><span class="sxs-lookup"><span data-stu-id="5b950-146">Gathering events from a single DSC operation</span></span>

<span data-ttu-id="5b950-147">DSC olay günlükleri, çeşitli DSC işlemleri tarafından oluşturulan olayları içerir.</span><span class="sxs-lookup"><span data-stu-id="5b950-147">DSC event logs contain events generated by various DSC operations.</span></span> <span data-ttu-id="5b950-148">Ancak, genellikle yalnızca tek bir belirli işlem hakkında endişe ayrıntılarla olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5b950-148">However, you'll usually be concerned with the detail about just one particular operation.</span></span> <span data-ttu-id="5b950-149">Tüm DSC günlükler her DSC işlem için benzersiz iş kimliği özelliği göre gruplandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="5b950-149">All DSC logs can be grouped by the job ID property that is unique for every DSC operation.</span></span> <span data-ttu-id="5b950-150">İş kimliği, tüm DSC olayları ilk özellik değeri olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5b950-150">The job ID is displayed as the first property value in all DSC events.</span></span> <span data-ttu-id="5b950-151">Aşağıdaki adımlarda, gruplandırılmış dizi yapıdaki tüm olayları ulaşıncaya kadar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b950-151">The following steps explain how to accumulate all events in a grouped array structure.</span></span>

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

<span data-ttu-id="5b950-152">Burada, değişken `$SeparateDscOperations` kimlikleri işi tarafından gruplandırılmış günlükleri içerir.</span><span class="sxs-lookup"><span data-stu-id="5b950-152">Here, the variable `$SeparateDscOperations` contains logs grouped by the job IDs.</span></span> <span data-ttu-id="5b950-153">Her dizi öğesi bu değişken grubunu erişimine günlükleri hakkında daha fazla bilgi için farklı bir DSC işlemi tarafından günlüğe kaydedilen olayları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5b950-153">Each array element of this variable represents a group of events logged by a different DSC operation, allowing access to more information about the logs.</span></span>

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

<span data-ttu-id="5b950-154">Veri değişkeni içinde ayıklayabilir `$SeparateDscOperations` kullanarak [Where-Object](https://technet.microsoft.com/library/ee177028.aspx).</span><span class="sxs-lookup"><span data-stu-id="5b950-154">You can extract the data in the variable `$SeparateDscOperations` using [Where-Object](https://technet.microsoft.com/library/ee177028.aspx).</span></span> <span data-ttu-id="5b950-155">DSC sorun giderme için verileri ayıklamak isteyebilirsiniz beş senaryolar aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5b950-155">Following are five scenarios in which you might want to extract data for troubleshooting DSC:</span></span>

### <a name="1-operations-failures"></a><span data-ttu-id="5b950-156">1: işlem hataları</span><span class="sxs-lookup"><span data-stu-id="5b950-156">1: Operations failures</span></span>

<span data-ttu-id="5b950-157">Tüm olaylar sahiptir [önem düzeyleri](https://msdn.microsoft.com/library/dd996917(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="5b950-157">All events have [severity levels](https://msdn.microsoft.com/library/dd996917(v=vs.85)).</span></span> <span data-ttu-id="5b950-158">Bu bilgiler hata olayları tanımlamak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="5b950-158">This information can be used to identify the error events:</span></span>

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}

Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a><span data-ttu-id="5b950-159">2: son yarım saat içinde çalıştırma işlemlerinin ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="5b950-159">2: Details of operations run in the last half hour</span></span>

<span data-ttu-id="5b950-160">`TimeCreated`, her Windows olay özelliği durumları olayın oluşturulduğu zaman.</span><span class="sxs-lookup"><span data-stu-id="5b950-160">`TimeCreated`, a property of every Windows event, states the time the event was created.</span></span> <span data-ttu-id="5b950-161">Bu özellik belirli bir tarih/saat nesnesi ile karşılaştırma tüm olayları filtrelemek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="5b950-161">Comparing this property with a particular date/time object can be used to filter all events:</span></span>

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}

Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a><span data-ttu-id="5b950-162">3: en son işlem iletileri</span><span class="sxs-lookup"><span data-stu-id="5b950-162">3: Messages from the latest operation</span></span>

<span data-ttu-id="5b950-163">En son işlemi dizi grubunun ilk dizininde depolanan `$SeparateDscOperations`.</span><span class="sxs-lookup"><span data-stu-id="5b950-163">The latest operation is stored in the first index of the array group `$SeparateDscOperations`.</span></span>
<span data-ttu-id="5b950-164">Dizin 0 için grubun iletileri sorgulama en son işlem için tüm iletileri döndürür:</span><span class="sxs-lookup"><span data-stu-id="5b950-164">Querying the group's messages for index 0 returns all messages for the latest operation:</span></span>

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

### <a name="4-error-messages-logged-for-recent-failed-operations"></a><span data-ttu-id="5b950-165">4: son başarısız işlemler için günlüğe hata iletileri</span><span class="sxs-lookup"><span data-stu-id="5b950-165">4: Error messages logged for recent failed operations</span></span>

<span data-ttu-id="5b950-166">`$SeparateDscOperations[0].Group` en son işlemi için olaylar kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="5b950-166">`$SeparateDscOperations[0].Group` contains a set of events for the latest operation.</span></span> <span data-ttu-id="5b950-167">Çalıştırma `Where-Object` olayları filtrelemek için cmdlet tabanlı üzerinde kullanıcıların düzeyi görünen adı.</span><span class="sxs-lookup"><span data-stu-id="5b950-167">Run the `Where-Object` cmdlet to filter the events based on their level display name.</span></span> <span data-ttu-id="5b950-168">Sonuçlar depolanır `$myFailedEvent` değişken olabilen daha fazla olay iletisi almayı dissected:</span><span class="sxs-lookup"><span data-stu-id="5b950-168">Results are stored in the `$myFailedEvent` variable, which can be further dissected to get the event message:</span></span>

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message

Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a><span data-ttu-id="5b950-169">5: belirli bir proje kimliği için oluşturulan tüm olaylar</span><span class="sxs-lookup"><span data-stu-id="5b950-169">5: All events generated for a particular job ID.</span></span>

<span data-ttu-id="5b950-170">`$SeparateDscOperations` grupları, her biri benzersiz iş kimliği ada sahip bir dizisi</span><span class="sxs-lookup"><span data-stu-id="5b950-170">`$SeparateDscOperations` is an array of groups, each of which has the name as the unique job ID.</span></span> <span data-ttu-id="5b950-171">Çalıştırarak `Where-Object` cmdlet'i, bu gruplara belirli iş Kimliğine sahip olayı ayıklamak:</span><span class="sxs-lookup"><span data-stu-id="5b950-171">By running the `Where-Object` cmdlet, you can extract those groups of events that have a particular job ID:</span></span>

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

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a><span data-ttu-id="5b950-172">DSC çözümlemek için xDscDiagnostics kullanarak günlükleri</span><span class="sxs-lookup"><span data-stu-id="5b950-172">Using xDscDiagnostics to analyze DSC logs</span></span>

<span data-ttu-id="5b950-173">**xDscDiagnostics** DSC hataları makinenizde çözümlemenize yardımcı olabilecek çeşitli işlevler içeren bir PowerShell modülüdür.</span><span class="sxs-lookup"><span data-stu-id="5b950-173">**xDscDiagnostics** is a PowerShell module that consists of several functions that can help analyze DSC failures on your machine.</span></span> <span data-ttu-id="5b950-174">Bu işlevler, tüm yerel olayları son DSC işlemlerden veya uzak bilgisayarlarda DSC olayları (geçerli kimlik bilgileriyle) belirlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5b950-174">These functions can help you identify all local events from past DSC operations, or DSC events on remote computers (with valid credentials).</span></span> <span data-ttu-id="5b950-175">Burada, DSC işlemi terimi, bir tek benzersiz DSC yürütmeyi, başlangıçtan sonuna tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5b950-175">Here, the term DSC operation is used to define a single unique DSC execution from its start to its end.</span></span> <span data-ttu-id="5b950-176">Örneğin, `Test-DscConfiguration` ayrı bir DSC işlemi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5b950-176">For example, `Test-DscConfiguration` would be a separate DSC operation.</span></span> <span data-ttu-id="5b950-177">Benzer şekilde, her diğer cmdlet DSC (gibi `Get-DscConfiguration`, `Start-DscConfiguration`, vs.) her ayrı DSC işlem olarak tanımlanamadı.</span><span class="sxs-lookup"><span data-stu-id="5b950-177">Similarly, every other cmdlet in DSC (such as `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) could each be identified as separate DSC operations.</span></span> <span data-ttu-id="5b950-178">İşlevler, açıklanmıştır [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span><span class="sxs-lookup"><span data-stu-id="5b950-178">The functions are explained at [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span></span> <span data-ttu-id="5b950-179">Yardım kullanılabilir çalıştırarak `Get-Help <cmdlet name>`.</span><span class="sxs-lookup"><span data-stu-id="5b950-179">Help is available by running `Get-Help <cmdlet name>`.</span></span>

### <a name="getting-details-of-dsc-operations"></a><span data-ttu-id="5b950-180">DSC işlemlerinin ayrıntıları alınıyor</span><span class="sxs-lookup"><span data-stu-id="5b950-180">Getting details of DSC operations</span></span>

<span data-ttu-id="5b950-181">`Get-xDscOperation` İşlevi bir veya birden çok bilgisayarda çalıştırma DSC işlemlerinin sonuçlarını bulmanıza olanak tanır ve olayları koleksiyonu içeren bir nesne her DSC işlemiyle oluşturulan döndürür.</span><span class="sxs-lookup"><span data-stu-id="5b950-181">The `Get-xDscOperation` function lets you find the results of the DSC operations that run on one or multiple computers, and returns an object that contains the collection of events produced by each DSC operation.</span></span> <span data-ttu-id="5b950-182">Örneğin, aşağıdaki çıktı, üç komutu çalıştırılamadı.</span><span class="sxs-lookup"><span data-stu-id="5b950-182">For example, in the following output, three commands were run.</span></span> <span data-ttu-id="5b950-183">İlk geçirilen ve diğer iki başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="5b950-183">The first one passed, and the other two failed.</span></span> <span data-ttu-id="5b950-184">Bu sonuçları çıktısında özetlenir `Get-xDscOperation`.</span><span class="sxs-lookup"><span data-stu-id="5b950-184">These results are summarized in the output of `Get-xDscOperation`.</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

<span data-ttu-id="5b950-185">Yalnızca sonuçları kullanarak en son işlemler için istediğiniz belirtebilirsiniz `Newest` parametresi:</span><span class="sxs-lookup"><span data-stu-id="5b950-185">You can also specify that you want only results for the most recent operations by using the `Newest` parameter:</span></span>

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

### <a name="getting-details-of-dsc-events"></a><span data-ttu-id="5b950-186">DSC olayların ayrıntıları alınıyor</span><span class="sxs-lookup"><span data-stu-id="5b950-186">Getting details of DSC events</span></span>

<span data-ttu-id="5b950-187">`Trace-xDscOperation` Cmdlet, olaylar, olay türlerini koleksiyonu içeren bir nesne döndürür ve ileti çıkış oluşturulan belirli bir DSC işlemi.</span><span class="sxs-lookup"><span data-stu-id="5b950-187">The `Trace-xDscOperation` cmdlet returns an object containing a collection of events, their event types, and the message output generated from a particular DSC operation.</span></span> <span data-ttu-id="5b950-188">Genellikle, ne zaman bulduğunuz hata kullanarak işlemleri hiçbirinde `Get-xDscOperation`, hangi olayların hata neden olduğunu bulmak için bu işlemi izleme.</span><span class="sxs-lookup"><span data-stu-id="5b950-188">Typically, when you find a failure in any of the operations using `Get-xDscOperation`, you would trace that operation to find out which of the events caused a failure.</span></span>

<span data-ttu-id="5b950-189">Kullanım `SequenceID` belirli bir bilgisayar için belirli bir işlemi için olaylar almak için parametre.</span><span class="sxs-lookup"><span data-stu-id="5b950-189">Use the `SequenceID` parameter to get the events for a specific operation for a specific computer.</span></span>
<span data-ttu-id="5b950-190">Örneğin, belirttiğiniz bir `SequenceID` 9, `Trace-xDscOperaion` son işlemden 9 olan DSC işlemi için izleme alın:</span><span class="sxs-lookup"><span data-stu-id="5b950-190">For example, if you specify a `SequenceID` of 9, `Trace-xDscOperaion` get the trace for the DSC operation that was 9th from the last operation:</span></span>

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

<span data-ttu-id="5b950-191">Geçirmek **GUID** belirli bir DSC işlemi için atanan (tarafından döndürülen `Get-xDscOperation` cmldet) bu DSC işlem için olay ayrıntılarını almak için:</span><span class="sxs-lookup"><span data-stu-id="5b950-191">Pass the **GUID** assigned to a specific DSC operation (as returned by the `Get-xDscOperation` cmldet) to get the event details for that DSC operation:</span></span>

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

<span data-ttu-id="5b950-192">Unutmayın, beri `Trace-xDscOperation` analitik, hata ayıklama olaylarını toplar ve işlemsel günlükleri, yukarıda açıklandığı gibi bu günlükleri etkinleştirmenizi ister.</span><span class="sxs-lookup"><span data-stu-id="5b950-192">Note that, since `Trace-xDscOperation` aggregates events from the Analytic, Debug, and Operational logs, it will prompt you to enable these logs as described above.</span></span>

<span data-ttu-id="5b950-193">Olaylar üzerinde çıkışını kaydederek bilgileri alternatif olarak, toplayabilirsiniz `Trace-xDscOperation` bir değişkenin içine.</span><span class="sxs-lookup"><span data-stu-id="5b950-193">Alternately, you can gather information on the events by saving the output of `Trace-xDscOperation` into a variable.</span></span> <span data-ttu-id="5b950-194">Belirli bir DSC işlem için tüm olayları görüntülemek için aşağıdaki komutları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b950-194">You can use the following commands to display all the events for a particular DSC operation.</span></span>

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

<span data-ttu-id="5b950-195">Bu aynı sonuçları görüntüler `Get-WinEvent` gibi aşağıdaki çıktıyı cmdlet'inin:</span><span class="sxs-lookup"><span data-stu-id="5b950-195">This will display the same results as the `Get-WinEvent` cmdlet, such as in the output below:</span></span>

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

<span data-ttu-id="5b950-196">İdeal olarak, ilk kullanacağınız `Get-xDscOperation` yapılandırma makinelerinizde çalışan en son birkaç DSC listesi.</span><span class="sxs-lookup"><span data-stu-id="5b950-196">Ideally, you would first use `Get-xDscOperation` to list out the last few DSC configuration runs on your machines.</span></span> <span data-ttu-id="5b950-197">Aşağıdaki (kendi SequenceId: veya JobId kullanılarak) herhangi tek bir işlem ile inceleyebilirsiniz `Trace-xDscOperation` perde arkasında neler kişiselleştirmeden bulunacak.</span><span class="sxs-lookup"><span data-stu-id="5b950-197">Following this, you can examine any single operation (using its SequenceID or JobID) with `Trace-xDscOperation` to discover what it did behind the scenes.</span></span>

### <a name="getting-events-for-a-remote-computer"></a><span data-ttu-id="5b950-198">Uzak bir bilgisayar için olayları alma</span><span class="sxs-lookup"><span data-stu-id="5b950-198">Getting events for a remote computer</span></span>

<span data-ttu-id="5b950-199">Kullanım `ComputerName` parametresinin `Trace-xDscOperation` uzak bir bilgisayarda olay ayrıntılarını almak için cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5b950-199">Use the `ComputerName` parameter of the `Trace-xDscOperation` cmdlet to get the event details on a remote computer.</span></span> <span data-ttu-id="5b950-200">Bunu yapmak için önce uzak bilgisayarda Uzaktan yönetime izin vermek için bir güvenlik duvarı kuralı oluşturmak sahip:</span><span class="sxs-lookup"><span data-stu-id="5b950-200">Before you can do this, you have to create a firewall rule to allow remote administration on the remote computer:</span></span>

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```

<span data-ttu-id="5b950-201">Bu bilgisayar çağrınız belirtebilirsiniz artık `Trace-xDscOperation`:</span><span class="sxs-lookup"><span data-stu-id="5b950-201">Now you can specify that computer in your call to `Trace-xDscOperation`:</span></span>

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

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a><span data-ttu-id="5b950-202">Kaynaklarım güncelleştirme olmayacaktır: önbelleğini sıfırlama</span><span class="sxs-lookup"><span data-stu-id="5b950-202">My resources won't update: How to reset the cache</span></span>

<span data-ttu-id="5b950-203">DSC altyapısını verimliliği amaçlar için bir PowerShell modülü olarak uygulanan kaynakları önbelleğe alır.</span><span class="sxs-lookup"><span data-stu-id="5b950-203">The DSC engine caches resources implemented as a PowerShell module for efficiency purposes.</span></span>
<span data-ttu-id="5b950-204">Ancak, bir kaynak yazma ve işlemi yeniden başlatılana kadar DSC önbelleğe alınmış sürümünü yükler için aynı anda test bu sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="5b950-204">However, this can cause problems when you are authoring a resource and testing it simultaneously because DSC will load the cached version until the process is restarted.</span></span> <span data-ttu-id="5b950-205">DSC daha yeni sürümünü yükleme yapmak için tek açıkça DSC altyapısını barındıran işlemi sonlandırmak için yoludur.</span><span class="sxs-lookup"><span data-stu-id="5b950-205">The only way to make DSC load the newer version is to explicitly kill the process hosting the DSC engine.</span></span>

<span data-ttu-id="5b950-206">Benzer şekilde, çalıştırdığınızda `Start-DscConfiguration`, ekleme ve özel bir kaynağı değiştirme sonra değişiklik sürece yürütülmeyebilir veya bilgisayar yeniden başlatılana kadar.</span><span class="sxs-lookup"><span data-stu-id="5b950-206">Similarly, when you run `Start-DscConfiguration`, after adding and modifying a custom resource, the modification may not execute unless, or until, the computer is rebooted.</span></span> <span data-ttu-id="5b950-207">DSC WMI sağlayıcısı ana bilgisayar işlemi (WmiPrvSE) çalışır ve genellikle aynı anda çalışan WmiPrvSE birçok örneği mevcuttur nedeni budur.</span><span class="sxs-lookup"><span data-stu-id="5b950-207">This is because DSC runs in the WMI Provider Host Process (WmiPrvSE), and usually, there are many instances of WmiPrvSE running at once.</span></span> <span data-ttu-id="5b950-208">Bilgisayarı yeniden başlattığınızda ana bilgisayar işlemi başlatılır ve önbellek temizlenir.</span><span class="sxs-lookup"><span data-stu-id="5b950-208">When you reboot, the host process is restarted and the cache is cleared.</span></span>

<span data-ttu-id="5b950-209">Başarılı bir şekilde yapılandırmayı geri dönüşüm ve yeniden başlatmaya gerek kalmadan önbelleği temizlemek için durdurun ve ana bilgisayar işlemi yeniden gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b950-209">To successfully recycle the configuration and clear the cache without rebooting, you must stop and then restart the host process.</span></span> <span data-ttu-id="5b950-210">Bu yapabildiği işlemi tanımlamak, durdurmak ve yeniden tek başına örnek temelinde, yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="5b950-210">This can be done on a per instance basis, whereby you identify the process, stop it, and restart it.</span></span> <span data-ttu-id="5b950-211">Veya, kullanabileceğiniz `DebugMode`PowerShell DSC kaynağı yeniden yüklemek için aşağıda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="5b950-211">Or, you can use `DebugMode`, as demonstrated below, to reload the PowerShell DSC resource.</span></span>

<span data-ttu-id="5b950-212">DSC altyapısını barındıran işlemi tanımlamak ve tek başına örnek temelinde durdurmak için DSC altyapısını barındıran WmiPrvSE işlem Kimliğini listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b950-212">To identify which process is hosting the DSC engine and stop it on a per instance basis, you can list the process ID of the WmiPrvSE which is hosting the DSC engine.</span></span> <span data-ttu-id="5b950-213">Ardından, sağlayıcı güncelleştirmek için çalıştırın ve aşağıdaki komutları kullanarak WmiPrvSE işlemi durdurmak **Başlat-DscConfiguration** yeniden.</span><span class="sxs-lookup"><span data-stu-id="5b950-213">Then, to update the provider, stop the WmiPrvSE process using the commands below, and then run **Start-DscConfiguration** again.</span></span>

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

## <a name="using-debugmode"></a><span data-ttu-id="5b950-214">DebugMode kullanma</span><span class="sxs-lookup"><span data-stu-id="5b950-214">Using DebugMode</span></span>

<span data-ttu-id="5b950-215">DSC yerel Configuration Manager (kullanılacak LCM) yapılandırabileceğiniz `DebugMode` her zaman, ana bilgisayar işlemi başlatıldığında önbelleği temizlemek için.</span><span class="sxs-lookup"><span data-stu-id="5b950-215">You can configure the DSC Local Configuration Manager (LCM) to use `DebugMode` to always clear the cache when the host process is restarted.</span></span> <span data-ttu-id="5b950-216">Ayarlandığında **TRUE**, PowerShell DSC kaynağı her zaman yeniden yüklemek altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b950-216">When set to **TRUE**, it causes the engine to always reload the PowerShell DSC resource.</span></span> <span data-ttu-id="5b950-217">İşiniz bittiğinde, kaynak yazma, bunu ayarlayabilirsiniz geri **FALSE** ve altyapısı, modülleri önbelleğe alma davranışını geri döner.</span><span class="sxs-lookup"><span data-stu-id="5b950-217">Once you are done writing your resource, you can set it back to **FALSE** and the engine will revert to its behavior of caching the modules.</span></span>

<span data-ttu-id="5b950-218">Gösterilecek bir örnek aşağıdadır nasıl `DebugMode` önbellek otomatik olarak yenileyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b950-218">Following is a demonstration to show how `DebugMode` can automatically refresh the cache.</span></span> <span data-ttu-id="5b950-219">İlk olarak, varsayılan yapılandırmayı göz atalım:</span><span class="sxs-lookup"><span data-stu-id="5b950-219">First, let's look at the default configuration:</span></span>

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

<span data-ttu-id="5b950-220">Gördüğünüz gibi `DebugMode` ayarlanır **"None"**.</span><span class="sxs-lookup"><span data-stu-id="5b950-220">You can see that `DebugMode` is set to **"None"**.</span></span>

<span data-ttu-id="5b950-221">Ayarlamak için `DebugMode` gösterim, aşağıdaki PowerShell kaynağı kullanın:</span><span class="sxs-lookup"><span data-stu-id="5b950-221">To set up the `DebugMode` demonstration, use the following PowerShell resource:</span></span>

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

<span data-ttu-id="5b950-222">Şimdi, adlı yukarıdaki kaynak kullanarak yapılandırma Yazar `TestProviderDebugMode`:</span><span class="sxs-lookup"><span data-stu-id="5b950-222">Now, author a configuration using the above resource called `TestProviderDebugMode`:</span></span>

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

<span data-ttu-id="5b950-223">Göreceksiniz dosyasının içeriğini: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` olduğu **1**.</span><span class="sxs-lookup"><span data-stu-id="5b950-223">You will see that the contents of file: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` is **1**.</span></span>

<span data-ttu-id="5b950-224">Artık, aşağıdaki betiği kullanarak sağlayıcı kodu güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="5b950-224">Now, update the provider code using the following script:</span></span>

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

<span data-ttu-id="5b950-225">Bu betik, rastgele bir sayı oluşturur ve sağlayıcı kodu uygun şekilde güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="5b950-225">This script generates a random number and updates the provider code accordingly.</span></span> <span data-ttu-id="5b950-226">İle `DebugMode` dosyasının içeriğini false olarak ayarlayın "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" hiçbir zaman değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="5b950-226">With `DebugMode` set to false, the contents of the file "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" are never changed.</span></span>

<span data-ttu-id="5b950-227">Şimdi, `DebugMode` için **"ForceModuleImport"** yapılandırma betiğinizde:</span><span class="sxs-lookup"><span data-stu-id="5b950-227">Now, set `DebugMode` to **"ForceModuleImport"** in your configuration script:</span></span>

```powershell
LocalConfigurationManager
{
    DebugMode = "ForceModuleImport"
}
```

<span data-ttu-id="5b950-228">Yukarıdaki komut dosyasını yeniden çalıştırdığınızda, dosyanın içeriğini her seferinde farklı olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="5b950-228">When you run the above script again, you will see that the content of the file is different every time.</span></span> <span data-ttu-id="5b950-229">(Çalıştırabileceğiniz `Get-DscConfiguration` bunu kontrol etmek için).</span><span class="sxs-lookup"><span data-stu-id="5b950-229">(You can run `Get-DscConfiguration` to check it).</span></span> <span data-ttu-id="5b950-230">(Komut dosyasını çalıştırırken sonuçlarınızı farklı olabilir) iki ek çalıştırma sonucunu aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="5b950-230">Below is the result of two additional runs (your results may be different when you run the script):</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5b950-231">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="5b950-231">See Also</span></span>

### <a name="reference"></a><span data-ttu-id="5b950-232">Başvuru</span><span class="sxs-lookup"><span data-stu-id="5b950-232">Reference</span></span>

- [<span data-ttu-id="5b950-233">DSC Log kaynağı</span><span class="sxs-lookup"><span data-stu-id="5b950-233">DSC Log Resource</span></span>](logResource.md)

### <a name="concepts"></a><span data-ttu-id="5b950-234">Kavramlar</span><span class="sxs-lookup"><span data-stu-id="5b950-234">Concepts</span></span>

- [<span data-ttu-id="5b950-235">Derleme özel Windows PowerShell Desired State Configuration kaynakları</span><span class="sxs-lookup"><span data-stu-id="5b950-235">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

### <a name="other-resources"></a><span data-ttu-id="5b950-236">Diğer Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="5b950-236">Other Resources</span></span>

- <span data-ttu-id="5b950-237">[Windows PowerShell cmdlet'leri Desired State Configuration](https://technet.microsoft.com/library/dn521624(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="5b950-237">[Windows PowerShell Desired State Configuration Cmdlets](https://technet.microsoft.com/library/dn521624(v=wps.630).aspx)</span></span>
