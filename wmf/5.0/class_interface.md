---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 2c007321789ae22b4a2e048d2d64162b065f9a75
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="declare-implemented-interface"></a>Uygulanan Arabirimi Bildirme

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