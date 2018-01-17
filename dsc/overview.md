---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "Windows PowerShell istenen durum yapılandırması genel bakış"
ms.openlocfilehash: 1d6ba0b2fdb514e703ddad11adf4cdace5c001a9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="windows-powershell-desired-state-configuration-overview"></a><span data-ttu-id="770ff-103">Windows PowerShell istenen durum yapılandırması genel bakış</span><span class="sxs-lookup"><span data-stu-id="770ff-103">Windows PowerShell Desired State Configuration Overview</span></span> 

> <span data-ttu-id="770ff-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="770ff-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="770ff-105">DSC olan bir yönetim platformunun PowerShell'de BT yönetmenizi sağlar ve geliştirme altyapı kodu yapılandırmaya sahip.</span><span class="sxs-lookup"><span data-stu-id="770ff-105">DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code.</span></span>

- <span data-ttu-id="770ff-106">DSC kullanarak iş avantajları genel bakış için bkz: [istenen durum yapılandırması için genel bakış karar alıcılar](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="770ff-106">For an overview of the business benefits of using DSC, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>
- <span data-ttu-id="770ff-107">Mühendislik DSC kullanmanın yararları genel bakış için bkz: [istenen durum yapılandırması için genel bakış mühendisleri](DscForEngineers.md).</span><span class="sxs-lookup"><span data-stu-id="770ff-107">For an overview of the engineering benefits of using DSC, see [Desired State Configuration Overview for Engineers](DscForEngineers.md).</span></span>
- <span data-ttu-id="770ff-108">DSC hızlı şekilde kullanmaya başlamak için bkz: [DSC Hızlı Başlangıç](quickStart.md).</span><span class="sxs-lookup"><span data-stu-id="770ff-108">To start using DSC quickly, see [DSC quick start](quickStart.md).</span></span>

## <a name="key-concepts"></a><span data-ttu-id="770ff-109">Temel kavramları</span><span class="sxs-lookup"><span data-stu-id="770ff-109">Key Concepts</span></span>

<span data-ttu-id="770ff-110">DSC yapılandırması, dağıtım ve yönetim sistemleri için kullanılan bildirim temelli bir platformdur.</span><span class="sxs-lookup"><span data-stu-id="770ff-110">DSC is a declarative platform used for configuration, deployment, and management of systems.</span></span> <span data-ttu-id="770ff-111">Üç birincil bileşenden oluşur:</span><span class="sxs-lookup"><span data-stu-id="770ff-111">It consists of three primary components:</span></span>

- <span data-ttu-id="770ff-112">[Yapılandırmaları](configurations.md) tanımlamak ve kaynakları örneklerini yapılandırın bildirim temelli bir PowerShell komut dosyaları.</span><span class="sxs-lookup"><span data-stu-id="770ff-112">[Configurations](configurations.md) are declarative PowerShell scripts which define and configure instances of resources.</span></span>
    <span data-ttu-id="770ff-113">Yapılandırma, DSC (ve yapılandırma tarafından çağrılan kaynaklar) çalışan işlem yalnızca "bunu kolaylaştırır", sistem yapılandırması tarafından düzenlendiği durumda var olduğu doğrulanıyor.</span><span class="sxs-lookup"><span data-stu-id="770ff-113">Upon running the configuration, DSC (and the resources being called by the configuration) will simply “make it so”, ensuring that the system exists in the state laid out by the configuration.</span></span> 
    <span data-ttu-id="770ff-114">DSC yapılandırmaları olan de ıdempotent: yerel Configuration Manager (LCM'yi) makineleri, ne olursa olsun yapılandırma durumu olarak yapılandırıldığından emin olmak devam edecek bildirir.</span><span class="sxs-lookup"><span data-stu-id="770ff-114">DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.</span></span>
- <span data-ttu-id="770ff-115">[Kaynakları](resources.md) "bunu make" DSC parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="770ff-115">[Resources](resources.md) are the "make it so" part of DSC.</span></span> <span data-ttu-id="770ff-116">Put ve yapılandırmasının hedef belirtilen durumda tutun kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="770ff-116">They contain the code that put and keep the target of a configuration in the specified state.</span></span> 
    <span data-ttu-id="770ff-117">Kaynaklar PowerShell modülleri bulunan ve genel olarak bir dosya veya bir Windows işlemini veya bir IIS sunucusu veya Azure'da çalışan VM olarak belirli bir şey modellemek için yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="770ff-117">Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.</span></span>
- <span data-ttu-id="770ff-118">[Yerel Configuration Manager (LCM'yi)](metaConfig.md) DSC kolaylaştıran kaynakları ve yapılandırmaları arasındaki etkileşimi altyapısıdır.</span><span class="sxs-lookup"><span data-stu-id="770ff-118">The [Local Configuration Manager (LCM)](metaConfig.md) is the engine by which DSC facilitates the interaction between resources and configurations.</span></span> 
    <span data-ttu-id="770ff-119">LCM'yi yapılandırması tarafından tanımlanan durumu korunduğundan emin olmak için kaynaklar tarafından uygulanan akış denetimi kullanarak sistem düzenli aralıklarla yoklar.</span><span class="sxs-lookup"><span data-stu-id="770ff-119">The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained.</span></span> 
    <span data-ttu-id="770ff-120">Sistem durumu dışında olduğunda LCM'yi kodu "bunu yapılandırmasına göre yapmak için" kaynaklarında çağrılar.</span><span class="sxs-lookup"><span data-stu-id="770ff-120">If the system is out of state, the LCM makes calls to the code in resources to “make it so” according to the configuration.</span></span> 

## <a name="see-also"></a><span data-ttu-id="770ff-121">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="770ff-121">See Also</span></span>

- [<span data-ttu-id="770ff-122">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="770ff-122">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="770ff-123">DSC kaynakları</span><span class="sxs-lookup"><span data-stu-id="770ff-123">DSC Resources</span></span>](resources.md)
- [<span data-ttu-id="770ff-124">Yerel Yapılandırma Yöneticisi'ni yapılandırma</span><span class="sxs-lookup"><span data-stu-id="770ff-124">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

