---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: f491e30859cbe6cbaa58f94389382ff231c52956
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="1f5c0-102">Sürüm aralıkları (1.\*, vb.) bildirme modülleri desteği</span><span class="sxs-lookup"><span data-stu-id="1f5c0-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="1f5c0-103">Birlikte **- MinimumVersion**, **- MaximumVersion** artık get/içeri aktarma modülü belirli aralık içinde kullanıcıya izin verir.</span><span class="sxs-lookup"><span data-stu-id="1f5c0-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="1f5c0-104">Parametresini de destekler **.** \*.</span><span class="sxs-lookup"><span data-stu-id="1f5c0-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="1f5c0-105">Aşağıdaki örnekte, nasıl çalıştığı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1f5c0-105">The following example shows how it works:</span></span>

<span data-ttu-id="1f5c0-106">Şimdi, birleştirebilirsiniz **- MinimumVersion** ve **- MaximumVersion** belirli aralık içinde modülü içeri aktarmak için:</span><span class="sxs-lookup"><span data-stu-id="1f5c0-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

```powershell
PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```
