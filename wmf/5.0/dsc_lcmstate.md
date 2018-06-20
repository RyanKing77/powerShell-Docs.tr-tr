---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219870"
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="5f4e3-102">LCM'yi durumu hakkında ayrıntılı bilgi</span><span class="sxs-lookup"><span data-stu-id="5f4e3-102">Detailed information about LCM state</span></span>

<span data-ttu-id="5f4e3-103">LCM'yi durumu ayrıntılarını gösterme biz geliştirmeler yapıldı.</span><span class="sxs-lookup"><span data-stu-id="5f4e3-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="5f4e3-104">Get-DscLocalConfigurationManager tarafından döndürülen LCMState şimdi aşağıdaki değerleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="5f4e3-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="5f4e3-105">**Boşta**</span><span class="sxs-lookup"><span data-stu-id="5f4e3-105">**Idle**</span></span>
* <span data-ttu-id="5f4e3-106">**Meşgul**</span><span class="sxs-lookup"><span data-stu-id="5f4e3-106">**Busy**</span></span>
* <span data-ttu-id="5f4e3-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="5f4e3-107">**PendingReboot**</span></span>
* <span data-ttu-id="5f4e3-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="5f4e3-108">**PendingConfiguration**</span></span>

<span data-ttu-id="5f4e3-109">Durumu hakkında daha fazla bilgi içeren bir LCMStateDetail özelliği de ekledik.</span><span class="sxs-lookup"><span data-stu-id="5f4e3-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
