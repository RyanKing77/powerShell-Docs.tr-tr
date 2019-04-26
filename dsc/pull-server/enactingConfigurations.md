---
ms.date: 10/16/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Yapılandırmaları Kabul Etme
ms.openlocfilehash: 2a40f2055dda78cc0cb6cb05a5e14dce48be9d00
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079957"
---
# <a name="enacting-configurations"></a><span data-ttu-id="2fa10-103">Yapılandırmaları Kabul Etme</span><span class="sxs-lookup"><span data-stu-id="2fa10-103">Enacting configurations</span></span>

><span data-ttu-id="2fa10-104">Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2fa10-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="2fa10-105">PowerShell Desired State Configuration (DSC) yapılandırmaları uygulamak için iki yolu vardır: anında iletme modu ve çekme modu.</span><span class="sxs-lookup"><span data-stu-id="2fa10-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="2fa10-106">Anında iletme modu</span><span class="sxs-lookup"><span data-stu-id="2fa10-106">Push mode</span></span>

<span data-ttu-id="2fa10-107">![Anında iletme modu](../images/pushModel.png "modu works nasıl anında iletme")</span><span class="sxs-lookup"><span data-stu-id="2fa10-107">![Push mode](../images/pushModel.png "How push mode works")</span></span>

<span data-ttu-id="2fa10-108">Anında iletme modu başvuran bir yapılandırma çağırarak hedef düğüme etkin bir şekilde uygulama bir kullanıcıya [Başlat-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="2fa10-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="2fa10-109">Oluşturma ve yapılandırma derleme sonra bunu gönderim modunda çağırarak geçireceğini [Başlat-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet'ini ayarlama - Path parametresini cmdlet yapılandırma MOF bulunduğu yolu.</span><span class="sxs-lookup"><span data-stu-id="2fa10-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span>
<span data-ttu-id="2fa10-110">Örneğin, ' % s'yapılandırması MOF adresindedir ise `C:\DSC\Configurations\localhost.mof`, aşağıdaki komutla yerel makineye uygulanacak: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="2fa10-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="2fa10-111">__Not__: Varsayılan olarak, DSC yapılandırma bir arka plan işi olarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="2fa10-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="2fa10-112">Yapılandırma etkileşimli olarak çalıştırmak için çağrı [Başlat-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) ile __-bekleyin__ parametresi.</span><span class="sxs-lookup"><span data-stu-id="2fa10-112">To run the configuration interactively, call the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) with the __-Wait__ parameter.</span></span>

## <a name="pull-mode"></a><span data-ttu-id="2fa10-113">Çekme modu</span><span class="sxs-lookup"><span data-stu-id="2fa10-113">Pull mode</span></span>

<span data-ttu-id="2fa10-114">![Çekme modu](../images/pullModel.png "nasıl modu works çekme")</span><span class="sxs-lookup"><span data-stu-id="2fa10-114">![Pull Mode](../images/pullModel.png "How pull mode works")</span></span>

<span data-ttu-id="2fa10-115">Çekme modu, uzak çekme hizmetinden istenen durum yapılandırmaları almak için çekme istemcileri yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="2fa10-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull service.</span></span>
<span data-ttu-id="2fa10-116">Benzer şekilde, çekme hizmetini DSC konak Hizmeti'ne ayarlanmış ve çekme istemciler tarafından gerekli kaynakları ve yapılandırmaları ile sağlandı.</span><span class="sxs-lookup"><span data-stu-id="2fa10-116">Likewise, the pull service has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span>
<span data-ttu-id="2fa10-117">Her bir tanıtım istemcisinde bir düğüm yapılandırmasını düzenli uyumluluk denetimi yapar zamanlanmış bir olayı vardır.</span><span class="sxs-lookup"><span data-stu-id="2fa10-117">Each of the pull clients has a scheduled event that performs a periodic compliance check on the configuration of the node.</span></span>
<span data-ttu-id="2fa10-118">İlk kez olayı tetiklendiğinde, tanıtım istemcisinde yerel Configuration Manager (LCM) LCM içinde belirtilen yapılandırmasını almak için çekme hizmetine bir istek gönderir.</span><span class="sxs-lookup"><span data-stu-id="2fa10-118">When the event is triggered the first time, the Local Configuration Manager (LCM) on the pull client makes a request to the pull service to get the configuration specified in the LCM.</span></span>
<span data-ttu-id="2fa10-119">Bu yapılandırma çekme hizmetini üzerinde var olduğundan ve ilk doğrulama denetimlerini geçirir, yapılandırmanın ardından LCM göre yürütüldüğü çekme istemcisi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="2fa10-119">If that configuration exists on the pull service, and it passes initial validation checks, the configuration is downloaded to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="2fa10-120">İstemci Yapılandırması tarafından belirtilen düzenli aralıklarla uyumlu olduğunu LCM denetler **ConfigurationModeFrequencyMins** LCM özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="2fa10-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span>
<span data-ttu-id="2fa10-121">LCM denetler çekme hizmetini güncelleştirilmiş yapılandırmalar tarafından belirtilen düzenli aralıklarla **RefreshModeFrequency** LCM özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="2fa10-121">The LCM checks for updated configurations on the pull service at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span>
<span data-ttu-id="2fa10-122">LCM yapılandırma hakkında daha fazla bilgi için bkz: [yerel Configuration Manager Yapılandırma](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="2fa10-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="2fa10-123">Bir çekme hizmetini barındıran için önerilen çözümdür DSC bulut hizmeti [Azure Otomasyonu](https://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="2fa10-123">The recommended solution for hosting a Pull Service, is the DSC cloud service, [Azure Automation](https://azure.microsoft.com/services/automation/).</span></span>
<span data-ttu-id="2fa10-124">Bu barındırılan grafik yönetimi, raporlama ve merkezi yönetim çözümü sağlar.</span><span class="sxs-lookup"><span data-stu-id="2fa10-124">This is hosted solution provides graphical management, reporting, and centralized administration.</span></span>

<span data-ttu-id="2fa10-125">Windows Server'da bir çekme hizmetini ayarlama hakkında daha fazla bilgi için bkz. [bir DSC web çekme sunucusu ayarlama](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="2fa10-125">For more information on setting up a Pull Service on Windows Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>
<span data-ttu-id="2fa10-126">Ancak, bu uygulamayla sınırlı özelliklere ve bazı "bunu kendiniz" tümleştirme gerektiriyor mu anlayın.</span><span class="sxs-lookup"><span data-stu-id="2fa10-126">Understand however, that this implementation has limited features and does require some "do it yourself" integration.</span></span>

<span data-ttu-id="2fa10-127">Aşağıdaki konularda, çekme hizmetini ve istemcilerin açıklanır:</span><span class="sxs-lookup"><span data-stu-id="2fa10-127">The following topics explain pull service and clients:</span></span>

- [<span data-ttu-id="2fa10-128">Azure Automation DSC genel bakış</span><span class="sxs-lookup"><span data-stu-id="2fa10-128">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="2fa10-129">Bir SMB çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="2fa10-129">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="2fa10-130">Çekme istemcisi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2fa10-130">Configuring a pull client</span></span>](pullClientConfigID.md)
