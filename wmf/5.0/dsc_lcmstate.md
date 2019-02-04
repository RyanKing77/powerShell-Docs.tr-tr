---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685749"
---
# <a name="detailed-information-about-lcm-state"></a>LCM durumu hakkında ayrıntılı bilgi

LCM durumu hakkında ayrıntıları gösterme içinde geliştirmeleri yaptık. Get-DscLocalConfigurationManager tarafından döndürülen LCMState artık aşağıdaki değerleri içerebilir:

* **Boşta**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

Durumu hakkında daha fazla bilgi içeren bir LCMStateDetail özelliği de ekledik.
