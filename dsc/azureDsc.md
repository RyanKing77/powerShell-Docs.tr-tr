---
ms.date: 03/15/2018
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: Microsoft Azure’da DSC Kullanma
ms.openlocfilehash: 5b0d577e1fecdeac38c2c5f8e955a2d23b1eb707
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="9fb6d-103">Microsoft Azure’da DSC Kullanma</span><span class="sxs-lookup"><span data-stu-id="9fb6d-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="9fb6d-104">İstenen durum Yapılandırması'nı (DSC) Microsoft Azure desteklenir [Azure istenen durum yapılandırması uzantısı işleyici](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) ve aracılığıyla [Azure Otomasyonu DSC](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="9fb6d-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="9fb6d-105">Azure istenen durum yapılandırma uzantısı işleyicisi</span><span class="sxs-lookup"><span data-stu-id="9fb6d-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="9fb6d-106">Azure DSC uzantısı, Microsoft ile DSC yönetilmesi için Azure içinde barındırılan sanal makineleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fb6d-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span>
<span data-ttu-id="9fb6d-107">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="9fb6d-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="9fb6d-108">Azure istenen durum yapılandırma uzantısı işleyicisi</span><span class="sxs-lookup"><span data-stu-id="9fb6d-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview)
- [<span data-ttu-id="9fb6d-109">Windows VMSS ve Azure Resource Manager şablonları ile istenen durum yapılandırması</span><span class="sxs-lookup"><span data-stu-id="9fb6d-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-template)
- [<span data-ttu-id="9fb6d-110">Kimlik bilgileri Azure DSC uzantısı işleyicisine geçirme</span><span class="sxs-lookup"><span data-stu-id="9fb6d-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-credentials)
- [<span data-ttu-id="9fb6d-111">Azure istenen durum yapılandırması uzantısı geçmişi</span><span class="sxs-lookup"><span data-stu-id="9fb6d-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="9fb6d-112">Azure Otomasyonu DSC</span><span class="sxs-lookup"><span data-stu-id="9fb6d-112">Azure Automation DSC</span></span>

<span data-ttu-id="9fb6d-113">[Azure Otomasyon hizmetine](https://azure.microsoft.com/services/automation/) DSC yapılandırmaları, kaynakları ve Azure içinde yönetilen düğümlerden yönetmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fb6d-113">The [Azure Automation service](https://azure.microsoft.com/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="9fb6d-114">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="9fb6d-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="9fb6d-115">Azure Otomasyonu DSC</span><span class="sxs-lookup"><span data-stu-id="9fb6d-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="9fb6d-116">Azure Otomasyonu DSC ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="9fb6d-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="9fb6d-117">Azure Otomasyonu DSC tarafından Yönetim için hazırlama makineler</span><span class="sxs-lookup"><span data-stu-id="9fb6d-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)