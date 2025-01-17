---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISEMenuItem Nesnesi
ms.openlocfilehash: a513a3e9f2eb97f3955fa817faedbcbf4e0ed018
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028947"
---
# <a name="the-isemenuitem-object"></a>ISEMenuItem Nesnesi

Bir **Isemenuıtem** nesnedir Microsoft.PowerShell.Host.ISE.ISEMenuItem sınıfının örneği. Tüm menü nesneler üzerinde **eklentileri** menü örnekleridir **Microsoft.PowerShell.Host.ISE.ISEMenuItem** sınıfı.

## <a name="properties"></a>Özellikler

### <a name="displayname"></a>Görünen Ad

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Menü öğesi görünen adını alır salt okunur özellik.

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a>Eylem

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Betik bloğu alan salt okunur özelliği. Menü öğesini tıkladığınızda eylemi çağırır.

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a>Kısayol

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Windows salt okunur özelliği, klavye kısayol menü öğesi için giriş.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a>Alt menüler

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Salt okunur özelliği [menülerinde listesi](The-ISEMenuItemCollection-Object.md) menü öğesinin.

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a>Komut dosyası örneği

Eklentileri menü ve komut satırı özelliklerini daha iyi anlamak için aşağıdaki komut örnek okuyun.

```powershell
# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu - a parent and a child submenu item.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
```

## <a name="see-also"></a>Ayrıca bkz:

- [Isemenuıtemcollection nesnesi](The-ISEMenuItemCollection-Object.md)
- [Windows PowerShell ISE betik oluşturma nesne modelinin amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)
