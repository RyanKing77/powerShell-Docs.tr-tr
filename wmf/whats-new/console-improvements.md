---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: WMF 5.1 Konsolu iyileştirmeleri
ms.openlocfilehash: d0dd8e3c31dc0ddebab1bb899468b77a9292954d
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856220"
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="7313a-103">WMF 5.1 Konsolu iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="7313a-103">Console Improvements in WMF 5.1</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="7313a-104">PowerShell Konsolu iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="7313a-104">PowerShell console improvements</span></span>

<span data-ttu-id="7313a-105">Aşağıdaki değişiklikler PowerShell.exe WMF 5.1, konsol deneyimini iyileştirmek üzere yapılmıştır:</span><span class="sxs-lookup"><span data-stu-id="7313a-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

### <a name="vt100-support"></a><span data-ttu-id="7313a-106">VT100 desteği</span><span class="sxs-lookup"><span data-stu-id="7313a-106">VT100 support</span></span>

<span data-ttu-id="7313a-107">Windows 10 için destek eklendi [VT100 kaçış dizileri](/windows/console/console-virtual-terminal-sequences).</span><span class="sxs-lookup"><span data-stu-id="7313a-107">Windows 10 added support for [VT100 escape sequences](/windows/console/console-virtual-terminal-sequences).</span></span>
<span data-ttu-id="7313a-108">PowerShell belirli VT100 biçimlendirme kaçış dizileri tablo genişlikleri hesaplarken göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="7313a-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="7313a-109">PowerShell VT100 desteklenip desteklenmediğini belirlemek için kod biçimlendirme içinde kullanılabilen yeni bir API de ekledik.</span><span class="sxs-lookup"><span data-stu-id="7313a-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span> <span data-ttu-id="7313a-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7313a-110">For example:</span></span>

```powershell
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```

<span data-ttu-id="7313a-111">İşte tam [örnek](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) eşleşme vurgulamak için kullanılabilen gelen `Select-String`.</span><span class="sxs-lookup"><span data-stu-id="7313a-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from `Select-String`.</span></span> <span data-ttu-id="7313a-112">Örnek adlı bir dosyaya kaydedin `MatchInfo.format.ps1xml`, ardından çalıştırarak, profilinizi veya başka yerde kullanmak için `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="7313a-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="7313a-113">Windows 10 Yıldönümü güncelleştirmesi ile başlayarak, VT100 kaçış dizileri yalnızca desteklendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7313a-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update.</span></span>
<span data-ttu-id="7313a-114">Eski sistemlerde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7313a-114">They are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="7313a-115">PSReadline VI modu desteği</span><span class="sxs-lookup"><span data-stu-id="7313a-115">Vi mode support in PSReadline</span></span>

<span data-ttu-id="7313a-116">[PSReadline](https://github.com/PowerShell/PSReadLine) VI modu desteği ekler.</span><span class="sxs-lookup"><span data-stu-id="7313a-116">[PSReadline](https://github.com/PowerShell/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="7313a-117">VI modunu kullanmak için çalıştırma `Set-PSReadlineOption -EditMode Vi`.</span><span class="sxs-lookup"><span data-stu-id="7313a-117">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="7313a-118">Etkileşimli giriş ile yeniden yönlendirilen stdin</span><span class="sxs-lookup"><span data-stu-id="7313a-118">Redirected stdin with interactive input</span></span>

<span data-ttu-id="7313a-119">PowerShell ile başlayarak önceki sürümlerde `powershell -File -` stdin yeniden yönlendirme ve etkileşimli olarak komut girmek istiyordu gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="7313a-119">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="7313a-120">WMF 5.1 ile bu seçeneği artık gerekli değildir bulmak zor.</span><span class="sxs-lookup"><span data-stu-id="7313a-120">With WMF 5.1, this hard to discover option is no longer necessary.</span></span> <span data-ttu-id="7313a-121">Hiçbir seçenek olmadan PowerShell başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7313a-121">You can start PowerShell without any options.</span></span>

<span data-ttu-id="7313a-122">PSReadline desteklemediği Not stdin, yeniden yönlendirilen ve yerleşik komut satırı düzenleme deneyimi ile yeniden yönlendirilen stdin son derece sınırlıdır, ok tuşları gibi çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="7313a-122">Note that PSReadline does not support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span> <span data-ttu-id="7313a-123">PSReadline'nın gelecek sürümlerinden birinde bu soruna.</span><span class="sxs-lookup"><span data-stu-id="7313a-123">A future release of PSReadline should address this issue.</span></span>