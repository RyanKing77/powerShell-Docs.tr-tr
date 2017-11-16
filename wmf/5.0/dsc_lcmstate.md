---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 4fc146f84588d368ac3eb819e3acb4cb8c5d8793
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="d2570-102">LCM'yi durumu hakkında ayrıntılı bilgi</span><span class="sxs-lookup"><span data-stu-id="d2570-102">Detailed information about LCM state</span></span>

<span data-ttu-id="d2570-103">LCM'yi durumu ayrıntılarını gösterme biz geliştirmeler yapıldı.</span><span class="sxs-lookup"><span data-stu-id="d2570-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="d2570-104">Get-DscLocalConfigurationManager tarafından döndürülen LCMState şimdi aşağıdaki değerleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="d2570-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="d2570-105">**Boşta**</span><span class="sxs-lookup"><span data-stu-id="d2570-105">**Idle**</span></span>
* <span data-ttu-id="d2570-106">**Meşgul**</span><span class="sxs-lookup"><span data-stu-id="d2570-106">**Busy**</span></span>
* <span data-ttu-id="d2570-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="d2570-107">**PendingReboot**</span></span>
* <span data-ttu-id="d2570-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="d2570-108">**PendingConfiguration**</span></span>

<span data-ttu-id="d2570-109">Durumu hakkında daha fazla bilgi içeren bir LCMStateDetail özelliği de ekledik.</span><span class="sxs-lookup"><span data-stu-id="d2570-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>

