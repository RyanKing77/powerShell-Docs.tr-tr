---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 7ad4a00f7beba0de70696d88cd5448c7c638c50c
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/27/2017
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

