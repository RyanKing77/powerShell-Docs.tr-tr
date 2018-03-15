---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: DSC rapor sunucusu kullanma
ms.openlocfilehash: fdf16a2de6aea46844d3812029fae474e80ae6ac
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="using-a-dsc-report-server"></a>DSC rapor sunucusu kullanma

> İçin geçerlidir: Windows PowerShell 5.0

>**Not:** PowerShell 4. 0 ' Bu konuda açıklanan rapor sunucusu kullanılamıyor.

Bir düğümün yerel Configuration Manager (LCM'yi), ardından bu verileri almak için sorgulanabilir bir çekme sunucusuna yapılandırma durumunu hakkında raporlar göndermek için yapılandırılabilir. Düğüm denetler ve bir yapılandırma uygulanabilir her zaman bir raporu rapor sunucusuna gönderir. Bu raporlar, sunucu üzerindeki bir veritabanında depolanır ve raporlama web hizmeti çağrısı yaparak alınabilir. Kullanılan kaynaklar, durum oluştu, başlangıç ve bitiş zamanlarını hataları, her rapor hangi yapılandırmaları uygulanan ve bunların başarılı olup olmadığı gibi bilgileri içerir.

## <a name="configuring-a-node-to-send-reports"></a>Bir düğüm raporları göndermek için yapılandırma

Raporları kullanarak bir sunucuya göndermek için bir düğüm söyleyin bir **ReportServerWeb** düğümün LCM'yi yapılandırmasında engelle (LCM'yi yapılandırma hakkında daha fazla bilgi için bkz: [yerel Configuration Manager Yapılandırma](metaConfig.md) ). Sunucunun, düğüm raporları gönderdiği (bir SMB paylaşımına raporları gönderilemiyor) web çekme sunucusu olarak ayarlanması gerekir. Bir çekme sunucusu kurma hakkında daha fazla bilgi için bkz: [DSC web çekme sunucusu kurma](pullServer.md). Rapor sunucusu, aynı hizmetin içinden düğüm yapılandırmaları çeker ve kaynakları alır veya farklı bir hizmet olabilir.
 
İçinde **ReportServerWeb** bloğu, çekme hizmeti ve sunucu için bilinen bir kayıt anahtarı URL'sini belirtin.
 
Aşağıdaki yapılandırma bir düğüm için çekme yapılandırmaları bir hizmetinden yapılandırır ve bir hizmet farklı bir sunucuda raporları gönderir. 
 
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

Aşağıdaki yapılandırma, tek bir sunucu yapılandırmaları, kaynaklar ve raporlama için kullanılmak üzere bir düğümü yapılandırır.

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

>**Not:** bir çekme sunucuyu, ayarladığınızda istediğiniz web hizmeti adı verebilirsiniz ancak **ServerURL** özelliği, hizmet adı eşleşmelidir.

## <a name="getting-report-data"></a>Rapor verileri alma

Çekme sunucusuna gönderilen raporlar sunucuda bir veritabanına girilir. Raporları, web hizmeti çağrıları aracılığıyla kullanılabilir. Belirli bir düğümün raporlar almak için aşağıdaki biçimde web hizmeti rapor için bir HTTP isteği göndermek: `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId= 'MyNodeAgentId')/Reports` burada `MyNodeAgentId` raporlar almak istediğiniz düğümü Agentıd olduğu. Çağırarak Agentıd için bir düğüm alabilirsiniz [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx) bu düğümde.

Raporlar JSON nesnelerinin bir dizisi döndürülür.

Aşağıdaki komut dosyası üzerinde çalıştığı düğüm raporları döndürür:

```powershell
function GetReport
{
    param($AgentId = "$((glcm).AgentId)", $serviceURL = "http://CONTOSO-REPORT:8080/PSDSCPullServer.svc")
    $requestUri = "$serviceURL/Nodes(AgentId= '$AgentId')/Reports"
    $request = Invoke-WebRequest -Uri $requestUri  -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" `
               -UseBasicParsing -Headers @{Accept = "application/json";ProtocolVersion = "2.0"} `
               -ErrorAction SilentlyContinue -ErrorVariable ev
    $object = ConvertFrom-Json $request.content
    return $object.value
}
```
    
## <a name="viewing-report-data"></a>Rapor verileri görüntüleme

Bir değişken sonucuna ayarlarsanız **GetReport** işlevi, tek tek alanların döndürülen dizi bir öğedeki görüntüleyebilirsiniz:

```powershell
$reports = GetReport
$reports[1]


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

Varsayılan olarak, raporları göre sıralanır **JobId**. En son rapor alınacağı raporları göre azalan sırada sıralayabilirsiniz **StartTime** özelliği ve dizinin get ilk öğe:

```powershell
$reportsByStartTime = $reports | Sort-Object {$_."StartTime" -as [DateTime] } -Descending
$reportMostRecent = $reportsByStartTime[0]
```

Dikkat **StatusData** özelliği olan bir dizi özellikleri olan bir nesne. Raporlama verilerini çoğunu olduğu budur. Tek tek alanlarda bakalım **StatusData** özelliği en son rapor için:

```powershell
$statusData = $reportMostRecent.StatusData | ConvertFrom-Json
$statusData

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

Bunun yanı sıra, bu iki kaynak en son yapılandırmayı çağrılır ve bu bunlardan birini istenen durumdaydı ve bunlardan biri değildi gösterir. Yalnızca daha okunabilir çıktısı alabilirsiniz **ResourcesNotInDesiredState** özelliği:

```powershell
$statusData.ResourcesInDesiredState

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

Rapor verileri ile neler yapabileceğiniz hakkında bir fikir vermek için bu örnekler yöneliktir unutmayın. PowerShell'de JSON ile çalışma hakkında giriş için bkz: [JSON ve PowerShell yürütme](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).

## <a name="see-also"></a>Ayrıca bkz:
- [Yerel Yapılandırma Yöneticisi'ni yapılandırma](metaConfig.md)
- [DSC çekme sunucusuna ayarlama](pullServer.md)
- [Yapılandırma adlarını kullanarak çekme istemcisi ayarlama](pullClientConfigNames.md)

