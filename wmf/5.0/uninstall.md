---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 385bb7223b19c8ace8088ba469e543721a527b99
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057539"
---
# <a name="uninstallation-instructions"></a>Kaldırma yönergeleri

## <a name="using-command-prompt"></a>Komut istemini kullanma
1.  Açık **komut istemi.**
2.  Çalıştırma [Windows Update tek başına Başlatıcısı](https://support.microsoft.com/en-us/kb/934307) aşağıda gösterildiği gibi:

Windows Server 2012 R2 ve Windows 8.1 üzerinde:
```powershell
wusa /uninstall /kb:3134758
```
Windows Server 2012:
```powershell
wusa /uninstall /kb:3134759
```
Windows Server 2008 R2 SP1 ve Windows 7 SP1:
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a>Denetim Masası'nı kullanarak
1.  Açık **Denetim Masası.**
2.  Açık **programlar**ve daha sonra **program Kaldır.**
3.  Tıklayın **yüklü güncelleştirmeleri görüntüle.**
4.  Seçin **Windows Management Framework 5.0** yüklü güncelleştirmeler listesinden. Bu karşılık gelir *KB3134758*, *KB3134759*, veya *KB3134760*. Tıklayın **kaldırın.**
