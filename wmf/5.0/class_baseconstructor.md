---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 1fd6d80d6b7effb4bd98c1594d64e531c4e5c9b5
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/27/2017
---
# <a name="call-base-class-constructor"></a>Taban sınıfı oluşturucusu çağırın

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

