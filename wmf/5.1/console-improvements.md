---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: WMF 5.1 Konsolu geliştirmeleri
ms.openlocfilehash: 2abc02010c6c1d9f7fc617e9831b2d1243e0a3ee
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="console-improvements-in-wmf-51"></a>WMF 5.1# Konsolu geliştirmeleri

## <a name="powershell-console-improvements"></a>PowerShell Konsolu geliştirmeleri

Aşağıdaki değişiklikleri WMF 5.1 PowerShell.exe konsol deneyimini geliştirmek üzere yapılmıştır:

###<a name="vt100-support"></a>VT100 desteği

Windows 10 desteği eklendi [VT100 kaçış sıraları](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).
PowerShell belirli VT100 biçimlendirme kaçış sıraları tablo genişlikleri hesaplanırken göz ardı eder.

PowerShell VT100 desteklenip desteklenmediğini belirlemek için kod biçimlendirmede kullanılabilir yeni bir API de eklenir.
Örneğin:

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
İşte tamamı [örnek](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) eşleşmeleri vurgulamak için kullanılabilir dizesinden seçin.
Örnek adlı bir dosyaya kaydedin `MatchInfo.format.ps1xml`, profilinizi veya başka bir yerde kullanmak için Çalıştır `Update-FormatData -Prepend MatchInfo.format.ps1xml`.

Windows 10 Anniversary güncelleştirmesiyle başlayarak VT100 kaçış sıraları yalnızca desteklendiğini unutmayın; Önceki sistemlerinde desteklenmez.

### <a name="vi-mode-support-in-psreadline"></a>PSReadline VI modu desteği

[PSReadline](https://github.com/lzybkr/PSReadLine) VI modu desteği ekler. VI modunu kullanmak için çalıştırın `Set-PSReadlineOption -EditMode Vi`.

### <a name="redirected-stdin-with-interactive-input"></a>Yeniden yönlendirilen stdin etkileşimli girişi

PowerShell ile başlayan önceki sürümlerde `powershell -File -` stdin yeniden yönlendirilen ve komutları etkileşimli olarak girmenizi isteyen gerekiyordu.

WMF 5.1 ile seçeneği artık gerekli değildir bulmak bu sabit.
Örneğin tüm seçenekleri olmadan PowerShell başlatabilirsiniz `powershell`.

PSReadline şu anda desteklemediği Not stdin, yeniden yönlendirilen ve yerleşik komut satırı düzenleme deneyimi yeniden yönlendirilen stdin çok sınırlı ise, örneğin, ok tuşları çalışmıyor.
Gelecek sürümlerinden birinde PSReadline bu soruna yönelik.