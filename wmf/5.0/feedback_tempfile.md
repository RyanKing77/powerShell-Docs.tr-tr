---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: ada4fcc0beb3eb74b099f221762341abbf2c3b4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="new-temporaryfile"></a><span data-ttu-id="fb928-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="fb928-102">New-TemporaryFile</span></span>
<span data-ttu-id="fb928-103">Bazen komut dosyalarınızı geçici bir dosya oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fb928-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="fb928-104">Bunu ile kolayca yapabilirsiniz **yeni TemporaryFile** cmdlet:</span><span class="sxs-lookup"><span data-stu-id="fb928-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="fb928-105">PS C:\\ &gt; $tempFile yeni TemporaryFile =</span><span class="sxs-lookup"><span data-stu-id="fb928-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="fb928-106">PS C:\\ &gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="fb928-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="fb928-107">C:\\kullanıcılar\\slee\\AppData\\yerel\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="fb928-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>