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
# <a name="using-a-dsc-report-server"></a>DSC rapor sunucusu kullanma

Şunun için geçerlidir: Windows PowerShell 5,0

> [!IMPORTANT]
> Çekme sunucusu (Windows özelliği *DSC-Service*) Windows Server 'ın desteklenen bir bileşenidir, ancak yeni özellikler veya yetenekler sunmaya yönelik bir plan yoktur. Yönetilen istemcileri [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) geçirmeyi (Windows Server 'Da çekme sunucusunun ötesindeki özellikleri içerir) veya [burada](pullserver.md#community-solutions-for-pull-service)listelenen topluluk çözümlerinin birini kullanmaya başlamanız önerilir.
>
> [!NOTE]
> Bu konuda açıklanan rapor sunucusu PowerShell 4,0 ' de kullanılamaz.

Bir düğümün yerel Configuration Manager (LCM), yapılandırma durumu hakkında raporları bir çekme sunucusuna gönderecek şekilde yapılandırılabilir ve bu da bu verileri almak için sorgulanabilecek. Düğüm bir yapılandırmayı denetleyip uyguladığı her seferinde rapor sunucusuna bir rapor gönderir. Bu raporlar sunucusundaki bir veritabanında depolanır ve Raporlama Web hizmeti çağırarak alınabilir. Her rapor, hangi yapılandırmaların uygulandığı ve başarılı olup olmadığı, kullanılan kaynaklar, oluşturulan tüm hatalar ve başlangıç ve bitiş zamanları gibi bilgileri içerir.

## <a name="configuring-a-node-to-send-reports"></a>Rapor göndermek için bir düğüm yapılandırma

Bir düğüme, düğümün LCM yapılandırmasında **Reportserverweb** bloğu kullanarak rapor göndermesini söylemiş olursunuz (LCM 'yi yapılandırma hakkında daha fazla bilgi için bkz. [yerel Configuration Manager yapılandırma](../managing-nodes/metaConfig.md)). Düğümün rapor gönderdiği sunucu bir Web çekme sunucusu olarak ayarlanmalıdır (bir SMB paylaşımında rapor gönderemezsiniz). Çekme sunucusu kurma hakkında daha fazla bilgi için bkz. [DSC Web çekme sunucusu](pullServer.md)kurma. Rapor sunucusu, düğümün yapılandırma almasını ve kaynakları almasını sağlayan aynı hizmet olabilir veya farklı bir hizmet olabilir.

**Reportserverweb** bloğunda, çekme hizmetinin URL 'sini ve sunucu tarafından bilinen bir kayıt anahtarını belirtirsiniz.

Aşağıdaki yapılandırma bir düğümü, bir hizmetten yapılandırmaları çekmek ve farklı bir sunucudaki bir hizmete rapor göndermek için yapılandırır.

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

Aşağıdaki yapılandırma, bir düğümü yapılandırmalar, kaynaklar ve raporlama için tek bir sunucu kullanacak şekilde yapılandırır.

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
> Web hizmetini bir çekme sunucusu ayarlarken istediğiniz her şey olarak adlandırabilirsiniz, ancak **ServerURL** özelliğinin hizmet adıyla eşleşmesi gerekir.

## <a name="getting-report-data"></a>Rapor verileri alınıyor

Çekme sunucusuna gönderilen raporlar sunucusundaki bir veritabanına girilir. Raporlar, Web hizmetine yapılan çağrılar aracılığıyla kullanılabilir. Belirli bir düğüme ait raporları almak için, aşağıdaki biçimde rapor Web hizmetine bir HTTP isteği gönderin:`http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`
Burada `MyNodeAgentId` , raporları almak istediğiniz düğümün olan. Bu düğümde [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) ' i çağırarak bir düğüm için bir düğüm Için sahip kimliği alabilirsiniz.

Raporlar, JSON nesneleri dizisi olarak döndürülür.

Aşağıdaki betik, üzerinde çalıştığı düğümün raporlarını döndürür:

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

## <a name="viewing-report-data"></a>Rapor verilerini görüntüleme

**Getreport** işlevinin sonucuna bir değişken ayarlarsanız, tek tek alanları döndürülen dizinin bir öğesi içinde görüntüleyebilirsiniz:

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

Varsayılan olarak, raporlar iş **kimliği**' ne göre sıralanır. En son raporu almak için raporları azalan **StartTime** özelliğine göre sıralayabilir ve sonra dizinin ilk öğesini alabilirsiniz:

```powershell
$reportsByStartTime = $reports | Sort-Object {$_."StartTime" -as [DateTime] } -Descending
$reportMostRecent = $reportsByStartTime[0]
```

**Statusdata** özelliğinin, çok sayıda özelliği olan bir nesne olduğuna dikkat edin. Bu, raporlama verilerinin büyük olduğu yerdir. En son rapor için **Statusdata** özelliğinin ayrı alanlarını inceleyelim:

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

Diğer şeyler arasında bu, en son yapılandırmanın iki kaynak olarak adlandırıldığını ve bunlardan birinin istenen durumda olduğunu ve bunlardan birinin ne olduğunu gösterir. Yalnızca **Resourcesnotındesıredstate** özelliğinden daha okunabilir bir çıktı alabilirsiniz:

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

Bu örneklerin rapor verileriyle neler yapabileceğinizi gösteren bir fikir sunyacağını unutmayın. PowerShell 'de JSON ile çalışmaya giriş için bkz. [JSON ve PowerShell Ile yürütme](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).

## <a name="see-also"></a>Ayrıca bkz:

[Yerel Configuration Manager yapılandırma](../managing-nodes/metaConfig.md)

[DSC Web çekme sunucusu ayarlama](pullServer.md)

[Yapılandırma adlarını kullanarak çekme istemcisi ayarlama](pullClientConfigNames.md)
