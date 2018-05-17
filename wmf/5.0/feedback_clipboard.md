---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: e6b54519d878ab572662075709beb4cf4454b0c6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="clipboard-cmdlets"></a>Pano cmdlet’leri
**Get-Pano** ve **kümesi Pano** içerik için ve bir Windows PowerShell oturumundan aktarımı kolaylaştırır. Örneğin, üç dosya panoya kopyalamak için Windows Gezgini'ni kullanın (onları seçerek ve tuşlarına basarak `ctrl-c`, örneğin), daha sonra kolayca Pano içeriğini dosyalar listesi olarak erişebilirsiniz:

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


Pano cmdlet'leri görüntüleri, ses dosyaları, dosya listelerinin ve metin destekler.
