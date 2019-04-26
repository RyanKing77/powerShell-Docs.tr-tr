---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: e2c9233734a6ede04e8ec2bbad05950cbb31cbba
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057522"
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="bcab5-102">Sürüm aralıklarını (1.\* vb.) bildirme için modüller desteği</span><span class="sxs-lookup"><span data-stu-id="bcab5-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="bcab5-103">Birlikte **- MinimumVersion**, **- MaximumVersion** artık belirli bir aralıkta get/içeri aktarma modülü kullanıcıya izin verir.</span><span class="sxs-lookup"><span data-stu-id="bcab5-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="bcab5-104">Parametresini de destekler **.** \*.</span><span class="sxs-lookup"><span data-stu-id="bcab5-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="bcab5-105">Aşağıdaki örnek, nasıl çalıştığını gösterir:</span><span class="sxs-lookup"><span data-stu-id="bcab5-105">The following example shows how it works:</span></span>

<span data-ttu-id="bcab5-106">Artık, birleştirebilirsiniz **- MinimumVersion** ve **- MaximumVersion** belirli bir aralıkta modülü içeri aktarmak için:</span><span class="sxs-lookup"><span data-stu-id="bcab5-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

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
