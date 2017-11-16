---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: ISEAddOnToolCollection nesnesi
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ba8b4e0e3952226407f00dea8b32785633256089
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="the-iseaddontoolcollection-object"></a>ISEAddOnToolCollection nesnesi
  **ISEAddOnToolCollection** nesnesidir koleksiyonu **ISEAddOnTool** nesneleri. Örnek **$psISE.CurrentPowerShellTab.VerticalAddOnTools** nesnesi.

## <a name="methods"></a>Yöntemler

### <a name="add-name-controltype-isvisible-"></a>Ekleme\( adı, ControlType, \[IsVisible\]\)
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

### <a name="remove-item-"></a>Kaldırma\( öğesi\)
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil. 

 Belirtilen eklenti aracı koleksiyondan kaldırır.

 **Öğe** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool Windows PowerShell ISE kaldırılacak nesne belirtir.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a>SetSelectedPowerShellTab\( psTab\)
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil. 

 Seçer PowerShell sekmesinde **psTab** parametresi belirtir.

 **psTab** -Microsoft.PowerShell.Host.ISE.PowerShellTab PowerShell sekmesini seçin.

```powershell
      $newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

### <a name="remove-pstab-"></a>Kaldırma\( psTab\)
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil. 

 Kaldırır PowerShell sekmesinde **psTab** parametresi belirtir.

 **psTab** -Microsoft.PowerShell.Host.ISE.PowerShellTab PowerShell sekmesini kaldırmak için.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a>Ayrıca bkz:
- [PowerShellTab nesnesi](The-PowerShellTab-Object.md) 
- [Windows PowerShell ISE nesne modeli komut dosyası oluşturma](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE nesne modeli başvurusu](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [ISE nesne modeli hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)

  
