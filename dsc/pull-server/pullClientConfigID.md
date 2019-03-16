---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: Bir çekme yapılandırma kimliklerinin PowerShell 5.0 ve üzeri kullanılarak istemcisi ayarlama
ms.openlocfilehash: 14db98d240bc87aca3ee985db08c14b7c65d8bb8
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055725"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="57e6f-103">Bir çekme yapılandırma kimliklerinin PowerShell 5.0 ve üzeri kullanılarak istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="57e6f-103">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="57e6f-104">Şunun için geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="57e6f-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="57e6f-105">Çekme sunucusu (Windows özelliği *DSC hizmet*) ancak desteklenen bir bileşen Windows Server'ın yeni özellikler veya yetenekler sunmak için herhangi bir plan vardır.</span><span class="sxs-lookup"><span data-stu-id="57e6f-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="57e6f-106">Geçişi başlıyor önerilir yönetilen istemcilere [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda dışında özellikler dahildir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="57e6f-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="57e6f-107">Çekme istemcisi ayarlama ayarlamadan önce bir çekme sunucusu ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="57e6f-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="57e6f-108">Bu sırada gerekli olmasa da gidermeye yardımcı olur ve kayıt başarılı olmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="57e6f-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="57e6f-109">Bir çekme sunucusu kurmak için aşağıdaki kılavuzları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="57e6f-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="57e6f-110">Bir DSC SMB çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="57e6f-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="57e6f-111">Bir DSC HTTP çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="57e6f-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="57e6f-112">Her hedef düğüm yapılandırmaları, kaynaklar, indirin ve bile durumunu raporlamak için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="57e6f-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="57e6f-113">Aşağıdaki bölümlerde bir SMB paylaşımı ya da HTTP DSC çekme sunucusuna çekme istemcisi yapılandırma işlemini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="57e6f-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="57e6f-114">Düğümün LCM yenilendiğinde atanan tüm yapılandırmaları indirmek için yapılandırılan konuma ulaşır.</span><span class="sxs-lookup"><span data-stu-id="57e6f-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="57e6f-115">Tüm gerekli kaynakları düğüm üzerinde mevcut değilse, bunu otomatik olarak bunları yapılandırılan konumdan indirir.</span><span class="sxs-lookup"><span data-stu-id="57e6f-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="57e6f-116">Düğüm ile yapılandırılmışsa, bir [rapor sunucusu](reportServer.md), sonra işlemin durumunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="57e6f-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="57e6f-117">Bu konu, PowerShell 5.0 için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="57e6f-117">This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="57e6f-118">PowerShell 4.0 çekme istemcisi ayarlama hakkında daha fazla bilgi için bkz: [PowerShell 4. 0'yapılandırma Kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="57e6f-118">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="57e6f-119">Çekme istemcisi LCM yapılandırma</span><span class="sxs-lookup"><span data-stu-id="57e6f-119">Configure the pull client LCM</span></span>

<span data-ttu-id="57e6f-120">Aşağıdaki örneklerde hiçbirini yürütme adlı yeni bir çıktı klasörü oluşturur **PullClientConfigID** ve metaconfiguration MOF dosyası var. koyar.</span><span class="sxs-lookup"><span data-stu-id="57e6f-120">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="57e6f-121">Bu durumda, metaconfiguration MOF dosyasını adlandırılacağını `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="57e6f-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="57e6f-122">Yapılandırmayı uygulamak için arama **Set-DscLocalConfigurationManager** cmdlet'i ile **yolu** metaconfiguration MOF dosyasının konumuna ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="57e6f-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="57e6f-123">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="57e6f-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="57e6f-124">Yapılandırma Kimliği</span><span class="sxs-lookup"><span data-stu-id="57e6f-124">Configuration ID</span></span>

<span data-ttu-id="57e6f-125">Ayarlar aşağıdaki örneklerden **ConfigurationID** LCM için özelliği bir **GUID** , önceden oluşturulmuş bu amaç için.</span><span class="sxs-lookup"><span data-stu-id="57e6f-125">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="57e6f-126">**ConfigurationID** LCM çekme sunucusunda uygun yapılandırma bulmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="57e6f-126">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="57e6f-127">Yapılandırma MOF dosyasının çekme sunucusunda adlandırılmalıdır `ConfigurationID.mof`burada *ConfigurationID* değeri **ConfigurationID** hedef düğümün LCM özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="57e6f-127">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="57e6f-128">Daha fazla bilgi için [yayımlama yapılandırmalar çekme sunucusuna (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="57e6f-128">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="57e6f-129">Rastgele bir sıra oluşturabilirsiniz **GUID** kullanarak veya aşağıdaki örneği kullanarak [yeni GUID](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="57e6f-129">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="57e6f-130">Kullanma hakkında daha fazla bilgi için **GUID'leri** ortamınızda bkz [planlama GUID'leri](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="57e6f-130">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="57e6f-131">Yapılandırmaları indirmek için bir çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="57e6f-131">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="57e6f-132">Her istemci yapılandırılmalıdır **çekme** modu ve çekme sunucusu URL'si yapılandırmasıyla depolandığı verilir.</span><span class="sxs-lookup"><span data-stu-id="57e6f-132">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="57e6f-133">Bunu yapmak için gerekli olan bilgileri yerel Configuration Manager (LCM) yapılandırma gerekir.</span><span class="sxs-lookup"><span data-stu-id="57e6f-133">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="57e6f-134">LCM yapılandırmak için özel bir tür ile donatılmış yapılandırması oluşturun. **DSCLocalConfigurationManager** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="57e6f-134">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="57e6f-135">LCM yapılandırma hakkında daha fazla bilgi için bkz. [yerel Configuration Manager Yapılandırma](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="57e6f-135">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="57e6f-136">HTTP DSC çekme sunucusuna</span><span class="sxs-lookup"><span data-stu-id="57e6f-136">HTTP DSC Pull Server</span></span>

<span data-ttu-id="57e6f-137">Aşağıdaki betik, "CONTOSO-PullSrv" adlı bir sunucudan çekme yapılandırmalarına LCM yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="57e6f-137">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="57e6f-138">Betikteki **ConfigurationRepositoryWeb** blok çekme sunucusu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="57e6f-138">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="57e6f-139">**ServerUrl** DSC çekme URL'sini belirtir</span><span class="sxs-lookup"><span data-stu-id="57e6f-139">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="57e6f-140">SMB paylaşımı</span><span class="sxs-lookup"><span data-stu-id="57e6f-140">SMB Share</span></span>

<span data-ttu-id="57e6f-141">Aşağıdaki betiği LCM çekme yapılandırmalar için SMB paylaşımından yapılandırır `\\SMBPullServer\Pull`.</span><span class="sxs-lookup"><span data-stu-id="57e6f-141">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

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
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="57e6f-142">Betikteki **ConfigurationRepositoryShare** blok, bu durumda, yalnızca bir SMB paylaşımına çekme sunucusu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="57e6f-142">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="57e6f-143">Kaynakları indirmek için bir çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="57e6f-143">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="57e6f-144">Yalnızca belirtirseniz **ConfigurationRepositoryWeb** veya **ConfigurationRepositoryShare** LCM yapılandırmanızda (önceki örnek) olduğu gibi engelleme, çekme istemcisi aynı kaynaklardan çeker konum, yapılandırmaları alır.</span><span class="sxs-lookup"><span data-stu-id="57e6f-144">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="57e6f-145">Kaynaklar için ayrı konumlar belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57e6f-145">You can also specify separate locations for resources.</span></span> <span data-ttu-id="57e6f-146">Bir kaynak konumu ayrı bir sunucu belirtmek için kullanın **ResourceRepositoryWeb** blok.</span><span class="sxs-lookup"><span data-stu-id="57e6f-146">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="57e6f-147">Bir kaynak konumu SMB paylaşımı belirtmek için kullanın **ResourceRepositoryShare** blok.</span><span class="sxs-lookup"><span data-stu-id="57e6f-147">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="57e6f-148">Birleştirebilirsiniz **ConfigurationRepositoryWeb** ile **ResourceRepositoryShare** veya **ConfigurationRepositoryShare** ile **ResourceRepositoryWeb** .</span><span class="sxs-lookup"><span data-stu-id="57e6f-148">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb**.</span></span> <span data-ttu-id="57e6f-149">Buna örnek olarak, aşağıda gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="57e6f-149">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="57e6f-150">HTTP DSC çekme sunucusuna</span><span class="sxs-lookup"><span data-stu-id="57e6f-150">HTTP DSC Pull Server</span></span>

<span data-ttu-id="57e6f-151">Çekme istemcisi kendi yapılandırmaları almak için aşağıdaki metaconfiguration yapılandırır **CONTOSO PullSrv** ve kaynaklarıyla **CONTOSO ResourceSrv**.</span><span class="sxs-lookup"><span data-stu-id="57e6f-151">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**.</span></span>

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
    }
}
PullClientConfigID
```

### <a name="smb-share"></a><span data-ttu-id="57e6f-152">SMB paylaşımı</span><span class="sxs-lookup"><span data-stu-id="57e6f-152">SMB Share</span></span>

<span data-ttu-id="57e6f-153">Aşağıdaki örnek, bir istemcinin SMB paylaşımından çekme yapılandırmaları ayarlayan bir metaconfiguration gösterir `\\SMBPullServer\Configurations`ve SMB paylaşımındaki kaynakları `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="57e6f-153">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

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
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="57e6f-154">Anında iletme modunda kaynakları otomatik olarak indir</span><span class="sxs-lookup"><span data-stu-id="57e6f-154">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="57e6f-155">İçin bile yapılandırılmış PowerShell 5. 0'den itibaren çekme istemcilerinize modülleri bir SMB paylaşımından indirebilir **anında iletme** modu.</span><span class="sxs-lookup"><span data-stu-id="57e6f-155">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="57e6f-156">Bu çekme sunucusu kurmak istediğiniz olmayan senaryolarda özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="57e6f-156">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="57e6f-157">**ResourceRepositoryShare** blok belirtmeden kullanılabilir bir **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="57e6f-157">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="57e6f-158">Aşağıdaki örnek, bir istemcinin bir SMB paylaşımından çekme kaynaklarına ayarlar bir metaconfiguration gösterir `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="57e6f-158">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="57e6f-159">Düğüm olduğunda **PUSHED** bir yapılandırma, otomatik olarak tüm gerekli kaynakları belirtilen paylaşımından indirir.</span><span class="sxs-lookup"><span data-stu-id="57e6f-159">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="57e6f-160">Rapor durumu çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="57e6f-160">Set up a Pull Client to report status</span></span>

<span data-ttu-id="57e6f-161">Varsayılan olarak, düğüm raporları yapılandırılmış bir çekme sunucusuna göndermezler.</span><span class="sxs-lookup"><span data-stu-id="57e6f-161">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="57e6f-162">Bir tek çekme sunucusu yapılandırmaları, kaynaklar ve raporlama için kullanabilirsiniz, ancak oluşturmak sahip olduğunuz bir **ReportRepositoryWeb** set up reporting bloğu.</span><span class="sxs-lookup"><span data-stu-id="57e6f-162">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="57e6f-163">HTTP DSC çekme sunucusuna</span><span class="sxs-lookup"><span data-stu-id="57e6f-163">HTTP DSC Pull Server</span></span>

<span data-ttu-id="57e6f-164">Aşağıdaki örnek, bir istemci çekme yapılandırmaları ve kaynakları ve verileri, bir tek çekme sunucusuna rapor veren gönder ayarlar bir metaconfiguration gösterir.</span><span class="sxs-lookup"><span data-stu-id="57e6f-164">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="57e6f-165">Bir rapor sunucusunu belirtmek için kullandığınız bir **ReportRepositoryWeb** blok.</span><span class="sxs-lookup"><span data-stu-id="57e6f-165">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="57e6f-166">Rapor sunucusu bir SMB sunucusu olamaz.</span><span class="sxs-lookup"><span data-stu-id="57e6f-166">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="57e6f-167">Çekme istemcisi kendi yapılandırmaları almak için aşağıdaki metaconfiguration yapılandırır **CONTOSO PullSrv** ve kaynaklarıyla **CONTOSO ResourceSrv**ve durum raporları göndermek için  **CONTOSO ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="57e6f-167">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="57e6f-168">SMB paylaşımı</span><span class="sxs-lookup"><span data-stu-id="57e6f-168">SMB Share</span></span>

<span data-ttu-id="57e6f-169">Rapor sunucusu bir SMB paylaşımı olamaz.</span><span class="sxs-lookup"><span data-stu-id="57e6f-169">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="57e6f-170">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="57e6f-170">Next Steps</span></span>

<span data-ttu-id="57e6f-171">Çekme istemcisi yapılandırıldıktan sonra sonraki adımları gerçekleştirmek için aşağıdaki kılavuzları kullanın:</span><span class="sxs-lookup"><span data-stu-id="57e6f-171">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="57e6f-172">Yapılandırmalar çekme sunucusuna (v4/v5) yayımlama</span><span class="sxs-lookup"><span data-stu-id="57e6f-172">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="57e6f-173">Paket ve karşıya yükleme kaynakları çekme sunucusuna (v4)</span><span class="sxs-lookup"><span data-stu-id="57e6f-173">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="57e6f-174">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="57e6f-174">See Also</span></span>

* [<span data-ttu-id="57e6f-175">Yapılandırma adları ile çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="57e6f-175">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)
