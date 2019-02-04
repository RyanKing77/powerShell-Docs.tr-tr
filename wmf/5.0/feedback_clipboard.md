---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: d5ec95abb1d3160afc4179cff991cb5ef72d85fe
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685924"
---
# <a name="clipboard-cmdlets"></a><span data-ttu-id="94547-102">Pano cmdlet’leri</span><span class="sxs-lookup"><span data-stu-id="94547-102">Clipboard cmdlets</span></span>
<span data-ttu-id="94547-103">**Get-Pano** ve **Set-Pano** için ve bir Windows PowerShell oturumundan içerik aktarımı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="94547-103">**Get-Clipboard** and **Set-Clipboard** make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="94547-104">Örneğin, üç dosyayı panoya kopyalamak için Windows Explorer kullanıyorsanız (seçip tuşuna basarak `ctrl-c`, örneğin), Pano içeriğini kolayca dosyalar listesi olarak erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="94547-104">For example, if you use Windows Explorer to copy three files to the clipboard (by selecting them and pressing `ctrl-c`, for example), you can then easily access the contents of the clipboard as a list of files:</span></span>

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


<span data-ttu-id="94547-105">Pano cmdlet'leri görüntüleri, ses dosyaları, dosya listeler ve metin destekler.</span><span class="sxs-lookup"><span data-stu-id="94547-105">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>
