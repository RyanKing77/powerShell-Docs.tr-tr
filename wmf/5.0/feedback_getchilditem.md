---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: d9f1ca10c948b06b234e17f688b8f899ed41c5d6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="get-childitem-has--depth-parameter"></a>-Derinliği parametresi Get-Childıtem var
**Get-Childıtem** artık bir **– derinliği** parametresi ile kullandığınız **– Recurse** özyineleme sınırlamak için:

PS C:\\kullanıcılar\\slee\\indirmeleri\\örnek&gt; Get-Childıtem-Recurse - derinliği 0

Dizin: C:\\kullanıcılar\\slee\\indirmeleri\\örneği

Mod LastWriteTime uzunluğu adı

---- ------------- ------ ----

d---4/14/2015 5:36 PM Depth0

-a---4/14/2015 tarihinde 13: 19'te 0 Dosya1.ref

-a---4/14/2015 tarihinde 13: 19'te 0 File2.txt

-a---4/14/2015 tarihinde 13: 19'te 0 File3.txt

PS C:\\kullanıcılar\\slee\\indirmeleri\\örnek&gt; Get-Childıtem-Recurse - derinliği 1

Dizin: C:\\kullanıcılar\\slee\\indirmeleri\\örneği

Mod LastWriteTime uzunluğu adı

---- ------------- ------ ----

d---4/14/2015 5:36 PM Depth0

-a---4/14/2015 tarihinde 13: 19'te 0 Dosya1.ref

-a---4/14/2015 tarihinde 13: 19'te 0 File2.txt

-a---4/14/2015 tarihinde 13: 19'te 0 File3.txt

Dizin: C:\\kullanıcılar\\slee\\indirmeleri\\örnek\\Depth0

Mod LastWriteTime uzunluğu adı

---- ------------- ------ ----

d---4/14/2015 5:33 PM Depth1
