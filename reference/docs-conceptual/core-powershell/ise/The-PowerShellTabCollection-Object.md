---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: PowerShellTabCollection nesnesi
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: dcdc16ae126453b6ade64917ac4950cc05e5f8ad
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="the-powershelltabcollection-object"></a>PowerShellTabCollection nesnesi
  **PowerShellTab** koleksiyon nesnesi koleksiyonudur **PowerShellTab** nesneleri. Her **PowerShellTab** nesne ayrı bir çalışma zamanı ortamı olarak çalışır. Microsoft.PowerShell.Host.ISE.PowerShellTabs sınıfının bir örneğidir. Örnek **$psISE.PowerShellTabs** nesnesi.

## <a name="methods"></a>Yöntemler

### <a name="add"></a>Ekleme\(\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Yeni bir PowerShell sekmesi koleksiyona ekler. Yeni eklenen sekmesini döndürür.

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Kaldırma\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Tarafından belirtilen sekmesini kaldırır **psTab** parametresi.

 **psTab** kaldırmak için PowerShell sekmesi.

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Tarafından belirtilen PowerShell sekmesinde seçer **psTab** parametresi şu anda etkin PowerShell sekmesinde yapın.

 **psTab** PowerShell sekmesini seçin.

```
# Save the current tab in a variable and rename it
$OldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName="Old Tab"
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab" 
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab=$oldtab
```

## <a name="see-also"></a>Ayrıca bkz:
- [PowerShellTab nesnesi](The-PowerShellTab-Object.md) 
- [Windows PowerShell ISE nesne modeli komut dosyası oluşturma](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE nesne modeli başvurusu](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [ISE nesne modeli hiyerarşisi](../ise/The-ISE-Object-Model-Hierarchy.md)

  
