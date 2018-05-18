---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a3ac215396206fba62bce303733429d60722ee6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="8b4af-102">RefreshMode ve ConfigurationMode sıklıklarını birbiriyle katları olması gerekmez</span><span class="sxs-lookup"><span data-stu-id="8b4af-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="8b4af-103">DSC önceki sürümünde LCM'yi davranmanız `RefreshFrequencyMins` ve `ConfigurationModeFrequencyMins` birbiriyle katları olarak.</span><span class="sxs-lookup"><span data-stu-id="8b4af-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="8b4af-104">WMF 5.0 RTM ile bu özelliklerin her biri bağımsız işlenir.</span><span class="sxs-lookup"><span data-stu-id="8b4af-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="8b4af-105">Daha fazla bilgi için bkz: [yerel Configuration Manager Yapılandırma](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="8b4af-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>
