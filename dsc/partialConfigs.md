---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: PowerShell Desired State Configuration kısmi yapılandırmalar
ms.openlocfilehash: 1b9ff8534f4c11d6859587830a04075be55a7d54
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268390"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a>PowerShell Desired State Configuration kısmi yapılandırmalar

_İçin geçerlidir: Windows PowerShell 5.0 ve üzeri._

PowerShell 5. 0'da, parçaları ve birden çok kaynaktan teslim edilecek yapılandırmaları Desired State Configuration ' nı (DSC) sağlar. Hedef düğümde yerel Configuration Manager (LCM) tek bir yapılandırma uygulamadan önce parçaların birlikte koyar. Bu özellik, paylaşım takımlar veya kişiler arasındaki yapılandırmasının denetimi sağlar. Bir hizmette Geliştirici ekipleri iki veya daha fazla işbirliği yapıyorsanız Örneğin, bunlar her hizmetin kendi parçası yönetmek için yapılandırmaları oluşturmak isteyebilirsiniz. Bu yapılandırmalardan birini her farklı çekme sunuculardan çekilmesi ve farklı yaşlardaki eklenemedi. Kısmi yapılandırmalar da farklı kişilere veya ekiplere düğümleri bir tek yapılandırma belgesini düzenleme koordine etmek zorunda kalmadan yapılandırma farklı yönlerini kontrol sağlar. Örneğin, bir takım başka bir takım, diğer uygulama ve hizmetlerin söz konusu VM'deki dağıtabilirsiniz ancak VM ve işletim sistemi dağıtmaktan sorumlu olabilir. Kısmi yapılandırmalar ile her ikisini gereksiz derecede karmaşık olmadan kendi yapılandırması her takım oluşturabilirsiniz.

Kısmi yapılandırmalar gönderme modunda, çekme modu veya ikisinin bir birleşimini kullanabilirsiniz.

## <a name="partial-configurations-in-push-mode"></a>Gönderme modunda kısmi yapılandırmalar

Kısmi yapılandırmalar gönderim modunda kullanmak için kısmi yapılandırmalar almak üzere hedef düğümde LCM yapılandırın. Her kısmi yapılandırması hedef kullanılarak gönderilen gerekir `Publish-DSCConfiguration` cmdlet'i. Hedef düğüm ardından tek bir yapılandırma kısmi yapılandırmaya birleştirir ve çağırarak yapılandırmayı uygulayabilir [Başlat-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet'i.

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a>Anında iletme modu kısmi yapılandırmalar için LCM yapılandırma

Kısmi yapılandırmalar için LCM gönderim modunda yapılandırmak için oluşturduğunuz bir **DSCLocalConfigurationManager** bir yapılandırmayla **PartialConfiguration** kısmi her yapılandırma için blok. LCM yapılandırma hakkında daha fazla bilgi için bkz. [yerel Configuration Manager Yapılandırma Windows](/powershell/dsc/metaConfig). Aşağıdaki örnek, iki kısmi yapılandırmalar bekliyor bir LCM yapılandırma gösterir; işletim sistemini dağıtan ve diğeri dağıtan ve SharePoint yapılandırır.

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

**RefreshMode** kısmi her yapılandırma "gönderme"temelli ayarlanır. Adlarını **PartialConfiguration** blokları (Bu durumda, "ServiceAccountConfig" ve "SharePointConfig"), tam olarak hedef düğüme itilir yapılandırmaların adlarının eşleşmesi gerekir.

> [!Note]
> Adlandırılmış her **PartialConfiguration** yapılandırma betiği, hedef düğüm adı ya da olmalıdırMOFdosyasıadıbelirtildiğişekilde,blokyapılandırmasınıngerçekadıeşleşmelidir`localhost`.

### <a name="publishing-and-starting-push-mode-partial-configurations"></a>Yayımlama ve anında iletme modu kısmi yapılandırmalar başlatılıyor

Ardından çağırın [Yayımla-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) her yapılandırma için olarak yapılandırma belgelerini içeren klasörleri aktarılmasından **yolu** parametreleri. `Publish-DSCConfiguration`Yapılandırma MOF dosyaları hedef düğümleri yerleştirir. Her iki yapılandırma yayımladıktan sonra çağırabilirsiniz `Start-DSCConfiguration –UseExisting` hedef düğümde bulunan.

Örneğin, aşağıdaki yapılandırma MOF belgeleri yazma düğümde derlenmişse:

```powershell
Get-ChildItem -Recurse
```

```output
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
Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
Start-DscConfiguration -UseExisting -ComputerName 'TestVM'
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

> [!Note]
> Çalıştıran kullanıcının [Yayımla-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet'i hedef düğümde yönetici ayrıcalıkları olması gerekir.

## <a name="partial-configurations-in-pull-mode"></a>Kısmi yapılandırmalar çekme modunda

Kısmi yapılandırmalar bir veya daha fazla çekme sunucusundan istenebilecek (çekme sunucuları hakkında daha fazla bilgi için bkz. [Windows PowerShell Desired State Configuration çekme sunucuları](pullServer.md). Bunu yapmak için kısmi yapılandırmalar çekme adlandırın ve yapılandırma belgelerini çekme sunucularda düzgün bir şekilde bulun. hedef düğümde LCM yapılandırmanız gerekir.

### <a name="configuring-the-lcm-for-pull-node-configurations"></a>Çekme düğüm yapılandırmaları için LCM yapılandırma

Kısmi yapılandırmalar çekme sunucusundan çekmek için LCM yapılandırmak için çekme sunucusu ya da tanımladığınız bir **ConfigurationRepositoryWeb** (için HTTP çekme sunucusu) veya **ConfigurationRepositoryShare** () SMB çekme sunucusu için) blok. Ardından oluşturduğunuz **PartialConfiguration** kullanarak çekme sunucusuna başvuran blokları **ConfigurationSource** özelliği. Ayrıca oluşturmanıza gerek bir **ayarları** blok LCM çekme modu kullandığını belirtmek ve belirtmek için **ConfigurationNames** veya **ConfigurationID** , çekme sunucusu ve Hedef düğüm yapılandırmaları tanımlamak için kullanın. Şu meta-yapılandırmayı PullSrv CONTOSO adlı bir HTTP çekme sunucusu tanımlar ve çekme sunucusuna kullanan iki kısmi yapılandırmalar.

LCM kullanarak yapılandırma hakkında daha fazla bilgi için **ConfigurationNames**, bkz: [yapılandırma adlarını kullanarak çekme istemcisi ayarlama](pullClientConfigNames.md). LCM kullanarak yapılandırma hakkında bilgi **ConfigurationID**, bkz: [yapılandırma Kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigID.md).

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a>Yapılandırma adlarını kullanarak çekme modu yapılandırmaları için LCM yapılandırma

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

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a>Çekme modu yapılandırmaları ConfigurationID kullanarak LCM yapılandırma

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

Kısmi yapılandırmalar birden fazla çekme sunucusundan çeker — her çekme sunucusu tanımlayın ve ardından her uygun çekme sunucusuna başvurmak yalnızca gerekir **PartialConfiguration** blok.

Meta-yapılandırma oluşturduktan sonra bunu bir yapılandırma belge (bir MOF dosyası) oluşturun ve ardından çağırmak için çalıştırmanız gerekir [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) LCM yapılandırmak için.

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a>Adlandırma ve yapılandırma belgelerini (ConfigurationNames) çekme sunucusunda yerleştirme

Kısmi yapılandırma belgelerini olarak belirtilen klasöre yerleştirilmelidir **Yapılandırmayolu** içinde `web.config` çekme sunucusu için dosya (genellikle `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a>Yapılandırma belgelerini PowerShell 5.1 çekme sunucusunda adlandırma

Bir çekme sunucusu yalnızca bir kısmi yapılandırmasından çeken, yapılandırma belgesi herhangi bir ad olabilir. Bir çekme sunucusu birden fazla kısmi yapılandırmasından çeken, yapılandırma belgesi ya da adlandırılabilir `<ConfigurationName>.mof`burada *ConfigurationName* kısmi yapılandırmanın adını veya `<ConfigurationName>.<NodeName>.mof`burada *ConfigurationName* kısmi yapılandırma adıdır ve *NodeName* hedef düğüm adıdır. Bu, çekme yapılandırmaları Azure Automation DSC çekme sunucusundan sağlar.

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a>PowerShell 5.0 çekme sunucusunda yapılandırma belgelerini adlandırma

Yapılandırma belgelerini gibi adlandırılmalıdır: `ConfigurationName.mof`burada *ConfigurationName* kısmi yapılandırma adıdır. Bizim örneğimizde, yapılandırma belgelerini şu şekilde adlandırılması:

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a>Adlandırma ve yapılandırma belgelerini (ConfigurationID) çekme sunucusunda yerleştirme

Kısmi yapılandırma belgelerini olarak belirtilen klasöre yerleştirilmelidir **Yapılandırmayolu** içinde `web.config` çekme sunucusu için dosya (genellikle `C:\Program Files\WindowsPowerShell\DscService\Configuration`). Yapılandırma belgelerini gibi adlandırılmalıdır: `<ConfigurationName>.<ConfigurationID>.mof`burada _ConfigurationName_ kısmi yapılandırma adıdır ve _ConfigurationID_ kimliği tanımlanan yapılandırma Hedef düğümde bulunan LCM. Bizim örneğimizde, yapılandırma belgelerini şu şekilde adlandırılması:

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a>Kısmi yapılandırmalar çekme sunucusundan çalıştırma

Hedef düğümde bulunan LCM yapılandırıldı ve belgeleri oluşturulduğundan ve doğru çekme sunucusunda adlı yapılandırma, hedef düğüm kısmi yapılandırmalar çeker sonra birleştirip ve normal sonuç yapılandırmasını Uygula tarafından belirtilen aralıklarla **RefreshFrequencyMins** LCM özelliğidir. Daha önce yenilemeye zorlamak istiyorsanız, çağırabilirsiniz [güncelleştirme-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) yapılandırmalar çekme cmdlet'ini ve ardından `Start-DSCConfiguration –UseExisting` uygulamak için.

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a>Karma gönderme ve çekme modlarında kısmi yapılandırmalar

Ayrıca, anında iletme karıştırın ve modları için kısmi yapılandırmalar çekme. Diğer bir deyişle, başka bir kısmi yapılandırma gönderilir, bir çekme sunucusundan çekilen bir kısmi yapılandırmasına sahip. Önceki bölümlerde açıklandığı gibi her kısmi yapılandırması için yenileme modunu belirtin. Örneğin, aşağıdaki meta-yapılandırması ile aynı örneği açıklar `ServiceAccountConfig` çekme modu kısmi yapılandırmasında ve `SharePointConfig` gönderme modunda kısmi yapılandırma.

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a>ConfigurationNames kullanarak karma gönderme ve çekme modu

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

### <a name="mixed-push-and-pull-modes-using-configurationid"></a>ConfigurationID kullanarak karma gönderme ve çekme modu

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

Unutmayın **RefreshMode** blok içinde belirtilen "Pull" olan ancak **RefreshMode** için `SharePointConfig` kısmi yapılandırmadır "Gönderme".

Ad ve bunların ilgili yenileme modları için yukarıda açıklandığı gibi yapılandırma MOF dosyaları bulun.
Çağrı `Publish-DSCConfiguration` yayımlamak için `SharePointConfig` kısmi yapılandırma ve ya da bekle `ServiceAccountConfig` çekme sunucusundan çekilmesi veya çağırarak daha önce yenilemeye zorlamak için yapılandırma [güncelleştirme-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).

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

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell Desired State Configuration çekme sunucuları](pullServer.md)

[Windows yerel Configuration Manager'ı yapılandırma](metaConfig.md)