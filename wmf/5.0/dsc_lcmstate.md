---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 4fc146f84588d368ac3eb819e3acb4cb8c5d8793
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="detailed-information-about-lcm-state"></a>LCM'yi durumu hakkında ayrıntılı bilgi

LCM'yi durumu ayrıntılarını gösterme biz geliştirmeler yapıldı. Get-DscLocalConfigurationManager tarafından döndürülen LCMState şimdi aşağıdaki değerleri içerebilir:

* **Boşta**
* **Meşgul**
* **PendingReboot**
* **PendingConfiguration**

Durumu hakkında daha fazla bilgi içeren bir LCMStateDetail özelliği de ekledik.

