---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 3392db954c22030bb64ae5093619d23952e1fcdb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="1a91c-102">Kaldırma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="1a91c-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="1a91c-103">Komut istemini kullanarak</span><span class="sxs-lookup"><span data-stu-id="1a91c-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="1a91c-104">Açık **komut istemi.**</span><span class="sxs-lookup"><span data-stu-id="1a91c-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="1a91c-105">Çalıştırma [Windows Update tek başına Başlatıcısı](https://support.microsoft.com/en-us/kb/934307) aşağıda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="1a91c-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="1a91c-106">Windows Server 2012 R2 ve Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="1a91c-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="1a91c-107">Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="1a91c-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="1a91c-108">Windows Server 2008 R2 SP1 ve Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="1a91c-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="1a91c-109">Denetim Masası'nı kullanarak</span><span class="sxs-lookup"><span data-stu-id="1a91c-109">Using Control Panel</span></span>
1.  <span data-ttu-id="1a91c-110">Açık **Denetim Masası.**</span><span class="sxs-lookup"><span data-stu-id="1a91c-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="1a91c-111">Açık **programları**, ardından açık **program Kaldır.**</span><span class="sxs-lookup"><span data-stu-id="1a91c-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="1a91c-112">Tıklatın **yüklü güncelleştirmeleri görüntüle.**</span><span class="sxs-lookup"><span data-stu-id="1a91c-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="1a91c-113">Seçin **Windows Management Framework 5.0** yüklü güncelleştirmeler listesinden.</span><span class="sxs-lookup"><span data-stu-id="1a91c-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="1a91c-114">Bu karşılık *KB3134758*, *KB3134759*, veya *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="1a91c-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="1a91c-115">Tıklatın **kaldırın.**</span><span class="sxs-lookup"><span data-stu-id="1a91c-115">Click **Uninstall.**</span></span>

