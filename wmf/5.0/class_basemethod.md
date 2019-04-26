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
# <a name="call-base-class-method"></a><span data-ttu-id="4ed60-102">Temel Sınıf Yöntemini Çağırma</span><span class="sxs-lookup"><span data-stu-id="4ed60-102">Call Base Class Method</span></span>

<span data-ttu-id="4ed60-103">Alt sınıfların mevcut yöntemleri geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ed60-103">You can override existing methods in subclasses.</span></span> <span data-ttu-id="4ed60-104">Bunu yapmak için aynı ada ve imzaya kullanarak yöntemleri bildirin:</span><span class="sxs-lookup"><span data-stu-id="4ed60-104">To do this, declare methods by using the same name and signature:</span></span>

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

<span data-ttu-id="4ed60-105">Geçersiz kılınan uygulamaları taban sınıf yöntemlerini çağırmak için temel sınıf için atama ([baseClass] $Bu) çağırma üzerinde:</span><span class="sxs-lookup"><span data-stu-id="4ed60-105">To call base class methods from overridden implementations, cast to the base class ([baseClass]$this) on invocation:</span></span>

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

<span data-ttu-id="4ed60-106">Tüm PowerShell yöntemler sanaldır.</span><span class="sxs-lookup"><span data-stu-id="4ed60-106">All PowerShell methods are virtual.</span></span> <span data-ttu-id="4ed60-107">Sanal olmayan .NET yöntemleri öğesinin alt sınıfı için bir geçersiz kılma olarak aynı sözdizimini kullanarak gizleyebilirsiniz: yalnızca aynı ada ve imzaya sahip bir yöntem bildirin.</span><span class="sxs-lookup"><span data-stu-id="4ed60-107">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: just declare methods with same name and signature.</span></span>

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
