---
ms.date: 08/27/2018
keywords: PowerShell cmdlet'i
title: Sistem Yönetimi için örnek betikler
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
ms.openlocfilehash: 3c771c9568f40ec3a4bb7061c122f33bba7d0382
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684188"
---
# <a name="sample-scripts-for-system-administration"></a><span data-ttu-id="0cb4a-103">Sistem Yönetimi için örnek betikler</span><span class="sxs-lookup"><span data-stu-id="0cb4a-103">Sample scripts for system administration</span></span>

<span data-ttu-id="0cb4a-104">PowerShell temel amacı kolay yönetim denetimi sistemleri, üzerinden etkileşimli olarak veya betikten sunuyor.</span><span class="sxs-lookup"><span data-stu-id="0cb4a-104">The fundamental goal of PowerShell is providing easy administrative control over systems, either interactively or from script.</span></span> <span data-ttu-id="0cb4a-105">Bu örnekleri koleksiyonunu sistemleri PowerShell ile yönetme senaryoları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0cb4a-105">This collection of examples walks through scenarios for administering systems with PowerShell.</span></span> <span data-ttu-id="0cb4a-106">Örnek betikler veya işlevler olarak daha sonra kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0cb4a-106">The examples can be used from scripts or as functions later.</span></span>

<span data-ttu-id="0cb4a-107">Bu örnekler, cmdlet'leri ve dış araçları bir karışımını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0cb4a-107">These examples use a mix of cmdlets and external tools.</span></span> <span data-ttu-id="0cb4a-108">Dış araçların kullanımını PowerShell uzun vadeli tasarım amacı bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="0cb4a-108">Use of external tools is part of the long-term design intent of PowerShell.</span></span> <span data-ttu-id="0cb4a-109">Kullanıcılar sistem büyüdükçe bile sürekli olarak nerede kullanılabilir takımları değil her şeyi durumları karşılaşıyor. Bunlar gerekir.</span><span class="sxs-lookup"><span data-stu-id="0cb4a-109">Even as the system grows, users continually encounter situations where the available toolsets do not do everything they need.</span></span> <span data-ttu-id="0cb4a-110">Cmdlet uygulamaları üzerinde yalnızca foster bağımlılık yerine, PowerShell, tüm kullanılabilir araçları tümleştirme çözümleri destekler.</span><span class="sxs-lookup"><span data-stu-id="0cb4a-110">Rather than foster dependency solely on cmdlet implementations, PowerShell support integrating solutions all available tools.</span></span>