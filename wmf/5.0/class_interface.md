---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4b593e9a1eca43ee7ad85fc921ae3c1d62722db9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687863"
---
# <a name="declare-implemented-interface"></a>Uygulanan Arabirimi Bildirme

Belirtilen hiçbir temel türü varsa temel türleri bir iki nokta üst üste (:) hemen sonra veya uygulanan arabirimleri bildirebilirsiniz. Tüm tür adları virgül kullanarak ayırın. Çok benzer C# söz dizimi.

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
