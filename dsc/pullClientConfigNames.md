---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: Yapılandırma adlarını kullanarak çekme istemcisi ayarlama
ms.openlocfilehash: dd0526b118b404854b1e9b445ca50bdaafdd01c7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="setting-up-a-pull-client-using-configuration-names"></a><span data-ttu-id="c8fe6-103">Yapılandırma adlarını kullanarak çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="c8fe6-103">Setting up a pull client using configuration names</span></span>

> <span data-ttu-id="c8fe6-104">İçin geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c8fe6-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="c8fe6-105">Çekme modunu kullanacak şekilde söylediyse ve yapılandırmaları almak için çekme sunucunun nerede ile bağlantı kurabildiğini URL verilen her hedef düğüme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span>
<span data-ttu-id="c8fe6-106">Bunu yapmak için gerekli olan bilgileri yerel Configuration Manager (LCM'yi) yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span>
<span data-ttu-id="c8fe6-107">Özel türde bir yapılandırma ile donatılmış, oluşturduğunuz LCM'yi yapılandırmak için **DSCLocalConfigurationManager** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-107">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span>
<span data-ttu-id="c8fe6-108">LCM'yi yapılandırma hakkında daha fazla bilgi için bkz: [yerel Configuration Manager Yapılandırma](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="c8fe6-108">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="c8fe6-109">**Not**: Bu konu, PowerShell 5.0 için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-109">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="c8fe6-110">PowerShell 4.0 çekme istemcisinde ayarlama hakkında daha fazla bilgi için bkz: [PowerShell 4. 0 ' yapılandırması kimliği kullanan bir çekme istemci ayarlama](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="c8fe6-110">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="c8fe6-111">Aşağıdaki komut dosyasını, "CONTOSO-PullSrv" adlı bir sunucudan çekme yapılandırmaları için LCM'yi yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="c8fe6-111">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv":</span></span>

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

<span data-ttu-id="c8fe6-112">Komut dosyasında **ConfigurationRepositoryWeb** blok çekme sunucunun tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-112">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span>
<span data-ttu-id="c8fe6-113">**ServerURL** özelliği, çekme sunucu için uç noktaya belirtir.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-113">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

<span data-ttu-id="c8fe6-114">**RegistrationKey** çekme sunucusuna ilişkin tüm istemci düğümleri ve çekme sunucu arasında paylaşılan bir anahtar bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-114">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span>
<span data-ttu-id="c8fe6-115">Aynı değere çekme sunucusunda bir dosyada depolanır.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-115">The same value is stored in a file on the pull server.</span></span>

<span data-ttu-id="c8fe6-116">**ConfigurationNames** istemci düğümü için hedeflenen yapılandırmaları adını belirten bir dizi bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-116">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
<span data-ttu-id="c8fe6-117">Çekme sunucusunda yapılandırma MOF dosyası bu istemci düğüm adlı için *ConfigurationNames*.mof, burada *ConfigurationNames* değeri ile eşleşen **ConfigurationNames**  özelliği bu meta yapılandırmasını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-117">On the pull server, the configuration MOF file for this client node must be named *ConfigurationNames*.mof, where *ConfigurationNames* matches the value of the **ConfigurationNames** property you set in this metaconfiguration.</span></span>

><span data-ttu-id="c8fe6-118">**Not:** birden fazla değer belirtirseniz, **ConfigurationNames**, de belirtmeniz gerekir **PartialConfiguration** yapılandırmanızda engeller.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-118">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
<span data-ttu-id="c8fe6-119">Kısmi yapılandırmaları hakkında daha fazla bilgi için bkz: [PowerShell istenen durum yapılandırması kısmi yapılandırmaları](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="c8fe6-119">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

<span data-ttu-id="c8fe6-120">Bu betik çalıştıktan sonra adlı yeni bir çıkış klasörü oluşturur **PullClientConfigNames** ve meta yapılandırmasını MOF dosyası var. yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-120">After this script runs, it creates a new output folder named **PullClientConfigNames** and puts a metaconfiguration MOF file there.</span></span>
<span data-ttu-id="c8fe6-121">Bu durumda, meta yapılandırmasını MOF dosyası adlandırılacağını `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="c8fe6-122">Yapılandırmayı uygulamak için arama **kümesi DscLocalConfigurationManager** cmdlet'i ile **yolu** meta yapılandırmasını MOF dosyasının konumunu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span>

```powershell
Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.
```

> <span data-ttu-id="c8fe6-123">**Not**: Kayıt anahtarlarını yalnızca web çekme sunucularıyla çalışır.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-123">**Note**: Registration keys work only with web pull servers.</span></span>
<span data-ttu-id="c8fe6-124">Hala kullanmalısınız **ConfigurationID** bir SMB çekme sunucusuyla.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-124">You must still use **ConfigurationID** with an SMB pull server.</span></span>
<span data-ttu-id="c8fe6-125">Bir çekme sunucusuna kullanarak yapılandırma hakkında bilgi için **ConfigurationID**, bkz: [yapılandırma Kimliğini kullanarak bir çekme istemci ayarı](PullClientConfigNames.md)</span><span class="sxs-lookup"><span data-stu-id="c8fe6-125">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](PullClientConfigNames.md)</span></span>

## <a name="resource-and-report-servers"></a><span data-ttu-id="c8fe6-126">Kaynak ve rapor sunucuları</span><span class="sxs-lookup"><span data-stu-id="c8fe6-126">Resource and report servers</span></span>

<span data-ttu-id="c8fe6-127">Yalnızca belirtirseniz bir **ConfigurationRepositoryWeb** veya **ConfigurationRepositoryShare** (önceki örnektekiyle) LCM'yi yapılandırmanızda engellemek, çekme istemci kaynaklardan çeker Belirtilen sunucu, ancak raporları için göndermez.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-127">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span>
<span data-ttu-id="c8fe6-128">Tek tanıtım sunucu yapılandırmaları, kaynaklar ve raporlama için kullanabilirsiniz, ancak oluşturmak zorunda bir **ReportRepositoryWeb** set up reporting bloğu.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-128">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>
<span data-ttu-id="c8fe6-129">Aşağıdaki örnek, bir istemciye çekme yapılandırmaları ve kaynakları ve veri, bir tek çekme sunucusuna raporlama Gönder ayarlar meta yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-129">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="c8fe6-130">Kaynaklar ve raporlama için farklı çekme sunucuları da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-130">You can also specify different pull servers for resources and reporting.</span></span>
<span data-ttu-id="c8fe6-131">Kaynak sunucuyu belirtmek için ya da kullandığınız bir **ResourceRepositoryWeb** (bir web çekme sunucusu için) veya bir **ResourceRepositoryShare** bloğu (SMB çekme sunucusu için).</span><span class="sxs-lookup"><span data-stu-id="c8fe6-131">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="c8fe6-132">Bir rapor sunucusu belirtmek için kullandığınız bir **ReportRepositoryWeb** bloğu.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-132">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span>
<span data-ttu-id="c8fe6-133">Bir rapor sunucusu bir SMB sunucusu olamaz.</span><span class="sxs-lookup"><span data-stu-id="c8fe6-133">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="c8fe6-134">Bir çekme istemci kendi yapılandırmalardan almak için şu meta yapılandırmasını yapılandırır **CONTOSO PullSrv** ve kaynaklarıyla **CONTOSO ResourceSrv**ve durum raporları göndermek için  **CONTOSO ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="c8fe6-134">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c8fe6-135">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="c8fe6-135">See Also</span></span>

* [<span data-ttu-id="c8fe6-136">Bir çekme istemci yapılandırması kimliği ile ayarlama</span><span class="sxs-lookup"><span data-stu-id="c8fe6-136">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="c8fe6-137">DSC çekme sunucusuna ayarlama</span><span class="sxs-lookup"><span data-stu-id="c8fe6-137">Setting up a DSC web pull server</span></span>](pullServer.md)