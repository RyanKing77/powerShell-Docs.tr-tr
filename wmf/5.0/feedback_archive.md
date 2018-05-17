---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9ca12ad3f0729a2e9595d7ca5ccf9041e47658a3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="archive-cmdlets"></a>Arşiv cmdlet'leri

İki yeni cmdlet'leri **sıkıştırma arşiv** ve **genişletme arşiv**, let Sıkıştır ve ZIP dosyaları genişletin.

## <a name="compress-archive"></a>Arşiv sıkıştırma
**Sıkıştırma arşiv** cmdlet'i, belirtilen dosyalardan yeni bir arşiv dosyası oluşturur. Bir arşiv dosyasına birden çok dosyaların paketlenir ve isteğe bağlı olarak daha kolay işleme ve depolama için tek bir dosyaya sıkıştırılmış olanak sağlar. Belirtilen bir sıkıştırma algoritması kullanılarak bir arşiv dosyasına sıkıştırılabilir **- CompressionLevel** parametresi.
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a>Genişletme arşiv
**Genişletme arşiv** cmdlet'i, belirtilen Arşiv dosyasından dosyaları ayıklar. Bir arşiv dosyasına birden çok dosyaların paketlenir ve isteğe bağlı olarak daha kolay işleme ve depolama için tek bir dosyaya sıkıştırılmış olanak sağlar.
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
