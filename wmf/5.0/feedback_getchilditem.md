---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 62cccabd7c63c6ba928fc2bf8addd3d11483e90f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
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