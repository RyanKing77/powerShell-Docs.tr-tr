---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 30055cff87159df98029e25409782e0fe2f0bae4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="1786f-102">RefreshMode ve ConfigurationMode sıklıklarını birbiriyle katları olması gerekmez</span><span class="sxs-lookup"><span data-stu-id="1786f-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="1786f-103">DSC önceki sürümünde LCM'yi davranmanız `RefreshFrequencyMins` ve `ConfigurationModeFrequencyMins` birbiriyle katları olarak.</span><span class="sxs-lookup"><span data-stu-id="1786f-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="1786f-104">WMF 5.0 RTM ile bu özelliklerin her biri bağımsız işlenir.</span><span class="sxs-lookup"><span data-stu-id="1786f-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span> 

<span data-ttu-id="1786f-105">Daha fazla bilgi için bkz: [yerel Configuration Manager Yapılandırma](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="1786f-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>

