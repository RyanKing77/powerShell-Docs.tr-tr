---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: f491e30859cbe6cbaa58f94389382ff231c52956
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Sürüm aralıkları (1.*, vb.) bildirme modülleri desteği
Birlikte **- MinimumVersion**, **- MaximumVersion** artık get/içeri aktarma modülü belirli aralık içinde kullanıcıya izin verir. Parametresini de destekler **.** \*. Aşağıdaki örnekte, nasıl çalıştığı gösterilmektedir:

Şimdi, birleştirebilirsiniz **- MinimumVersion** ve **- MaximumVersion** belirli aralık içinde modülü içeri aktarmak için:

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
