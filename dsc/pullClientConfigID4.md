---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: PowerShell 4. 0 ' yapılandırması kimliği kullanan bir çekme istemci ayarlama
ms.openlocfilehash: f9bea92f1a2dce94792d72e03bef884d2729f3c0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a><span data-ttu-id="ec9ce-103">PowerShell 4. 0 ' yapılandırması kimliği kullanan bir çekme istemci ayarlama</span><span class="sxs-lookup"><span data-stu-id="ec9ce-103">Setting up a pull client using configuration ID in PowerShell 4.0</span></span>

><span data-ttu-id="ec9ce-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ec9ce-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="ec9ce-105">Çekme modunu kullanacak şekilde söylediyse ve yapılandırmaları almak için çekme sunucunun nerede ile bağlantı kurabildiğini URL verilen her hedef düğüme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ec9ce-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="ec9ce-106">Bunu yapmak için gerekli olan bilgileri yerel Configuration Manager (LCM'yi) yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec9ce-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="ec9ce-107">LCM'yi yapılandırmak için bir "meta yapılandırmasını" bilinen yapılandırma özel bir tür oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ec9ce-107">To configure the LCM, you create a special type of configuration known as a "metaconfiguration".</span></span> <span data-ttu-id="ec9ce-108">LCM'yi yapılandırma hakkında daha fazla bilgi için bkz: [Windows PowerShell 4.0 istenen durum yapılandırması yerel Configuration Manager](metaConfig4.md)</span><span class="sxs-lookup"><span data-stu-id="ec9ce-108">For more information about configuring the LCM, see [Windows PowerShell 4.0 Desired State Configuration Local Configuration Manager](metaConfig4.md)</span></span>

<span data-ttu-id="ec9ce-109">Aşağıdaki komut dosyası LCM'yi çekme yapılandırmaları için "PullServer" adlı bir sunucudan yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="ec9ce-109">The following script configures the LCM to pull configurations from a server named "PullServer":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull
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
SimpleMetaConfigurationForPull -Output "."
```

<span data-ttu-id="ec9ce-110">Komut dosyasında **DownloadManagerCustomData** geçişleri URL çekme sunucusunun ve (Bu örneğin), güvenli olmayan bir bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec9ce-110">In the script, **DownloadManagerCustomData** passes the URL of the pull server and (for this example) allows an unsecured connection.</span></span>

<span data-ttu-id="ec9ce-111">Bu betik çalıştıktan sonra adlı yeni bir çıkış klasörü oluşturur **SimpleMetaConfigurationForPull** ve meta yapılandırmasını MOF dosyası var. yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="ec9ce-111">After this script runs, it creates a new output folder called **SimpleMetaConfigurationForPull** and puts a metaconfiguration MOF file there.</span></span>

<span data-ttu-id="ec9ce-112">Yapılandırmayı uygulamak için kullanmak **kümesi DscLocalConfigurationManager** parametrelere sahip **ComputerName** ("localhost" kullanın) ve **yolu** (konumu yolu düğümün localhost.meta.mof dosya hedef).</span><span class="sxs-lookup"><span data-stu-id="ec9ce-112">To apply the configuration, use **Set-DscLocalConfigurationManager** with parameters for **ComputerName** (use “localhost”) and **Path** (the path to the location of the target node’s localhost.meta.mof file).</span></span> <span data-ttu-id="ec9ce-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ec9ce-113">For example:</span></span>
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="ec9ce-114">Yapılandırma Kimliği</span><span class="sxs-lookup"><span data-stu-id="ec9ce-114">Configuration ID</span></span>
<span data-ttu-id="ec9ce-115">Komut dosyası kümeleri **ConfigurationID** bu amaç için daha önce oluşturulmuş bir GUID LCM'yi özelliği (kullanarak bir GUID oluşturabilirsiniz **yeni GUID** cmdlet'i).</span><span class="sxs-lookup"><span data-stu-id="ec9ce-115">The script sets the **ConfigurationID** property of the LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="ec9ce-116">**ConfigurationID** LCM'yi çekme sunucusunda uygun yapılandırma bulmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="ec9ce-116">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="ec9ce-117">Çekme sunucusunda yapılandırma MOF dosyası olarak adlandırılmalıdır `ConfigurationID.mof`, burada *ConfigurationID* değeri **ConfigurationID** hedef düğümün LCM'yi özelliği.</span><span class="sxs-lookup"><span data-stu-id="ec9ce-117">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="pulling-from-an-smb-server"></a><span data-ttu-id="ec9ce-118">Bir SMB sunucusundan çekme</span><span class="sxs-lookup"><span data-stu-id="ec9ce-118">Pulling from an SMB server</span></span>

<span data-ttu-id="ec9ce-119">Belirttiğiniz çekme sunucusuna bir web hizmeti yerine bir SMB dosya paylaşımı olarak ayarlanırsa, **DscFileDownloadManager** yerine **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="ec9ce-119">If the pull server is set up as an SMB file share, rather than a web service, you specify the **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span>
<span data-ttu-id="ec9ce-120">**DscFileDownloadManager** geçen bir **KaynakYolu** özelliği yerine **ServerUrl**.</span><span class="sxs-lookup"><span data-stu-id="ec9ce-120">The **DscFileDownloadManager** takes a **SourcePath** property instead of **ServerUrl**.</span></span> <span data-ttu-id="ec9ce-121">Aşağıdaki komut dosyası "CONTOSO-SERVER" adlı bir sunucuda "SmbDscShare" adlı bir SMB paylaşımına yapılandırmalardan çıkarmak için LCM'yi yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="ec9ce-121">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull
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
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a><span data-ttu-id="ec9ce-122">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ec9ce-122">See Also</span></span>

- [<span data-ttu-id="ec9ce-123">DSC çekme sunucusuna ayarlama</span><span class="sxs-lookup"><span data-stu-id="ec9ce-123">Setting up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="ec9ce-124">DSC SMB çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="ec9ce-124">Setting up a DSC SMB pull server</span></span>](pullServerSMB.md)