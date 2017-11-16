---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: ISEMenuItemCollection nesnesi
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7ce9132021d4d5e755503e0adb355beb388a625a
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="the-isemenuitemcollection-object"></a>ISEMenuItemCollection nesnesi
  Bir **ISEMenuItemCollection** nesnesidir koleksiyonu **ISEMenuItem** nesneleri. Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection sınıfının bir örneğidir. Örnek **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** özelleştirmek için kullanılan nesne **eklenti** menü içinde Windows PowerShell® Tümleşik komut dosyası ortamı (ISE).

## <a name="method"></a>Yöntem

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Ekleme\(DisplayName, System.Management.Automation.ScriptBlock eylem System.Windows.Input.KeyGesture kısayol dize\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Menü öğesi koleksiyona ekler.

 **DisplayName** eklenmesi için menüsünde görünen adı.

 **Eylem** **System.Management.Automation.ScriptBlock** nesne bu menü öğesiyle ilişkili eylemi belirtir.

 **Kısayol** eylemi için klavye kısayolu.

 **Döndürür** yeni eklediğiniz ISEMenuItem nesnesi.

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### <a name="clear"></a>Temizle\(\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Tüm alt menüler menü öğesinden kaldırır.

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## <a name="see-also"></a>Ayrıca bkz:
- [ISEMenuItem nesnesi](The-ISEMenuItem-Object.md) 
- [Windows PowerShell ISE nesne modeli komut dosyası oluşturma](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE nesne modeli başvurusu](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [ISE nesne modeli hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)

  
