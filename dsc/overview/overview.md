---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Windows PowerShell Desired State Configuration ' ne genel bakış
ms.openlocfilehash: 3e4f0afa17ab60bfa98f1b86b9830462a7c8e1cf
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405877"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a><span data-ttu-id="3f392-103">Windows PowerShell Desired State Configuration ' ne genel bakış</span><span class="sxs-lookup"><span data-stu-id="3f392-103">Windows PowerShell Desired State Configuration Overview</span></span>

> <span data-ttu-id="3f392-104">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3f392-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="3f392-105">DSC, BT yönetmenize olanak sağlayan PowerShell bir yönetim platformudur ve yapılandırmayı kod olarak ile geliştirme altyapısı.</span><span class="sxs-lookup"><span data-stu-id="3f392-105">DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code.</span></span>

- <span data-ttu-id="3f392-106">DSC kullanarak iş avantajları genel bakış için bkz. [karar alıcılar için genel Desired State Configuration](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="3f392-106">For an overview of the business benefits of using DSC, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>
- <span data-ttu-id="3f392-107">Mühendislik DSC kullanmanın avantajları genel bakış için bkz. [Desired State Configuration ' ne genel bakış mühendislerin](DscForEngineers.md).</span><span class="sxs-lookup"><span data-stu-id="3f392-107">For an overview of the engineering benefits of using DSC, see [Desired State Configuration Overview for Engineers](DscForEngineers.md).</span></span>
- <span data-ttu-id="3f392-108">DSC hızlı şekilde kullanmaya başlamak için bkz: [DSC Hızlı Başlangıç](../quickstarts/website-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="3f392-108">To start using DSC quickly, see [DSC quick start](../quickstarts/website-quickstart.md).</span></span>

## <a name="key-concepts"></a><span data-ttu-id="3f392-109">Temel kavramları</span><span class="sxs-lookup"><span data-stu-id="3f392-109">Key Concepts</span></span>

<span data-ttu-id="3f392-110">DSC yapılandırması, dağıtım ve yönetim sistemleri için kullanılan bildirim temelli bir platformdur.</span><span class="sxs-lookup"><span data-stu-id="3f392-110">DSC is a declarative platform used for configuration, deployment, and management of systems.</span></span> <span data-ttu-id="3f392-111">Bu, üç birincil bileşenden oluşur:</span><span class="sxs-lookup"><span data-stu-id="3f392-111">It consists of three primary components:</span></span>

- <span data-ttu-id="3f392-112">[Yapılandırmaları](../configurations/configurations.md) tanımlayın ve örneklerinin yapılandırma bildirim temelli bir PowerShell komut dosyaları.</span><span class="sxs-lookup"><span data-stu-id="3f392-112">[Configurations](../configurations/configurations.md) are declarative PowerShell scripts which define and configure instances of resources.</span></span>
    <span data-ttu-id="3f392-113">Yapılandırma, DSC (ve yapılandırma tarafından çağrılan kaynakları) çalıştıran yalnızca "bunu kolaylaştırır", sistem yapılandırması tarafından düzenlendiği durumunda var olduğu doğrulanıyor.</span><span class="sxs-lookup"><span data-stu-id="3f392-113">Upon running the configuration, DSC (and the resources being called by the configuration) will simply “make it so”, ensuring that the system exists in the state laid out by the configuration.</span></span>
    <span data-ttu-id="3f392-114">DSC yapılandırmaları ıdempotent yapılmıştır: yerel Configuration Manager (LCM) makineleri ne olursa olsun yapılandırma durumu yapılandırıldığından emin olun devam edecek bildirir.</span><span class="sxs-lookup"><span data-stu-id="3f392-114">DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.</span></span>
- <span data-ttu-id="3f392-115">[Kaynakları](../resources/resources.md) DSC, "bunu olun" parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="3f392-115">[Resources](../resources/resources.md) are the "make it so" part of DSC.</span></span> <span data-ttu-id="3f392-116">Yerleştirin ve hedef yapılandırmasının belirtilen durumda tutmak kod içerirler.</span><span class="sxs-lookup"><span data-stu-id="3f392-116">They contain the code that put and keep the target of a configuration in the specified state.</span></span>
    <span data-ttu-id="3f392-117">Kaynaklar, PowerShell modülleri bulunan ve genel olarak bir dosya ya da Windows işlem veya bir IIS sunucusu veya Azure'da çalışan bir VM olarak belirli bir şey model yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="3f392-117">Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.</span></span>
- <span data-ttu-id="3f392-118">[Yerel Configuration Manager'ı (LCM)](../managing-nodes/metaConfig.md) DSC kolaylaştıran kaynakları ve yapılandırmaları arasındaki etkileşimi altyapısıdır.</span><span class="sxs-lookup"><span data-stu-id="3f392-118">The [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md) is the engine by which DSC facilitates the interaction between resources and configurations.</span></span>
    <span data-ttu-id="3f392-119">LCM durumu yapılandırması tarafından tanımlanan korunduğundan emin olmak için kaynaklar tarafından uygulanan denetim akışı kullanarak sistem düzenli olarak yoklar.</span><span class="sxs-lookup"><span data-stu-id="3f392-119">The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained.</span></span>
    <span data-ttu-id="3f392-120">Sistem durumu dışında olduğunda, LCM "bunu yapılandırmasına göre sağlamak için" kaynakları koddaki çağrıları yapar.</span><span class="sxs-lookup"><span data-stu-id="3f392-120">If the system is out of state, the LCM makes calls to the code in resources to “make it so” according to the configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f392-121">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="3f392-121">See Also</span></span>

- [<span data-ttu-id="3f392-122">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="3f392-122">DSC Configurations</span></span>](../configurations/configurations.md)
- [<span data-ttu-id="3f392-123">DSC kaynakları</span><span class="sxs-lookup"><span data-stu-id="3f392-123">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="3f392-124">Yerel Configuration Manager'ı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3f392-124">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
