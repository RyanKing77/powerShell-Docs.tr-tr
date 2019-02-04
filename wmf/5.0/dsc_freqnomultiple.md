---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 23a5c8832f7c2888880a1ee846d75feaa95ebe47
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688206"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>RefreshMode ve ConfigurationMode frekansları birbirinin katları olmanız gerekmez

DSC önceki sürümünde LCM ele almanız `RefreshFrequencyMins` ve `ConfigurationModeFrequencyMins` birbirine katları olarak. WMF 5.0 RTM'ye şu özellikleri birbirinden bağımsız işlenir.

Daha fazla bilgi için [yerel Configuration Manager Yapılandırma](https://msdn.microsoft.com/powershell/dsc/metaconfig).
