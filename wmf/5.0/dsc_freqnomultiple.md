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
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>RefreshMode ve ConfigurationMode sıklıklarını birbiriyle katları olması gerekmez

DSC önceki sürümünde LCM'yi davranmanız `RefreshFrequencyMins` ve `ConfigurationModeFrequencyMins` birbiriyle katları olarak. WMF 5.0 RTM ile bu özelliklerin her biri bağımsız işlenir. 

Daha fazla bilgi için bkz: [yerel Configuration Manager Yapılandırma](https://msdn.microsoft.com/powershell/dsc/metaconfig).

