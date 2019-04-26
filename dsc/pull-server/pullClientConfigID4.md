---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: Yapılandırma kimliklerinin PowerShell 4. 0'kullanarak bir çekme istemcisi ayarlama
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079481"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a><span data-ttu-id="6f8e2-103">Yapılandırma kimliklerinin PowerShell 4. 0'kullanarak bir çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="6f8e2-103">Set up a Pull Client using Configuration IDs in PowerShell 4.0</span></span>

><span data-ttu-id="6f8e2-104">Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6f8e2-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6f8e2-105">Çekme sunucusu (Windows özelliği *DSC hizmet*) ancak desteklenen bir bileşen Windows Server'ın yeni özellikler veya yetenekler sunmak için herhangi bir plan vardır.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="6f8e2-106">Geçişi başlıyor önerilir yönetilen istemcilere [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda dışında özellikler dahildir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="6f8e2-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="6f8e2-107">Çekme istemcisi ayarlama ayarlamadan önce bir çekme sunucusu ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="6f8e2-108">Bu sırada gerekli olmasa da gidermeye yardımcı olur ve kayıt başarılı olmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="6f8e2-109">Bir çekme sunucusu kurmak için aşağıdaki kılavuzları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6f8e2-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="6f8e2-110">Bir DSC SMB çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="6f8e2-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="6f8e2-111">Bir DSC HTTP çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="6f8e2-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="6f8e2-112">Her hedef düğüm yapılandırmaları, kaynaklar, indirin ve bile durumunu raporlamak için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="6f8e2-113">Aşağıdaki bölümlerde bir SMB paylaşımı ya da HTTP DSC çekme sunucusuna çekme istemcisi yapılandırma işlemini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="6f8e2-114">Düğümün LCM yenilendiğinde atanan tüm yapılandırmaları indirmek için yapılandırılan konuma ulaşır.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="6f8e2-115">Tüm gerekli kaynakları düğüm üzerinde mevcut değilse, bunu otomatik olarak bunları yapılandırılan konumdan indirir.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="6f8e2-116">Düğüm ile yapılandırılmışsa, bir [rapor sunucusu](reportServer.md), sonra işlemin durumunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="6f8e2-117">Çekme istemcisi LCM yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6f8e2-117">Configure the pull client LCM</span></span>

<span data-ttu-id="6f8e2-118">Aşağıdaki örneklerde hiçbirini yürütme adlı yeni bir çıktı klasörü oluşturur **PullClientConfigID** ve metaconfiguration MOF dosyası var. koyar.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-118">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="6f8e2-119">Bu durumda, metaconfiguration MOF dosyasını adlandırılacağını `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-119">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="6f8e2-120">Yapılandırmayı uygulamak için arama **Set-DscLocalConfigurationManager** cmdlet'i ile **yolu** metaconfiguration MOF dosyasının konumuna ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-120">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="6f8e2-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6f8e2-121">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="6f8e2-122">Yapılandırma Kimliği</span><span class="sxs-lookup"><span data-stu-id="6f8e2-122">Configuration ID</span></span>

<span data-ttu-id="6f8e2-123">Aşağıdaki kümesi örneklerden **ConfigurationID** LCM için özelliği bir **GUID** , önceden oluşturulmuş bu amaç için.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-123">The examples below set the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="6f8e2-124">**ConfigurationID** LCM çekme sunucusunda uygun yapılandırma bulmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-124">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="6f8e2-125">Yapılandırma MOF dosyasının çekme sunucusunda adlandırılmalıdır `ConfigurationID.mof`burada *ConfigurationID* değeri **ConfigurationID** hedef düğümün LCM özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-125">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="6f8e2-126">Daha fazla bilgi için [yayımlama yapılandırmalar çekme sunucusuna (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="6f8e2-126">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="6f8e2-127">Rastgele bir sıra oluşturabilirsiniz **GUID** aşağıdaki örneği kullanarak.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-127">You can create a random **Guid** using the example below.</span></span>

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="6f8e2-128">Yapılandırmaları indirmek için bir çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="6f8e2-128">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="6f8e2-129">Her istemci yapılandırılmalıdır **çekme** modu ve çekme sunucusu URL'si yapılandırmasıyla depolandığı verilir.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-129">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="6f8e2-130">Bunu yapmak için gerekli olan bilgileri yerel Configuration Manager (LCM) yapılandırma gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-130">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="6f8e2-131">LCM yapılandırmak için yapılandırma, özel bir tür ile oluşturduğunuz bir **LocalConfigurationManager** blok.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-131">To configure the LCM, you create a special type of configuration, with a **LocalConfigurationManager** block.</span></span> <span data-ttu-id="6f8e2-132">LCM yapılandırma hakkında daha fazla bilgi için bkz. [yerel Configuration Manager Yapılandırma](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="6f8e2-132">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig4.md).</span></span>

## <a name="http-dsc-pull-server"></a><span data-ttu-id="6f8e2-133">HTTP DSC çekme sunucusuna</span><span class="sxs-lookup"><span data-stu-id="6f8e2-133">HTTP DSC Pull Server</span></span>

<span data-ttu-id="6f8e2-134">Çekme sunucusu web hizmeti olarak ayarlanıp ayarlanmadığını ayarladığınız **DownloadManagerName** için **WebDownloadManager**.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-134">If the pull server is set up as a web service, you set the **DownloadManagerName** to **WebDownloadManager**.</span></span> <span data-ttu-id="6f8e2-135">**WebDownloadManager** belirtmenizi gerektiren bir **ServerUrl** için **DownloadManagerCustomData** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-135">The **WebDownloadManager** requires that you specify a **ServerUrl** to the **DownloadManagerCustomData** key.</span></span> <span data-ttu-id="6f8e2-136">İçin bir değer belirtebilirsiniz **AllowUnsecureConnection**, aşağıdaki örnekte gösterilen şekilde.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-136">You can also specify a value for **AllowUnsecureConnection**, as in the example below.</span></span> <span data-ttu-id="6f8e2-137">Aşağıdaki betiği LCM "PullServer" adlı bir sunucudan çekme yapılandırmaları için yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-137">The following script configures the LCM to pull configurations from a server named "PullServer".</span></span>

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a><span data-ttu-id="6f8e2-138">SMB paylaşımı</span><span class="sxs-lookup"><span data-stu-id="6f8e2-138">SMB Share</span></span>

<span data-ttu-id="6f8e2-139">Çekme sunucusu bir web hizmeti yerine bir SMB dosya paylaşımı olarak ayarlanmışsa, ayarladığınız **DownloadManagerName** için **DscFileDownloadManager** yerine **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-139">If the pull server is set up as an SMB file share, rather than a web service, you set the **DownloadManagerName** to **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span> <span data-ttu-id="6f8e2-140">**DscFileDownloadManager** belirtmenizi gerektiren bir **SourcePath** özelliğinde **DownloadManagerCustomData**.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-140">The **DscFileDownloadManager** requires that you specify a **SourcePath** property in the **DownloadManagerCustomData**.</span></span> <span data-ttu-id="6f8e2-141">Aşağıdaki betik, "CONTOSO-SERVER" adlı bir sunucu üzerinde "SmbDscShare" adlı bir SMB paylaşımından yapılandırmalar çekme LCM yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="6f8e2-141">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER".</span></span>

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
PullClientConfigId -Output "."
```

## <a name="next-steps"></a><span data-ttu-id="6f8e2-142">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="6f8e2-142">Next Steps</span></span>

<span data-ttu-id="6f8e2-143">Çekme istemcisi yapılandırıldıktan sonra sonraki adımları gerçekleştirmek için aşağıdaki kılavuzları kullanın:</span><span class="sxs-lookup"><span data-stu-id="6f8e2-143">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="6f8e2-144">Yapılandırmalar çekme sunucusuna (v4/v5) yayımlama</span><span class="sxs-lookup"><span data-stu-id="6f8e2-144">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="6f8e2-145">Paket ve karşıya yükleme kaynakları çekme sunucusuna (v4)</span><span class="sxs-lookup"><span data-stu-id="6f8e2-145">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="6f8e2-146">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6f8e2-146">See Also</span></span>

- [<span data-ttu-id="6f8e2-147">Bir DSC web çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="6f8e2-147">Set up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="6f8e2-148">DSC SMB çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="6f8e2-148">Set up a DSC SMB pull server</span></span>](pullServerSMB.md)
