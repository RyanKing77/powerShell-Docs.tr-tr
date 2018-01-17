---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "PowerShell istenen durum yapılandırması kısmi yapılandırmaları"
ms.openlocfilehash: 66791bb7b14898d292b9da38dd27ba45b7c75d88
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a>PowerShell istenen durum yapılandırması kısmi yapılandırmaları

>İçin geçerlidir: Windows PowerShell 5.0 ve sonraki sürümleri.

PowerShell 5. 0'da, istenen durum Yapılandırması'nı (DSC) parçada ve birden fazla kaynaktan teslim edilecek yapılandırmaları sağlar. Hedef düğümde bulunan yerel Configuration Manager (LCM'yi) tek bir yapılandırma olarak uygulamadan önce parçaları birlikte koyar. Paylaşım denetimi ekip veya kişiler arasındaki yapılandırmasının bu yeteneği sağlar. İki veya daha fazla takıma geliştiricilerin bir hizmette işbirliği, örneğin, bunlar her hizmetin kendi parçası yönetmek için yapılandırmaları oluşturmak isteyebilirsiniz. Bu yapılandırmalar her farklı çekme sunucularından çekilen ve geliştirme farklı aşamalarında eklenemedi. Kısmi yapılandırmaları de farklı kişilere veya ekiplere düğümleri bir tek yapılandırma belgesini düzenleme koordine etmek zorunda kalmadan yapılandırma farklı yönlerini kontrol olanak sağlar. Örneğin, bir takım başka bir takım diğer uygulama ve hizmetlerin bu VM'de dağıtılabileceği sırada VM ve işletim sistemi dağıtmak için sorumlu olabilir. Kısmi yapılandırmaları ile her takım her ikisini gereksiz yere karmaşık olmadan kendi yapılandırması oluşturabilirsiniz.

Kısmi yapılandırmalarını itme modu, çekme modu veya ikisinin birleşimini kullanabilirsiniz.

## <a name="partial-configurations-in-push-mode"></a>Zorlama modunda kısmi yapılandırmaları
Kısmi yapılandırmaları zorlama modunda kullanmak için LCM'yi kısmi yapılandırmalarını almak için hedef düğümde yapılandırın. Her bir kısmi yapılandırmasının hedef Yayımla DSCConfiguration cmdlet'ini kullanarak gönderilir gerekir. Hedef düğüm ardından tek bir yapılandırması kısmi yapılandırmaya birleştirir ve çağırarak yapılandırma uygulayabilirsiniz [başlangıç DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet'i.

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a>Anında iletme modu kısmi yapılandırmaları için LCM'yi yapılandırma
Kısmi yapılandırmaları için LCM'yi zorlama modunda yapılandırmak için oluşturduğunuz bir **DSCLocalConfigurationManager** bir yapılandırmayla **PartialConfiguration** kısmi her yapılandırma için bloğu. LCM'yi yapılandırma hakkında daha fazla bilgi için bkz: [yerel Configuration Manager Yapılandırma Windows](https://technet.microsoft.com/en-us/library/mt421188.aspx). Aşağıdaki örnek, iki kısmi yapılandırmaları bekliyor LCM'yi yapılandırma gösterir — işletim sistemi dağıtan, diğeri dağıtır ve SharePoint yapılandırır.

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        
           PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}
PartialConfigDemo 
```

**RefreshMode** her kısmi yapılandırma "gönderme"temelli ayarlayın. Adları **PartialConfiguration** blokları (Bu durumda, "ServiceAccountConfig" ve "SharePointConfig"), hedef düğüme gönderilen yapılandırmaları adlarını tam olarak eşleşmelidir.

>**Not:** adlandırılmış her **PartialConfiguration** yapılandırma betiği, MOF dosyası adını değil belirtildiği gibi blok yapılandırmasının gerçek adını eşleşmesi gerekir ya da adı olan Hedef düğüm veya `localhost`.

### <a name="publishing-and-starting-push-mode-partial-configurations"></a>Yayımlama ve başlangıç itme modu kısmi yapılandırmaları

Ardından çağıran [Yayımla DSCConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) her yapılandırma için yapılandırma belgeleri olarak içeren klasörleri geçirme **yolu** parametreleri. `Publish-DSCConfiguration`Hedef düğümleri yapılandırma MOF dosyasına yerleştirir. Her iki yapılandırma yayımladıktan sonra çağırabilirsiniz `Start-DSCConfiguration –UseExisting` hedef düğümde bulunan.

Örneğin, aşağıdaki yapılandırma MOF belgeleri yazma düğümde derlenmiş ise:

```powershell
PS C:\PartialConfigTest> Get-ChildItem -Recurse


    Directory: C:\PartialConfigTest


Mode                LastWriteTime         Length Name                                                                                                                                         
----                -------------         ------ ----                                                                                                                                         
d-----        8/11/2016   1:55 PM                ServiceAccountConfig                                                                                                                  
d-----       11/17/2016   4:14 PM                SharePointConfig                                                                                                                                    


    Directory: C:\PartialConfigTest\ServiceAccountConfig


Mode                LastWriteTime         Length Name                                                                                                                                         
----                -------------         ------ ----                                                                                                                                         
-a----        8/11/2016   2:02 PM           2034 TestVM.mof                                                                                                                                


    Directory: C:\DscTests\SharePointConfig


Mode                LastWriteTime         Length Name                                                                                                                                         
----                -------------         ------ ----                                                                                                                                         
-a----       11/17/2016   4:14 PM           1930 TestVM.mof                                                                                                                                     
```

Yayımlama ve yapılandırmaları aşağıdaki şekilde çalıştırmanız:

```powershell
PS C:\PartialConfigTest> Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Start-DscConfiguration -UseExisting -ComputerName 'TestVM'

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command                  
--     ----            -------------   -----         -----------     --------             -------                  
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

>**Not:** çalıştıran kullanıcının [Yayımla DSCConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) cmdlet'i hedef düğümde yönetici ayrıcalıkları olması gerekir.

## <a name="partial-configurations-in-pull-mode"></a>Çekme modunda kısmi yapılandırmaları

Kısmi yapılandırmaları bir veya daha fazla çekme sunucularından çekilen (çekme sunucuları hakkında daha fazla bilgi için bkz: [Windows PowerShell istenen durum yapılandırma çekme sunucularına](pullServer.md). Bunu yapmak için kısmi yapılandırmaları çekme ve ad ve yapılandırma belgelerini çekme sunucularda düzgün bir şekilde bulmak için hedef düğümde bulunan LCM'yi yapılandırmanız gerekir.

### <a name="configuring-the-lcm-for-pull-node-configurations"></a>Çekme düğüm yapılandırmaları için LCM'yi yapılandırma

Bir çekme sunucudan kısmi yapılandırmaları çıkarmak için LCM'yi yapılandırmak için çekme sunucu ya da tanımladığınız bir **ConfigurationRepositoryWeb** (için bir HTTP istek sunucusu) veya **ConfigurationRepositoryShare** () SMB çekme server için) blok. Ardından oluşturduğunuz **PartialConfiguration** kullanarak çekme sunucusuna başvuran blokları **ConfigurationSource** özelliği. Oluşturmak için gereken bir **ayarları** blok LCM'yi çekme modunu kullandığını belirtmek ve belirtmek için **ConfigurationNames** veya **ConfigurationID** , çekme sunucunun ve Hedef düğüm yapılandırmaları tanımlamak için kullanın. Kullanan iki kısmi yapılandırmaları çekme sunucusuna ve CONTOSO PullSrv adlı bir HTTP çekme sunucusunda aşağıdaki meta yapılandırmasını tanımlar.

LCM'yi kullanarak yapılandırma hakkında daha fazla bilgi için **ConfigurationNames**, bkz: [yapılandırma adları kullanarak bir çekme istemcisi kurarken](pullClientConfigNames.md). LCM'yi kullanarak yapılandırma hakkında bilgi için **ConfigurationID**, bkz: [yapılandırma Kimliğini kullanarak bir çekme istemcisi kurarken](pullClientConfigID.md).

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a>Yapılandırma adları kullanarak çekme modu yapılandırmaları için LCM'yi yapılandırma

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'    
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38     
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }     
        
        PartialConfiguration ServiceAccountConfig 
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv") 
        }
 
        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }
   
}
``` 

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a>LCM'yi ConfigurationID kullanarak çekme modu yapılandırmaları için yapılandırma

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30 
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }
        
           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo 
```

Birden çok çekme sunucusundan kısmi yapılandırmaları çekebilir — her çekme sunucusuna tanımlamak ve ardından her uygun çekme sunucusuna başvurmak yalnızca gerekir **PartialConfiguration** bloğu.

Meta yapılandırma oluşturduktan sonra yapılandırma belge (bir MOF dosyası) oluşturun ve ardından çağıran çalıştırmalısınız [kümesi DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) LCM'yi yapılandırmak için.

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a>Adlandırma ve çekme sunucusunda (ConfigurationNames) yapılandırma belgelerini yerleştirme

Kısmi yapılandırma belgeleri olarak belirtilen klasöre yerleştirilmelidir **ConfigurationPath** içinde `web.config` çekme sunucusuna ilişkin dosyasını (genellikle `C:\Program Files\WindowsPowerShell\DscService\Configuration`). 

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a>PowerShell 5.1 çekme sunucusunda yapılandırma Belgeleri adlandırma

Bir tek tek çekme sunucusuna yalnızca bir kısmi yapılandırmasından çekme, yapılandırma belgesini herhangi bir ad olabilir. Birden fazla kısmi yapılandırmasını çekme sunucusundan çekme, yapılandırma belge ya da adlandırılabilir `<ConfigurationName>.mof`, burada _ConfigurationName_ kısmi yapılandırma adı veya `<ConfigurationName>.<NodeName>.mof`, burada  _ConfigurationName_ kısmi yapılandırma adıdır ve _NodeName_ hedef düğüm adıdır. Bu, çekme yapılandırmaları için Azure Otomasyonu DSC istek sunucusundan sağlar.


#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a>PowerShell 5.0 çekme sunucusunda yapılandırma Belgeleri adlandırma

Aşağıdaki gibi yapılandırma belgelerini adlı: `ConfigurationName.mof`, burada _ConfigurationName_ kısmi yapılandırma adıdır. Bizim örneğimizde, aşağıdaki gibi yapılandırma belgelerini adlı:

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a>Adlandırma ve çekme sunucusunda (ConfigurationID) yapılandırma belgelerini yerleştirme

Kısmi yapılandırma belgeleri olarak belirtilen klasöre yerleştirilmelidir **ConfigurationPath** içinde `web.config` çekme sunucusuna ilişkin dosyasını (genellikle `C:\Program Files\WindowsPowerShell\DscService\Configuration`). Aşağıdaki gibi yapılandırma belgelerini adlı: _ConfigurationName_. _ConfigurationID_`.mof`, burada _ConfigurationName_ kısmi yapılandırma adıdır ve _ConfigurationID_ yapılandırması kimliği üzerinde LCM'yi tanımlanır Hedef düğüm. Bizim örneğimizde, aşağıdaki gibi yapılandırma belgelerini adlı:

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```


### <a name="running-partial-configurations-from-a-pull-server"></a>Bir çekme sunucusundan kısmi yapılandırmaları çalıştırma

Hedef düğümde bulunan LCM'yi yapılandırılmış ve belgeleri oluşturulduğundan ve düzgün şekilde çekme sunucusunda adlı yapılandırma, hedef düğüm kısmi yapılandırmaları çeker sonra bunları birleştirmek ve normal sonuç yapılandırmasını Uygula tarafından belirlenen aralıklarla **RefreshFrequencyMins** LCM'yi özelliği. Yenilemeye zorlamak istiyorsanız, çağırabilirsiniz [güncelleştirme DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx) yapılandırmaları çekme cmdlet'ini ve ardından `Start-DSCConfiguration –UseExisting` bunları uygulamak için.


## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a>Karma İtme hem de çekme modlarında kısmi yapılandırmaları

Ayrıca, anında iletme karıştırmak ve modları kısmi yapılandırmaları için çekme. Diğer bir deyişle, başka bir kısmi yapılandırma gönderilen karşın, bir istek sunucusundan çekilen bir kısmi yapılandırmasına sahip olabilir. Kısmi her yapılandırma için yenileme modu önceki bölümlerde açıklandığı gibi belirtin. Örneğin, aşağıdaki meta yapılandırması ile aynı örnek açıklar `ServiceAccountConfig` çekme modunda kısmi yapılandırma ve `SharePointConfig` zorlama modunda kısmi yapılandırma.

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a>ConfigurationNames kullanarak karma anında iletme ve çekme modları

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'    
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38     
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }     
        
        PartialConfiguration ServiceAccountConfig 
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull' 
        }
 
        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }
   
}
``` 

### <a name="mixed-push-and-pull-modes-using-configurationid"></a>ConfigurationID kullanarak karma anında iletme ve çekme modları

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30 
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }
        
           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo 
```

Unutmayın **RefreshMode** ayarları bloğunda belirtilen "Çekme" olan ancak **RefreshMode** için `SharePointConfig` kısmi yapılandırmadır "Gönderme".

Ad ve bunların ilgili yenileme modları için yukarıda açıklandığı gibi yapılandırma MOF dosyaları bulun. Çağrı **Yayımla DSCConfiguration** yayımlamak için `SharePointConfig` kısmi yapılandırması ve ya da bekle `ServiceAccountConfig` istek sunucusundan çekebilir veya çağırarak yenilemeye zorlamak için yapılandırma [ Güncelleştirme DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).

## <a name="example-serviceaccountconfig-partial-configuration"></a>Örnek ServiceAccountConfig kısmi yapılandırma

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration


    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential
            
        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig

```
## <a name="example-sharepointconfig-partial-configuration"></a>Örnek SharePointConfig kısmi yapılandırma
```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```
##<a name="see-also"></a>Ayrıca bkz: 

**Kavramları**
[Windows PowerShell istenen durum yapılandırması çekme sunucuları](pullServer.md) 

[Windows yerel Configuration Manager'ı yapılandırma](https://technet.microsoft.com/en-us/library/mt421188.aspx) 

