---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5280ef5ff95679dc8721be8f5f81031a4ffe796f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085270"
---
# <a name="updates-to-fileinfo-object"></a><span data-ttu-id="6204e-102">FileInfo nesnesi güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="6204e-102">Updates to FileInfo object</span></span>
<span data-ttu-id="6204e-103">Dosya sürümü bilgilerini, özellikle dosyasının nerede oluşturulmuştur durumlarda yanıltıcı.</span><span class="sxs-lookup"><span data-stu-id="6204e-103">File version information can be misleading, particularly in cases where the file was patched.</span></span> <span data-ttu-id="6204e-104">WMF 5.0, bu sürümünde yeni ekler **FileVersionRaw** ve **ProductVersionRaw** betik FileInfo nesnelere özellikler.</span><span class="sxs-lookup"><span data-stu-id="6204e-104">This release of WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to FileInfo objects.</span></span> <span data-ttu-id="6204e-105">Powershell.exe (PowerShell işlemin Kimliğini $pid olduğunu varsayarak) için görüntülenen özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6204e-105">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
