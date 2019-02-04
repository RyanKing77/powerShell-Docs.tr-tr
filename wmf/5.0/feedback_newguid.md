---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685112"
---
# <a name="new-guid"></a>New-Guid
Genellikle komut dosyası (veya belki de bir DSC kaynağı yazma) benzersiz bir tanımlayıcı gerek vardır. GUID'ler işe ve .NET Framework Guid sınıfı için bir çağrı kolaydır ancak bir cmdlet sahip bu .NET Framework sınıf ile tanıdık olmayan son kullanıcılar için daha bulunabilir hale getirir:

PS C:\\&gt; New-Guid

GUID

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
