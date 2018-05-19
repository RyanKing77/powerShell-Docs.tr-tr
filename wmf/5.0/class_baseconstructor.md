---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9486fdbaeca66c83551564c76ce47482f77c36b9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="call-base-class-constructor"></a>Temel Sınıf Oluşturucusunu Çağırma

Bir alt sınıfı bir temel sınıf oluşturucu çağrısı için anahtar kullanın **temel**:

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

Bir taban sınıf (parametre) varsayılan bir oluşturucu varsa, bir açık oluşturucu çağrısı atlayabilirsiniz:

```powershell
class C : B
{
    C([int]$c) {}
}
```
