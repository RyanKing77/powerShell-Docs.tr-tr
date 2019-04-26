---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085805"
---
# <a name="detailed-information-about-lcm-state"></a>LCM durumu hakkında ayrıntılı bilgi

LCM durumu hakkında ayrıntıları gösterme içinde geliştirmeleri yaptık. Get-DscLocalConfigurationManager tarafından döndürülen LCMState artık aşağıdaki değerleri içerebilir:

* **Boşta**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

Durumu hakkında daha fazla bilgi içeren bir LCMStateDetail özelliği de ekledik.
