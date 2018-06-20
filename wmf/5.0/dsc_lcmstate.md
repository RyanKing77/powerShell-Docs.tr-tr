---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219870"
---
# <a name="detailed-information-about-lcm-state"></a>LCM'yi durumu hakkında ayrıntılı bilgi

LCM'yi durumu ayrıntılarını gösterme biz geliştirmeler yapıldı. Get-DscLocalConfigurationManager tarafından döndürülen LCMState şimdi aşağıdaki değerleri içerebilir:

* **Boşta**
* **Meşgul**
* **PendingReboot**
* **PendingConfiguration**

Durumu hakkında daha fazla bilgi içeren bir LCMStateDetail özelliği de ekledik.
