---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC’de sorun giderme
ms.openlocfilehash: c08f91b514aae438578fa278228fe5ec879a4012
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="troubleshooting-dsc"></a><span data-ttu-id="1a07c-103">DSC’de sorun giderme</span><span class="sxs-lookup"><span data-stu-id="1a07c-103">Troubleshooting DSC</span></span>

><span data-ttu-id="1a07c-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1a07c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="1a07c-105">Bu konuda ortaya sorun çıktığında DSC gidermenin yolları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1a07c-105">This topic describes ways to troubleshoot DSC when problems arise.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="1a07c-106">WinRM bağımlılık</span><span class="sxs-lookup"><span data-stu-id="1a07c-106">WinRM Dependency</span></span>

<span data-ttu-id="1a07c-107">Windows PowerShell istenen durum yapılandırması (DSC) üzerinde WinRM bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1a07c-107">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="1a07c-108">WinRM Windows Server 2008 R2 ve Windows 7 varsayılan olarak etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="1a07c-108">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="1a07c-109">Çalıştırma ```Set-WSManQuickConfig```, Windows PowerShell'de yükseltilmiş WinRM etkinleştirmek için oturumu.</span><span class="sxs-lookup"><span data-stu-id="1a07c-109">Run ```Set-WSManQuickConfig```, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="using-get-dscconfigurationstatus"></a><span data-ttu-id="1a07c-110">Get-DscConfigurationStatus kullanma</span><span class="sxs-lookup"><span data-stu-id="1a07c-110">Using Get-DscConfigurationStatus</span></span>

<span data-ttu-id="1a07c-111">[Get-DscConfigurationStatus](https://technet.microsoft.com/library/mt517868.aspx) cmdlet'i, hedef düğüm yapılandırması durumu hakkındaki bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="1a07c-111">The [Get-DscConfigurationStatus](https://technet.microsoft.com/library/mt517868.aspx) cmdlet gets information about configuration status from a target node.</span></span>
<span data-ttu-id="1a07c-112">Yapılandırma çalıştırma veya desteklemediğini başarılı hakkında üst düzey bilgileri içeren zengin bir nesne döndürdü.</span><span class="sxs-lookup"><span data-stu-id="1a07c-112">A rich object is returned that includes high-level information about whether or not the configuration run was successful or not.</span></span> <span data-ttu-id="1a07c-113">Gibi çalıştırmak yapılandırması hakkında ayrıntıları keşfetmek için nesnesine derinliklerine:</span><span class="sxs-lookup"><span data-stu-id="1a07c-113">You can dig into the object to discover details about the configuration run such as:</span></span>

* <span data-ttu-id="1a07c-114">Tüm başarısız kaynakları</span><span class="sxs-lookup"><span data-stu-id="1a07c-114">All of the resources that failed</span></span>
* <span data-ttu-id="1a07c-115">Bir sistem yeniden başlatması herhangi bir kaynak</span><span class="sxs-lookup"><span data-stu-id="1a07c-115">Any resource that requested a reboot</span></span>
* <span data-ttu-id="1a07c-116">Çalışma zamanında yapılandırmasının meta yapılandırma ayarları</span><span class="sxs-lookup"><span data-stu-id="1a07c-116">Meta-Configuration settings at time of configuration run</span></span>
* <span data-ttu-id="1a07c-117">VS.</span><span class="sxs-lookup"><span data-stu-id="1a07c-117">Etc.</span></span>

<span data-ttu-id="1a07c-118">Aşağıdaki parametre kümesi çalıştırmak son yapılandırma durum bilgilerini döndürür:</span><span class="sxs-lookup"><span data-stu-id="1a07c-118">The following parameter set returns the status information for the last configuration run:</span></span>

```powershell
Get-DscConfigurationStatus  [-CimSession <CimSession[]>]
                            [-ThrottleLimit <int>]
                            [-AsJob]
                            [<CommonParameters>]
```
<span data-ttu-id="1a07c-119">Aşağıdaki parametre kümesi önceki tüm yapılandırma çalışmaları için durum bilgilerini döndürür:</span><span class="sxs-lookup"><span data-stu-id="1a07c-119">The following parameter set returns the status information for all previous configuration runs:</span></span>

```powershell
Get-DscConfigurationStatus  -All
                            [-CimSession <CimSession[]>]
                            [-ThrottleLimit <int>]
                            [-AsJob]
                            [<CommonParameters>]
```

## <a name="example"></a><span data-ttu-id="1a07c-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a07c-120">Example</span></span>

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

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a><span data-ttu-id="1a07c-121">My komut çalışmaz: kullanarak DSC günlüklerini komut dosyası hataları tanılamak için</span><span class="sxs-lookup"><span data-stu-id="1a07c-121">My script won’t run: Using DSC logs to diagnose script errors</span></span>

<span data-ttu-id="1a07c-122">Tüm Windows yazılımı gibi DSC hatalarını ve olaylarını kaydeder [günlükleri](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) alanından görüntülenebilir [Olay Görüntüleyicisi'ni](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer).</span><span class="sxs-lookup"><span data-stu-id="1a07c-122">Like all Windows software, DSC records errors and events in [logs](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) that can be viewed from the [Event Viewer](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer).</span></span> <span data-ttu-id="1a07c-123">Bu günlükler inceleyerek neden belirli bir işlem başarısız oldu, hata gelecekte oluşmasını engellemek nasıl anlamanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1a07c-123">Examining these logs can help you understand why a particular operation failed, and how to prevent failure in the future.</span></span> <span data-ttu-id="1a07c-124">Yapılandırma komut dosyası yazma bu nedenle, yazar olarak izleme hataları kolaylaştırmak, DSC günlük kaynak yapılandırmanızı DSC analitik olay günlüğünde ilerlemesini izlemek için kullanın zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="1a07c-124">Writing configuration scripts can be tricky, so to make tracking errors easier as you author, use the DSC Log resource to track the progress of your configuration in the DSC Analytic event log.</span></span>

## <a name="where-are-dsc-event-logs"></a><span data-ttu-id="1a07c-125">DSC olay günlüklerini nerede?</span><span class="sxs-lookup"><span data-stu-id="1a07c-125">Where are DSC event logs?</span></span>

<span data-ttu-id="1a07c-126">DSC olayları bulunan Olay Görüntüleyicisi'nde: **uygulamalar ve hizmetler günlükleri/Microsoft/Windows/istenen durum yapılandırması**</span><span class="sxs-lookup"><span data-stu-id="1a07c-126">In Event Viewer, DSC events are in: **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span></span>

<span data-ttu-id="1a07c-127">Karşılık gelen PowerShell cmdlet'ini [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), olay günlüklerini görüntülemek için da çalıştırılabilir:</span><span class="sxs-lookup"><span data-stu-id="1a07c-127">The corresponding PowerShell cmdlet, [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), can also be run to view the event logs:</span></span>

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

<span data-ttu-id="1a07c-128">Yukarıda gösterildiği gibi DSC'SİNİN birincil günlük adıdır **Microsoft -> Windows DSC ->** (diğer günlük adları Windows altında burada okumanızdır gösterilmez).</span><span class="sxs-lookup"><span data-stu-id="1a07c-128">As shown above, DSC’s primary log name is **Microsoft->Windows->DSC** (other log names under Windows are not shown here for brevity).</span></span> <span data-ttu-id="1a07c-129">Birincil adı tam günlük adını oluşturmak için kanal ada eklenir.</span><span class="sxs-lookup"><span data-stu-id="1a07c-129">The primary name is appended to the channel name to create the complete log name.</span></span> <span data-ttu-id="1a07c-130">DSC altyapısı genellikle üç tür günlükleri Yazar: [işlemsel Analitik ve hata ayıklama günlüklerini](https://technet.microsoft.com/library/cc722404.aspx).</span><span class="sxs-lookup"><span data-stu-id="1a07c-130">The DSC engine writes mainly into three types of logs: [Operational, Analytic, and Debug logs](https://technet.microsoft.com/library/cc722404.aspx).</span></span> <span data-ttu-id="1a07c-131">Bu yana Analitik ve hata ayıklama günlükleri devre dışı bırakma varsayılan olarak, Olay Görüntüleyicisi'nde etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1a07c-131">Since the analytic and debug logs are turned off by default, you should enable them in Event Viewer.</span></span> <span data-ttu-id="1a07c-132">Bunu yapmak için Windows PowerShell'de Göster olay günlüğüne yazarak Olay Görüntüleyicisi'ni açın; veya tıklatın **Başlat** düğmesini tıklatın, **Denetim Masası**, tıklatın **Yönetimsel Araçlar**ve ardından **Olay Görüntüleyicisi'ni**.</span><span class="sxs-lookup"><span data-stu-id="1a07c-132">To do this, open Event Viewer by typing Show-EventLog in Windows PowerShell; or, click the **Start** button, click **Control Panel**, click **Administrative Tools**, and then click **Event Viewer**.</span></span> <span data-ttu-id="1a07c-133">Üzerinde **Görünüm** Olay Görüntüleyicisi'nde menüsünü **Analitik ve hata ayıklama günlüklerini göster**.</span><span class="sxs-lookup"><span data-stu-id="1a07c-133">On the **View** menu in Event viewer, click **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="1a07c-134">Günlük adı analitik kanalı **Microsoft-Windows-Dsc/analitik**, ve hata ayıklama kanalıdır **Microsoft-Windows-Dsc/Debug**.</span><span class="sxs-lookup"><span data-stu-id="1a07c-134">The log name for the analytic channel is **Microsoft-Windows-Dsc/Analytic**, and the debug channel is **Microsoft-Windows-Dsc/Debug**.</span></span> <span data-ttu-id="1a07c-135">De kullanabilirsiniz [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) yardımcı programını kullanarak aşağıdaki örnekte gösterildiği gibi günlüklerini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="1a07c-135">You could also use the [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) utility to enable the logs, as shown in the following example.</span></span>

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a><span data-ttu-id="1a07c-136">DSC günlükleri neler içerir?</span><span class="sxs-lookup"><span data-stu-id="1a07c-136">What do DSC logs contain?</span></span>

<span data-ttu-id="1a07c-137">DSC günlükleri ileti önemini dayalı üç günlük kanalları üzerinden bölünür.</span><span class="sxs-lookup"><span data-stu-id="1a07c-137">DSC logs are split over the three log channels based on the importance of the message.</span></span> <span data-ttu-id="1a07c-138">DSC işlem günlüğünde tüm hata iletilerini içerir ve bir sorunu tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1a07c-138">The operational log in DSC contains all error messages, and can be used to identify a problem.</span></span> <span data-ttu-id="1a07c-139">Analitik günlük olaylarının daha yüksek bir birimin vardır ve hatalarla oluştuğu tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a07c-139">The analytic log has a higher volume of events, and can identify where error(s) occurred.</span></span> <span data-ttu-id="1a07c-140">Bu kanal, ayrıca (varsa) ayrıntılı iletiler içerir.</span><span class="sxs-lookup"><span data-stu-id="1a07c-140">This channel also contains verbose messages (if any).</span></span> <span data-ttu-id="1a07c-141">Hata ayıklama günlüğü nasıl hataları oluştu anlamanıza yardımcı olacak günlükleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1a07c-141">The debug log contains logs that can help you understand how the errors occurred.</span></span> <span data-ttu-id="1a07c-142">Her olay iletisi benzersiz olarak DSC işlemini temsil eden bir iş kimliği ile başlar, DSC olay iletileri yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1a07c-142">DSC event messages are structured such that every event message begins with a job ID that uniquely represents a DSC operation.</span></span> <span data-ttu-id="1a07c-143">Aşağıdaki örnek işletimsel DSC günlüğüne kaydedilmiş ilk olayı ileti almak çalışır.</span><span class="sxs-lookup"><span data-stu-id="1a07c-143">The example below attempts to obtain the message from the first event logged into the operational DSC log.</span></span>

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

<span data-ttu-id="1a07c-144">DSC olaylar kullanıcının bir DSC işten toplama olaylarına sağlayan belirli bir yapı günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="1a07c-144">DSC events are logged in a particular structure that enables the user to aggregate events from one DSC job.</span></span> <span data-ttu-id="1a07c-145">Yapısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="1a07c-145">The structure is as follows:</span></span>

<span data-ttu-id="1a07c-146">**İş Kimliği: <Guid>**
**<Event Message>**</span><span class="sxs-lookup"><span data-stu-id="1a07c-146">**Job ID : <Guid>**
**<Event Message>**</span></span>

## <a name="gathering-events-from-a-single-dsc-operation"></a><span data-ttu-id="1a07c-147">Tek bir DSC işlem toplama olayları</span><span class="sxs-lookup"><span data-stu-id="1a07c-147">Gathering events from a single DSC operation</span></span>

<span data-ttu-id="1a07c-148">DSC olay günlüklerini çeşitli DSC işlemleri tarafından oluşturulan olayları içerir.</span><span class="sxs-lookup"><span data-stu-id="1a07c-148">DSC event logs contain events generated by various DSC operations.</span></span> <span data-ttu-id="1a07c-149">Ancak, genellikle ayrıntılarla tek belirli işlemi hakkında endişe olmanız.</span><span class="sxs-lookup"><span data-stu-id="1a07c-149">However, you’ll usually be concerned with the detail about just one particular operation.</span></span> <span data-ttu-id="1a07c-150">Tüm DSC günlükler, her DSC işlem için benzersiz olan iş kimliği özelliği tarafından gruplandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="1a07c-150">All DSC logs can be grouped by the job ID property that is unique for every DSC operation.</span></span> <span data-ttu-id="1a07c-151">İş kimliği, tüm DSC olayları ilk özellik değeri olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1a07c-151">The job ID is displayed as the first property value in all DSC events.</span></span> <span data-ttu-id="1a07c-152">Aşağıdaki adımları gruplandırılmış dizi yapısındaki tüm olayları birikmesini açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1a07c-152">The following steps explain how to accumulate all events in a grouped array structure.</span></span>

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

<span data-ttu-id="1a07c-153">Burada, değişkeni `$SeparateDscOperations` kimlikleri iş tarafından gruplandırılmış günlükleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1a07c-153">Here, the variable `$SeparateDscOperations` contains logs grouped by the job IDs.</span></span> <span data-ttu-id="1a07c-154">Her dizi öğesi, bu değişkenin günlükleri hakkında daha fazla bilgi için erişim farklı bir DSC işlem tarafından günlüğe kaydedilen olayları grubunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1a07c-154">Each array element of this variable represents a group of events logged by a different DSC operation, allowing access to more information about the logs.</span></span>

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

<span data-ttu-id="1a07c-155">Değişkeni verilerde ayıklayabilirsiniz `$SeparateDscOperations` kullanarak [Where-Object](https://technet.microsoft.com/library/ee177028.aspx).</span><span class="sxs-lookup"><span data-stu-id="1a07c-155">You can extract the data in the variable `$SeparateDscOperations` using [Where-Object](https://technet.microsoft.com/library/ee177028.aspx).</span></span> <span data-ttu-id="1a07c-156">DSC sorun giderme için verileri ayıklamak isteyeceğiniz beş senaryolar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1a07c-156">Following are five scenarios in which you might want to extract data for troubleshooting DSC:</span></span>

### <a name="1-operations-failures"></a><span data-ttu-id="1a07c-157">1: işlemleri hataları</span><span class="sxs-lookup"><span data-stu-id="1a07c-157">1: Operations failures</span></span>

<span data-ttu-id="1a07c-158">Tüm olayları sahip [önem düzeyleri](https://msdn.microsoft.com/library/dd996917(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="1a07c-158">All events have [severity levels](https://msdn.microsoft.com/library/dd996917(v=vs.85)).</span></span> <span data-ttu-id="1a07c-159">Bu bilgiler, hata olayları tanımlamak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="1a07c-159">This information can be used to identify the error events:</span></span>

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a><span data-ttu-id="1a07c-160">2: işlem ayrıntılarını son bir yarım saatte çalıştırın</span><span class="sxs-lookup"><span data-stu-id="1a07c-160">2: Details of operations run in the last half hour</span></span>

<span data-ttu-id="1a07c-161">`TimeCreated`, her Windows olay özelliği durumları olayın oluşturulduğu saat.</span><span class="sxs-lookup"><span data-stu-id="1a07c-161">`TimeCreated`, a property of every Windows event, states the time the event was created.</span></span> <span data-ttu-id="1a07c-162">Bu özellik belirli bir tarih/saat nesnesi ile karşılaştırma tüm olayları filtrelemek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="1a07c-162">Comparing this property with a particular date/time object can be used to filter all events:</span></span>

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a><span data-ttu-id="1a07c-163">3: en son işlem iletileri</span><span class="sxs-lookup"><span data-stu-id="1a07c-163">3: Messages from the latest operation</span></span>

<span data-ttu-id="1a07c-164">Son işlemi dizi grubuna ilk dizininde depolanan `$SeparateDscOperations`.</span><span class="sxs-lookup"><span data-stu-id="1a07c-164">The latest operation is stored in the first index of the array group `$SeparateDscOperations`.</span></span> <span data-ttu-id="1a07c-165">Dizin 0 için grubun iletileri sorgulama son işlemi için tüm iletileri döndürür:</span><span class="sxs-lookup"><span data-stu-id="1a07c-165">Querying the group’s messages for index 0 returns all messages for the latest operation:</span></span>

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

### <a name="4-error-messages-logged-for-recent-failed-operations"></a><span data-ttu-id="1a07c-166">4: en son başarısız işlemler için günlüğe hata iletileri</span><span class="sxs-lookup"><span data-stu-id="1a07c-166">4: Error messages logged for recent failed operations</span></span>

<span data-ttu-id="1a07c-167">`$SeparateDscOperations[0].Group` Son işlemi olayları kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="1a07c-167">`$SeparateDscOperations[0].Group` contains a set of events for the latest operation.</span></span> <span data-ttu-id="1a07c-168">Çalıştırma `Where-Object` olayları filtrelemek için cmdlet tabanlı kullanıcıların düzeyi görünen adı.</span><span class="sxs-lookup"><span data-stu-id="1a07c-168">Run the `Where-Object` cmdlet to filter the events based on their level display name.</span></span> <span data-ttu-id="1a07c-169">Sonuçları depolanır `$myFailedEvent` değişkenine olabilen başka olay iletisini almak için dissected:</span><span class="sxs-lookup"><span data-stu-id="1a07c-169">Results are stored in the `$myFailedEvent` variable, which can be further dissected to get the event message:</span></span>

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a><span data-ttu-id="1a07c-170">5: belirli iş kimliği için oluşturulan tüm olayları</span><span class="sxs-lookup"><span data-stu-id="1a07c-170">5: All events generated for a particular job ID.</span></span>

<span data-ttu-id="1a07c-171">`$SeparateDscOperations` her biri benzersiz iş kimliği ada sahip bir dizi gruplarının</span><span class="sxs-lookup"><span data-stu-id="1a07c-171">`$SeparateDscOperations` is an array of groups, each of which has the name as the unique job ID.</span></span> <span data-ttu-id="1a07c-172">Çalıştırarak `Where-Object` cmdlet'ini gruplarıyla belirli iş kimliği olan olayları ayıklamak:</span><span class="sxs-lookup"><span data-stu-id="1a07c-172">By running the `Where-Object` cmdlet, you can extract those groups of events that have a particular job ID:</span></span>

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

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a><span data-ttu-id="1a07c-173">Günlüklerini DSC çözümlemek için xDscDiagnostics kullanma</span><span class="sxs-lookup"><span data-stu-id="1a07c-173">Using xDscDiagnostics to analyze DSC logs</span></span>

<span data-ttu-id="1a07c-174">**xDscDiagnostics** DSC hataları makinenizde çözümlemenize yardımcı olabilecek birçok işlevleri oluşan bir PowerShell modülüdür.</span><span class="sxs-lookup"><span data-stu-id="1a07c-174">**xDscDiagnostics** is a PowerShell module that consists of several functions that can help analyze DSC failures on your machine.</span></span> <span data-ttu-id="1a07c-175">Bu işlevler geçmiş DSC Operations tüm yerel olayları veya uzak bilgisayarlarda DSC olayları (geçerli kimlik bilgileriyle) belirlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1a07c-175">These functions can help you identify all local events from past DSC operations, or DSC events on remote computers (with valid credentials).</span></span> <span data-ttu-id="1a07c-176">Burada, DSC işlemi terimi, bir tek benzersiz DSC yürütülmesine onun başlangıçtan sonunu tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1a07c-176">Here, the term DSC operation is used to define a single unique DSC execution from its start to its end.</span></span> <span data-ttu-id="1a07c-177">Örneğin, `Test-DscConfiguration` ayrı bir DSC işlemi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1a07c-177">For example, `Test-DscConfiguration` would be a separate DSC operation.</span></span> <span data-ttu-id="1a07c-178">Benzer şekilde, her diğer cmdlet'ini DSC (gibi `Get-DscConfiguration`, `Start-DscConfiguration`, vs.) her ayrı DSC işlemleri olarak tanımlanamadı.</span><span class="sxs-lookup"><span data-stu-id="1a07c-178">Similarly, every other cmdlet in DSC (such as `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) could each be identified as separate DSC operations.</span></span> <span data-ttu-id="1a07c-179">İşlevler en açıklanacak [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span><span class="sxs-lookup"><span data-stu-id="1a07c-179">The functions are explained at [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span></span>
<span data-ttu-id="1a07c-180">Yardım kullanılabilir çalıştırarak `Get-Help <cmdlet name>`.</span><span class="sxs-lookup"><span data-stu-id="1a07c-180">Help is available by running `Get-Help <cmdlet name>`.</span></span>

### <a name="getting-details-of-dsc-operations"></a><span data-ttu-id="1a07c-181">DSC işlemlerinin ayrıntıları alınıyor</span><span class="sxs-lookup"><span data-stu-id="1a07c-181">Getting details of DSC operations</span></span>

<span data-ttu-id="1a07c-182">`Get-xDscOperation` İşlevi bir veya birden çok bilgisayar üzerinde çalışacak DSC işlemlerinin sonuçlarını bulmanıza sağlar ve her DSC işlemi tarafından üretilen olayları koleksiyonunu içeren bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="1a07c-182">The `Get-xDscOperation` function lets you find the results of the DSC operations that run on one or multiple computers, and returns an object that contains the collection of events produced by each DSC operation.</span></span>
<span data-ttu-id="1a07c-183">Örneğin, aşağıdaki çıktıda üç komutları çalıştırılmadı.</span><span class="sxs-lookup"><span data-stu-id="1a07c-183">For example, in the following output, three commands were run.</span></span> <span data-ttu-id="1a07c-184">Birinci geçirilen ve diğer iki başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="1a07c-184">The first one passed, and the other two failed.</span></span> <span data-ttu-id="1a07c-185">Bu sonuçları çıktısında özetlenir `Get-xDscOperation`.</span><span class="sxs-lookup"><span data-stu-id="1a07c-185">These results are summarized in the output of `Get-xDscOperation`.</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...

```

<span data-ttu-id="1a07c-186">Kullanarak, en son işlemleri için yalnızca sonuçları istemediğinizi de belirtebilirsiniz `Newest` parametre:</span><span class="sxs-lookup"><span data-stu-id="1a07c-186">You can also specify that you want only results for the most recent operations by using the `Newest` parameter:</span></span>

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

### <a name="getting-details-of-dsc-events"></a><span data-ttu-id="1a07c-187">DSC olaylarının ayrıntılarını alma</span><span class="sxs-lookup"><span data-stu-id="1a07c-187">Getting details of DSC events</span></span>

<span data-ttu-id="1a07c-188">`Trace-xDscOperation` Cmdlet'i olaylar, kendi olay türleri koleksiyonunu içeren bir nesne döndürür ve çıktı mesajı oluşturulan belirli bir DSC işlemi.</span><span class="sxs-lookup"><span data-stu-id="1a07c-188">The `Trace-xDscOperation` cmdlet returns an object containing a collection of events, their event types, and the message output generated from a particular DSC operation.</span></span> <span data-ttu-id="1a07c-189">Genellikle, ne zaman bulduğunuz hata kullanarak işlemleri hiçbirinde `Get-xDscOperation`, hangi olayların bir hata neden olduğunu bulmak için bu işlemi izleme.</span><span class="sxs-lookup"><span data-stu-id="1a07c-189">Typically, when you find a failure in any of the operations using `Get-xDscOperation`, you would trace that operation to find out which of the events caused a failure.</span></span>

<span data-ttu-id="1a07c-190">Kullanım `SequenceID` belirli bir bilgisayar için belirli bir işlemi olayları almak için parametre.</span><span class="sxs-lookup"><span data-stu-id="1a07c-190">Use the  `SequenceID` parameter to get the events for a specific operation for a specific computer.</span></span> <span data-ttu-id="1a07c-191">Örneğin, belirttiğiniz bir `SequenceID` 9, `Trace-xDscOperaion` son işlem 9 edildi DSC işlemi için izleme alın:</span><span class="sxs-lookup"><span data-stu-id="1a07c-191">For example, if you specify a `SequenceID` of 9, `Trace-xDscOperaion` get the trace for the DSC operation that was 9th from the last operation:</span></span>

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

<span data-ttu-id="1a07c-192">Geçirmek **GUID** belirli bir DSC işlemi atanan (tarafından döndürülen `Get-xDscOperation` cmldet) bu DSC işlemi için olay ayrıntıları almak için:</span><span class="sxs-lookup"><span data-stu-id="1a07c-192">Pass the **GUID** assigned to a specific DSC operation (as returned by the `Get-xDscOperation` cmldet) to get the event details for that DSC operation:</span></span>

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

<span data-ttu-id="1a07c-193">Unutmayın, beri `Trace-xDscOperation` analitik, hata ayıklama, olayları toplayan ve işlemsel günlükleri, bunu yukarıda açıklandığı gibi bu günlükleri etkinleştirmek isteyip istemediğinizi sorar.</span><span class="sxs-lookup"><span data-stu-id="1a07c-193">Note that, since `Trace-xDscOperation` aggregates events from the Analytic, Debug, and Operational logs, it will prompt you to enable these logs as described above.</span></span>

<span data-ttu-id="1a07c-194">Olaylar üzerinde çıktısını kaydederek bilgiler alternatif olarak, toplayabilirsiniz `Trace-xDscOperation` bir değişkenin içine.</span><span class="sxs-lookup"><span data-stu-id="1a07c-194">Alternately, you can gather information on the events by saving the output of `Trace-xDscOperation` into a variable.</span></span> <span data-ttu-id="1a07c-195">Belirli bir DSC işlem için tüm olayları görüntülemek için aşağıdaki komutları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a07c-195">You can use the following commands to display all the events for a particular DSC operation.</span></span>

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

<span data-ttu-id="1a07c-196">Bu aynı sonuçları görüntüler `Get-WinEvent` çıkış olduğu gibi cmdlet:</span><span class="sxs-lookup"><span data-stu-id="1a07c-196">This will display the same results as the `Get-WinEvent` cmdlet, such as in the output below:</span></span>

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

<span data-ttu-id="1a07c-197">İdeal olarak, ilk kullanacağınız `Get-xDscOperation` en son birkaç DSC listelemek için yapılandırma makinelerinizi üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="1a07c-197">Ideally, you would first use `Get-xDscOperation` to list out the last few DSC configuration runs on your machines.</span></span> <span data-ttu-id="1a07c-198">Bu (SequenceId: veya JobId kullanarak) herhangi bir tek işlem ile inceleyebilirsiniz `Trace-xDscOperation` ne arka planda yaptığını bulmak için.</span><span class="sxs-lookup"><span data-stu-id="1a07c-198">Following this, you can examine any single operation (using its SequenceID or JobID) with `Trace-xDscOperation` to discover what it did behind the scenes.</span></span>

### <a name="getting-events-for-a-remote-computer"></a><span data-ttu-id="1a07c-199">Bir uzak bilgisayara olayları alma</span><span class="sxs-lookup"><span data-stu-id="1a07c-199">Getting events for a remote computer</span></span>

<span data-ttu-id="1a07c-200">Kullanım `ComputerName` parametresinin `Trace-xDscOperation` uzak bir bilgisayarda olay ayrıntıları almak için cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1a07c-200">Use the `ComputerName` parameter of the `Trace-xDscOperation` cmdlet to get the event details on a remote computer.</span></span> <span data-ttu-id="1a07c-201">Bunu yapmak için önce uzak bilgisayarda Uzaktan yönetime izin vermek için bir güvenlik duvarı kuralı oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="1a07c-201">Before you can do this, you have to create a firewall rule to allow remote administration on the remote computer:</span></span>

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```
<span data-ttu-id="1a07c-202">Aramanız için o bilgisayarın belirtebilirsiniz artık `Trace-xDscOperation`:</span><span class="sxs-lookup"><span data-stu-id="1a07c-202">Now you can specify that computer in your call to `Trace-xDscOperation`:</span></span>

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

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a><span data-ttu-id="1a07c-203">Kaynaklarım güncelleştirme olmaz: önbellek sıfırlama</span><span class="sxs-lookup"><span data-stu-id="1a07c-203">My resources won’t update: How to reset the cache</span></span>

<span data-ttu-id="1a07c-204">DSC altyapısı verimliliği amaçlar için bir PowerShell modülü olarak uygulanan kaynakları önbelleğe alır.</span><span class="sxs-lookup"><span data-stu-id="1a07c-204">The DSC engine caches resources implemented as a PowerShell module for efficiency purposes.</span></span> <span data-ttu-id="1a07c-205">Ancak, bir kaynak yazma ve işlemi yeniden başlatılana kadar DSC önbelleğe alınan sürüm yükler için aynı anda sınama bu sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="1a07c-205">However, this can cause problems when you are authoring a resource and testing it simultaneously because DSC will load the cached version until the process is restarted.</span></span> <span data-ttu-id="1a07c-206">Daha yeni sürümü yüklemek DSC yapmak için tek açıkça DSC altyapısı barındırma işlemi sonlandırmak için yoludur.</span><span class="sxs-lookup"><span data-stu-id="1a07c-206">The only way to make DSC load the newer version is to explicitly kill the process hosting the DSC engine.</span></span>

<span data-ttu-id="1a07c-207">Benzer şekilde, çalıştırdığınızda `Start-DscConfiguration`ekleme ve özel bir kaynak değiştirildikten sonra değişikliğin sürece yürütülmeyebilir veya bilgisayar yeniden başlatılana kadar.</span><span class="sxs-lookup"><span data-stu-id="1a07c-207">Similarly, when you run `Start-DscConfiguration`, after adding and modifying a custom resource, the modification may not execute unless, or until, the computer is rebooted.</span></span> <span data-ttu-id="1a07c-208">DSC WMI sağlayıcısı ana bilgisayar işlemi (WmiPrvSE) çalışır ve genellikle birçok WmiPrvSE aynı anda çalışan örneklerini vardır nedeni budur.</span><span class="sxs-lookup"><span data-stu-id="1a07c-208">This is because DSC runs in the WMI Provider Host Process (WmiPrvSE), and usually, there are many instances of WmiPrvSE running at once.</span></span> <span data-ttu-id="1a07c-209">Bilgisayarı yeniden başlattığınızda, ana bilgisayar işlemi yeniden ve önbellek temizlenir.</span><span class="sxs-lookup"><span data-stu-id="1a07c-209">When you reboot, the host process is restarted and the cache is cleared.</span></span>

<span data-ttu-id="1a07c-210">Başarıyla yapılandırmasını geri dönüşüm ve başlatmadan önbelleğini temizlemek için durdurun ve ana bilgisayar işlemi yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="1a07c-210">To successfully recycle the configuration and clear the cache without rebooting, you must stop and then restart the host process.</span></span> <span data-ttu-id="1a07c-211">Bu yapabildiği işlemi tanımlamak, durdurmak ve yeniden başlatmak için tek başına örnek temelinde, yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="1a07c-211">This can be done on a per instance basis, whereby you identify the process, stop it, and restart it.</span></span> <span data-ttu-id="1a07c-212">Veya, kullanabileceğiniz `DebugMode`, PowerShell DSC kaynağı yeniden yüklemek için aşağıda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="1a07c-212">Or, you can use `DebugMode`, as demonstrated below, to reload the PowerShell DSC resource.</span></span>

<span data-ttu-id="1a07c-213">DSC altyapısı barındırma hangi işlemi tanımlamak ve tek başına örnek temelinde durdurmak için DSC altyapısı barındırma WmiPrvSE işlem kimliği listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a07c-213">To identify which process is hosting the DSC engine and stop it on a per instance basis, you can list the process ID of the WmiPrvSE which is hosting the DSC engine.</span></span> <span data-ttu-id="1a07c-214">Ardından, sağlayıcı güncelleştirmek için aşağıdaki komutları kullanarak WmiPrvSE işlemi ve çalıştırın Durdur **başlangıç DscConfiguration** yeniden.</span><span class="sxs-lookup"><span data-stu-id="1a07c-214">Then, to update the provider, stop the WmiPrvSE process using the commands below, and then run **Start-DscConfiguration** again.</span></span>

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

## <a name="using-debugmode"></a><span data-ttu-id="1a07c-215">DebugMode kullanma</span><span class="sxs-lookup"><span data-stu-id="1a07c-215">Using DebugMode</span></span>

<span data-ttu-id="1a07c-216">DSC yerel Configuration Manager (kullanmak için LCM'yi) yapılandırabilirsiniz `DebugMode` her zaman ana bilgisayar işlemi başlatıldığında önbelleğini temizlemek için.</span><span class="sxs-lookup"><span data-stu-id="1a07c-216">You can configure the DSC Local Configuration Manager (LCM) to use `DebugMode` to always clear the cache when the host process is restarted.</span></span> <span data-ttu-id="1a07c-217">Ayarlandığında **doğru**, PowerShell DSC kaynağı her zaman yeniden altyapısı neden olur.</span><span class="sxs-lookup"><span data-stu-id="1a07c-217">When set to **TRUE**, it causes the engine to always reload the PowerShell DSC resource.</span></span> <span data-ttu-id="1a07c-218">Tamamladıktan sonra kaynak yazma, onu ayarlayabilirsiniz geri **FALSE** ve altyapı modülleri önbelleğe alma davranışını döner.</span><span class="sxs-lookup"><span data-stu-id="1a07c-218">Once you are done writing your resource, you can set it back to **FALSE** and the engine will revert to its behavior of caching the modules.</span></span>

<span data-ttu-id="1a07c-219">Aşağıdaki olduğunu göstermek için bir tanıtım nasıl `DebugMode` önbellek otomatik olarak yenileyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a07c-219">Following is a demonstration to show how `DebugMode` can automatically refresh the cache.</span></span> <span data-ttu-id="1a07c-220">İlk olarak, varsayılan yapılandırmasını bakalım:</span><span class="sxs-lookup"><span data-stu-id="1a07c-220">First, let’s look at the default configuration:</span></span>

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

<span data-ttu-id="1a07c-221">Görebilirsiniz `DebugMode` ayarlanır **FALSE**.</span><span class="sxs-lookup"><span data-stu-id="1a07c-221">You can see that `DebugMode` is set to **FALSE**.</span></span>

<span data-ttu-id="1a07c-222">Ayarlamak için `DebugMode` gösterimi, aşağıdaki PowerShell kaynağı kullanın:</span><span class="sxs-lookup"><span data-stu-id="1a07c-222">To set up the `DebugMode` demonstration, use the following PowerShell resource:</span></span>

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

<span data-ttu-id="1a07c-223">Şimdi, denilen yukarıdaki kaynağı kullanarak yapılandırma Yazar `TestProviderDebugMode`:</span><span class="sxs-lookup"><span data-stu-id="1a07c-223">Now, author a configuration using the above resource called `TestProviderDebugMode`:</span></span>

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

<span data-ttu-id="1a07c-224">Göreceksiniz dosyasının içeriğini: "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" olan **1**.</span><span class="sxs-lookup"><span data-stu-id="1a07c-224">You will see that the contents of file: “**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**” is **1**.</span></span>

<span data-ttu-id="1a07c-225">Şimdi, aşağıdaki komut dosyası kullanarak sağlayıcı kodunu güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="1a07c-225">Now, update the provider code using the following script:</span></span>

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

<span data-ttu-id="1a07c-226">Bu komut dosyası rastgele bir sayı oluşturur ve sağlayıcı kodu buna göre güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="1a07c-226">This script generates a random number and updates the provider code accordingly.</span></span> <span data-ttu-id="1a07c-227">İle `DebugMode` dosyasının içeriğini false olarak ayarlayın "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" hiçbir zaman değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="1a07c-227">With `DebugMode` set to false, the contents of the file “**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**” are never changed.</span></span>

<span data-ttu-id="1a07c-228">Şimdi, `DebugMode` için **TRUE** yapılandırma komut:</span><span class="sxs-lookup"><span data-stu-id="1a07c-228">Now, set `DebugMode` to **TRUE** in your configuration script:</span></span>

```powershell
LocalConfigurationManager
{
    DebugMode = $true
}
```

<span data-ttu-id="1a07c-229">Yukarıdaki komut dosyasını yeniden çalıştırdığınızda, dosyanın içeriği her zaman farklı olduğunu göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1a07c-229">When you run the above script again, you will see that the content of the file is different every time.</span></span> <span data-ttu-id="1a07c-230">(Çalıştırabilirsiniz `Get-DscConfiguration` bunu denetlemek için).</span><span class="sxs-lookup"><span data-stu-id="1a07c-230">(You can run `Get-DscConfiguration` to check it).</span></span> <span data-ttu-id="1a07c-231">(Komut dosyasını çalıştırdığınızda sonuçlarınızı farklı olabilir) iki ek çalıştırmaları sonucu aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="1a07c-231">Below is the result of two additional runs (your results may be different when you run the script):</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1a07c-232">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="1a07c-232">See Also</span></span>

### <a name="reference"></a><span data-ttu-id="1a07c-233">Başvuru</span><span class="sxs-lookup"><span data-stu-id="1a07c-233">Reference</span></span>
* [<span data-ttu-id="1a07c-234">DSC günlük kaynak</span><span class="sxs-lookup"><span data-stu-id="1a07c-234">DSC Log Resource</span></span>](logResource.md)

### <a name="concepts"></a><span data-ttu-id="1a07c-235">Kavramlar</span><span class="sxs-lookup"><span data-stu-id="1a07c-235">Concepts</span></span>
* [<span data-ttu-id="1a07c-236">Özel Windows PowerShell istenen durum yapılandırması kaynakları oluşturma</span><span class="sxs-lookup"><span data-stu-id="1a07c-236">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

### <a name="other-resources"></a><span data-ttu-id="1a07c-237">Diğer Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="1a07c-237">Other Resources</span></span>
* <span data-ttu-id="1a07c-238">[Windows PowerShell istenen durum yapılandırma cmdlet'leri](https://technet.microsoft.com/library/dn521624(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="1a07c-238">[Windows PowerShell Desired State Configuration Cmdlets](https://technet.microsoft.com/library/dn521624(v=wps.630).aspx)</span></span>