---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: WMF 5.1 Konsolu iyileştirmeleri
ms.openlocfilehash: a8e82e2f973916c2ed5007eba90ee6f2b7a9a769
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892935"
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="b6c11-103">WMF 5.1 Konsolu iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="b6c11-103">Console Improvements in WMF 5.1</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="b6c11-104">PowerShell Konsolu iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="b6c11-104">PowerShell console improvements</span></span>

<span data-ttu-id="b6c11-105">Aşağıdaki değişiklikler PowerShell.exe WMF 5.1, konsol deneyimini iyileştirmek üzere yapılmıştır:</span><span class="sxs-lookup"><span data-stu-id="b6c11-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

### <a name="vt100-support"></a><span data-ttu-id="b6c11-106">VT100 desteği</span><span class="sxs-lookup"><span data-stu-id="b6c11-106">VT100 support</span></span>

<span data-ttu-id="b6c11-107">Windows 10 için destek eklendi [VT100 kaçış dizileri](/windows/console/console-virtual-terminal-sequences).</span><span class="sxs-lookup"><span data-stu-id="b6c11-107">Windows 10 added support for [VT100 escape sequences](/windows/console/console-virtual-terminal-sequences).</span></span>
<span data-ttu-id="b6c11-108">PowerShell belirli VT100 biçimlendirme kaçış dizileri tablo genişlikleri hesaplarken göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="b6c11-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="b6c11-109">PowerShell VT100 desteklenip desteklenmediğini belirlemek için kod biçimlendirme içinde kullanılabilen yeni bir API de ekledik.</span><span class="sxs-lookup"><span data-stu-id="b6c11-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span>
<span data-ttu-id="b6c11-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b6c11-110">For example:</span></span>

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

<span data-ttu-id="b6c11-111">İşte tam [örnek](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) eşleşme vurgulamak için kullanılabilen gelen `Select-String`.</span><span class="sxs-lookup"><span data-stu-id="b6c11-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from `Select-String`.</span></span>
<span data-ttu-id="b6c11-112">Örnek adlı bir dosyaya kaydedin `MatchInfo.format.ps1xml`, ardından çalıştırarak, profilinizi veya başka yerde kullanmak için `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="b6c11-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="b6c11-113">Windows 10 Yıldönümü güncelleştirmesi ile başlayarak, VT100 kaçış dizileri yalnızca desteklendiğini unutmayın; eski sistemlerde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b6c11-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update; they are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="b6c11-114">PSReadline VI modu desteği</span><span class="sxs-lookup"><span data-stu-id="b6c11-114">Vi mode support in PSReadline</span></span>

<span data-ttu-id="b6c11-115">[PSReadline](https://github.com/lzybkr/PSReadLine) VI modu desteği ekler.</span><span class="sxs-lookup"><span data-stu-id="b6c11-115">[PSReadline](https://github.com/lzybkr/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="b6c11-116">VI modunu kullanmak için çalıştırma `Set-PSReadlineOption -EditMode Vi`.</span><span class="sxs-lookup"><span data-stu-id="b6c11-116">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="b6c11-117">Etkileşimli giriş ile yeniden yönlendirilen stdin</span><span class="sxs-lookup"><span data-stu-id="b6c11-117">Redirected stdin with interactive input</span></span>

<span data-ttu-id="b6c11-118">PowerShell ile başlayarak önceki sürümlerde `powershell -File -` stdin yeniden yönlendirme ve etkileşimli olarak komut girmek istiyordu gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="b6c11-118">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="b6c11-119">WMF 5.1 ile bu seçeneği artık gerekli değildir bulmak zor.</span><span class="sxs-lookup"><span data-stu-id="b6c11-119">With WMF 5.1, this hard to discover option is no longer necessary.</span></span>
<span data-ttu-id="b6c11-120">Hiçbir seçenek olmadan, örneğin PowerShell başlayabilirsiniz `powershell`.</span><span class="sxs-lookup"><span data-stu-id="b6c11-120">You can start PowerShell without any options, e.g. `powershell`.</span></span>

<span data-ttu-id="b6c11-121">PSReadline şu anda desteklemediği Not stdin, yeniden yönlendirilen ve yerleşik komut satırı düzenleme deneyimi ile yeniden yönlendirilen stdin son derece sınırlıdır, ok tuşları gibi çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="b6c11-121">Note that PSReadline does not currently support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span>
<span data-ttu-id="b6c11-122">PSReadline'nın gelecek sürümlerinden birinde bu soruna.</span><span class="sxs-lookup"><span data-stu-id="b6c11-122">A future release of PSReadline should address this issue.</span></span>