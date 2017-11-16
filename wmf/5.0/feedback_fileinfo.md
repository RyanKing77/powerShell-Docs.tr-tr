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
# <a name="updates-to-fileinfo-object"></a><span data-ttu-id="6b933-102">FileInfo nesne güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="6b933-102">Updates to FileInfo object</span></span>
<span data-ttu-id="6b933-103">Dosya sürümü bilgilerini, özellikle dosya burada oluşturulmuştur durumlarda yanıltıcı.</span><span class="sxs-lookup"><span data-stu-id="6b933-103">File version information can be misleading, particularly in cases where the file was patched.</span></span> <span data-ttu-id="6b933-104">Bu sürüm WMF 5.0 yeni ekler **FileVersionRaw** ve **ProductVersionRaw** komut nesnelere FileInfo özellikleri.</span><span class="sxs-lookup"><span data-stu-id="6b933-104">This release of WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to FileInfo objects.</span></span> <span data-ttu-id="6b933-105">(PowerShell işlem Kimliğini $pid olduğunu varsayarak) powershell.exe için görüntülendiği gibi özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6b933-105">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117

