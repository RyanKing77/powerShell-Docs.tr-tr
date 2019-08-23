---
ms.date: 06/12/2017
keywords: DSC, PowerShell, yapılandırma, kurulum
title: DSC rapor sunucusu kullanma
ms.openlocfilehash: 1ccd4f96b782b41b7d7c953735cb41b3ba3d2bce
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986553"
---
# <a name="using-a-dsc-report-server"></a><span data-ttu-id="e6f20-103">DSC rapor sunucusu kullanma</span><span class="sxs-lookup"><span data-stu-id="e6f20-103">Using a DSC report server</span></span>

<span data-ttu-id="e6f20-104">Şunun için geçerlidir: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="e6f20-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e6f20-105">Çekme sunucusu (Windows özelliği *DSC-Service*) Windows Server 'ın desteklenen bir bileşenidir, ancak yeni özellikler veya yetenekler sunmaya yönelik bir plan yoktur.</span><span class="sxs-lookup"><span data-stu-id="e6f20-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="e6f20-106">Yönetilen istemcileri [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) geçirmeyi (Windows Server 'Da çekme sunucusunun ötesindeki özellikleri içerir) veya [burada](pullserver.md#community-solutions-for-pull-service)listelenen topluluk çözümlerinin birini kullanmaya başlamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="e6f20-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>
>
> [!NOTE]
> <span data-ttu-id="e6f20-107">Bu konuda açıklanan rapor sunucusu PowerShell 4,0 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e6f20-107">The report server described in this topic is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="e6f20-108">Bir düğümün yerel Configuration Manager (LCM), yapılandırma durumu hakkında raporları bir çekme sunucusuna gönderecek şekilde yapılandırılabilir ve bu da bu verileri almak için sorgulanabilecek.</span><span class="sxs-lookup"><span data-stu-id="e6f20-108">The Local Configuration Manager (LCM) of a node can be configured to send reports about its configuration status to a pull server, which can then be queried to retrieve that data.</span></span> <span data-ttu-id="e6f20-109">Düğüm bir yapılandırmayı denetleyip uyguladığı her seferinde rapor sunucusuna bir rapor gönderir.</span><span class="sxs-lookup"><span data-stu-id="e6f20-109">Each time the node checks and applies a configuration, it sends a report to the report server.</span></span> <span data-ttu-id="e6f20-110">Bu raporlar sunucusundaki bir veritabanında depolanır ve Raporlama Web hizmeti çağırarak alınabilir.</span><span class="sxs-lookup"><span data-stu-id="e6f20-110">These reports are stored in a database on the server, and can be retrieved by calling the reporting web service.</span></span> <span data-ttu-id="e6f20-111">Her rapor, hangi yapılandırmaların uygulandığı ve başarılı olup olmadığı, kullanılan kaynaklar, oluşturulan tüm hatalar ve başlangıç ve bitiş zamanları gibi bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="e6f20-111">Each report contains information such as what configurations were applied and whether they succeeded, the resources used, any errors that were thrown, and start and finish times.</span></span>

## <a name="configuring-a-node-to-send-reports"></a><span data-ttu-id="e6f20-112">Rapor göndermek için bir düğüm yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e6f20-112">Configuring a node to send reports</span></span>

<span data-ttu-id="e6f20-113">Bir düğüme, düğümün LCM yapılandırmasında **Reportserverweb** bloğu kullanarak rapor göndermesini söylemiş olursunuz (LCM 'yi yapılandırma hakkında daha fazla bilgi için bkz. [yerel Configuration Manager yapılandırma](../managing-nodes/metaConfig.md)).</span><span class="sxs-lookup"><span data-stu-id="e6f20-113">You tell a node to send reports to a server by using a **ReportServerWeb** block in the node's LCM configuration (for information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md)).</span></span> <span data-ttu-id="e6f20-114">Düğümün rapor gönderdiği sunucu bir Web çekme sunucusu olarak ayarlanmalıdır (bir SMB paylaşımında rapor gönderemezsiniz).</span><span class="sxs-lookup"><span data-stu-id="e6f20-114">The server to which the node sends reports must be set up as a web pull server (you cannot send reports to an SMB share).</span></span> <span data-ttu-id="e6f20-115">Çekme sunucusu kurma hakkında daha fazla bilgi için bkz. [DSC Web çekme sunucusu](pullServer.md)kurma.</span><span class="sxs-lookup"><span data-stu-id="e6f20-115">For information about setting up a pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span> <span data-ttu-id="e6f20-116">Rapor sunucusu, düğümün yapılandırma almasını ve kaynakları almasını sağlayan aynı hizmet olabilir veya farklı bir hizmet olabilir.</span><span class="sxs-lookup"><span data-stu-id="e6f20-116">The report server can be the same service from which the node pulls configurations and gets resources, or it can be a different service.</span></span>

<span data-ttu-id="e6f20-117">**Reportserverweb** bloğunda, çekme hizmetinin URL 'sini ve sunucu tarafından bilinen bir kayıt anahtarını belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6f20-117">In the **ReportServerWeb** block, you specify the URL of the pull service and a registration key that is known to the server.</span></span>

<span data-ttu-id="e6f20-118">Aşağıdaki yapılandırma bir düğümü, bir hizmetten yapılandırmaları çekmek ve farklı bir sunucudaki bir hizmete rapor göndermek için yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e6f20-118">The following configuration configures a node to pull configurations from one service, and send reports to a service on a different server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration ReportClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded   = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PULL:8080/PSDSCPullServer.svc'
            RegistrationKey    = 'bbb9778f-43f2-47de-b61e-a0daff474c6d'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL               = 'http://CONTOSO-REPORT:8080/PSDSCPullServer.svc'
            RegistrationKey         = 'ba39daaa-96c5-4f2f-9149-f95c46460faa'
            AllowUnsecureConnection = $true
        }
    }
}

ReportClientConfig
```

<span data-ttu-id="e6f20-119">Aşağıdaki yapılandırma, bir düğümü yapılandırmalar, kaynaklar ve raporlama için tek bir sunucu kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e6f20-119">The following configuration configures a node to use a single server for configurations, resources, and reporting.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }



        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfig
```

> [!NOTE]
> <span data-ttu-id="e6f20-120">Web hizmetini bir çekme sunucusu ayarlarken istediğiniz her şey olarak adlandırabilirsiniz, ancak **ServerURL** özelliğinin hizmet adıyla eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6f20-120">You can name the web service whatever you want when you set up a pull server, but the **ServerURL** property must match the service name.</span></span>

## <a name="getting-report-data"></a><span data-ttu-id="e6f20-121">Rapor verileri alınıyor</span><span class="sxs-lookup"><span data-stu-id="e6f20-121">Getting report data</span></span>

<span data-ttu-id="e6f20-122">Çekme sunucusuna gönderilen raporlar sunucusundaki bir veritabanına girilir.</span><span class="sxs-lookup"><span data-stu-id="e6f20-122">Reports sent to the pull server are entered into a database on the server.</span></span> <span data-ttu-id="e6f20-123">Raporlar, Web hizmetine yapılan çağrılar aracılığıyla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e6f20-123">The reports are available through calls to the web service.</span></span> <span data-ttu-id="e6f20-124">Belirli bir düğüme ait raporları almak için, aşağıdaki biçimde rapor Web hizmetine bir HTTP isteği gönderin:`http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`</span><span class="sxs-lookup"><span data-stu-id="e6f20-124">To retrieve reports for a specific node, send an HTTP request to the report web service in the following form: `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`</span></span>
<span data-ttu-id="e6f20-125">Burada `MyNodeAgentId` , raporları almak istediğiniz düğümün olan.</span><span class="sxs-lookup"><span data-stu-id="e6f20-125">where `MyNodeAgentId` is the AgentId of the node for which you want to get reports.</span></span> <span data-ttu-id="e6f20-126">Bu düğümde [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) ' i çağırarak bir düğüm için bir düğüm Için sahip kimliği alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6f20-126">You can get the AgentID for a node by calling [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) on that node.</span></span>

<span data-ttu-id="e6f20-127">Raporlar, JSON nesneleri dizisi olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e6f20-127">The reports are returned as an array of JSON objects.</span></span>

<span data-ttu-id="e6f20-128">Aşağıdaki betik, üzerinde çalıştığı düğümün raporlarını döndürür:</span><span class="sxs-lookup"><span data-stu-id="e6f20-128">The following script returns the reports for the node on which it is run:</span></span>

```powershell
function GetReport
{
    param
    (
        $AgentId = "$((glcm).AgentId)", 
        $serviceURL = "http://CONTOSO-REPORT:8080/PSDSCPullServer.svc"
    )

    $requestUri = "$serviceURL/Nodes(AgentId= '$AgentId')/Reports"
    $request = Invoke-WebRequest -Uri $requestUri  -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" `
               -UseBasicParsing -Headers @{Accept = "application/json";ProtocolVersion = "2.0"} `
               -ErrorAction SilentlyContinue -ErrorVariable ev
    $object = ConvertFrom-Json $request.content
    return $object.value
}
```

## <a name="viewing-report-data"></a><span data-ttu-id="e6f20-129">Rapor verilerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e6f20-129">Viewing report data</span></span>

<span data-ttu-id="e6f20-130">**Getreport** işlevinin sonucuna bir değişken ayarlarsanız, tek tek alanları döndürülen dizinin bir öğesi içinde görüntüleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e6f20-130">If you set a variable to the result of the **GetReport** function, you can view the individual fields in an element of the array that is returned:</span></span>

```powershell
$reports = GetReport
$reports[1]
```

```output
JobId                : 019dfbe5-f99f-11e5-80c6-001dd8b8065c
OperationType        : Consistency
RefreshMode          : Pull
Status               : Success
ReportFormatVersion  : 2.0
ConfigurationVersion : 2.0.0
StartTime            : 04/03/2016 06:21:43
EndTime              : 04/03/2016 06:22:04
RebootRequested      : False
Errors               : {}
StatusData           : {{"StartDate":"2016-04-03T06:21:43.7220000-07:00","IPV6Addresses":["2001:4898:d8:f2f2:852b:b255:b071:283b","fe80::852b:b255:b071
                       :283b%12","::2000:0:0:0","::1","::2000:0:0:0"],"DurationInSeconds":"21","JobID":"{019DFBE5-F99F-11E5-80C6-001DD8B8065C}","Curren
                       tChecksum":"A7797571CB9C3AF4D74C39A0FDA11DAF33273349E1182385528FFC1E47151F7F","MetaData":"Author: configAuthor; Name:
                       Sample_ArchiveFirewall; Version: 2.0.0; GenerationDate: 04/01/2016 15:23:30; GenerationHost: CONTOSO-PullSrv;","RebootRequested":"False
                       ","Status":"Success","IPV4Addresses":["10.240.179.151","127.0.0.1"],"LCMVersion":"2.0","ResourcesNotInDesiredState":[{"SourceInf
                       o":"C:\\ReportTest\\Sample_xFirewall_AddFirewallRule.ps1::23::9::xFirewall","ModuleName":"xNetworking","DurationInSeconds":"8.785",
                       "InstanceName":"Firewall","StartDate":"2016-04-03T06:21:56.4650000-07:00","ResourceName":"xFirewall","ModuleVersion":"2.7.0.0","
                       RebootRequested":"False","ResourceId":"[xFirewall]Firewall","ConfigurationName":"Sample_ArchiveFirewall","InDesiredState":"False
                       "}],"NumberOfResources":"2","Type":"Consistency","HostName":"CONTOSO-PULLCLI","ResourcesInDesiredState":[{"SourceInfo":"C:\\ReportTest\\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive","ModuleName":"PSDesiredStateConfiguration","DurationInSeconds":"1.848",
                       "InstanceName":"ArchiveExample","StartDate":"2016-04-03T06:21:56.4650000-07:00","ResourceName":"Archive","ModuleVersion":"1.1","
                       RebootRequested":"False","ResourceId":"[Archive]ArchiveExample","ConfigurationName":"Sample_ArchiveFirewall","InDesiredState":"T
                       rue"}],"MACAddresses":["00-1D-D8-B8-06-5C","00-00-00-00-00-00-00-E0"],"MetaConfiguration":{"AgentId":"52DA826D-00DE-4166-8ACB-73F2B46A7E00",
                       "ConfigurationDownloadManagers":[{"SourceInfo":"C:\\ReportTest\\LCMConfig.ps1::14::9::ConfigurationRepositoryWeb","A
                       llowUnsecureConnection":"True","ServerURL":"http://CONTOSO-PullSrv:8080/PSDSCPullServer.svc","RegistrationKey":"","ResourceId":"[Config
                       urationRepositoryWeb]CONTOSO-PullSrv","ConfigurationNames":["ClientConfig"]}],"ActionAfterReboot":"ContinueConfiguration","LCMCo
                       mpatibleVersions":["1.0","2.0"],"LCMState":"Idle","ResourceModuleManagers":[],"ReportManagers":[{"AllowUnsecureConnection":"True
                       ","RegistrationKey":"","ServerURL":"http://CONTOSO-PullSrv:8080/PSDSCPullServer.svc","ResourceId":"[ReportServerWeb]CONTOSO-PullSrv","S
                       ourceInfo":"C:\\ReportTest\\LCMConfig.ps1::24::9::ReportServerWeb"}],"StatusRetentionTimeInDays":"10","LCMVersion":"2.0","Config
                       urationMode":"ApplyAndMonitor","RefreshFrequencyMins":"30","RebootNodeIfNeeded":"True","RefreshMode":"Pull","DebugMode":["NONE"]
                       ,"LCMStateDetail":"","AllowModuleOverwrite":"False","ConfigurationModeFrequencyMins":"15"},"Locale":"en-US","Mode":"Pull"}}
AdditionalData       : {}
```

<span data-ttu-id="e6f20-131">Varsayılan olarak, raporlar iş **kimliği**' ne göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="e6f20-131">By default, the reports are sorted by **JobID**.</span></span> <span data-ttu-id="e6f20-132">En son raporu almak için raporları azalan **StartTime** özelliğine göre sıralayabilir ve sonra dizinin ilk öğesini alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e6f20-132">To get the most recent report, you can sort the reports by descending **StartTime** property, and then get the first element of the array:</span></span>

```powershell
$reportsByStartTime = $reports | Sort-Object {$_."StartTime" -as [DateTime] } -Descending
$reportMostRecent = $reportsByStartTime[0]
```

<span data-ttu-id="e6f20-133">**Statusdata** özelliğinin, çok sayıda özelliği olan bir nesne olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="e6f20-133">Notice that the **StatusData** property is an object with a number of properties.</span></span> <span data-ttu-id="e6f20-134">Bu, raporlama verilerinin büyük olduğu yerdir.</span><span class="sxs-lookup"><span data-stu-id="e6f20-134">This is where much of the reporting data is.</span></span> <span data-ttu-id="e6f20-135">En son rapor için **Statusdata** özelliğinin ayrı alanlarını inceleyelim:</span><span class="sxs-lookup"><span data-stu-id="e6f20-135">Let's look at the individual fields of the **StatusData** property for the most recent report:</span></span>

```powershell
$statusData = $reportMostRecent.StatusData | ConvertFrom-Json
$statusData
```

```output
StartDate                  : 2016-04-04T11:21:41.2990000-07:00
IPV6Addresses              : {2001:4898:d8:f2f2:852b:b255:b071:283b, fe80::852b:b255:b071:283b%12, ::2000:0:0:0, ::1...}
DurationInSeconds          : 25
JobID                      : {135D230E-FA92-11E5-80C6-001DD8B8065C}
CurrentChecksum            : A7797571CB9C3AF4D74C39A0FDA11DAF33273349E1182385528FFC1E47151F7F
MetaData                   : Author: configAuthor; Name: Sample_ArchiveFirewall; Version: 2.0.0; GenerationDate: 04/01/2016 15:23:30; GenerationHost:
                             CONTOSO-PullSrv;
RebootRequested            : False
Status                     : Success
IPV4Addresses              : {10.240.179.151, 127.0.0.1}
LCMVersion                 : 2.0
ResourcesNotInDesiredState : {@{SourceInfo=C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::23::9::xFirewall; ModuleName=xNetworking;
                             DurationInSeconds=10.725; InstanceName=Firewall; StartDate=2016-04-04T11:21:55.7200000-07:00; ResourceName=xFirewall;
                             ModuleVersion=2.7.0.0; RebootRequested=False; ResourceId=[xFirewall]Firewall; ConfigurationName=Sample_ArchiveFirewall;
                             InDesiredState=False}}
NumberOfResources          : 2
Type                       : Consistency
HostName                   : CONTOSO-PULLCLI
ResourcesInDesiredState    : {@{SourceInfo=C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive; ModuleName=PSDesiredStateConfiguration;
                             DurationInSeconds=2.672; InstanceName=ArchiveExample; StartDate=2016-04-04T11:21:55.7200000-07:00; ResourceName=Archive;
                             ModuleVersion=1.1; RebootRequested=False; ResourceId=[Archive]ArchiveExample; ConfigurationName=Sample_ArchiveFirewall;
                             InDesiredState=True}}
MACAddresses               : {00-1D-D8-B8-06-5C, 00-00-00-00-00-00-00-E0}
MetaConfiguration          : @{AgentId=52DA826D-00DE-4166-8ACB-73F2B46A7E00; ConfigurationDownloadManagers=System.Object[];
                             ActionAfterReboot=ContinueConfiguration; LCMCompatibleVersions=System.Object[]; LCMState=Idle;
                             ResourceModuleManagers=System.Object[]; ReportManagers=System.Object[]; StatusRetentionTimeInDays=10; LCMVersion=2.0;
                             ConfigurationMode=ApplyAndMonitor; RefreshFrequencyMins=30; RebootNodeIfNeeded=True; RefreshMode=Pull;
                             DebugMode=System.Object[]; LCMStateDetail=; AllowModuleOverwrite=False; ConfigurationModeFrequencyMins=15}
Locale                     : en-US
Mode                       : Pull
```

<span data-ttu-id="e6f20-136">Diğer şeyler arasında bu, en son yapılandırmanın iki kaynak olarak adlandırıldığını ve bunlardan birinin istenen durumda olduğunu ve bunlardan birinin ne olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e6f20-136">Among other things, this shows that the most recent configuration called two resources, and that one of them was in the desired state, and one of them was not.</span></span> <span data-ttu-id="e6f20-137">Yalnızca **Resourcesnotındesıredstate** özelliğinden daha okunabilir bir çıktı alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e6f20-137">You can get a more readable output of just the **ResourcesNotInDesiredState** property:</span></span>

```powershell
$statusData.ResourcesInDesiredState
```

```output
SourceInfo        : C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive
ModuleName        : PSDesiredStateConfiguration
DurationInSeconds : 2.672
InstanceName      : ArchiveExample
StartDate         : 2016-04-04T11:21:55.7200000-07:00
ResourceName      : Archive
ModuleVersion     : 1.1
RebootRequested   : False
ResourceId        : [Archive]ArchiveExample
ConfigurationName : Sample_ArchiveFirewall
InDesiredState    : True
```

<span data-ttu-id="e6f20-138">Bu örneklerin rapor verileriyle neler yapabileceğinizi gösteren bir fikir sunyacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e6f20-138">Note that these examples are meant to give you an idea of what you can do with report data.</span></span> <span data-ttu-id="e6f20-139">PowerShell 'de JSON ile çalışmaya giriş için bkz. [JSON ve PowerShell Ile yürütme](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).</span><span class="sxs-lookup"><span data-stu-id="e6f20-139">For an introduction on working with JSON in PowerShell, see [Playing with JSON and PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).</span></span>

## <a name="see-also"></a><span data-ttu-id="e6f20-140">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e6f20-140">See Also</span></span>

[<span data-ttu-id="e6f20-141">Yerel Configuration Manager yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e6f20-141">Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="e6f20-142">DSC Web çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="e6f20-142">Setting up a DSC web pull server</span></span>](pullServer.md)

[<span data-ttu-id="e6f20-143">Yapılandırma adlarını kullanarak çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="e6f20-143">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
