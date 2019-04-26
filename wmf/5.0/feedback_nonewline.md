---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: e01f6ceea361f5a9b3de645346d0652986b6267d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057240"
---
# <a name="nonewline-parameter"></a><span data-ttu-id="cd7f7-102">NoNewLine parametresi</span><span class="sxs-lookup"><span data-stu-id="cd7f7-102">NoNewLine parameter</span></span>
<span data-ttu-id="cd7f7-103">**Dosya Dışarı**, **içerik ekleyin**, ve **Set-Content** artık yeni bir sahip **– NoNewline** anahtarı yalnızca yeni bir satır sonraki çıktı atlar.</span><span class="sxs-lookup"><span data-stu-id="cd7f7-103">**Out-File**, **Add-Content**, and **Set-Content** now have a new **–NoNewline** switch which simply omits a new line after the output.</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
<span data-ttu-id="cd7f7-104">Olmadan **– NoNewline** belirtilen her parça ayrı bir satırda olacaktır:</span><span class="sxs-lookup"><span data-stu-id="cd7f7-104">Without **–NoNewline** specified, each fragment would be on a separate line:</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```
