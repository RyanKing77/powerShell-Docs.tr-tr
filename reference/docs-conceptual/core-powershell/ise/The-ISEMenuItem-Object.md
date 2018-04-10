---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISEMenuItem Nesnesi
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 556f88117c07100b1734c8ffd8956dce6efe6fb1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="the-isemenuitem-object"></a>ISEMenuItem Nesnesi

Bir **ISEMenuItem** nesnesidir Microsoft.PowerShell.Host.ISE.ISEMenuItem sınıfının bir örneği. Tüm menü nesnelerde **eklentileri** menü örnekleridir **Microsoft.PowerShell.Host.ISE.ISEMenuItem** sınıfı.

## <a name="properties"></a>Özellikler

### <a name="displayname"></a>Görünen Ad

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Menü öğesi görünen adını alır salt okunur özellik.

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a>Eylem

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Komut dosyası bloğunda alır salt okunur özellik. Menü öğesini tıklattığınızda eylemi çağırır.

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a>Kısayol

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Windows alır salt okunur özellik klavye kısayol menü öğesi için girin.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a>Alt menüler

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Alır salt okunur özellik [alt menüler listesi](The-ISEMenuItemCollection-Object.md) menü öğesinin.

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a>Komut dosyası örneği

Eklentiler menü ve kodlanabilir özelliklerini kullanımını daha iyi anlamak için aşağıdaki komut dosyası örneği okuyun.

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

- [ISEMenuItemCollection nesnesi](The-ISEMenuItemCollection-Object.md)
- [Nesne modeli komut dosyası Windows PowerShell ISE amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)