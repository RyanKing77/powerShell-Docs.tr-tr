---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 0e79127faf3f9bf6fe7d525db5bb946daf3b93e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058633"
---
# <a name="call-base-class-method"></a>Temel Sınıf Yöntemini Çağırma

Alt sınıfların mevcut yöntemleri geçersiz kılabilirsiniz. Bunu yapmak için aynı ada ve imzaya kullanarak yöntemleri bildirin:

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

Geçersiz kılınan uygulamaları taban sınıf yöntemlerini çağırmak için temel sınıf için atama ([baseClass] $Bu) çağırma üzerinde:

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

Tüm PowerShell yöntemler sanaldır. Sanal olmayan .NET yöntemleri öğesinin alt sınıfı için bir geçersiz kılma olarak aynı sözdizimini kullanarak gizleyebilirsiniz: yalnızca aynı ada ve imzaya sahip bir yöntem bildirin.

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```
