---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: WMF 5.0 kaldırma
ms.openlocfilehash: f562a4a4506bfdede6b23bd186b80f40cc9e45ca
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856192"
---
# <a name="uninstallation-instructions"></a>Kaldırma yönergeleri

## <a name="using-command-prompt"></a>Komut istemini kullanma

1. Açık **komut istemi.**
2. Çalıştırma [Windows Update tek başına Başlatıcısı](https://support.microsoft.com/en-us/kb/934307) aşağıda gösterildiği gibi:

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

1. Açık **Denetim Masası.**
2. Açık **programlar**ve daha sonra **program Kaldır.**
3. Tıklayın **yüklü güncelleştirmeleri görüntüle.**
4. Seçin **Windows Management Framework 5.0** yüklü güncelleştirmeler listesinden. Bu karşılık gelir *KB3134758*, *KB3134759*, veya *KB3134760*. Tıklayın **kaldırın.**
