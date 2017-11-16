---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: ISEMenuItem nesnesi
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 5561955040e56110a6af0619c286548f5812fb47
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="the-isemenuitem-object"></a>ISEMenuItem nesnesi
  Bir **ISEMenuItem** nesnesidir Microsoft.PowerShell.Host.ISE.ISEMenuItem sınıfının bir örneği. Tüm menü nesnelerde **eklentileri** menü örnekleridir **Microsoft.PowerShell.Host.ISE.ISEMenuItem** sınıfı.

## <a name="properties"></a>Özellikler

### <a name="displayname"></a>Görünen Ad
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Menü öğesi görünen adını alır salt okunur özellik.

```
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName

```

### <a name="action"></a>Eylem
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Komut dosyası bloğunda alır salt okunur özellik. Menü öğesini tıklattığınızda eylemi çağırır.

```
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item 
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a>Kısayol
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Windows alır salt okunur özellik klavye kısayol menü öğesi için girin.

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a>Alt menüler
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Alır salt okunur özellik [alt menüler listesi](The-ISEMenuItemCollection-Object.md) menü öğesinin.

```
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a>Komut dosyası örneği
 Eklentiler menü ve kodlanabilir özelliklerini kullanımını daha iyi anlamak için aşağıdaki komut dosyası örneği okuyun.

```

# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu - a parent and a child submenu item. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")

```

## <a name="see-also"></a>Ayrıca bkz:
- [ISEMenuItemCollection nesnesi](The-ISEMenuItemCollection-Object.md) 
- [Windows PowerShell ISE nesne modeli komut dosyası oluşturma](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE nesne modeli başvurusu](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [ISE nesne modeli hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)
