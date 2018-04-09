---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 12c47d3583274e58edbd2171fef50c779aac9fce
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="df41e-102">Sürüm aralıkları (1.\*, vb.) bildirme modülleri desteği</span><span class="sxs-lookup"><span data-stu-id="df41e-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="df41e-103">Birlikte **- MinimumVersion**, **- MaximumVersion** artık get/içeri aktarma modülü belirli aralık içinde kullanıcıya izin verir.</span><span class="sxs-lookup"><span data-stu-id="df41e-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="df41e-104">Parametresini de destekler **.** \*.</span><span class="sxs-lookup"><span data-stu-id="df41e-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="df41e-105">Aşağıdaki örnekte, nasıl çalıştığı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="df41e-105">The following example shows how it works:</span></span>

```powershell
Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:

PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```