---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: aa2e9540af8b3d4c5de5e00377a84e0e5edd6e4a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685119"
---
# <a name="new-temporaryfile"></a><span data-ttu-id="2f716-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="2f716-102">New-TemporaryFile</span></span>
<span data-ttu-id="2f716-103">Bazen betiğinizde, geçici bir dosya oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2f716-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="2f716-104">Bunu kolayca yapabilirsiniz **yeni TemporaryFile** cmdlet:</span><span class="sxs-lookup"><span data-stu-id="2f716-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="2f716-105">PS: C:\\ &gt; $tempFile yeni TemporaryFile =</span><span class="sxs-lookup"><span data-stu-id="2f716-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="2f716-106">PS: C:\\ &gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="2f716-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="2f716-107">C:\\kullanıcılar\\slee\\AppData\\yerel\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="2f716-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>
