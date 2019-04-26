---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: PowerShellTabCollection Nesnesi
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: d9088b26de35360b8258d3f15924b3010a986d15
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086627"
---
# <a name="the-powershelltabcollection-object"></a>PowerShellTabCollection Nesnesi

**PowerShellTab** koleksiyon nesnesi, koleksiyonudur **PowerShellTab** nesneleri. Her **PowerShellTab** nesne ayrı bir çalışma zamanı ortamı olarak çalışır. Microsoft.PowerShell.Host.ISE.PowerShellTabs sınıfının bir örneğidir. Bir örnek **$psISE.PowerShellTabs** nesne.

## <a name="methods"></a>Yöntemler

### <a name="add"></a>Ekleme\(\)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Yeni bir PowerShell sekmesi koleksiyona ekler. Yeni eklenen sekmesine döndürür.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Kaldırma\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Tarafından belirtilen sekmesini kaldırır **psTab** parametresi.

**psTab** kaldırmak için bir PowerShell sekmesi.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Tarafından belirtilen PowerShell sekme seçer **psTab** şu anda etkin PowerShell sekme yapmak için parametre.

**psTab** PowerShell sekmesini seçin.

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a>Ayrıca bkz:

- [PowerShellTab nesnesi](The-PowerShellTab-Object.md)
- [Windows PowerShell ISE betik oluşturma nesne modelinin amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)