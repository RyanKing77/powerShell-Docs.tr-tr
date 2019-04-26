---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 424e0b7a4d62fc35e5040a7e425950e887021d7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085890"
---
# <a name="call-base-class-constructor"></a>Temel Sınıf Oluşturucusunu Çağırma

Bir temel sınıf oluşturucusunu bir alt sınıfı için anahtar sözcüğünü kullanın **temel**:

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

Bir temel sınıf (parametre) varsayılan bir oluşturucusu varsa, bir açık oluşturucu çağrısı atlayabilirsiniz:

```powershell
class C : B
{
    C([int]$c) {}
}
```
