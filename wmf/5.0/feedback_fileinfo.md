---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 63c3b8237a9883b147380dfe9cb173107cea9aa9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225649"
---
# <a name="updates-to-fileinfo-object"></a>FileInfo nesnesi güncelleştirmeleri
Dosya sürümü bilgilerini, özellikle dosya burada oluşturulmuştur durumlarda yanıltıcı. Bu sürüm WMF 5.0 yeni ekler **FileVersionRaw** ve **ProductVersionRaw** komut nesnelere FileInfo özellikleri. (PowerShell işlem Kimliğini $pid olduğunu varsayarak) powershell.exe için görüntülendiği gibi özellikleri şunlardır:

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
