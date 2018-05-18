---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 2d6a25908de746e296bef91e05c3d4e250aa77c9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="nonewline-parameter"></a><span data-ttu-id="1acc4-102">NoNewLine parametresi</span><span class="sxs-lookup"><span data-stu-id="1acc4-102">NoNewLine parameter</span></span>
<span data-ttu-id="1acc4-103">**Out-File**, **Ekle-Content**, ve **Set-Content** artık yeni bir sahip **– NoNewline** yalnızca yeni bir satır çıktıdan sonra atlar anahtarı.</span><span class="sxs-lookup"><span data-stu-id="1acc4-103">**Out-File**, **Add-Content**, and **Set-Content** now have a new **–NoNewline** switch which simply omits a new line after the output.</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
<span data-ttu-id="1acc4-104">Olmadan **– NoNewline** belirtilen her parça ayrı bir satırda olacaktır:</span><span class="sxs-lookup"><span data-stu-id="1acc4-104">Without **–NoNewline** specified, each fragment would be on a separate line:</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```
