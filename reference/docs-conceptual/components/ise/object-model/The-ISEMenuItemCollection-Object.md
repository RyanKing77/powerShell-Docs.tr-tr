---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISEMenuItemCollection Nesnesi
ms.openlocfilehash: b3795af1a6ed61ed6e371e5fc20cc4e95f643fd4
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030530"
---
# <a name="the-isemenuitemcollection-object"></a>ISEMenuItemCollection Nesnesi

Bir **Isemenuıtemcollection** nesnedir koleksiyonu **Isemenuıtem** nesneleri. Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection sınıfının bir örneğidir. Bir örnek **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** özelleştirmek için kullanılan nesne **eklenti** menü, Windows PowerShell® Tümleşik komut dosyası ortamı (ISE).

## <a name="method"></a>Yöntem

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Ekleme\(DisplayName, System.Management.Automation.ScriptBlock eylem System.Windows.Input.KeyGesture kısayol dize \)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Bir menü öğesi koleksiyonuna ekler.

**DisplayName** eklenecek menüsünde görünen adı.

**Eylem** **System.Management.Automation.ScriptBlock** nesnesini bu menü öğesiyle ilişkili eylemi belirtir.

**Kısayol** eylemi için klavye kısayol.

**Döndürür** yeni eklenenler Isemenuıtem nesnesi.

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a>Temizle\(\)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Tüm alt menü öğesinden kaldırır.

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a>Ayrıca bkz:

- [Isemenuıtem nesnesi](The-ISEMenuItem-Object.md)
- [Windows PowerShell ISE betik oluşturma nesne modelinin amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)
