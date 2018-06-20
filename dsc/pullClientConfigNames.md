---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: Yapılandırma adlarını kullanarak çekme istemcisi ayarlama
ms.openlocfilehash: d71376d84b9d4b0e74fdccab4b9249b2ca4263cb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188100"
---
# <a name="setting-up-a-pull-client-using-configuration-names"></a><span data-ttu-id="38c75-103">Yapılandırma adlarını kullanarak çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="38c75-103">Setting up a pull client using configuration names</span></span>

> <span data-ttu-id="38c75-104">İçin geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="38c75-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38c75-105">Çekme sunucusuna (Windows özelliği *DSC hizmet*) vardır ancak desteklenen bir bileşen Windows Server'ın yeni özellikleri veya yetenekleri sunmak için herhangi bir plan vardır.</span><span class="sxs-lookup"><span data-stu-id="38c75-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="38c75-106">Geçiş başlamak için önerilen yönetilen istemcilere [Azure Otomasyonu DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda ötesinde özellikler içerir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="38c75-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="38c75-107">Çekme modunu kullanacak şekilde söylediyse ve yapılandırmaları almak için çekme sunucunun nerede ile bağlantı kurabildiğini URL verilen her hedef düğüme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="38c75-107">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span>
<span data-ttu-id="38c75-108">Bunu yapmak için gerekli olan bilgileri yerel Configuration Manager (LCM'yi) yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="38c75-108">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span>
<span data-ttu-id="38c75-109">Özel türde bir yapılandırma ile donatılmış, oluşturduğunuz LCM'yi yapılandırmak için **DSCLocalConfigurationManager** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="38c75-109">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span>
<span data-ttu-id="38c75-110">LCM'yi yapılandırma hakkında daha fazla bilgi için bkz: [yerel Configuration Manager Yapılandırma](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="38c75-110">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="38c75-111">**Not**: Bu konu, PowerShell 5.0 için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="38c75-111">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="38c75-112">PowerShell 4.0 çekme istemcisinde ayarlama hakkında daha fazla bilgi için bkz: [PowerShell 4. 0 ' yapılandırması kimliği kullanan bir çekme istemci ayarlama](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="38c75-112">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="38c75-113">Aşağıdaki komut dosyasını, "CONTOSO-PullSrv" adlı bir sunucudan çekme yapılandırmaları için LCM'yi yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="38c75-113">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv":</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

<span data-ttu-id="38c75-114">Komut dosyasında **ConfigurationRepositoryWeb** blok çekme sunucunun tanımlar.</span><span class="sxs-lookup"><span data-stu-id="38c75-114">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span>
<span data-ttu-id="38c75-115">**ServerURL** özelliği, çekme sunucu için uç noktaya belirtir.</span><span class="sxs-lookup"><span data-stu-id="38c75-115">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

<span data-ttu-id="38c75-116">**RegistrationKey** çekme sunucusuna ilişkin tüm istemci düğümleri ve çekme sunucu arasında paylaşılan bir anahtar bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="38c75-116">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span>
<span data-ttu-id="38c75-117">Aynı değere çekme sunucusunda bir dosyada depolanır.</span><span class="sxs-lookup"><span data-stu-id="38c75-117">The same value is stored in a file on the pull server.</span></span>

<span data-ttu-id="38c75-118">**ConfigurationNames** istemci düğümü için hedeflenen yapılandırmaları adını belirten bir dizi bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="38c75-118">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
<span data-ttu-id="38c75-119">Çekme sunucusunda yapılandırma MOF dosyası bu istemci düğüm adlı için *ConfigurationNames*.mof, burada *ConfigurationNames* değeri ile eşleşen **ConfigurationNames**  özelliği bu meta yapılandırmasını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="38c75-119">On the pull server, the configuration MOF file for this client node must be named *ConfigurationNames*.mof, where *ConfigurationNames* matches the value of the **ConfigurationNames** property you set in this metaconfiguration.</span></span>

><span data-ttu-id="38c75-120">**Not:** birden fazla değer belirtirseniz, **ConfigurationNames**, de belirtmeniz gerekir **PartialConfiguration** yapılandırmanızda engeller.</span><span class="sxs-lookup"><span data-stu-id="38c75-120">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
<span data-ttu-id="38c75-121">Kısmi yapılandırmaları hakkında daha fazla bilgi için bkz: [PowerShell istenen durum yapılandırması kısmi yapılandırmaları](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="38c75-121">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

<span data-ttu-id="38c75-122">Bu betik çalıştıktan sonra adlı yeni bir çıkış klasörü oluşturur **PullClientConfigNames** ve meta yapılandırmasını MOF dosyası var. yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="38c75-122">After this script runs, it creates a new output folder named **PullClientConfigNames** and puts a metaconfiguration MOF file there.</span></span>
<span data-ttu-id="38c75-123">Bu durumda, meta yapılandırmasını MOF dosyası adlandırılacağını `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="38c75-123">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="38c75-124">Yapılandırmayı uygulamak için arama **kümesi DscLocalConfigurationManager** cmdlet'i ile **yolu** meta yapılandırmasını MOF dosyasının konumunu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="38c75-124">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span>

```powershell
Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.
```

> <span data-ttu-id="38c75-125">**Not**: Kayıt anahtarlarını yalnızca web çekme sunucularıyla çalışır.</span><span class="sxs-lookup"><span data-stu-id="38c75-125">**Note**: Registration keys work only with web pull servers.</span></span>
<span data-ttu-id="38c75-126">Hala kullanmalısınız **ConfigurationID** bir SMB çekme sunucusuyla.</span><span class="sxs-lookup"><span data-stu-id="38c75-126">You must still use **ConfigurationID** with an SMB pull server.</span></span>
<span data-ttu-id="38c75-127">Bir çekme sunucusuna kullanarak yapılandırma hakkında bilgi için **ConfigurationID**, bkz: [yapılandırma Kimliğini kullanarak bir çekme istemci ayarı](PullClientConfigNames.md)</span><span class="sxs-lookup"><span data-stu-id="38c75-127">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](PullClientConfigNames.md)</span></span>

## <a name="resource-and-report-servers"></a><span data-ttu-id="38c75-128">Kaynak ve rapor sunucuları</span><span class="sxs-lookup"><span data-stu-id="38c75-128">Resource and report servers</span></span>

<span data-ttu-id="38c75-129">Yalnızca belirtirseniz bir **ConfigurationRepositoryWeb** veya **ConfigurationRepositoryShare** (önceki örnektekiyle) LCM'yi yapılandırmanızda engellemek, çekme istemci kaynaklardan çeker Belirtilen sunucu, ancak raporları için göndermez.</span><span class="sxs-lookup"><span data-stu-id="38c75-129">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span>
<span data-ttu-id="38c75-130">Tek tanıtım sunucu yapılandırmaları, kaynaklar ve raporlama için kullanabilirsiniz, ancak oluşturmak zorunda bir **ReportRepositoryWeb** set up reporting bloğu.</span><span class="sxs-lookup"><span data-stu-id="38c75-130">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>
<span data-ttu-id="38c75-131">Aşağıdaki örnek, bir istemciye çekme yapılandırmaları ve kaynakları ve veri, bir tek çekme sunucusuna raporlama Gönder ayarlar meta yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="38c75-131">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigNames
```

<span data-ttu-id="38c75-132">Kaynaklar ve raporlama için farklı çekme sunucuları da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38c75-132">You can also specify different pull servers for resources and reporting.</span></span>
<span data-ttu-id="38c75-133">Kaynak sunucuyu belirtmek için ya da kullandığınız bir **ResourceRepositoryWeb** (bir web çekme sunucusu için) veya bir **ResourceRepositoryShare** bloğu (SMB çekme sunucusu için).</span><span class="sxs-lookup"><span data-stu-id="38c75-133">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="38c75-134">Bir rapor sunucusu belirtmek için kullandığınız bir **ReportRepositoryWeb** bloğu.</span><span class="sxs-lookup"><span data-stu-id="38c75-134">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span>
<span data-ttu-id="38c75-135">Bir rapor sunucusu bir SMB sunucusu olamaz.</span><span class="sxs-lookup"><span data-stu-id="38c75-135">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="38c75-136">Bir çekme istemci kendi yapılandırmalardan almak için şu meta yapılandırmasını yapılandırır **CONTOSO PullSrv** ve kaynaklarıyla **CONTOSO ResourceSrv**ve durum raporları göndermek için  **CONTOSO ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="38c75-136">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="38c75-137">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="38c75-137">See Also</span></span>

* [<span data-ttu-id="38c75-138">Bir çekme istemci yapılandırması kimliği ile ayarlama</span><span class="sxs-lookup"><span data-stu-id="38c75-138">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="38c75-139">DSC çekme sunucusuna ayarlama</span><span class="sxs-lookup"><span data-stu-id="38c75-139">Setting up a DSC web pull server</span></span>](pullServer.md)