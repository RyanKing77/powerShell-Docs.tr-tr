---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: e6b54519d878ab572662075709beb4cf4454b0c6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188066"
---
# <a name="clipboard-cmdlets"></a><span data-ttu-id="104c7-102">Pano cmdlet’leri</span><span class="sxs-lookup"><span data-stu-id="104c7-102">Clipboard cmdlets</span></span>
<span data-ttu-id="104c7-103">**Get-Pano** ve **kümesi Pano** içerik için ve bir Windows PowerShell oturumundan aktarımı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="104c7-103">**Get-Clipboard** and **Set-Clipboard** make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="104c7-104">Örneğin, üç dosya panoya kopyalamak için Windows Gezgini'ni kullanın (onları seçerek ve tuşlarına basarak `ctrl-c`, örneğin), daha sonra kolayca Pano içeriğini dosyalar listesi olarak erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="104c7-104">For example, if you use Windows Explorer to copy three files to the clipboard (by selecting them and pressing `ctrl-c`, for example), you can then easily access the contents of the clipboard as a list of files:</span></span>

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


<span data-ttu-id="104c7-105">Pano cmdlet'leri görüntüleri, ses dosyaları, dosya listelerinin ve metin destekler.</span><span class="sxs-lookup"><span data-stu-id="104c7-105">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>
