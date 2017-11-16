---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 968e78beb8df77588a08a9ce8732e4abcadde4d0
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/27/2017
---
# <a name="declare-implemented-interface"></a>Uygulanan arabirimi bildirme

Belirtilen temel tür ise hemen sonra iki nokta üst üste (:) veya temel türleri, uygulanan arabirimler bildirebilirsiniz. Tüm tür adları virgül kullanarak ayırın. C# sözdizimine çok benzer.

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

