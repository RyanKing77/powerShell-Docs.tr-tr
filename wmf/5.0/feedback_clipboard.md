---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: d34a267bae7e48afe4442256d7f112da3a97eb7d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
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