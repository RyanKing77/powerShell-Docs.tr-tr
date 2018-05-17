---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a3ac215396206fba62bce303733429d60722ee6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>RefreshMode ve ConfigurationMode sıklıklarını birbiriyle katları olması gerekmez

DSC önceki sürümünde LCM'yi davranmanız `RefreshFrequencyMins` ve `ConfigurationModeFrequencyMins` birbiriyle katları olarak. WMF 5.0 RTM ile bu özelliklerin her biri bağımsız işlenir.

Daha fazla bilgi için bkz: [yerel Configuration Manager Yapılandırma](https://msdn.microsoft.com/powershell/dsc/metaconfig).
