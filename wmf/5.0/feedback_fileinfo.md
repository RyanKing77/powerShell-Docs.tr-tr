---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 6356902193fc6ec651b2f7e53f8885cb59f17542
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="updates-to-fileinfo-object"></a>FileInfo nesnesi güncelleştirmeleri
Dosya sürümü bilgilerini, özellikle dosya burada oluşturulmuştur durumlarda yanıltıcı. Bu sürüm WMF 5.0 yeni ekler **FileVersionRaw** ve **ProductVersionRaw** komut nesnelere FileInfo özellikleri. (PowerShell işlem Kimliğini $pid olduğunu varsayarak) powershell.exe için görüntülendiği gibi özellikleri şunlardır:

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117