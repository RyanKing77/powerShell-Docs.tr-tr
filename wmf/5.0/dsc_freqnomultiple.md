---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 23a5c8832f7c2888880a1ee846d75feaa95ebe47
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058412"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="1b65a-102">RefreshMode ve ConfigurationMode frekansları birbirinin katları olmanız gerekmez</span><span class="sxs-lookup"><span data-stu-id="1b65a-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="1b65a-103">DSC önceki sürümünde LCM ele almanız `RefreshFrequencyMins` ve `ConfigurationModeFrequencyMins` birbirine katları olarak.</span><span class="sxs-lookup"><span data-stu-id="1b65a-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="1b65a-104">WMF 5.0 RTM'ye şu özellikleri birbirinden bağımsız işlenir.</span><span class="sxs-lookup"><span data-stu-id="1b65a-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="1b65a-105">Daha fazla bilgi için [yerel Configuration Manager Yapılandırma](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="1b65a-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>
