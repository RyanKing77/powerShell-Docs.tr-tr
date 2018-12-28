---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISEMenuItemCollection Nesnesi
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7e5030416df394aaa9e9d3f63978e204a7faabf1
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405923"
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