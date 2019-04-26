---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC rapor sunucusu kullanma
ms.openlocfilehash: 73208477a74ff3c615d7d515fcad555beabe8f32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079243"
---
# <a name="using-a-dsc-report-server"></a><span data-ttu-id="04da3-103">DSC rapor sunucusu kullanma</span><span class="sxs-lookup"><span data-stu-id="04da3-103">Using a DSC report server</span></span>

<span data-ttu-id="04da3-104">Uygulama hedefi: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="04da3-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="04da3-105">Çekme sunucusu (Windows özelliği *DSC hizmet*) ancak desteklenen bir bileşen Windows Server'ın yeni özellikler veya yetenekler sunmak için herhangi bir plan vardır.</span><span class="sxs-lookup"><span data-stu-id="04da3-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="04da3-106">Geçişi başlıyor önerilir yönetilen istemcilere [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda dışında özellikler dahildir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="04da3-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>
>
> [!NOTE]
> <span data-ttu-id="04da3-107">PowerShell 4. 0 ', bu konuda açıklanan rapor sunucusu kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="04da3-107">The report server described in this topic is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="04da3-108">Bir düğümün yerel Configuration Manager (LCM) yapılandırma durumu hakkında raporlar daha sonra bu verileri almak için sorgulanabilir bir çekme sunucusuna göndermek için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="04da3-108">The Local Configuration Manager (LCM) of a node can be configured to send reports about its configuration status to a pull server, which can then be queried to retrieve that data.</span></span> <span data-ttu-id="04da3-109">Düğüm denetler ve bir yapılandırma uygulanabilir her zaman bir raporu rapor sunucusuna gönderir.</span><span class="sxs-lookup"><span data-stu-id="04da3-109">Each time the node checks and applies a configuration, it sends a report to the report server.</span></span> <span data-ttu-id="04da3-110">Bu raporlar, sunucu üzerindeki bir veritabanında depolanır ve raporlama web hizmeti çağrılarak alınabilir.</span><span class="sxs-lookup"><span data-stu-id="04da3-110">These reports are stored in a database on the server, and can be retrieved by calling the reporting web service.</span></span> <span data-ttu-id="04da3-111">Her rapor bunların başarılı olup olmadığını ve hangi yapılandırmaları uygulanan gibi bilgiler içerir, kullanılan kaynaklar, oluşturulan, başlangıç ve bitiş zamanlarını hataları.</span><span class="sxs-lookup"><span data-stu-id="04da3-111">Each report contains information such as what configurations were applied and whether they succeeded, the resources used, any errors that were thrown, and start and finish times.</span></span>

## <a name="configuring-a-node-to-send-reports"></a><span data-ttu-id="04da3-112">Raporları göndermek için bir düğüm yapılandırma</span><span class="sxs-lookup"><span data-stu-id="04da3-112">Configuring a node to send reports</span></span>

<span data-ttu-id="04da3-113">Raporları kullanarak bir sunucuya göndermek için bir düğüm size bir **ReportServerWeb** düğümün LCM yapılandırmasında engelleyin (LCM yapılandırma hakkında daha fazla bilgi için bkz. [yerel Configuration Manager Yapılandırma](../managing-nodes/metaConfig.md) ).</span><span class="sxs-lookup"><span data-stu-id="04da3-113">You tell a node to send reports to a server by using a **ReportServerWeb** block in the node's LCM configuration (for information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md)).</span></span> <span data-ttu-id="04da3-114">Raporlar, düğümün gönderdiği server (bir SMB paylaşımına raporları gönderilemiyor) web çekme sunucusu olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="04da3-114">The server to which the node sends reports must be set up as a web pull server (you cannot send reports to an SMB share).</span></span> <span data-ttu-id="04da3-115">Bir çekme sunucusu ayarlama hakkında daha fazla bilgi için bkz: [bir DSC web çekme sunucusu ayarlama](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="04da3-115">For information about setting up a pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span> <span data-ttu-id="04da3-116">Rapor sunucusu, aynı hizmeti, düğüm yapılandırmaları çeker ve kaynaklarını alan veya farklı bir hizmet olabilir.</span><span class="sxs-lookup"><span data-stu-id="04da3-116">The report server can be the same service from which the node pulls configurations and gets resources, or it can be a different service.</span></span>

<span data-ttu-id="04da3-117">İçinde **ReportServerWeb** bloğu çekme hizmetini ve sunucu için bilinen bir kayıt anahtarı URL'sini belirtin.</span><span class="sxs-lookup"><span data-stu-id="04da3-117">In the **ReportServerWeb** block, you specify the URL of the pull service and a registration key that is known to the server.</span></span>

<span data-ttu-id="04da3-118">Aşağıdaki yapılandırmayı bir düğüm için çekme yapılandırmaları hizmetten yapılandırır ve bir hizmet farklı bir sunucuda raporlar gönderir.</span><span class="sxs-lookup"><span data-stu-id="04da3-118">The following configuration configures a node to pull configurations from one service, and send reports to a service on a different server.</span></span>

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
            ServerURL               = 'http://CONTOSO-REPORT:8080/PSDSCReportServer.svc'
            RegistrationKey         = 'ba39daaa-96c5-4f2f-9149-f95c46460faa'
            AllowUnsecureConnection = $true
        }
    }
}

ReportClientConfig
```

<span data-ttu-id="04da3-119">Aşağıdaki yapılandırma, bir düğüm yapılandırmaları, kaynaklar ve raporlama için tek bir sunucu kullanmak için yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="04da3-119">The following configuration configures a node to use a single server for configurations, resources, and reporting.</span></span>

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
> <span data-ttu-id="04da3-120">Web hizmeti, bir çekme sunucusu ayarladığınızda istediğiniz adı verebilirsiniz ancak **ServerURL** özelliği, hizmet adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="04da3-120">You can name the web service whatever you want when you set up a pull server, but the **ServerURL** property must match the service name.</span></span>

## <a name="getting-report-data"></a><span data-ttu-id="04da3-121">Rapor verilerini alma</span><span class="sxs-lookup"><span data-stu-id="04da3-121">Getting report data</span></span>

<span data-ttu-id="04da3-122">Çekme sunucusuna gönderilen raporlar, sunucu üzerinde bir veritabanına girilir.</span><span class="sxs-lookup"><span data-stu-id="04da3-122">Reports sent to the pull server are entered into a database on the server.</span></span> <span data-ttu-id="04da3-123">Raporları, web hizmetine çağrı aracılığıyla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="04da3-123">The reports are available through calls to the web service.</span></span> <span data-ttu-id="04da3-124">Belirli bir düğümün raporları almak için aşağıdaki biçimde rapor web hizmeti için bir HTTP isteği gönder: `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`</span><span class="sxs-lookup"><span data-stu-id="04da3-124">To retrieve reports for a specific node, send an HTTP request to the report web service in the following form: `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`</span></span>
<span data-ttu-id="04da3-125">Burada `MyNodeAgentId` raporları almak istediğiniz düğümün Agentıd olduğu.</span><span class="sxs-lookup"><span data-stu-id="04da3-125">where `MyNodeAgentId` is the AgentId of the node for which you want to get reports.</span></span> <span data-ttu-id="04da3-126">Çağırarak bir düğüm için Agentıd alabilirsiniz [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) bu düğümde.</span><span class="sxs-lookup"><span data-stu-id="04da3-126">You can get the AgentID for a node by calling [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) on that node.</span></span>

<span data-ttu-id="04da3-127">Raporları, bir dizi JSON nesnesi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="04da3-127">The reports are returned as an array of JSON objects.</span></span>

<span data-ttu-id="04da3-128">Aşağıdaki komut dosyasını raporlar üzerinde çalıştığı düğüm için döndürür:</span><span class="sxs-lookup"><span data-stu-id="04da3-128">The following script returns the reports for the node on which it is run:</span></span>

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

## <a name="viewing-report-data"></a><span data-ttu-id="04da3-129">Rapor verileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="04da3-129">Viewing report data</span></span>

<span data-ttu-id="04da3-130">Sonucu için bir değişken ayarlarsanız **GetReport** işlevi, tek tek alanları döndürülen dizinin bir öğedeki görüntüleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="04da3-130">If you set a variable to the result of the **GetReport** function, you can view the individual fields in an element of the array that is returned:</span></span>

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

<span data-ttu-id="04da3-131">Varsayılan olarak, raporları göre sıralanır **JobId**.</span><span class="sxs-lookup"><span data-stu-id="04da3-131">By default, the reports are sorted by **JobID**.</span></span> <span data-ttu-id="04da3-132">En son rapor almak için raporları göre azalan düzende sıralayabilir **StartTime** özelliği ve dizinin get ilk öğesi:</span><span class="sxs-lookup"><span data-stu-id="04da3-132">To get the most recent report, you can sort the reports by descending **StartTime** property, and then get the first element of the array:</span></span>

```powershell
$reportsByStartTime = $reports | Sort-Object {$_."StartTime" -as [DateTime] } -Descending
$reportMostRecent = $reportsByStartTime[0]
```

<span data-ttu-id="04da3-133">Dikkat **StatusData** birçok özellik içeren bir nesne bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="04da3-133">Notice that the **StatusData** property is an object with a number of properties.</span></span> <span data-ttu-id="04da3-134">Raporlama verilerini çoğunu olduğu budur.</span><span class="sxs-lookup"><span data-stu-id="04da3-134">This is where much of the reporting data is.</span></span> <span data-ttu-id="04da3-135">Tek tek alanlarda bakalım **StatusData** özelliği için en son Rapor:</span><span class="sxs-lookup"><span data-stu-id="04da3-135">Let's look at the individual fields of the **StatusData** property for the most recent report:</span></span>

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

<span data-ttu-id="04da3-136">Yanı sıra, bu iki kaynağın en son yapılandırmayı adlı ve bunları birinin istenen durumda olduğu ve bunlardan biri değildi gösterir.</span><span class="sxs-lookup"><span data-stu-id="04da3-136">Among other things, this shows that the most recent configuration called two resources, and that one of them was in the desired state, and one of them was not.</span></span> <span data-ttu-id="04da3-137">Yalnızca bir daha okunabilir çıktısını almak **ResourcesNotInDesiredState** özelliği:</span><span class="sxs-lookup"><span data-stu-id="04da3-137">You can get a more readable output of just the **ResourcesNotInDesiredState** property:</span></span>

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

<span data-ttu-id="04da3-138">Bu örnek rapor verilerle yapabilecekleriniz hakkında fikir vermek için yöneliktir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="04da3-138">Note that these examples are meant to give you an idea of what you can do with report data.</span></span> <span data-ttu-id="04da3-139">PowerShell'de, JSON ile çalışma hakkında giriş için bkz [JSON ve PowerShell ile yürütmeyi](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).</span><span class="sxs-lookup"><span data-stu-id="04da3-139">For an introduction on working with JSON in PowerShell, see [Playing with JSON and PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).</span></span>

## <a name="see-also"></a><span data-ttu-id="04da3-140">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="04da3-140">See Also</span></span>

[<span data-ttu-id="04da3-141">Yerel Configuration Manager'ı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="04da3-141">Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="04da3-142">Bir DSC web çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="04da3-142">Setting up a DSC web pull server</span></span>](pullServer.md)

[<span data-ttu-id="04da3-143">Yapılandırma adlarını kullanarak çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="04da3-143">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)