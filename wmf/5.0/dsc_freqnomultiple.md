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
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>RefreshMode ve ConfigurationMode frekansları birbirinin katları olmanız gerekmez

DSC önceki sürümünde LCM ele almanız `RefreshFrequencyMins` ve `ConfigurationModeFrequencyMins` birbirine katları olarak. WMF 5.0 RTM'ye şu özellikleri birbirinden bağımsız işlenir.

Daha fazla bilgi için [yerel Configuration Manager Yapılandırma](https://msdn.microsoft.com/powershell/dsc/metaconfig).
