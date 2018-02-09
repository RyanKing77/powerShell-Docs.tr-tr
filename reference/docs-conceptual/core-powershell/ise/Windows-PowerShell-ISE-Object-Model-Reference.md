---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Windows PowerShell ISE Nesne Modeli Başvurusu"
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
ms.openlocfilehash: 624ddca3895ba3e24bf52a27babdb07e8714baae
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2018
---
# <a name="windows-powershell-ise-object-model-reference"></a>Windows PowerShell ISE Nesne Modeli Başvurusu
  
## <a name="object-model-reference"></a>Nesne Modeli Başvurusu
 Bu bölüm, çeşitli nesneleri inWindows PowerShell® Tümleşik komut dosyası ortamı (ISE) tanımlayan temel sınıflar üzerinde bir başvuru sağlar. Kendi hiyerarşilerinde düzenlenmiş nesneleri görmek için bkz: [işe nesne modeli hiyerarşisi](The-ISE-Object-Model-Hierarchy.md).

 [ISEAddOnTool nesne](The-ISEAddOnTool-Object.md) örnekler: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.

 [ISEAddOnTool nesne](The-ISEAddOnTool-Object.md) [ISEEditor nesne](The-ISEEditor-Object.md) örnekler: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.

 [ISEFile nesne](The-ISEFile-Object.md) örnekler: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].

 [ISEFileCollection nesne](The-ISEFileCollection-Object.md) örnekler: $psISE.PowerShellTabs.Files.

 [ISEMenuItem nesne](The-ISEMenuItem-Object.md) örnekler: $psISE.CurrentPowerShellTab.AddOnsMenu, $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].

 [ISEMenuItemCollection nesne](The-ISEMenuItemCollection-Object.md) örnek: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.

 [ISEOptions nesne](The-ISEOptions-Object.md) örnekler: $psISE.Options, $psISE.Options.DefaultOptions.

 [ObjectModelRoot nesne](The-ObjectModelRoot-Object.md) örnek: kök $psISE nesnesi.

 [PowerShellTab nesne](The-PowerShellTab-Object.md) örnekler: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].

 [PowerShellTabCollection nesne](The-PowerShellTabCollection-Object.md) örnek: $psISE.PowerShellTabs.

## <a name="see-also"></a>Ayrıca bkz:
- [Windows PowerShell ISE nesne modeli komut dosyası oluşturma](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
