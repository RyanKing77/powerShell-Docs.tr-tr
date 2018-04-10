---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: eeafdd8d7a50e0bfc5ebd0ca8e9852c3d7405bf0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="call-base-class-method"></a>Temel Sınıf Yöntemini Çağırma

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