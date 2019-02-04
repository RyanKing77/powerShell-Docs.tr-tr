---
ms.date: 03/15/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: Microsoft Azure’da DSC Kullanma
ms.openlocfilehash: 54a317a415ff12c3d270897f414cba88716f0728
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684881"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="531de-103">Microsoft Azure’da DSC Kullanma</span><span class="sxs-lookup"><span data-stu-id="531de-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="531de-104">Desired State Configuration ' nı (DSC), Microsoft Azure içerisinde desteklendiği [Azure Desired State Configuration uzantısı işleyicisi](/azure/virtual-machines/extensions/dsc-overview) ve ile [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="531de-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="531de-105">Azure Desired State Configuration uzantısı işleyicisi</span><span class="sxs-lookup"><span data-stu-id="531de-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="531de-106">Azure DSC uzantısı DSC ile yönetilmek üzere Microsoft azure'da barındırılan sanal makineleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="531de-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span>
<span data-ttu-id="531de-107">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="531de-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="531de-108">Azure Desired State Configuration uzantısı işleyicisi</span><span class="sxs-lookup"><span data-stu-id="531de-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="531de-109">Windows VMSS ve Desired State Configuration ' Azure Resource Manager şablonları ile</span><span class="sxs-lookup"><span data-stu-id="531de-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="531de-110">Kimlik bilgileri Azure DSC uzantısı işleyicisine geçirme</span><span class="sxs-lookup"><span data-stu-id="531de-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="531de-111">Azure Desired State Configuration uzantısı geçmişi</span><span class="sxs-lookup"><span data-stu-id="531de-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="531de-112">Azure Otomasyonu DSC</span><span class="sxs-lookup"><span data-stu-id="531de-112">Azure Automation DSC</span></span>

<span data-ttu-id="531de-113">[Azure Otomasyonu hizmetine](https://azure.microsoft.com/en-us/services/automation/) DSC yapılandırmaları, kaynaklar ve Azure yönetilen düğümü yönetmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="531de-113">The [Azure Automation service](https://azure.microsoft.com/en-us/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="531de-114">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="531de-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="531de-115">Azure Otomasyonu DSC</span><span class="sxs-lookup"><span data-stu-id="531de-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="531de-116">Azure Otomasyonu DSC ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="531de-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="531de-117">Makineleri Azure Automation DSC tarafından Yönetim için hazırlama</span><span class="sxs-lookup"><span data-stu-id="531de-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)