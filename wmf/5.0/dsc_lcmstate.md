---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085805"
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="02184-102">LCM durumu hakkında ayrıntılı bilgi</span><span class="sxs-lookup"><span data-stu-id="02184-102">Detailed information about LCM state</span></span>

<span data-ttu-id="02184-103">LCM durumu hakkında ayrıntıları gösterme içinde geliştirmeleri yaptık.</span><span class="sxs-lookup"><span data-stu-id="02184-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="02184-104">Get-DscLocalConfigurationManager tarafından döndürülen LCMState artık aşağıdaki değerleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="02184-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="02184-105">**Boşta**</span><span class="sxs-lookup"><span data-stu-id="02184-105">**Idle**</span></span>
* <span data-ttu-id="02184-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="02184-106">**Busy**</span></span>
* <span data-ttu-id="02184-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="02184-107">**PendingReboot**</span></span>
* <span data-ttu-id="02184-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="02184-108">**PendingConfiguration**</span></span>

<span data-ttu-id="02184-109">Durumu hakkında daha fazla bilgi içeren bir LCMStateDetail özelliği de ekledik.</span><span class="sxs-lookup"><span data-stu-id="02184-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
