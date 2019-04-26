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
# <a name="archive-cmdlets"></a>Arşiv cmdlet'leri

İki yeni cmdlet **arşiv sıkıştırma** ve **genişletme arşiv**, let sıkıştırma ve ZIP dosyaları genişletin.

## <a name="compress-archive"></a>Arşiv sıkıştırma
**Arşiv sıkıştırma** cmdlet'i, belirtilen dosyalardan yeni arşiv dosyası oluşturur. Bir arşiv dosyasını, birden çok, dosyaların paketlenmeli ve isteğe bağlı olarak daha kolay işleme ve depolama için tek bir dosya halinde sıkıştırılmış olanak sağlar. Belirtilen bir sıkıştırma algoritması kullanarak bir arşiv dosyasını sıkıştırılabilir **- CompressionLevel** parametresi.
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a>Arşiv genişletin
**Genişletme arşiv** cmdlet'i, belirtilen Arşiv dosyasından dosyalarını ayıklar. Bir arşiv dosyasını, birden çok, dosyaların paketlenmeli ve isteğe bağlı olarak daha kolay işleme ve depolama için tek bir dosya halinde sıkıştırılmış olanak sağlar.
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
