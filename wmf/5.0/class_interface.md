---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 116f79a95126d0a1c579a95ec99eb5d8b75cc1e0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225496"
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="4738d-102">Uygulanan Arabirimi Bildirme</span><span class="sxs-lookup"><span data-stu-id="4738d-102">Declare Implemented Interface</span></span>

<span data-ttu-id="4738d-103">Belirtilen temel tür ise hemen sonra iki nokta üst üste (:) veya temel türleri, uygulanan arabirimler bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4738d-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="4738d-104">Tüm tür adları virgül kullanarak ayırın.</span><span class="sxs-lookup"><span data-stu-id="4738d-104">Separate all type names by using commas.</span></span> <span data-ttu-id="4738d-105">C# sözdizimine çok benzer.</span><span class="sxs-lookup"><span data-stu-id="4738d-105">It’s very similar to C# syntax.</span></span>

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
