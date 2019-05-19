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
# <a name="uninstallation-instructions"></a><span data-ttu-id="6b242-103">Kaldırma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6b242-103">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="6b242-104">Komut istemini kullanma</span><span class="sxs-lookup"><span data-stu-id="6b242-104">Using Command Prompt</span></span>

1. <span data-ttu-id="6b242-105">Açık **komut istemi.**</span><span class="sxs-lookup"><span data-stu-id="6b242-105">Open **Command Prompt.**</span></span>
2. <span data-ttu-id="6b242-106">Çalıştırma [Windows Update tek başına Başlatıcısı](https://support.microsoft.com/en-us/kb/934307) aşağıda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="6b242-106">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="6b242-107">Windows Server 2012 R2 ve Windows 8.1 üzerinde:</span><span class="sxs-lookup"><span data-stu-id="6b242-107">On Windows Server 2012 R2 and Windows 8.1:</span></span>

```powershell
wusa /uninstall /kb:3134758
```

<span data-ttu-id="6b242-108">Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="6b242-108">On Windows Server 2012:</span></span>

```powershell
wusa /uninstall /kb:3134759
```

<span data-ttu-id="6b242-109">Windows Server 2008 R2 SP1 ve Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="6b242-109">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>

```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="6b242-110">Denetim Masası'nı kullanarak</span><span class="sxs-lookup"><span data-stu-id="6b242-110">Using Control Panel</span></span>

1. <span data-ttu-id="6b242-111">Açık **Denetim Masası.**</span><span class="sxs-lookup"><span data-stu-id="6b242-111">Open **Control Panel.**</span></span>
2. <span data-ttu-id="6b242-112">Açık **programlar**ve daha sonra **program Kaldır.**</span><span class="sxs-lookup"><span data-stu-id="6b242-112">Open **Programs**, then open **Uninstall a program.**</span></span>
3. <span data-ttu-id="6b242-113">Tıklayın **yüklü güncelleştirmeleri görüntüle.**</span><span class="sxs-lookup"><span data-stu-id="6b242-113">Click **View installed updates.**</span></span>
4. <span data-ttu-id="6b242-114">Seçin **Windows Management Framework 5.0** yüklü güncelleştirmeler listesinden.</span><span class="sxs-lookup"><span data-stu-id="6b242-114">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="6b242-115">Bu karşılık gelir *KB3134758*, *KB3134759*, veya *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="6b242-115">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="6b242-116">Tıklayın **kaldırın.**</span><span class="sxs-lookup"><span data-stu-id="6b242-116">Click **Uninstall.**</span></span>
