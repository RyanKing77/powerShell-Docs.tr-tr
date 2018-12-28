---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: PowerShell Desired State Configuration kısmi yapılandırmalar
ms.openlocfilehash: b2b17e35597707eb97ecdcea9dda4466deeab0cb
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405813"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="32a96-103">PowerShell Desired State Configuration kısmi yapılandırmalar</span><span class="sxs-lookup"><span data-stu-id="32a96-103">PowerShell Desired State Configuration partial configurations</span></span>

<span data-ttu-id="32a96-104">_Uygulama hedefi: Windows PowerShell 5.0 ve üzeri._</span><span class="sxs-lookup"><span data-stu-id="32a96-104">_Applies To: Windows PowerShell 5.0 and later._</span></span>

<span data-ttu-id="32a96-105">PowerShell 5. 0'da, parçaları ve birden çok kaynaktan teslim edilecek yapılandırmaları Desired State Configuration ' nı (DSC) sağlar.</span><span class="sxs-lookup"><span data-stu-id="32a96-105">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="32a96-106">Hedef düğümde yerel Configuration Manager (LCM) tek bir yapılandırma uygulamadan önce parçaların birlikte koyar.</span><span class="sxs-lookup"><span data-stu-id="32a96-106">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="32a96-107">Bu özellik, paylaşım takımlar veya kişiler arasındaki yapılandırmasının denetimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="32a96-107">This capability allows sharing control of configuration between teams or individuals.</span></span> <span data-ttu-id="32a96-108">Bir hizmette Geliştirici ekipleri iki veya daha fazla işbirliği yapıyorsanız Örneğin, bunlar her hizmetin kendi parçası yönetmek için yapılandırmaları oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32a96-108">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="32a96-109">Bu yapılandırmalardan birini her farklı çekme sunuculardan çekilmesi ve farklı yaşlardaki eklenemedi.</span><span class="sxs-lookup"><span data-stu-id="32a96-109">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="32a96-110">Kısmi yapılandırmalar da farklı kişilere veya ekiplere düğümleri bir tek yapılandırma belgesini düzenleme koordine etmek zorunda kalmadan yapılandırma farklı yönlerini kontrol sağlar.</span><span class="sxs-lookup"><span data-stu-id="32a96-110">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="32a96-111">Örneğin, bir takım başka bir takım, diğer uygulama ve hizmetlerin söz konusu VM'deki dağıtabilirsiniz ancak VM ve işletim sistemi dağıtmaktan sorumlu olabilir.</span><span class="sxs-lookup"><span data-stu-id="32a96-111">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="32a96-112">Kısmi yapılandırmalar ile her ikisini gereksiz derecede karmaşık olmadan kendi yapılandırması her takım oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32a96-112">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="32a96-113">Kısmi yapılandırmalar gönderme modunda, çekme modu veya ikisinin bir birleşimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32a96-113">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="32a96-114">Gönderme modunda kısmi yapılandırmalar</span><span class="sxs-lookup"><span data-stu-id="32a96-114">Partial configurations in push mode</span></span>

<span data-ttu-id="32a96-115">Kısmi yapılandırmalar gönderim modunda kullanmak için kısmi yapılandırmalar almak üzere hedef düğümde LCM yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="32a96-115">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="32a96-116">Her kısmi yapılandırması hedef kullanılarak gönderilen gerekir `Publish-DSCConfiguration` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="32a96-116">Each partial configuration must be pushed to the target by using the `Publish-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="32a96-117">Hedef düğüm ardından tek bir yapılandırma kısmi yapılandırmaya birleştirir ve çağırarak yapılandırmayı uygulayabilir [Başlat-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="32a96-117">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="32a96-118">Anında iletme modu kısmi yapılandırmalar için LCM yapılandırma</span><span class="sxs-lookup"><span data-stu-id="32a96-118">Configuring the LCM for push-mode partial configurations</span></span>

<span data-ttu-id="32a96-119">Kısmi yapılandırmalar için LCM gönderim modunda yapılandırmak için oluşturduğunuz bir **DSCLocalConfigurationManager** bir yapılandırmayla **PartialConfiguration** kısmi her yapılandırma için blok.</span><span class="sxs-lookup"><span data-stu-id="32a96-119">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="32a96-120">LCM yapılandırma hakkında daha fazla bilgi için bkz. [yerel Configuration Manager Yapılandırma Windows](/powershell/dsc/metaConfig).</span><span class="sxs-lookup"><span data-stu-id="32a96-120">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](/powershell/dsc/metaConfig).</span></span> <span data-ttu-id="32a96-121">Aşağıdaki örnek, iki kısmi yapılandırmalar bekliyor bir LCM yapılandırma gösterir; işletim sistemini dağıtan ve diğeri dağıtan ve SharePoint yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="32a96-121">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

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

<span data-ttu-id="32a96-122">**RefreshMode** kısmi her yapılandırma "gönderme"temelli ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="32a96-122">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="32a96-123">Adlarını **PartialConfiguration** blokları (Bu durumda, "ServiceAccountConfig" ve "SharePointConfig"), tam olarak hedef düğüme itilir yapılandırmaların adlarının eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="32a96-123">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

> [!Note]
> <span data-ttu-id="32a96-124">Adlandırılmış her **PartialConfiguration** yapılandırma betiği, hedef düğüm adı ya da olmalıdırMOFdosyasıadıbelirtildiğişekilde,blokyapılandırmasınıngerçekadıeşleşmelidir`localhost`.</span><span class="sxs-lookup"><span data-stu-id="32a96-124">The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="32a96-125">Yayımlama ve anında iletme modu kısmi yapılandırmalar başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="32a96-125">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="32a96-126">Ardından çağırın [Yayımla-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) her yapılandırma için olarak yapılandırma belgelerini içeren klasörleri aktarılmasından **yolu** parametreleri.</span><span class="sxs-lookup"><span data-stu-id="32a96-126">You then call [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="32a96-127">`Publish-DSCConfiguration`Yapılandırma MOF dosyaları hedef düğümleri yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="32a96-127">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="32a96-128">Her iki yapılandırma yayımladıktan sonra çağırabilirsiniz `Start-DSCConfiguration –UseExisting` hedef düğümde bulunan.</span><span class="sxs-lookup"><span data-stu-id="32a96-128">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="32a96-129">Örneğin, aşağıdaki yapılandırma MOF belgeleri yazma düğümde derlenmişse:</span><span class="sxs-lookup"><span data-stu-id="32a96-129">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

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

<span data-ttu-id="32a96-130">Yayımlama ve yapılandırmaları aşağıdaki şekilde çalıştırmanız:</span><span class="sxs-lookup"><span data-stu-id="32a96-130">You would publish and run the configurations as follows:</span></span>

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
> <span data-ttu-id="32a96-131">Çalıştıran kullanıcının [Yayımla-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet'i hedef düğümde yönetici ayrıcalıkları olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="32a96-131">The user running the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="32a96-132">Kısmi yapılandırmalar çekme modunda</span><span class="sxs-lookup"><span data-stu-id="32a96-132">Partial configurations in pull mode</span></span>

<span data-ttu-id="32a96-133">Kısmi yapılandırmalar bir veya daha fazla çekme sunucusundan istenebilecek (çekme sunucuları hakkında daha fazla bilgi için bkz. [Windows PowerShell Desired State Configuration çekme sunucuları](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="32a96-133">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="32a96-134">Bunu yapmak için kısmi yapılandırmalar çekme adlandırın ve yapılandırma belgelerini çekme sunucularda düzgün bir şekilde bulun. hedef düğümde LCM yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="32a96-134">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="32a96-135">Çekme düğüm yapılandırmaları için LCM yapılandırma</span><span class="sxs-lookup"><span data-stu-id="32a96-135">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="32a96-136">Kısmi yapılandırmalar çekme sunucusundan çekmek için LCM yapılandırmak için çekme sunucusu ya da tanımladığınız bir **ConfigurationRepositoryWeb** (için HTTP çekme sunucusu) veya **ConfigurationRepositoryShare** () SMB çekme sunucusu için) blok.</span><span class="sxs-lookup"><span data-stu-id="32a96-136">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="32a96-137">Ardından oluşturduğunuz **PartialConfiguration** kullanarak çekme sunucusuna başvuran blokları **ConfigurationSource** özelliği.</span><span class="sxs-lookup"><span data-stu-id="32a96-137">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="32a96-138">Ayrıca oluşturmanıza gerek bir **ayarları** blok LCM çekme modu kullandığını belirtmek ve belirtmek için **ConfigurationNames** veya **ConfigurationID** , çekme sunucusu ve Hedef düğüm yapılandırmaları tanımlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="32a96-138">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="32a96-139">Şu meta-yapılandırmayı PullSrv CONTOSO adlı bir HTTP çekme sunucusu tanımlar ve çekme sunucusuna kullanan iki kısmi yapılandırmalar.</span><span class="sxs-lookup"><span data-stu-id="32a96-139">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="32a96-140">LCM kullanarak yapılandırma hakkında daha fazla bilgi için **ConfigurationNames**, bkz: [yapılandırma adlarını kullanarak çekme istemcisi ayarlama](pullClientConfigNames.md).</span><span class="sxs-lookup"><span data-stu-id="32a96-140">For more information about configuring the LCM using **ConfigurationNames**, see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span> <span data-ttu-id="32a96-141">LCM kullanarak yapılandırma hakkında bilgi **ConfigurationID**, bkz: [yapılandırma Kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="32a96-141">For information about configuring the LCM using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="32a96-142">Yapılandırma adlarını kullanarak çekme modu yapılandırmaları için LCM yapılandırma</span><span class="sxs-lookup"><span data-stu-id="32a96-142">Configuring the LCM for pull mode configurations using configuration names</span></span>

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

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="32a96-143">Çekme modu yapılandırmaları ConfigurationID kullanarak LCM yapılandırma</span><span class="sxs-lookup"><span data-stu-id="32a96-143">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

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

<span data-ttu-id="32a96-144">Kısmi yapılandırmalar birden fazla çekme sunucusundan çeker — her çekme sunucusu tanımlayın ve ardından her uygun çekme sunucusuna başvurmak yalnızca gerekir **PartialConfiguration** blok.</span><span class="sxs-lookup"><span data-stu-id="32a96-144">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="32a96-145">Meta-yapılandırma oluşturduktan sonra bunu bir yapılandırma belge (bir MOF dosyası) oluşturun ve ardından çağırmak için çalıştırmanız gerekir [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) LCM yapılandırmak için.</span><span class="sxs-lookup"><span data-stu-id="32a96-145">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="32a96-146">Adlandırma ve yapılandırma belgelerini (ConfigurationNames) çekme sunucusunda yerleştirme</span><span class="sxs-lookup"><span data-stu-id="32a96-146">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="32a96-147">Kısmi yapılandırma belgelerini olarak belirtilen klasöre yerleştirilmelidir **Yapılandırmayolu** içinde `web.config` çekme sunucusu için dosya (genellikle `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="32a96-147">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="32a96-148">Yapılandırma belgelerini PowerShell 5.1 çekme sunucusunda adlandırma</span><span class="sxs-lookup"><span data-stu-id="32a96-148">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="32a96-149">Bir çekme sunucusu yalnızca bir kısmi yapılandırmasından çeken, yapılandırma belgesi herhangi bir ad olabilir.</span><span class="sxs-lookup"><span data-stu-id="32a96-149">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span> <span data-ttu-id="32a96-150">Bir çekme sunucusu birden fazla kısmi yapılandırmasından çeken, yapılandırma belgesi ya da adlandırılabilir `<ConfigurationName>.mof`burada *ConfigurationName* kısmi yapılandırmanın adını veya `<ConfigurationName>.<NodeName>.mof`burada *ConfigurationName* kısmi yapılandırma adıdır ve *NodeName* hedef düğüm adıdır.</span><span class="sxs-lookup"><span data-stu-id="32a96-150">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where *ConfigurationName* is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where *ConfigurationName* is the name of the partial configuration, and *NodeName* is the name of the target node.</span></span> <span data-ttu-id="32a96-151">Bu, çekme yapılandırmaları Azure Automation DSC çekme sunucusundan sağlar.</span><span class="sxs-lookup"><span data-stu-id="32a96-151">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="32a96-152">PowerShell 5.0 çekme sunucusunda yapılandırma belgelerini adlandırma</span><span class="sxs-lookup"><span data-stu-id="32a96-152">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="32a96-153">Yapılandırma belgelerini gibi adlandırılmalıdır: `ConfigurationName.mof`burada *ConfigurationName* kısmi yapılandırma adıdır.</span><span class="sxs-lookup"><span data-stu-id="32a96-153">The configuration documents must be named as follows: `ConfigurationName.mof`, where *ConfigurationName* is the name of the partial configuration.</span></span> <span data-ttu-id="32a96-154">Bizim örneğimizde, yapılandırma belgelerini şu şekilde adlandırılması:</span><span class="sxs-lookup"><span data-stu-id="32a96-154">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="32a96-155">Adlandırma ve yapılandırma belgelerini (ConfigurationID) çekme sunucusunda yerleştirme</span><span class="sxs-lookup"><span data-stu-id="32a96-155">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="32a96-156">Kısmi yapılandırma belgelerini olarak belirtilen klasöre yerleştirilmelidir **Yapılandırmayolu** içinde `web.config` çekme sunucusu için dosya (genellikle `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="32a96-156">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="32a96-157">Yapılandırma belgelerini gibi adlandırılmalıdır: `<ConfigurationName>.<ConfigurationID>.mof`burada _ConfigurationName_ kısmi yapılandırma adıdır ve _ConfigurationID_ kimliği tanımlanan yapılandırma Hedef düğümde bulunan LCM.</span><span class="sxs-lookup"><span data-stu-id="32a96-157">The configuration documents must be named as follows: `<ConfigurationName>.<ConfigurationID>.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="32a96-158">Bizim örneğimizde, yapılandırma belgelerini şu şekilde adlandırılması:</span><span class="sxs-lookup"><span data-stu-id="32a96-158">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="32a96-159">Kısmi yapılandırmalar çekme sunucusundan çalıştırma</span><span class="sxs-lookup"><span data-stu-id="32a96-159">Running partial configurations from a pull server</span></span>

<span data-ttu-id="32a96-160">Hedef düğümde bulunan LCM yapılandırıldı ve belgeleri oluşturulduğundan ve doğru çekme sunucusunda adlı yapılandırma, hedef düğüm kısmi yapılandırmalar çeker sonra birleştirip ve normal sonuç yapılandırmasını Uygula tarafından belirtilen aralıklarla **RefreshFrequencyMins** LCM özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="32a96-160">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="32a96-161">Daha önce yenilemeye zorlamak istiyorsanız, çağırabilirsiniz [güncelleştirme-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) yapılandırmalar çekme cmdlet'ini ve ardından `Start-DSCConfiguration –UseExisting` uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="32a96-161">If you want to force a refresh, you can call the [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="32a96-162">Karma gönderme ve çekme modlarında kısmi yapılandırmalar</span><span class="sxs-lookup"><span data-stu-id="32a96-162">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="32a96-163">Ayrıca, anında iletme karıştırın ve modları için kısmi yapılandırmalar çekme.</span><span class="sxs-lookup"><span data-stu-id="32a96-163">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="32a96-164">Diğer bir deyişle, başka bir kısmi yapılandırma gönderilir, bir çekme sunucusundan çekilen bir kısmi yapılandırmasına sahip.</span><span class="sxs-lookup"><span data-stu-id="32a96-164">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="32a96-165">Önceki bölümlerde açıklandığı gibi her kısmi yapılandırması için yenileme modunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="32a96-165">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span> <span data-ttu-id="32a96-166">Örneğin, aşağıdaki meta-yapılandırması ile aynı örneği açıklar `ServiceAccountConfig` çekme modu kısmi yapılandırmasında ve `SharePointConfig` gönderme modunda kısmi yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="32a96-166">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="32a96-167">ConfigurationNames kullanarak karma gönderme ve çekme modu</span><span class="sxs-lookup"><span data-stu-id="32a96-167">Mixed push and pull modes using ConfigurationNames</span></span>

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

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="32a96-168">ConfigurationID kullanarak karma gönderme ve çekme modu</span><span class="sxs-lookup"><span data-stu-id="32a96-168">Mixed push and pull modes using ConfigurationID</span></span>

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

<span data-ttu-id="32a96-169">Unutmayın **RefreshMode** blok içinde belirtilen "Pull" olan ancak **RefreshMode** için `SharePointConfig` kısmi yapılandırmadır "Gönderme".</span><span class="sxs-lookup"><span data-stu-id="32a96-169">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="32a96-170">Ad ve bunların ilgili yenileme modları için yukarıda açıklandığı gibi yapılandırma MOF dosyaları bulun.</span><span class="sxs-lookup"><span data-stu-id="32a96-170">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span>
<span data-ttu-id="32a96-171">Çağrı `Publish-DSCConfiguration` yayımlamak için `SharePointConfig` kısmi yapılandırma ve ya da bekle `ServiceAccountConfig` çekme sunucusundan çekilmesi veya çağırarak daha önce yenilemeye zorlamak için yapılandırma [güncelleştirme-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span><span class="sxs-lookup"><span data-stu-id="32a96-171">Call `Publish-DSCConfiguration` to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="32a96-172">Örnek ServiceAccountConfig kısmi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="32a96-172">Example ServiceAccountConfig Partial Configuration</span></span>

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

## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="32a96-173">Örnek SharePointConfig kısmi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="32a96-173">Example SharePointConfig Partial Configuration</span></span>

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

## <a name="see-also"></a><span data-ttu-id="32a96-174">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="32a96-174">See Also</span></span>

[<span data-ttu-id="32a96-175">Windows PowerShell Desired State Configuration çekme sunucuları</span><span class="sxs-lookup"><span data-stu-id="32a96-175">Windows PowerShell Desired State Configuration Pull Servers</span></span>](pullServer.md)

[<span data-ttu-id="32a96-176">Windows yerel Configuration Manager'ı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="32a96-176">Windows Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)