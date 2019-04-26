---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: cc5d2d799c1292f68de5fb2360fcba220c2c010b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085309"
---
# <a name="get-childitem-has--depth-parameter"></a>Get-childıtem öğesinin-Depth parametresi var
**Get-Childıtem** artık bir **– derinliği** parametresi ile kullandığınız **– Recurse** özyineleme sınırlamak için:

PS: C:\\kullanıcılar\\slee\\indirir\\örnek&gt; Get-Childıtem-Recurse - derinliği 0

Dizini: C:\\kullanıcılar\\slee\\indirir\\örneği

Mod LastWriteTime uzunluğu adı

---- ------------- ------ ----

d---4/14/2015-17:36 Depth0

-a---14/4/2015 13: 19'te 0 Dosya1.ref

-a---14/4/2015 13: 19'te 0 File2.txt

-a---14/4/2015 13: 19'te 0 File3.txt

PS: C:\\kullanıcılar\\slee\\indirir\\örnek&gt; Get-Childıtem-Recurse - derinlik 1

Dizini: C:\\kullanıcılar\\slee\\indirir\\örneği

Mod LastWriteTime uzunluğu adı

---- ------------- ------ ----

d---4/14/2015-17:36 Depth0

-a---14/4/2015 13: 19'te 0 Dosya1.ref

-a---14/4/2015 13: 19'te 0 File2.txt

-a---14/4/2015 13: 19'te 0 File3.txt

Dizini: C:\\kullanıcılar\\slee\\indirir\\örnek\\Depth0

Mod LastWriteTime uzunluğu adı

---- ------------- ------ ----

d---4/14/2015-17:33 Depth1
