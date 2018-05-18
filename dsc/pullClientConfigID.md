---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: Yapılandırma kimliğini kullanarak çekme istemcisi ayarlama
ms.openlocfilehash: b4a45c4d014b3c4fc0140ad492f81474b260065a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a><span data-ttu-id="740ac-103">Yapılandırma kimliğini kullanarak çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="740ac-103">Setting up a pull client using configuration ID</span></span>

> <span data-ttu-id="740ac-104">İçin geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="740ac-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="740ac-105">Çekme sunucusuna (Windows özelliği *DSC hizmet*) vardır ancak desteklenen bir bileşen Windows Server'ın yeni özellikleri veya yetenekleri sunmak için herhangi bir plan vardır.</span><span class="sxs-lookup"><span data-stu-id="740ac-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="740ac-106">Geçiş başlamak için önerilen yönetilen istemcilere [Azure Otomasyonu DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda ötesinde özellikler içerir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="740ac-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="740ac-107">Çekme modunu kullanacak şekilde söylediyse ve yapılandırmaları almak için çekme sunucunun nerede ile bağlantı kurabildiğini URL verilen her hedef düğüme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="740ac-107">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="740ac-108">Bunu yapmak için gerekli olan bilgileri yerel Configuration Manager (LCM'yi) yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="740ac-108">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="740ac-109">Özel türde bir yapılandırma ile donatılmış, oluşturduğunuz LCM'yi yapılandırmak için **DSCLocalConfigurationManager** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="740ac-109">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="740ac-110">LCM'yi yapılandırma hakkında daha fazla bilgi için bkz: [yerel Configuration Manager Yapılandırma](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="740ac-110">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="740ac-111">**Not**: Bu konu, PowerShell 5.0 için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="740ac-111">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="740ac-112">PowerShell 4.0 çekme istemcisinde ayarlama hakkında daha fazla bilgi için bkz: [PowerShell 4. 0 ' yapılandırması kimliği kullanan bir çekme istemci ayarlama](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="740ac-112">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="740ac-113">Aşağıdaki komut dosyası LCM'yi "CONTOSO-PullSrv" adlı bir sunucudan çekme yapılandırmaları için yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="740ac-113">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

<span data-ttu-id="740ac-114">Komut dosyasında **ConfigurationRepositoryWeb** blok çekme sunucunun tanımlar.</span><span class="sxs-lookup"><span data-stu-id="740ac-114">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="740ac-115">**ServerURL**</span><span class="sxs-lookup"><span data-stu-id="740ac-115">The **ServerURL**</span></span>

<span data-ttu-id="740ac-116">Bu betik çalıştıktan sonra adlı yeni bir çıkış klasörü oluşturur **PullClientConfigID** ve meta yapılandırmasını MOF dosyası var. yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="740ac-116">After this script runs, it creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="740ac-117">Bu durumda, meta yapılandırmasını MOF dosyası adlandırılacağını `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="740ac-117">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="740ac-118">Yapılandırmayı uygulamak için arama **kümesi DscLocalConfigurationManager** cmdlet'i ile **yolu** meta yapılandırmasını MOF dosyasının konumunu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="740ac-118">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="740ac-119">Örneğin: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span><span class="sxs-lookup"><span data-stu-id="740ac-119">For example: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span></span>

## <a name="configuration-id"></a><span data-ttu-id="740ac-120">Yapılandırma Kimliği</span><span class="sxs-lookup"><span data-stu-id="740ac-120">Configuration ID</span></span>

<span data-ttu-id="740ac-121">Komut dosyası kümeleri **ConfigurationID** LCM'yi bu amaç için daha önce oluşturulmuş bir GUID özelliği (kullanarak bir GUID oluşturabilirsiniz **yeni GUID** cmdlet'i).</span><span class="sxs-lookup"><span data-stu-id="740ac-121">The script sets the **ConfigurationID** property of LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="740ac-122">**ConfigurationID** LCM'yi çekme sunucusunda uygun yapılandırma bulmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="740ac-122">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="740ac-123">Çekme sunucusunda yapılandırma MOF dosyası olarak adlandırılmalıdır _ConfigurationID_.mof, burada _ConfigurationID_ değeri **ConfigurationID** hedef özelliği düğümün LCM'yi.</span><span class="sxs-lookup"><span data-stu-id="740ac-123">The configuration MOF file on the pull server must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="smb-pull-server"></a><span data-ttu-id="740ac-124">SMB çekme sunucusuna</span><span class="sxs-lookup"><span data-stu-id="740ac-124">SMB pull server</span></span>

<span data-ttu-id="740ac-125">Bir istemcinin bir SMB sunucusundan çekme yapılandırmaları ayarlamak için kullanın bir **ConfigurationRepositoryShare** bloğu.</span><span class="sxs-lookup"><span data-stu-id="740ac-125">To set up a client to pull configurations from an SMB server, use a **ConfigurationRepositoryShare** block.</span></span> <span data-ttu-id="740ac-126">İçinde bir **ConfigurationRepositoryShare** bloğu ayarlayarak sunucu yolunu belirtin **KaynakYolu** özelliği.</span><span class="sxs-lookup"><span data-stu-id="740ac-126">In a **ConfigurationRepositoryShare** block, you specify the path to the server by setting the **SourcePath** property.</span></span> <span data-ttu-id="740ac-127">Adlı bir SMB çekme sunucusundan çıkarmak için hedef düğümü aşağıdaki meta yapılandırmasını yapılandırır **SMBPullServer**.</span><span class="sxs-lookup"><span data-stu-id="740ac-127">The following metaconfiguration configures the target node to pull from an SMB pull server named **SMBPullServer**.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\PullSource'

        }
    }
}
PullClientConfigID
```

## <a name="resource-and-report-servers"></a><span data-ttu-id="740ac-128">Kaynak ve rapor sunucuları</span><span class="sxs-lookup"><span data-stu-id="740ac-128">Resource and report servers</span></span>

<span data-ttu-id="740ac-129">Yalnızca belirtirseniz bir **ConfigurationRepositoryWeb** veya **ConfigurationRepositoryShare** (önceki örnektekiyle) LCM'yi yapılandırmanızda engellemek, çekme istemci kaynaklardan çeker Belirtilen sunucu, ancak raporları için göndermez.</span><span class="sxs-lookup"><span data-stu-id="740ac-129">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span> <span data-ttu-id="740ac-130">Tek tanıtım sunucu yapılandırmaları, kaynaklar ve raporlama için kullanabilirsiniz, ancak oluşturmak zorunda bir **ReportRepositoryWeb** set up reporting bloğu.</span><span class="sxs-lookup"><span data-stu-id="740ac-130">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

<span data-ttu-id="740ac-131">Aşağıdaki örnek, bir istemciye çekme yapılandırmaları ve kaynakları ve veri, bir tek çekme sunucusuna raporlama Gönder ayarlar meta yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="740ac-131">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }


        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="740ac-132">Kaynaklar ve raporlama için farklı çekme sunucuları da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="740ac-132">You can also specify different pull servers for resources and reporting.</span></span> <span data-ttu-id="740ac-133">Kaynak sunucuyu belirtmek için ya da kullandığınız bir **ResourceRepositoryWeb** (bir web çekme sunucusu için) veya bir **ResourceRepositoryShare** bloğu (SMB çekme sunucusu için).</span><span class="sxs-lookup"><span data-stu-id="740ac-133">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="740ac-134">Bir rapor sunucusu belirtmek için kullandığınız bir **ReportRepositoryWeb** bloğu.</span><span class="sxs-lookup"><span data-stu-id="740ac-134">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="740ac-135">Bir rapor sunucusu bir SMB sunucusu olamaz.</span><span class="sxs-lookup"><span data-stu-id="740ac-135">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="740ac-136">Bir çekme istemci kendi yapılandırmalardan almak için şu meta yapılandırmasını yapılandırır **CONTOSO PullSrv** ve kaynaklarıyla **CONTOSO ResourceSrv**ve durum raporları göndermek için  **CONTOSO ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="740ac-136">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

## <a name="see-also"></a><span data-ttu-id="740ac-137">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="740ac-137">See Also</span></span>

* [<span data-ttu-id="740ac-138">Bir çekme istemci yapılandırma adları ile ayarlama</span><span class="sxs-lookup"><span data-stu-id="740ac-138">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)