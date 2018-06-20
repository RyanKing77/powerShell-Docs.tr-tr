---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: d7aec1a2ba8964e877ddd7406609fe135b1eb462
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219751"
---
# <a name="call-base-class-method"></a><span data-ttu-id="1ceda-102">Temel Sınıf Yöntemini Çağırma</span><span class="sxs-lookup"><span data-stu-id="1ceda-102">Call Base Class Method</span></span>

<span data-ttu-id="1ceda-103">Alt sınıfların varolan yöntemleri geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ceda-103">You can override existing methods in subclasses.</span></span> <span data-ttu-id="1ceda-104">Bunu yapmak için aynı ad ve imza kullanarak yöntemleri bildirin:</span><span class="sxs-lookup"><span data-stu-id="1ceda-104">To do this, declare methods by using the same name and signature:</span></span>

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

<span data-ttu-id="1ceda-105">Taban sınıf yöntemlerini geçersiz kılınan uygulamaları çağırmak için temel sınıf cast ([baseClass] $Bu) çağırma üzerinde:</span><span class="sxs-lookup"><span data-stu-id="1ceda-105">To call base class methods from overridden implementations, cast to the base class ([baseClass]$this) on invocation:</span></span>

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

<span data-ttu-id="1ceda-106">Tüm PowerShell sanal yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="1ceda-106">All PowerShell methods are virtual.</span></span> <span data-ttu-id="1ceda-107">Bir geçersiz kılma için yaptığınız gibi aynı sözdizimini kullanarak bir alt kümesi sanal olmayan .NET yöntemlerinde gizleyebilirsiniz: yalnızca aynı ad ve imza yöntemleriyle bildirin.</span><span class="sxs-lookup"><span data-stu-id="1ceda-107">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: just declare methods with same name and signature.</span></span>

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
