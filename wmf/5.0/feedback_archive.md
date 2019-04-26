---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: db9c630bcb8e9e0da423c779976739f1ae76f13e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057443"
---
# <a name="archive-cmdlets"></a><span data-ttu-id="eb79c-102">Arşiv cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="eb79c-102">Archive cmdlets</span></span>

<span data-ttu-id="eb79c-103">İki yeni cmdlet **arşiv sıkıştırma** ve **genişletme arşiv**, let sıkıştırma ve ZIP dosyaları genişletin.</span><span class="sxs-lookup"><span data-stu-id="eb79c-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="eb79c-104">Arşiv sıkıştırma</span><span class="sxs-lookup"><span data-stu-id="eb79c-104">Compress-Archive</span></span>
<span data-ttu-id="eb79c-105">**Arşiv sıkıştırma** cmdlet'i, belirtilen dosyalardan yeni arşiv dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eb79c-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="eb79c-106">Bir arşiv dosyasını, birden çok, dosyaların paketlenmeli ve isteğe bağlı olarak daha kolay işleme ve depolama için tek bir dosya halinde sıkıştırılmış olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb79c-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="eb79c-107">Belirtilen bir sıkıştırma algoritması kullanarak bir arşiv dosyasını sıkıştırılabilir **- CompressionLevel** parametresi.</span><span class="sxs-lookup"><span data-stu-id="eb79c-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="eb79c-108">Arşiv genişletin</span><span class="sxs-lookup"><span data-stu-id="eb79c-108">Expand-Archive</span></span>
<span data-ttu-id="eb79c-109">**Genişletme arşiv** cmdlet'i, belirtilen Arşiv dosyasından dosyalarını ayıklar.</span><span class="sxs-lookup"><span data-stu-id="eb79c-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="eb79c-110">Bir arşiv dosyasını, birden çok, dosyaların paketlenmeli ve isteğe bağlı olarak daha kolay işleme ve depolama için tek bir dosya halinde sıkıştırılmış olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb79c-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
