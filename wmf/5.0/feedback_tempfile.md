---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 90e0ab3579e1840598cc3050c27db0b73ba6f69d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="new-temporaryfile"></a><span data-ttu-id="6bee8-102">TemporaryFile yeni</span><span class="sxs-lookup"><span data-stu-id="6bee8-102">New-TemporaryFile</span></span>
<span data-ttu-id="6bee8-103">Bazen komut dosyalarınızı geçici bir dosya oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6bee8-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="6bee8-104">Bunu ile kolayca yapabilirsiniz **yeni TemporaryFile** cmdlet:</span><span class="sxs-lookup"><span data-stu-id="6bee8-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="6bee8-105">PS C:\\ &gt; $tempFile yeni TemporaryFile =</span><span class="sxs-lookup"><span data-stu-id="6bee8-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="6bee8-106">PS C:\\ &gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="6bee8-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="6bee8-107">C:\\kullanıcılar\\slee\\AppData\\yerel\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="6bee8-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>

