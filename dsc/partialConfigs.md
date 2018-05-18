---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: PowerShell istenen durum yapılandırması kısmi yapılandırmaları
ms.openlocfilehash: e6d80b065ad9e68517d2952b7643e4c611d82a0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="c9516-103">PowerShell istenen durum yapılandırması kısmi yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="c9516-103">PowerShell Desired State Configuration partial configurations</span></span>

><span data-ttu-id="c9516-104">İçin geçerlidir: Windows PowerShell 5.0 ve sonraki sürümleri.</span><span class="sxs-lookup"><span data-stu-id="c9516-104">Applies To: Windows PowerShell 5.0 and later.</span></span>

<span data-ttu-id="c9516-105">PowerShell 5. 0'da, istenen durum Yapılandırması'nı (DSC) parçada ve birden fazla kaynaktan teslim edilecek yapılandırmaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9516-105">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="c9516-106">Hedef düğümde bulunan yerel Configuration Manager (LCM'yi) tek bir yapılandırma olarak uygulamadan önce parçaları birlikte koyar.</span><span class="sxs-lookup"><span data-stu-id="c9516-106">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="c9516-107">Paylaşım denetimi ekip veya kişiler arasındaki yapılandırmasının bu yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9516-107">This capability allows sharing control of configuration between teams or individuals.</span></span>
<span data-ttu-id="c9516-108">İki veya daha fazla takıma geliştiricilerin bir hizmette işbirliği, örneğin, bunlar her hizmetin kendi parçası yönetmek için yapılandırmaları oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9516-108">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="c9516-109">Bu yapılandırmalar her farklı çekme sunucularından çekilen ve geliştirme farklı aşamalarında eklenemedi.</span><span class="sxs-lookup"><span data-stu-id="c9516-109">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="c9516-110">Kısmi yapılandırmaları de farklı kişilere veya ekiplere düğümleri bir tek yapılandırma belgesini düzenleme koordine etmek zorunda kalmadan yapılandırma farklı yönlerini kontrol olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9516-110">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="c9516-111">Örneğin, bir takım başka bir takım diğer uygulama ve hizmetlerin bu VM'de dağıtılabileceği sırada VM ve işletim sistemi dağıtmak için sorumlu olabilir.</span><span class="sxs-lookup"><span data-stu-id="c9516-111">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="c9516-112">Kısmi yapılandırmaları ile her takım her ikisini gereksiz yere karmaşık olmadan kendi yapılandırması oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9516-112">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="c9516-113">Kısmi yapılandırmalarını itme modu, çekme modu veya ikisinin birleşimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9516-113">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="c9516-114">Zorlama modunda kısmi yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="c9516-114">Partial configurations in push mode</span></span>
<span data-ttu-id="c9516-115">Kısmi yapılandırmaları zorlama modunda kullanmak için LCM'yi kısmi yapılandırmalarını almak için hedef düğümde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="c9516-115">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="c9516-116">Her bir kısmi yapılandırmasının hedef Yayımla DSCConfiguration cmdlet'ini kullanarak gönderilir gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9516-116">Each partial configuration must be pushed to the target by using the Publish-DSCConfiguration cmdlet.</span></span> <span data-ttu-id="c9516-117">Hedef düğüm ardından tek bir yapılandırması kısmi yapılandırmaya birleştirir ve çağırarak yapılandırma uygulayabilirsiniz [başlangıç DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="c9516-117">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="c9516-118">Anında iletme modu kısmi yapılandırmaları için LCM'yi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c9516-118">Configuring the LCM for push-mode partial configurations</span></span>
<span data-ttu-id="c9516-119">Kısmi yapılandırmaları için LCM'yi zorlama modunda yapılandırmak için oluşturduğunuz bir **DSCLocalConfigurationManager** bir yapılandırmayla **PartialConfiguration** kısmi her yapılandırma için bloğu.</span><span class="sxs-lookup"><span data-stu-id="c9516-119">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="c9516-120">LCM'yi yapılandırma hakkında daha fazla bilgi için bkz: [yerel Configuration Manager Yapılandırma Windows](https://technet.microsoft.com/library/mt421188.aspx).</span><span class="sxs-lookup"><span data-stu-id="c9516-120">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](https://technet.microsoft.com/library/mt421188.aspx).</span></span>
<span data-ttu-id="c9516-121">Aşağıdaki örnek, iki kısmi yapılandırmaları bekliyor LCM'yi yapılandırma gösterir — işletim sistemi dağıtan, diğeri dağıtır ve SharePoint yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c9516-121">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

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

<span data-ttu-id="c9516-122">**RefreshMode** her kısmi yapılandırma "gönderme"temelli ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c9516-122">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="c9516-123">Adları **PartialConfiguration** blokları (Bu durumda, "ServiceAccountConfig" ve "SharePointConfig"), hedef düğüme gönderilen yapılandırmaları adlarını tam olarak eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="c9516-123">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

><span data-ttu-id="c9516-124">**Not:** adlandırılmış her **PartialConfiguration** yapılandırma betiği, MOF dosyası adını değil belirtildiği gibi blok yapılandırmasının gerçek adını eşleşmesi gerekir ya da adı olan Hedef düğüm veya `localhost`.</span><span class="sxs-lookup"><span data-stu-id="c9516-124">**Note:** The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="c9516-125">Yayımlama ve başlangıç itme modu kısmi yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="c9516-125">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="c9516-126">Ardından çağıran [Yayımla DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) her yapılandırma için yapılandırma belgeleri olarak içeren klasörleri geçirme **yolu** parametreleri.</span><span class="sxs-lookup"><span data-stu-id="c9516-126">You then call [Publish-DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="c9516-127">`Publish-DSCConfiguration`Hedef düğümleri yapılandırma MOF dosyasına yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="c9516-127">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="c9516-128">Her iki yapılandırma yayımladıktan sonra çağırabilirsiniz `Start-DSCConfiguration –UseExisting` hedef düğümde bulunan.</span><span class="sxs-lookup"><span data-stu-id="c9516-128">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="c9516-129">Örneğin, aşağıdaki yapılandırma MOF belgeleri yazma düğümde derlenmiş ise:</span><span class="sxs-lookup"><span data-stu-id="c9516-129">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

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

<span data-ttu-id="c9516-130">Yayımlama ve yapılandırmaları aşağıdaki şekilde çalıştırmanız:</span><span class="sxs-lookup"><span data-stu-id="c9516-130">You would publish and run the configurations as follows:</span></span>

```powershell
PS C:\PartialConfigTest> Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Start-DscConfiguration -UseExisting -ComputerName 'TestVM'

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

><span data-ttu-id="c9516-131">**Not:** çalıştıran kullanıcının [Yayımla DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) cmdlet'i hedef düğümde yönetici ayrıcalıkları olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9516-131">**Note:** The user running the [Publish-DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="c9516-132">Çekme modunda kısmi yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="c9516-132">Partial configurations in pull mode</span></span>

<span data-ttu-id="c9516-133">Kısmi yapılandırmaları bir veya daha fazla çekme sunucularından çekilen (çekme sunucuları hakkında daha fazla bilgi için bkz: [Windows PowerShell istenen durum yapılandırma çekme sunucularına](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="c9516-133">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="c9516-134">Bunu yapmak için kısmi yapılandırmaları çekme ve ad ve yapılandırma belgelerini çekme sunucularda düzgün bir şekilde bulmak için hedef düğümde bulunan LCM'yi yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9516-134">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="c9516-135">Çekme düğüm yapılandırmaları için LCM'yi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c9516-135">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="c9516-136">Bir çekme sunucudan kısmi yapılandırmaları çıkarmak için LCM'yi yapılandırmak için çekme sunucu ya da tanımladığınız bir **ConfigurationRepositoryWeb** (için bir HTTP istek sunucusu) veya **ConfigurationRepositoryShare** () SMB çekme server için) blok.</span><span class="sxs-lookup"><span data-stu-id="c9516-136">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="c9516-137">Ardından oluşturduğunuz **PartialConfiguration** kullanarak çekme sunucusuna başvuran blokları **ConfigurationSource** özelliği.</span><span class="sxs-lookup"><span data-stu-id="c9516-137">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="c9516-138">Oluşturmak için gereken bir **ayarları** blok LCM'yi çekme modunu kullandığını belirtmek ve belirtmek için **ConfigurationNames** veya **ConfigurationID** , çekme sunucunun ve Hedef düğüm yapılandırmaları tanımlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="c9516-138">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="c9516-139">Kullanan iki kısmi yapılandırmaları çekme sunucusuna ve CONTOSO PullSrv adlı bir HTTP çekme sunucusunda aşağıdaki meta yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9516-139">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="c9516-140">LCM'yi kullanarak yapılandırma hakkında daha fazla bilgi için **ConfigurationNames**, bkz: [yapılandırma adları kullanarak bir çekme istemcisi kurarken](pullClientConfigNames.md).</span><span class="sxs-lookup"><span data-stu-id="c9516-140">For more information about configuring the LCM using **ConfigurationNames**, see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span>
<span data-ttu-id="c9516-141">LCM'yi kullanarak yapılandırma hakkında bilgi için **ConfigurationID**, bkz: [yapılandırma Kimliğini kullanarak bir çekme istemcisi kurarken](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="c9516-141">For information about configuring the LCM using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="c9516-142">Yapılandırma adları kullanarak çekme modu yapılandırmaları için LCM'yi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c9516-142">Configuring the LCM for pull mode configurations using configuration names</span></span>

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

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="c9516-143">LCM'yi ConfigurationID kullanarak çekme modu yapılandırmaları için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c9516-143">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

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

<span data-ttu-id="c9516-144">Birden çok çekme sunucusundan kısmi yapılandırmaları çekebilir — her çekme sunucusuna tanımlamak ve ardından her uygun çekme sunucusuna başvurmak yalnızca gerekir **PartialConfiguration** bloğu.</span><span class="sxs-lookup"><span data-stu-id="c9516-144">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="c9516-145">Meta yapılandırma oluşturduktan sonra yapılandırma belge (bir MOF dosyası) oluşturun ve ardından çağıran çalıştırmalısınız [kümesi DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) LCM'yi yapılandırmak için.</span><span class="sxs-lookup"><span data-stu-id="c9516-145">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="c9516-146">Adlandırma ve çekme sunucusunda (ConfigurationNames) yapılandırma belgelerini yerleştirme</span><span class="sxs-lookup"><span data-stu-id="c9516-146">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="c9516-147">Kısmi yapılandırma belgeleri olarak belirtilen klasöre yerleştirilmelidir **ConfigurationPath** içinde `web.config` çekme sunucusuna ilişkin dosyasını (genellikle `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="c9516-147">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="c9516-148">PowerShell 5.1 çekme sunucusunda yapılandırma Belgeleri adlandırma</span><span class="sxs-lookup"><span data-stu-id="c9516-148">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="c9516-149">Bir tek tek çekme sunucusuna yalnızca bir kısmi yapılandırmasından çekme, yapılandırma belgesini herhangi bir ad olabilir.</span><span class="sxs-lookup"><span data-stu-id="c9516-149">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span>
<span data-ttu-id="c9516-150">Birden fazla kısmi yapılandırmasını çekme sunucusundan çekme, yapılandırma belge ya da adlandırılabilir `<ConfigurationName>.mof`, burada _ConfigurationName_ kısmi yapılandırma adı veya `<ConfigurationName>.<NodeName>.mof`, burada  _ConfigurationName_ kısmi yapılandırma adıdır ve _NodeName_ hedef düğüm adıdır.</span><span class="sxs-lookup"><span data-stu-id="c9516-150">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where _ConfigurationName_ is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where  _ConfigurationName_ is the name of the partial configuration, and _NodeName_ is the name of the target node.</span></span>
<span data-ttu-id="c9516-151">Bu, çekme yapılandırmaları için Azure Otomasyonu DSC istek sunucusundan sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9516-151">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>


#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="c9516-152">PowerShell 5.0 çekme sunucusunda yapılandırma Belgeleri adlandırma</span><span class="sxs-lookup"><span data-stu-id="c9516-152">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="c9516-153">Aşağıdaki gibi yapılandırma belgelerini adlı: `ConfigurationName.mof`, burada _ConfigurationName_ kısmi yapılandırma adıdır.</span><span class="sxs-lookup"><span data-stu-id="c9516-153">The configuration documents must be named as follows: `ConfigurationName.mof`, where _ConfigurationName_ is the name of the partial configuration.</span></span> <span data-ttu-id="c9516-154">Bizim örneğimizde, aşağıdaki gibi yapılandırma belgelerini adlı:</span><span class="sxs-lookup"><span data-stu-id="c9516-154">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="c9516-155">Adlandırma ve çekme sunucusunda (ConfigurationID) yapılandırma belgelerini yerleştirme</span><span class="sxs-lookup"><span data-stu-id="c9516-155">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="c9516-156">Kısmi yapılandırma belgeleri olarak belirtilen klasöre yerleştirilmelidir **ConfigurationPath** içinde `web.config` çekme sunucusuna ilişkin dosyasını (genellikle `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="c9516-156">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="c9516-157">Aşağıdaki gibi yapılandırma belgelerini adlı: _ConfigurationName_.</span><span class="sxs-lookup"><span data-stu-id="c9516-157">The configuration documents must be named as follows: _ConfigurationName_.</span></span> <span data-ttu-id="c9516-158">_ConfigurationID_`.mof`, burada _ConfigurationName_ kısmi yapılandırma adıdır ve _ConfigurationID_ yapılandırması kimliği hedefte LCM'yi tanımlanır düğüm.</span><span class="sxs-lookup"><span data-stu-id="c9516-158">_ConfigurationID_`.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="c9516-159">Bizim örneğimizde, aşağıdaki gibi yapılandırma belgelerini adlı:</span><span class="sxs-lookup"><span data-stu-id="c9516-159">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```


### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="c9516-160">Bir çekme sunucusundan kısmi yapılandırmaları çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c9516-160">Running partial configurations from a pull server</span></span>

<span data-ttu-id="c9516-161">Hedef düğümde bulunan LCM'yi yapılandırılmış ve belgeleri oluşturulduğundan ve düzgün şekilde çekme sunucusunda adlı yapılandırma, hedef düğüm kısmi yapılandırmaları çeker sonra bunları birleştirmek ve normal sonuç yapılandırmasını Uygula tarafından belirlenen aralıklarla **RefreshFrequencyMins** LCM'yi özelliği.</span><span class="sxs-lookup"><span data-stu-id="c9516-161">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="c9516-162">Yenilemeye zorlamak istiyorsanız, çağırabilirsiniz [güncelleştirme DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx) yapılandırmaları çekme cmdlet'ini ve ardından `Start-DSCConfiguration –UseExisting` bunları uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="c9516-162">If you want to force a refresh, you can call the [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>


## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="c9516-163">Karma İtme hem de çekme modlarında kısmi yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="c9516-163">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="c9516-164">Ayrıca, anında iletme karıştırmak ve modları kısmi yapılandırmaları için çekme.</span><span class="sxs-lookup"><span data-stu-id="c9516-164">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="c9516-165">Diğer bir deyişle, başka bir kısmi yapılandırma gönderilen karşın, bir istek sunucusundan çekilen bir kısmi yapılandırmasına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="c9516-165">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="c9516-166">Kısmi her yapılandırma için yenileme modu önceki bölümlerde açıklandığı gibi belirtin.</span><span class="sxs-lookup"><span data-stu-id="c9516-166">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span>
<span data-ttu-id="c9516-167">Örneğin, aşağıdaki meta yapılandırması ile aynı örnek açıklar `ServiceAccountConfig` çekme modunda kısmi yapılandırma ve `SharePointConfig` zorlama modunda kısmi yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="c9516-167">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="c9516-168">ConfigurationNames kullanarak karma anında iletme ve çekme modları</span><span class="sxs-lookup"><span data-stu-id="c9516-168">Mixed push and pull modes using ConfigurationNames</span></span>

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

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="c9516-169">ConfigurationID kullanarak karma anında iletme ve çekme modları</span><span class="sxs-lookup"><span data-stu-id="c9516-169">Mixed push and pull modes using ConfigurationID</span></span>

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

<span data-ttu-id="c9516-170">Unutmayın **RefreshMode** ayarları bloğunda belirtilen "Çekme" olan ancak **RefreshMode** için `SharePointConfig` kısmi yapılandırmadır "Gönderme".</span><span class="sxs-lookup"><span data-stu-id="c9516-170">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="c9516-171">Ad ve bunların ilgili yenileme modları için yukarıda açıklandığı gibi yapılandırma MOF dosyaları bulun.</span><span class="sxs-lookup"><span data-stu-id="c9516-171">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span> <span data-ttu-id="c9516-172">Çağrı **Yayımla DSCConfiguration** yayımlamak için `SharePointConfig` kısmi yapılandırması ve ya da bekle `ServiceAccountConfig` istek sunucusundan çekebilir veya çağırarak yenilemeye zorlamak için yapılandırma [ Güncelleştirme DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).</span><span class="sxs-lookup"><span data-stu-id="c9516-172">Call **Publish-DSCConfiguration** to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="c9516-173">Örnek ServiceAccountConfig kısmi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c9516-173">Example ServiceAccountConfig Partial Configuration</span></span>

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
## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="c9516-174">Örnek SharePointConfig kısmi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c9516-174">Example SharePointConfig Partial Configuration</span></span>
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
##<a name="see-also"></a><span data-ttu-id="c9516-175">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="c9516-175">See Also</span></span>

<span data-ttu-id="c9516-176">**Kavramları**
[Windows PowerShell istenen durum yapılandırması çekme sunucuları](pullServer.md)</span><span class="sxs-lookup"><span data-stu-id="c9516-176">**Concepts**
[Windows PowerShell Desired State Configuration Pull Servers](pullServer.md)</span></span>

[<span data-ttu-id="c9516-177">Windows yerel Configuration Manager'ı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c9516-177">Windows Configuring the Local Configuration Manager</span></span>](https://technet.microsoft.com/library/mt421188.aspx)