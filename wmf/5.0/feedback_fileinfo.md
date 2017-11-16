---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 587f3f592f4aab53c95bbc6d37ea37d7f2364aec
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="updates-to-fileinfo-object"></a>FileInfo nesne güncelleştirmeleri
Dosya sürümü bilgilerini, özellikle dosya burada oluşturulmuştur durumlarda yanıltıcı. Bu sürüm WMF 5.0 yeni ekler **FileVersionRaw** ve **ProductVersionRaw** komut nesnelere FileInfo özellikleri. (PowerShell işlem Kimliğini $pid olduğunu varsayarak) powershell.exe için görüntülendiği gibi özellikleri şunlardır:

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117

