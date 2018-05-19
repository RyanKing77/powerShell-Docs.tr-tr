---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 116f79a95126d0a1c579a95ec99eb5d8b75cc1e0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
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
