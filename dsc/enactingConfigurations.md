---
ms.date: 2017-10-16
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "Yapılandırmaları ederek ilerlemesini kabul ederek"
ms.openlocfilehash: 01294b85d33e147593299de8ecf46c027a69f7a3
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="enacting-configurations"></a><span data-ttu-id="07f91-103">Yapılandırmaları ederek ilerlemesini kabul ederek</span><span class="sxs-lookup"><span data-stu-id="07f91-103">Enacting configurations</span></span>

><span data-ttu-id="07f91-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="07f91-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="07f91-105">PowerShell istenen durum yapılandırması (DSC) yapılandırmaları yürürlüğe iki yolu vardır: itme modu ve çekme modu.</span><span class="sxs-lookup"><span data-stu-id="07f91-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="07f91-106">Anında iletme modu</span><span class="sxs-lookup"><span data-stu-id="07f91-106">Push mode</span></span>

<span data-ttu-id="07f91-107">![Anında iletme modu](images/pushModel.png "nasıl modu works bildirme")</span><span class="sxs-lookup"><span data-stu-id="07f91-107">![Push mode](images/pushModel.png "How push mode works")</span></span>

<span data-ttu-id="07f91-108">Anında iletme modu başvuruyor etkin olarak çağırarak bir yapılandırma için bir hedef düğüm uygulama bir kullanıcıya [başlangıç DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="07f91-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet.</span></span>

<span data-ttu-id="07f91-109">Oluşturma ve yapılandırma derleme sonra onu zorlama modunda çağırarak yürürlüğe [başlangıç DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, ayarı cmdlet'inin MOF yapılandırma bulunduğu yolu Path parametresi.</span><span class="sxs-lookup"><span data-stu-id="07f91-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span>
<span data-ttu-id="07f91-110">Örneğin, yapılandırma MOF adresindedir ise `C:\DSC\Configurations\localhost.mof`, aşağıdaki komut ile yerel makineye uygulanacak: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="07f91-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="07f91-111">__Not__: varsayılan olarak, DSC yapılandırma bir arka plan işi olarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="07f91-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="07f91-112">Yapılandırma etkileşimli olarak çalıştırmak için arama [başlangıç DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) ile __-bekleyin__ parametresi.</span><span class="sxs-lookup"><span data-stu-id="07f91-112">To run the configuration interactively, call the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) with the __-Wait__ parameter.</span></span>

## <a name="pull-mode"></a><span data-ttu-id="07f91-113">Çekme modu</span><span class="sxs-lookup"><span data-stu-id="07f91-113">Pull mode</span></span>

<span data-ttu-id="07f91-114">![Çekme modu](images/pullModel.png "nasıl modu works isteme")</span><span class="sxs-lookup"><span data-stu-id="07f91-114">![Pull Mode](images/pullModel.png "How pull mode works")</span></span>

<span data-ttu-id="07f91-115">Çekme modunda, bir uzak çekme hizmetinden istenen durumu yapılandırmalarını almak için çekme istemcileri yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="07f91-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull service.</span></span>
<span data-ttu-id="07f91-116">Benzer şekilde, çekme hizmeti konak DSC hizmeti için ayarlanmış ve yapılandırmaları ve çekme istemciler tarafından gerekli kaynaklarla sağlanmış.</span><span class="sxs-lookup"><span data-stu-id="07f91-116">Likewise, the pull service has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span>
<span data-ttu-id="07f91-117">Her çekme istemcilerin düğümün yapılandırması üzerinde düzenli uyumluluk denetimi gerçekleştirir zamanlanmış bir olay vardır.</span><span class="sxs-lookup"><span data-stu-id="07f91-117">Each of the pull clients has a scheduled event that performs a periodic compliance check on the configuration of the node.</span></span>
<span data-ttu-id="07f91-118">İlk kez olay tetiklendiğinde çekme istemci üzerindeki yerel Configuration Manager (LCM'yi) LCM'yi belirtilen yapılandırmasını almak için çekme hizmetine istekte bulunur.</span><span class="sxs-lookup"><span data-stu-id="07f91-118">When the event is triggered the first time, the Local Configuration Manager (LCM) on the pull client makes a request to the pull service to get the configuration specified in the LCM.</span></span>
<span data-ttu-id="07f91-119">Bu yapılandırma çekme hizmette varsa ve ilk doğrulama denetimlerini geçirir, yapılandırma, ardından tarafından LCM'yi yürütüldüğü çekme istemciye indirilir.</span><span class="sxs-lookup"><span data-stu-id="07f91-119">If that configuration exists on the pull service, and it passes initial validation checks, the configuration is downloaded to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="07f91-120">İstemci Yapılandırması tarafından belirtilen düzenli aralıklarla uyumlu olduğunu LCM'yi denetler **ConfigurationModeFrequencyMins** LCM'yi özelliği.</span><span class="sxs-lookup"><span data-stu-id="07f91-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span>
<span data-ttu-id="07f91-121">Tarafından belirtilen düzenli aralıklarla çekme hizmetinde güncelleştirilmiş yapılandırmaları için LCM'yi denetler **RefreshModeFrequency** LCM'yi özelliği.</span><span class="sxs-lookup"><span data-stu-id="07f91-121">The LCM checks for updated configurations on the pull service at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span>
<span data-ttu-id="07f91-122">LCM'yi yapılandırma hakkında daha fazla bilgi için bkz: [yerel Configuration Manager Yapılandırma](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="07f91-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

<span data-ttu-id="07f91-123">Bir çekme hizmetini barındırmak için önerilen çözümdür DSC bulut hizmeti [Azure Otomasyonu](https://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="07f91-123">The recommended solution for hosting a Pull Service, is the DSC cloud service, [Azure Automation](https://azure.microsoft.com/services/automation/).</span></span>
<span data-ttu-id="07f91-124">Bu barındırılan grafik yönetim, raporlama ve merkezi yönetim çözümü sağlar.</span><span class="sxs-lookup"><span data-stu-id="07f91-124">This is hosted solution provides graphical management, reporting, and centralized administration.</span></span>

<span data-ttu-id="07f91-125">Bir çekme hizmeti Windows Server'da ayarlama hakkında daha fazla bilgi için bkz: [DSC web çekme sunucusu kurma](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="07f91-125">For more information on setting up a Pull Service on Windows Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>
<span data-ttu-id="07f91-126">Ancak, bu uygulama kısıtlı özelliklere sahiptir ve bazı "bunu kendiniz" tümleştirme gerektiriyor mu anlayın.</span><span class="sxs-lookup"><span data-stu-id="07f91-126">Understand however, that this implementation has limited features and does require some "do it yourself" integration.</span></span>

<span data-ttu-id="07f91-127">Aşağıdaki konularda, çekme hizmet ve istemcileri açıklanır:</span><span class="sxs-lookup"><span data-stu-id="07f91-127">The following topics explain pull service and clients:</span></span>

- [<span data-ttu-id="07f91-128">Azure Otomasyonu DSC genel bakış</span><span class="sxs-lookup"><span data-stu-id="07f91-128">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="07f91-129">Bir SMB çekme sunucusu kurma</span><span class="sxs-lookup"><span data-stu-id="07f91-129">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="07f91-130">Bir çekme istemci yapılandırma</span><span class="sxs-lookup"><span data-stu-id="07f91-130">Configuring a pull client</span></span>](pullClientConfigID.md)
