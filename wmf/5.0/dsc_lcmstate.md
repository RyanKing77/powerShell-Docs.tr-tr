---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: baa35e9acd24d6f6155acf617a0d2c2210742af7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="655d8-102">LCM'yi durumu hakkında ayrıntılı bilgi</span><span class="sxs-lookup"><span data-stu-id="655d8-102">Detailed information about LCM state</span></span>

<span data-ttu-id="655d8-103">LCM'yi durumu ayrıntılarını gösterme biz geliştirmeler yapıldı.</span><span class="sxs-lookup"><span data-stu-id="655d8-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="655d8-104">Get-DscLocalConfigurationManager tarafından döndürülen LCMState şimdi aşağıdaki değerleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="655d8-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="655d8-105">**Boşta**</span><span class="sxs-lookup"><span data-stu-id="655d8-105">**Idle**</span></span>
* <span data-ttu-id="655d8-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="655d8-106">**Busy**</span></span>
* <span data-ttu-id="655d8-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="655d8-107">**PendingReboot**</span></span>
* <span data-ttu-id="655d8-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="655d8-108">**PendingConfiguration**</span></span>

<span data-ttu-id="655d8-109">Durumu hakkında daha fazla bilgi içeren bir LCMStateDetail özelliği de ekledik.</span><span class="sxs-lookup"><span data-stu-id="655d8-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>