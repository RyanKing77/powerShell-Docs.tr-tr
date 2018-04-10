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