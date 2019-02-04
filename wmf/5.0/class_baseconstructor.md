---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 424e0b7a4d62fc35e5040a7e425950e887021d7e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683782"
---
# <a name="call-base-class-constructor"></a><span data-ttu-id="723e9-102">Temel Sınıf Oluşturucusunu Çağırma</span><span class="sxs-lookup"><span data-stu-id="723e9-102">Call Base Class Constructor</span></span>

<span data-ttu-id="723e9-103">Bir temel sınıf oluşturucusunu bir alt sınıfı için anahtar sözcüğünü kullanın **temel**:</span><span class="sxs-lookup"><span data-stu-id="723e9-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

<span data-ttu-id="723e9-104">Bir temel sınıf (parametre) varsayılan bir oluşturucusu varsa, bir açık oluşturucu çağrısı atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="723e9-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```
