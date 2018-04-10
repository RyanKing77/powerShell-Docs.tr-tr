---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: e1faf71436c8ba0ae02a166ce06d03de9f66f094
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>RefreshMode ve ConfigurationMode sıklıklarını birbiriyle katları olması gerekmez

DSC önceki sürümünde LCM'yi davranmanız `RefreshFrequencyMins` ve `ConfigurationModeFrequencyMins` birbiriyle katları olarak. WMF 5.0 RTM ile bu özelliklerin her biri bağımsız işlenir.

Daha fazla bilgi için bkz: [yerel Configuration Manager Yapılandırma](https://msdn.microsoft.com/powershell/dsc/metaconfig).