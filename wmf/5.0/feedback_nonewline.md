---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 4d32ced8e75042f494477408424b97be8958854e
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/27/2017
---
# <a name="nonewline-parameter"></a><span data-ttu-id="598ba-102">NoNewLine parametresi</span><span class="sxs-lookup"><span data-stu-id="598ba-102">NoNewLine parameter</span></span>
<span data-ttu-id="598ba-103">**Out-File**, **Ekle-Content**, ve **Set-Content** artık yeni bir sahip **– NoNewline** yalnızca yeni bir satır çıktıdan sonra atlar anahtarı.</span><span class="sxs-lookup"><span data-stu-id="598ba-103">**Out-File**, **Add-Content**, and **Set-Content** now have a new **–NoNewline** switch which simply omits a new line after the output.</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
<span data-ttu-id="598ba-104">Olmadan **– NoNewline** belirtilen her parça ayrı bir satırda olacaktır:</span><span class="sxs-lookup"><span data-stu-id="598ba-104">Without **–NoNewline** specified, each fragment would be on a separate line:</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```

