---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: Windows PowerShell istenen durum yapılandırması genel bakış
ms.openlocfilehash: 3f357ea11a388a05b73539a63e52e639ee906f68
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="windows-powershell-desired-state-configuration-overview"></a><span data-ttu-id="92a55-103">Windows PowerShell istenen durum yapılandırması genel bakış</span><span class="sxs-lookup"><span data-stu-id="92a55-103">Windows PowerShell Desired State Configuration Overview</span></span>

> <span data-ttu-id="92a55-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="92a55-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="92a55-105">DSC olan bir yönetim platformunun PowerShell'de BT yönetmenizi sağlar ve geliştirme altyapı kodu yapılandırmaya sahip.</span><span class="sxs-lookup"><span data-stu-id="92a55-105">DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code.</span></span>

- <span data-ttu-id="92a55-106">DSC kullanarak iş avantajları genel bakış için bkz: [istenen durum yapılandırması için genel bakış karar alıcılar](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="92a55-106">For an overview of the business benefits of using DSC, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>
- <span data-ttu-id="92a55-107">Mühendislik DSC kullanmanın yararları genel bakış için bkz: [istenen durum yapılandırması için genel bakış mühendisleri](DscForEngineers.md).</span><span class="sxs-lookup"><span data-stu-id="92a55-107">For an overview of the engineering benefits of using DSC, see [Desired State Configuration Overview for Engineers](DscForEngineers.md).</span></span>
- <span data-ttu-id="92a55-108">DSC hızlı şekilde kullanmaya başlamak için bkz: [DSC Hızlı Başlangıç](quickStart.md).</span><span class="sxs-lookup"><span data-stu-id="92a55-108">To start using DSC quickly, see [DSC quick start](quickStart.md).</span></span>

## <a name="key-concepts"></a><span data-ttu-id="92a55-109">Temel kavramları</span><span class="sxs-lookup"><span data-stu-id="92a55-109">Key Concepts</span></span>

<span data-ttu-id="92a55-110">DSC yapılandırması, dağıtım ve yönetim sistemleri için kullanılan bildirim temelli bir platformdur.</span><span class="sxs-lookup"><span data-stu-id="92a55-110">DSC is a declarative platform used for configuration, deployment, and management of systems.</span></span> <span data-ttu-id="92a55-111">Üç birincil bileşenden oluşur:</span><span class="sxs-lookup"><span data-stu-id="92a55-111">It consists of three primary components:</span></span>

- <span data-ttu-id="92a55-112">[Yapılandırmaları](configurations.md) tanımlamak ve kaynakları örneklerini yapılandırın bildirim temelli bir PowerShell komut dosyaları.</span><span class="sxs-lookup"><span data-stu-id="92a55-112">[Configurations](configurations.md) are declarative PowerShell scripts which define and configure instances of resources.</span></span>
    <span data-ttu-id="92a55-113">Yapılandırma, DSC (ve yapılandırma tarafından çağrılan kaynaklar) çalışan işlem yalnızca "bunu kolaylaştırır", sistem yapılandırması tarafından düzenlendiği durumda var olduğu doğrulanıyor.</span><span class="sxs-lookup"><span data-stu-id="92a55-113">Upon running the configuration, DSC (and the resources being called by the configuration) will simply “make it so”, ensuring that the system exists in the state laid out by the configuration.</span></span>
    <span data-ttu-id="92a55-114">DSC yapılandırmaları olan de ıdempotent: yerel Configuration Manager (LCM'yi) makineleri, ne olursa olsun yapılandırma durumu olarak yapılandırıldığından emin olmak devam edecek bildirir.</span><span class="sxs-lookup"><span data-stu-id="92a55-114">DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.</span></span>
- <span data-ttu-id="92a55-115">[Kaynakları](resources.md) "bunu make" DSC parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="92a55-115">[Resources](resources.md) are the "make it so" part of DSC.</span></span> <span data-ttu-id="92a55-116">Put ve yapılandırmasının hedef belirtilen durumda tutun kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="92a55-116">They contain the code that put and keep the target of a configuration in the specified state.</span></span>
    <span data-ttu-id="92a55-117">Kaynaklar PowerShell modülleri bulunan ve genel olarak bir dosya veya bir Windows işlemini veya bir IIS sunucusu veya Azure'da çalışan VM olarak belirli bir şey modellemek için yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="92a55-117">Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.</span></span>
- <span data-ttu-id="92a55-118">[Yerel Configuration Manager (LCM'yi)](metaConfig.md) DSC kolaylaştıran kaynakları ve yapılandırmaları arasındaki etkileşimi altyapısıdır.</span><span class="sxs-lookup"><span data-stu-id="92a55-118">The [Local Configuration Manager (LCM)](metaConfig.md) is the engine by which DSC facilitates the interaction between resources and configurations.</span></span>
    <span data-ttu-id="92a55-119">LCM'yi yapılandırması tarafından tanımlanan durumu korunduğundan emin olmak için kaynaklar tarafından uygulanan akış denetimi kullanarak sistem düzenli aralıklarla yoklar.</span><span class="sxs-lookup"><span data-stu-id="92a55-119">The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained.</span></span>
    <span data-ttu-id="92a55-120">Sistem durumu dışında olduğunda LCM'yi kodu "bunu yapılandırmasına göre yapmak için" kaynaklarında çağrılar.</span><span class="sxs-lookup"><span data-stu-id="92a55-120">If the system is out of state, the LCM makes calls to the code in resources to “make it so” according to the configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="92a55-121">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="92a55-121">See Also</span></span>

- [<span data-ttu-id="92a55-122">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="92a55-122">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="92a55-123">DSC kaynakları</span><span class="sxs-lookup"><span data-stu-id="92a55-123">DSC Resources</span></span>](resources.md)
- [<span data-ttu-id="92a55-124">Yerel Yapılandırma Yöneticisi'ni yapılandırma</span><span class="sxs-lookup"><span data-stu-id="92a55-124">Configuring The Local Configuration Manager</span></span>](metaConfig.md)