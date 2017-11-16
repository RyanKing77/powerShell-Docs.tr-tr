---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 4185d9395f2f3e5ba1c8daa0c365cb2bf322936b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
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

