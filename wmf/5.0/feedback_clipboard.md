---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 8d5f8cc8c85d584b195483e464e878857629a78e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
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

