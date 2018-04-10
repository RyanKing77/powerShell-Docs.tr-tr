---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 78ae7ecd40b4d8ad0a6750f43002986483ab18a7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="uninstallation-instructions"></a>Kaldırma yönergeleri

## <a name="using-command-prompt"></a>Komut istemini kullanarak
1.  Açık **komut istemi.**
2.  Çalıştırma [Windows Update tek başına Başlatıcısı](https://support.microsoft.com/en-us/kb/934307) aşağıda gösterildiği gibi:

Windows Server 2012 R2 ve Windows 8.1:
```powershell
wusa /uninstall /kb:3134758
```
On Windows Server 2012:
```powershell
wusa /uninstall /kb:3134759
```
Windows Server 2008 R2 SP1 ve Windows 7 SP1:
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a>Denetim Masası'nı kullanarak
1.  Açık **Denetim Masası.**
2.  Açık **programları**, ardından açık **program Kaldır.**
3.  Tıklatın **yüklü güncelleştirmeleri görüntüle.**
4.  Seçin **Windows Management Framework 5.0** yüklü güncelleştirmeler listesinden. Bu karşılık *KB3134758*, *KB3134759*, veya *KB3134760*. Tıklatın **kaldırın.**