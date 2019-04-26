---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Bir çekme PowerShell 5.0 ve üzeri yapılandırma adlarını kullanarak istemcisi ayarlama
ms.openlocfilehash: d591e2a757130ccecaf4eaf9f363f607fca82b93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079396"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a><span data-ttu-id="f04f0-103">Bir çekme PowerShell 5.0 ve üzeri yapılandırma adlarını kullanarak istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="f04f0-103">Set up a Pull Client using Configuration Names in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="f04f0-104">Uygulama hedefi: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f04f0-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f04f0-105">Çekme sunucusu (Windows özelliği *DSC hizmet*) ancak desteklenen bir bileşen Windows Server'ın yeni özellikler veya yetenekler sunmak için herhangi bir plan vardır.</span><span class="sxs-lookup"><span data-stu-id="f04f0-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="f04f0-106">Geçişi başlıyor önerilir yönetilen istemcilere [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda dışında özellikler dahildir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="f04f0-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="f04f0-107">Çekme istemcisi ayarlama ayarlamadan önce bir çekme sunucusu ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f04f0-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="f04f0-108">Bu sırada gerekli olmasa da gidermeye yardımcı olur ve kayıt başarılı olmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="f04f0-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="f04f0-109">Bir çekme sunucusu kurmak için aşağıdaki kılavuzları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f04f0-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="f04f0-110">Bir DSC SMB çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="f04f0-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="f04f0-111">Bir DSC HTTP çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="f04f0-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="f04f0-112">Her hedef düğüm yapılandırmaları, kaynaklar, indirin ve bile durumunu raporlamak için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="f04f0-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="f04f0-113">Aşağıdaki bölümlerde bir SMB paylaşımı ya da HTTP DSC çekme sunucusuna çekme istemcisi yapılandırma işlemini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f04f0-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="f04f0-114">Düğümün LCM yenilendiğinde atanan tüm yapılandırmaları indirmek için yapılandırılan konuma ulaşır.</span><span class="sxs-lookup"><span data-stu-id="f04f0-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="f04f0-115">Tüm gerekli kaynakları düğüm üzerinde mevcut değilse, bunu otomatik olarak bunları yapılandırılan konumdan indirir.</span><span class="sxs-lookup"><span data-stu-id="f04f0-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="f04f0-116">Düğüm ile yapılandırılmışsa, bir [rapor sunucusu](reportServer.md), sonra işlemin durumunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="f04f0-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="f04f0-117">Bu konu, PowerShell 5.0 için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f04f0-117">This topic applies to PowerShell 5.0.</span></span>
> <span data-ttu-id="f04f0-118">PowerShell 4.0 çekme istemcisi ayarlama hakkında daha fazla bilgi için bkz: [PowerShell 4. 0'yapılandırma Kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="f04f0-118">For information on setting up a pull client in PowerShell 4.0, see [Set up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="f04f0-119">Çekme istemcisi LCM yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f04f0-119">Configure the pull client LCM</span></span>

<span data-ttu-id="f04f0-120">Aşağıdaki örneklerde hiçbirini yürütme adlı yeni bir çıktı klasörü oluşturur **PullClientConfigName** ve metaconfiguration MOF dosyası var. koyar.</span><span class="sxs-lookup"><span data-stu-id="f04f0-120">Executing any of the examples below creates a new output folder named **PullClientConfigName** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="f04f0-121">Bu durumda, metaconfiguration MOF dosyasını adlandırılacağını `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="f04f0-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="f04f0-122">Yapılandırmayı uygulamak için arama **Set-DscLocalConfigurationManager** cmdlet'i ile **yolu** metaconfiguration MOF dosyasının konumuna ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f04f0-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="f04f0-123">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f04f0-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a><span data-ttu-id="f04f0-124">Yapılandırma adı</span><span class="sxs-lookup"><span data-stu-id="f04f0-124">Configuration Name</span></span>

<span data-ttu-id="f04f0-125">Ayarlar aşağıdaki örneklerden **ConfigurationName** LCM önceden derlenmiş bir yapılandırma adı özelliği bu amaç için oluşturulan.</span><span class="sxs-lookup"><span data-stu-id="f04f0-125">The examples below sets the **ConfigurationName** property of the LCM to the name of a previously compiled Configuration, created for this purpose.</span></span> <span data-ttu-id="f04f0-126">**ConfigurationName** LCM çekme sunucusunda uygun yapılandırma bulmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="f04f0-126">The **ConfigurationName** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="f04f0-127">Yapılandırma MOF dosyasının çekme sunucusunda adlandırılmalıdır `<ConfigurationName>.mof`, bu durumda, "ClientConfig.mof".</span><span class="sxs-lookup"><span data-stu-id="f04f0-127">The configuration MOF file on the pull server must be named `<ConfigurationName>.mof`, in this case, "ClientConfig.mof".</span></span> <span data-ttu-id="f04f0-128">Daha fazla bilgi için [yayımlama yapılandırmalar çekme sunucusuna (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="f04f0-128">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="f04f0-129">Yapılandırmaları indirmek için bir çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="f04f0-129">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="f04f0-130">Her istemci yapılandırılmalıdır **çekme** modu ve çekme sunucusu URL'si yapılandırmasıyla depolandığı verilir.</span><span class="sxs-lookup"><span data-stu-id="f04f0-130">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="f04f0-131">Bunu yapmak için gerekli olan bilgileri yerel Configuration Manager (LCM) yapılandırma gerekir.</span><span class="sxs-lookup"><span data-stu-id="f04f0-131">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="f04f0-132">LCM yapılandırmak için özel bir tür ile donatılmış yapılandırması oluşturun. **DSCLocalConfigurationManager** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f04f0-132">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="f04f0-133">LCM yapılandırma hakkında daha fazla bilgi için bkz. [yerel Configuration Manager Yapılandırma](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="f04f0-133">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="f04f0-134">Aşağıdaki betik, "CONTOSO-PullSrv" adlı bir sunucudan çekme yapılandırmalarına LCM yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f04f0-134">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

- <span data-ttu-id="f04f0-135">Betikteki **ConfigurationRepositoryWeb** blok çekme sunucusu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f04f0-135">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="f04f0-136">**ServerURL** özelliği, çekme sunucusu için uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="f04f0-136">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

- <span data-ttu-id="f04f0-137">**RegistrationKey** bir çekme sunucusu için tüm istemci düğümleri bu çekme sunucusu arasında paylaşılan bir anahtar özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="f04f0-137">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span> <span data-ttu-id="f04f0-138">Bir dosyayı çekme sunucusunda aynı değeri depolanır.</span><span class="sxs-lookup"><span data-stu-id="f04f0-138">The same value is stored in a file on the pull server.</span></span>
  > [!NOTE]
  > <span data-ttu-id="f04f0-139">Kayıt anahtarları yalnızca çalışın **web** çekme sunucuları.</span><span class="sxs-lookup"><span data-stu-id="f04f0-139">Registration keys work only with **web** pull servers.</span></span> <span data-ttu-id="f04f0-140">Yine de kullanmalısınız **ConfigurationID** ile bir **SMB** çekme sunucusu.</span><span class="sxs-lookup"><span data-stu-id="f04f0-140">You must still use **ConfigurationID** with an **SMB** pull server.</span></span>
  > <span data-ttu-id="f04f0-141">Bir çekme sunucusu kullanarak yapılandırma hakkında bilgi için **ConfigurationID**, bkz: [yapılandırma Kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigId.md)</span><span class="sxs-lookup"><span data-stu-id="f04f0-141">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigId.md)</span></span>

- <span data-ttu-id="f04f0-142">**ConfigurationNames** istemci düğümü için hedeflenen yapılandırmaları adlarını belirten bir dizi bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="f04f0-142">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
  ><span data-ttu-id="f04f0-143">**Not:** Birden fazla değer belirtirseniz **ConfigurationNames**, de belirtmeniz gerekir **PartialConfiguration** yapılandırmanızda engeller.</span><span class="sxs-lookup"><span data-stu-id="f04f0-143">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
  ><span data-ttu-id="f04f0-144">Kısmi yapılandırmalar hakkında daha fazla bilgi için bkz. [PowerShell Desired State Configuration kısmi yapılandırmalar](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="f04f0-144">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

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

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="f04f0-145">Kaynakları indirmek için bir çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="f04f0-145">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="f04f0-146">Yalnızca belirtirseniz bir **ConfigurationRepositoryWeb** veya **ConfigurationRepositoryShare** (önceki örnekteki) LCM yapılandırmanızda engelleme, çekme istemcisi aynı kaynaklardan çeker ".mof" dosyalarınızın depolandığı konum.</span><span class="sxs-lookup"><span data-stu-id="f04f0-146">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from same location where your ".mof" files are stored.</span></span> <span data-ttu-id="f04f0-147">İstemciler kaynakları yükleyebileceğiniz farklı konumlar belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f04f0-147">You can also specify different locations where clients can download resources.</span></span> <span data-ttu-id="f04f0-148">Kaynak sunucuyu belirtmek için ya da kullandığınız bir **ResourceRepositoryWeb** (için web çekme sunucusu) veya bir **ResourceRepositoryShare** bloğu (SMB çekme sunucusu için).</span><span class="sxs-lookup"><span data-stu-id="f04f0-148">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>

<span data-ttu-id="f04f0-149">Aşağıdaki örnek, bir istemcinin yapılandırmaları bir çekme sunucusu ve kaynaklardan bir SMB paylaşımından indirmek için ayarlar bir metaconfiguration gösterir.</span><span class="sxs-lookup"><span data-stu-id="f04f0-149">The following example shows a metaconfiguration that sets up a client to download configurations from a Pull Server, and resources from an SMB share.</span></span>

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

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="f04f0-150">Rapor durumu çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="f04f0-150">Set up a Pull Client to report status</span></span>

<span data-ttu-id="f04f0-151">Bir tek çekme sunucusu yapılandırmaları, kaynaklar ve raporlama için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f04f0-151">You can use a single pull server for configurations, resources, and reporting.</span></span> <span data-ttu-id="f04f0-152">Raporlama için istemcileri varsayılan olarak yapılandırılmamış.</span><span class="sxs-lookup"><span data-stu-id="f04f0-152">Reporting is not configured for clients by default.</span></span> <span data-ttu-id="f04f0-153">Oluşturmak zorunda için durumu rapor edebilmiş istemciyi yapılandırmak için bir **ReportRepositoryWeb** blok.</span><span class="sxs-lookup"><span data-stu-id="f04f0-153">To configure a client to report status, you have to create a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="f04f0-154">Aşağıdaki örnek, bir istemci çekme yapılandırmaları ve kaynakları ve verileri, bir tek çekme sunucusuna rapor veren gönder ayarlar bir metaconfiguration gösterir.</span><span class="sxs-lookup"><span data-stu-id="f04f0-154">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="f04f0-155">Rapor sunucusu bir SMB paylaşımı olamaz.</span><span class="sxs-lookup"><span data-stu-id="f04f0-155">A report server cannot be an SMB share.</span></span>

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
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="f04f0-156">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="f04f0-156">See Also</span></span>

* [<span data-ttu-id="f04f0-157">Yapılandırma kimliği ile çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="f04f0-157">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="f04f0-158">Bir DSC web çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="f04f0-158">Setting up a DSC web pull server</span></span>](pullServer.md)
