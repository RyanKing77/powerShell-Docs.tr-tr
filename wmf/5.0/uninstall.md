---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 64a29aa87507e65a182837df538c5e695c420cb3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="1e6e7-102">Kaldırma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="1e6e7-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="1e6e7-103">Komut istemini kullanarak</span><span class="sxs-lookup"><span data-stu-id="1e6e7-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="1e6e7-104">Açık **komut istemi.**</span><span class="sxs-lookup"><span data-stu-id="1e6e7-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="1e6e7-105">Çalıştırma [Windows Update tek başına Başlatıcısı](https://support.microsoft.com/en-us/kb/934307) aşağıda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="1e6e7-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="1e6e7-106">Windows Server 2012 R2 ve Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="1e6e7-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="1e6e7-107">Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="1e6e7-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="1e6e7-108">Windows Server 2008 R2 SP1 ve Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="1e6e7-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="1e6e7-109">Denetim Masası'nı kullanarak</span><span class="sxs-lookup"><span data-stu-id="1e6e7-109">Using Control Panel</span></span>
1.  <span data-ttu-id="1e6e7-110">Açık **Denetim Masası.**</span><span class="sxs-lookup"><span data-stu-id="1e6e7-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="1e6e7-111">Açık **programları**, ardından açık **program Kaldır.**</span><span class="sxs-lookup"><span data-stu-id="1e6e7-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="1e6e7-112">Tıklatın **yüklü güncelleştirmeleri görüntüle.**</span><span class="sxs-lookup"><span data-stu-id="1e6e7-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="1e6e7-113">Seçin **Windows Management Framework 5.0** yüklü güncelleştirmeler listesinden.</span><span class="sxs-lookup"><span data-stu-id="1e6e7-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="1e6e7-114">Bu karşılık *KB3134758*, *KB3134759*, veya *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="1e6e7-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="1e6e7-115">Tıklatın **kaldırın.**</span><span class="sxs-lookup"><span data-stu-id="1e6e7-115">Click **Uninstall.**</span></span>
