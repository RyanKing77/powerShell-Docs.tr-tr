---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 385bb7223b19c8ace8088ba469e543721a527b99
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688528"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="ae29d-102">Kaldırma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ae29d-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="ae29d-103">Komut istemini kullanma</span><span class="sxs-lookup"><span data-stu-id="ae29d-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="ae29d-104">Açık **komut istemi.**</span><span class="sxs-lookup"><span data-stu-id="ae29d-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="ae29d-105">Çalıştırma [Windows Update tek başına Başlatıcısı](https://support.microsoft.com/en-us/kb/934307) aşağıda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="ae29d-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="ae29d-106">Windows Server 2012 R2 ve Windows 8.1 üzerinde:</span><span class="sxs-lookup"><span data-stu-id="ae29d-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="ae29d-107">Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="ae29d-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="ae29d-108">Windows Server 2008 R2 SP1 ve Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="ae29d-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="ae29d-109">Denetim Masası'nı kullanarak</span><span class="sxs-lookup"><span data-stu-id="ae29d-109">Using Control Panel</span></span>
1.  <span data-ttu-id="ae29d-110">Açık **Denetim Masası.**</span><span class="sxs-lookup"><span data-stu-id="ae29d-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="ae29d-111">Açık **programlar**ve daha sonra **program Kaldır.**</span><span class="sxs-lookup"><span data-stu-id="ae29d-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="ae29d-112">Tıklayın **yüklü güncelleştirmeleri görüntüle.**</span><span class="sxs-lookup"><span data-stu-id="ae29d-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="ae29d-113">Seçin **Windows Management Framework 5.0** yüklü güncelleştirmeler listesinden.</span><span class="sxs-lookup"><span data-stu-id="ae29d-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="ae29d-114">Bu karşılık gelir *KB3134758*, *KB3134759*, veya *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="ae29d-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="ae29d-115">Tıklayın **kaldırın.**</span><span class="sxs-lookup"><span data-stu-id="ae29d-115">Click **Uninstall.**</span></span>
