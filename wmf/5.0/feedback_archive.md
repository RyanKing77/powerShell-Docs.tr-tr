---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 0c450d765531c18c0b73c5c64262e9895f92068a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="archive-cmdlets"></a><span data-ttu-id="66afe-102">Arşiv cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="66afe-102">Archive cmdlets</span></span>

<span data-ttu-id="66afe-103">İki yeni cmdlet'leri **sıkıştırma arşiv** ve **genişletme arşiv**, let Sıkıştır ve ZIP dosyaları genişletin.</span><span class="sxs-lookup"><span data-stu-id="66afe-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="66afe-104">Arşiv sıkıştırma</span><span class="sxs-lookup"><span data-stu-id="66afe-104">Compress-Archive</span></span>
<span data-ttu-id="66afe-105">**Sıkıştırma arşiv** cmdlet'i, belirtilen dosyalardan yeni bir arşiv dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="66afe-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="66afe-106">Bir arşiv dosyasına birden çok dosyaların paketlenir ve isteğe bağlı olarak daha kolay işleme ve depolama için tek bir dosyaya sıkıştırılmış olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="66afe-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="66afe-107">Belirtilen bir sıkıştırma algoritması kullanılarak bir arşiv dosyasına sıkıştırılabilir **- CompressionLevel** parametresi.</span><span class="sxs-lookup"><span data-stu-id="66afe-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="66afe-108">Genişletme arşiv</span><span class="sxs-lookup"><span data-stu-id="66afe-108">Expand-Archive</span></span>
<span data-ttu-id="66afe-109">**Genişletme arşiv** cmdlet'i, belirtilen Arşiv dosyasından dosyaları ayıklar.</span><span class="sxs-lookup"><span data-stu-id="66afe-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="66afe-110">Bir arşiv dosyasına birden çok dosyaların paketlenir ve isteğe bağlı olarak daha kolay işleme ve depolama için tek bir dosyaya sıkıştırılmış olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="66afe-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```