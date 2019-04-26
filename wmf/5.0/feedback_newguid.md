---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085340"
---
# <a name="new-guid"></a>New-Guid
Genellikle komut dosyası (veya belki de bir DSC kaynağı yazma) benzersiz bir tanımlayıcı gerek vardır. GUID'ler işe ve .NET Framework Guid sınıfı için bir çağrı kolaydır ancak bir cmdlet sahip bu .NET Framework sınıf ile tanıdık olmayan son kullanıcılar için daha bulunabilir hale getirir:

PS C:\\&gt; New-Guid

Guid

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
