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
# <a name="declare-implemented-interface"></a><span data-ttu-id="b7eea-102">Uygulanan arabirimi bildirme</span><span class="sxs-lookup"><span data-stu-id="b7eea-102">Declare Implemented Interface</span></span>

<span data-ttu-id="b7eea-103">Belirtilen temel tür ise hemen sonra iki nokta üst üste (:) veya temel türleri, uygulanan arabirimler bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7eea-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="b7eea-104">Tüm tür adları virgül kullanarak ayırın.</span><span class="sxs-lookup"><span data-stu-id="b7eea-104">Separate all type names by using commas.</span></span> <span data-ttu-id="b7eea-105">C# sözdizimine çok benzer.</span><span class="sxs-lookup"><span data-stu-id="b7eea-105">It’s very similar to C# syntax.</span></span>

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

