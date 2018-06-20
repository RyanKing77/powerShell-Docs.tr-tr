---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9ca12ad3f0729a2e9595d7ca5ccf9041e47658a3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218102"
---
# <a name="archive-cmdlets"></a><span data-ttu-id="a984b-102">Arşiv cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="a984b-102">Archive cmdlets</span></span>

<span data-ttu-id="a984b-103">İki yeni cmdlet'leri **sıkıştırma arşiv** ve **genişletme arşiv**, let Sıkıştır ve ZIP dosyaları genişletin.</span><span class="sxs-lookup"><span data-stu-id="a984b-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="a984b-104">Arşiv sıkıştırma</span><span class="sxs-lookup"><span data-stu-id="a984b-104">Compress-Archive</span></span>
<span data-ttu-id="a984b-105">**Sıkıştırma arşiv** cmdlet'i, belirtilen dosyalardan yeni bir arşiv dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a984b-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="a984b-106">Bir arşiv dosyasına birden çok dosyaların paketlenir ve isteğe bağlı olarak daha kolay işleme ve depolama için tek bir dosyaya sıkıştırılmış olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a984b-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="a984b-107">Belirtilen bir sıkıştırma algoritması kullanılarak bir arşiv dosyasına sıkıştırılabilir **- CompressionLevel** parametresi.</span><span class="sxs-lookup"><span data-stu-id="a984b-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="a984b-108">Genişletme arşiv</span><span class="sxs-lookup"><span data-stu-id="a984b-108">Expand-Archive</span></span>
<span data-ttu-id="a984b-109">**Genişletme arşiv** cmdlet'i, belirtilen Arşiv dosyasından dosyaları ayıklar.</span><span class="sxs-lookup"><span data-stu-id="a984b-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="a984b-110">Bir arşiv dosyasına birden çok dosyaların paketlenir ve isteğe bağlı olarak daha kolay işleme ve depolama için tek bir dosyaya sıkıştırılmış olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a984b-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
