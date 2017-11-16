---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
title: "WMF 5.1 Konsolu geliştirmeleri"
ms.openlocfilehash: b0859191ea310c9b73fe9f255d7f256a1cc1af1f
ms.sourcegitcommit: fee03bb9802222078c8d5f6c8efb0698024406ed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2017
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="5ecee-103">WMF 5.1# Konsolu geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="5ecee-103">Console Improvements in WMF 5.1#</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="5ecee-104">PowerShell Konsolu geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="5ecee-104">PowerShell console improvements</span></span>

<span data-ttu-id="5ecee-105">Aşağıdaki değişiklikleri WMF 5.1 PowerShell.exe konsol deneyimini geliştirmek üzere yapılmıştır:</span><span class="sxs-lookup"><span data-stu-id="5ecee-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

###<a name="vt100-support"></a><span data-ttu-id="5ecee-106">VT100 desteği</span><span class="sxs-lookup"><span data-stu-id="5ecee-106">VT100 support</span></span>

<span data-ttu-id="5ecee-107">Windows 10 desteği eklendi [VT100 kaçış sıraları](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="5ecee-107">Windows 10 added support for [VT100 escape sequences](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).</span></span>
<span data-ttu-id="5ecee-108">PowerShell belirli VT100 biçimlendirme kaçış sıraları tablo genişlikleri hesaplanırken göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="5ecee-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="5ecee-109">PowerShell VT100 desteklenip desteklenmediğini belirlemek için kod biçimlendirmede kullanılabilir yeni bir API de eklenir.</span><span class="sxs-lookup"><span data-stu-id="5ecee-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span> <span data-ttu-id="5ecee-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="5ecee-110">For example:</span></span>

```
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
<span data-ttu-id="5ecee-111">İşte tamamı [örnek](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) eşleşmeleri vurgulamak için kullanılabilir dizesinden seçin.</span><span class="sxs-lookup"><span data-stu-id="5ecee-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from Select-String.</span></span>
<span data-ttu-id="5ecee-112">Örnek adlı bir dosyaya kaydedin `MatchInfo.format.ps1xml`, profilinizi veya başka bir yerde kullanmak için Çalıştır `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="5ecee-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="5ecee-113">Windows 10 Anniversary güncelleştirmesiyle başlayarak VT100 kaçış sıraları yalnızca desteklendiğini unutmayın; Önceki sistemlerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="5ecee-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update; they are not supported on earlier systems.</span></span>   

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="5ecee-114">PSReadline VI modu desteği</span><span class="sxs-lookup"><span data-stu-id="5ecee-114">Vi mode support in PSReadline</span></span>

<span data-ttu-id="5ecee-115">[PSReadline](https://github.com/lzybkr/PSReadLine) VI modu desteği ekler.</span><span class="sxs-lookup"><span data-stu-id="5ecee-115">[PSReadline](https://github.com/lzybkr/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="5ecee-116">VI modunu kullanmak için çalıştırın `Set-PSReadlineOption -EditMode Vi`.</span><span class="sxs-lookup"><span data-stu-id="5ecee-116">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="5ecee-117">Yeniden yönlendirilen stdin etkileşimli girişi</span><span class="sxs-lookup"><span data-stu-id="5ecee-117">Redirected stdin with interactive input</span></span> 

<span data-ttu-id="5ecee-118">PowerShell ile başlayan önceki sürümlerde `powershell -File -` stdin yeniden yönlendirilen ve komutları etkileşimli olarak girmenizi isteyen gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="5ecee-118">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="5ecee-119">WMF 5.1 ile seçeneği artık gerekli değildir bulmak bu sabit.</span><span class="sxs-lookup"><span data-stu-id="5ecee-119">With WMF 5.1, this hard to discover option is no longer necessary.</span></span> <span data-ttu-id="5ecee-120">Örneğin tüm seçenekleri olmadan PowerShell başlatabilirsiniz `powershell`.</span><span class="sxs-lookup"><span data-stu-id="5ecee-120">You can start PowerShell without any options, e.g. `powershell`.</span></span>

<span data-ttu-id="5ecee-121">PSReadline şu anda desteklemediği Not stdin, yeniden yönlendirilen ve yerleşik komut satırı düzenleme deneyimi yeniden yönlendirilen stdin çok sınırlı ise, örneğin, ok tuşları çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="5ecee-121">Note that PSReadline does not currently support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span> <span data-ttu-id="5ecee-122">Gelecek sürümlerinden birinde PSReadline bu soruna yönelik.</span><span class="sxs-lookup"><span data-stu-id="5ecee-122">A future release of PSReadline should address this issue.</span></span>   

