---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISEMenuItemCollection Nesnesi
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7e5030416df394aaa9e9d3f63978e204a7faabf1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="the-isemenuitemcollection-object"></a>ISEMenuItemCollection Nesnesi

Bir **ISEMenuItemCollection** nesnesidir koleksiyonu **ISEMenuItem** nesneleri. Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection sınıfının bir örneğidir. Örnek **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** özelleştirmek için kullanılan nesne **eklenti** menü içinde Windows PowerShell® Tümleşik komut dosyası ortamı (ISE).

## <a name="method"></a>Yöntem

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Menü öğesi koleksiyona ekler.

**DisplayName** eklenmesi için menüsünde görünen adı.

**Eylem** **System.Management.Automation.ScriptBlock** nesne bu menü öğesiyle ilişkili eylemi belirtir.

**Kısayol** eylemi için klavye kısayolu.

**Döndürür** yeni eklediğiniz ISEMenuItem nesnesi.

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a>Temizle\(\)

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Tüm alt menüler menü öğesinden kaldırır.

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a>Ayrıca bkz:

- [ISEMenuItem nesnesi](The-ISEMenuItem-Object.md)
- [Nesne modeli komut dosyası Windows PowerShell ISE amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)