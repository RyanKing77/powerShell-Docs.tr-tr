---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISEAddOnToolCollection Nesnesi
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ff4f19d1a85a592f2f4f09c62caa0971751bdff7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="the-iseaddontoolcollection-object"></a>ISEAddOnToolCollection Nesnesi

**ISEAddOnToolCollection** nesnesidir koleksiyonu **ISEAddOnTool** nesneleri. Örnek **$psISE.CurrentPowerShellTab.VerticalAddOnTools** nesnesi.

## <a name="methods"></a>Yöntemler

### <a name="add-name-controltype-isvisible-"></a>Ekleme\( adı, ControlType, \[IsVisible\] \)

Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

Yeni bir eklenti aracı koleksiyona ekler. Yeni eklenen eklenti aracı döndürür. Bu komutu çalıştırmadan önce yerel bilgisayarda eklenti aracını yükleyin ve derleme yükleme.

**Ad** -dize için Windows PowerShell ISE eklenen eklenti aracı görünen adını belirtir.

**ControlType** -eklenen denetim türünü belirtir.

**\[IsVisible\]**  -isteğe bağlı Boole ayarlayın **$true**, eklenti araçtır hemen ilişkili araç bölmesinde görünür.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a>Kaldırma\( öğesi \)

Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

Belirtilen eklenti aracı koleksiyondan kaldırır.

**Öğe** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool Windows PowerShell ISE kaldırılacak nesne belirtir.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a>SetSelectedPowerShellTab\( psTab \)

Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

Seçer PowerShell sekmesinde **psTab** parametresi belirtir.

**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a>Kaldırma\( psTab \)

Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

Kaldırır PowerShell sekmesinde **psTab** parametresi belirtir.

**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a>Ayrıca bkz:

- [The PowerShellTab Object](The-PowerShellTab-Object.md)
- [Nesne modeli komut dosyası Windows PowerShell ISE amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)