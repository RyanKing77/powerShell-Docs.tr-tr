---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4b593e9a1eca43ee7ad85fc921ae3c1d62722db9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085873"
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="89cd7-102">Uygulanan Arabirimi Bildirme</span><span class="sxs-lookup"><span data-stu-id="89cd7-102">Declare Implemented Interface</span></span>

<span data-ttu-id="89cd7-103">Belirtilen hiçbir temel türü varsa temel türleri bir iki nokta üst üste (:) hemen sonra veya uygulanan arabirimleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89cd7-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="89cd7-104">Tüm tür adları virgül kullanarak ayırın.</span><span class="sxs-lookup"><span data-stu-id="89cd7-104">Separate all type names by using commas.</span></span> <span data-ttu-id="89cd7-105">Çok benzer C# söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="89cd7-105">It’s very similar to C# syntax.</span></span>

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
