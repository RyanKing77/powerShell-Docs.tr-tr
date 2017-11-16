---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 7817769c3fc060a51c833b7469f7b556b9b40e87
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/27/2017
---
# <a name="call-base-class-method"></a>Taban sınıf yöntemini çağırın

Alt sınıfların varolan yöntemleri geçersiz kılabilirsiniz. Bunu yapmak için aynı ad ve imza kullanarak yöntemleri bildirin:

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

Taban sınıf yöntemlerini geçersiz kılınan uygulamaları çağırmak için temel sınıf cast ([baseClass] $Bu) çağırma üzerinde:

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

Tüm PowerShell sanal yöntemleridir. Bir geçersiz kılma için yaptığınız gibi aynı sözdizimini kullanarak bir alt kümesi sanal olmayan .NET yöntemlerinde gizleyebilirsiniz: yalnızca aynı ad ve imza yöntemleriyle bildirin.

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

