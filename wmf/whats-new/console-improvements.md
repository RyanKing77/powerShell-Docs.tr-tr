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
# <a name="console-improvements-in-wmf-51"></a>WMF 5.1 Konsolu iyileştirmeleri

## <a name="powershell-console-improvements"></a>PowerShell Konsolu iyileştirmeleri

Aşağıdaki değişiklikler PowerShell.exe WMF 5.1, konsol deneyimini iyileştirmek üzere yapılmıştır:

### <a name="vt100-support"></a>VT100 desteği

Windows 10 için destek eklendi [VT100 kaçış dizileri](/windows/console/console-virtual-terminal-sequences).
PowerShell belirli VT100 biçimlendirme kaçış dizileri tablo genişlikleri hesaplarken göz ardı eder.

PowerShell VT100 desteklenip desteklenmediğini belirlemek için kod biçimlendirme içinde kullanılabilen yeni bir API de ekledik. Örneğin:

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

İşte tam [örnek](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) eşleşme vurgulamak için kullanılabilen gelen `Select-String`. Örnek adlı bir dosyaya kaydedin `MatchInfo.format.ps1xml`, ardından çalıştırarak, profilinizi veya başka yerde kullanmak için `Update-FormatData -Prepend MatchInfo.format.ps1xml`.

Windows 10 Yıldönümü güncelleştirmesi ile başlayarak, VT100 kaçış dizileri yalnızca desteklendiğini unutmayın.
Eski sistemlerde desteklenmez.

### <a name="vi-mode-support-in-psreadline"></a>PSReadline VI modu desteği

[PSReadline](https://github.com/PowerShell/PSReadLine) VI modu desteği ekler. VI modunu kullanmak için çalıştırma `Set-PSReadlineOption -EditMode Vi`.

### <a name="redirected-stdin-with-interactive-input"></a>Etkileşimli giriş ile yeniden yönlendirilen stdin

PowerShell ile başlayarak önceki sürümlerde `powershell -File -` stdin yeniden yönlendirme ve etkileşimli olarak komut girmek istiyordu gerekiyordu.

WMF 5.1 ile bu seçeneği artık gerekli değildir bulmak zor. Hiçbir seçenek olmadan PowerShell başlayabilirsiniz.

PSReadline desteklemediği Not stdin, yeniden yönlendirilen ve yerleşik komut satırı düzenleme deneyimi ile yeniden yönlendirilen stdin son derece sınırlıdır, ok tuşları gibi çalışmaz. PSReadline'nın gelecek sürümlerinden birinde bu soruna.