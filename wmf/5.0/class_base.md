---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 8b3ebd22e03bf9bdd5f26965137a1b1ce9f47c3e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058786"
---
# <a name="declare-base-class"></a>Temel Sınıf Bildirme
Bir Windows PowerShell sınıfı, başka bir Windows PowerShell sınıfı için bir temel tür olarak bildirebilirsiniz.

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

Temel sınıf olarak var olan .NET Framework türleri de kullanabilirsiniz:

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```
