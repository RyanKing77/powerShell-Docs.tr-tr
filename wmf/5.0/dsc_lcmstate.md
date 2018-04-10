---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: baa35e9acd24d6f6155acf617a0d2c2210742af7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="detailed-information-about-lcm-state"></a>LCM'yi durumu hakkında ayrıntılı bilgi

LCM'yi durumu ayrıntılarını gösterme biz geliştirmeler yapıldı. Get-DscLocalConfigurationManager tarafından döndürülen LCMState şimdi aşağıdaki değerleri içerebilir:

* **Boşta**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

Durumu hakkında daha fazla bilgi içeren bir LCMStateDetail özelliği de ekledik.