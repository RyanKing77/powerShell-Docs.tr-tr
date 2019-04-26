---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: d5ec95abb1d3160afc4179cff991cb5ef72d85fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057307"
---
# <a name="clipboard-cmdlets"></a>Pano cmdlet’leri
**Get-Pano** ve **Set-Pano** için ve bir Windows PowerShell oturumundan içerik aktarımı kolaylaştırır. Örneğin, üç dosyayı panoya kopyalamak için Windows Explorer kullanıyorsanız (seçip tuşuna basarak `ctrl-c`, örneğin), Pano içeriğini kolayca dosyalar listesi olarak erişebilirsiniz:

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


Pano cmdlet'leri görüntüleri, ses dosyaları, dosya listeler ve metin destekler.
