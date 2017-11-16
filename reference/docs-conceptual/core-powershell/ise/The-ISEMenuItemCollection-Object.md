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
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="9217a-103">ISEMenuItemCollection nesnesi</span><span class="sxs-lookup"><span data-stu-id="9217a-103">The ISEMenuItemCollection Object</span></span>
  <span data-ttu-id="9217a-104">Bir **ISEMenuItemCollection** nesnesidir koleksiyonu **ISEMenuItem** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9217a-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="9217a-105">Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection sınıfının bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="9217a-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="9217a-106">Örnek **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** özelleştirmek için kullanılan nesne **eklenti** menü içinde Windows PowerShell® Tümleşik komut dosyası ortamı (ISE).</span><span class="sxs-lookup"><span data-stu-id="9217a-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="9217a-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9217a-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="9217a-108">Ekleme\(DisplayName, System.Management.Automation.ScriptBlock eylem System.Windows.Input.KeyGesture kısayol dize\)</span><span class="sxs-lookup"><span data-stu-id="9217a-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>
  <span data-ttu-id="9217a-109">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9217a-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9217a-110">Menü öğesi koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="9217a-110">Adds a menu item to the collection.</span></span>

 <span data-ttu-id="9217a-111">**DisplayName** eklenmesi için menüsünde görünen adı.</span><span class="sxs-lookup"><span data-stu-id="9217a-111">**DisplayName** The display name of the menu to be added.</span></span>

 <span data-ttu-id="9217a-112">**Eylem** **System.Management.Automation.ScriptBlock** nesne bu menü öğesiyle ilişkili eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="9217a-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

 <span data-ttu-id="9217a-113">**Kısayol** eylemi için klavye kısayolu.</span><span class="sxs-lookup"><span data-stu-id="9217a-113">**Shortcut** The keyboard shortcut for the action.</span></span>

 <span data-ttu-id="9217a-114">**Döndürür** yeni eklediğiniz ISEMenuItem nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9217a-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### <a name="clear"></a><span data-ttu-id="9217a-115">Temizle\(\)</span><span class="sxs-lookup"><span data-stu-id="9217a-115">Clear\(\)</span></span>
  <span data-ttu-id="9217a-116">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9217a-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9217a-117">Tüm alt menüler menü öğesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9217a-117">Removes all submenus from the menu item.</span></span>

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## <a name="see-also"></a><span data-ttu-id="9217a-118">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="9217a-118">See Also</span></span>
- [<span data-ttu-id="9217a-119">ISEMenuItem nesnesi</span><span class="sxs-lookup"><span data-stu-id="9217a-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md) 
- [<span data-ttu-id="9217a-120">Windows PowerShell ISE nesne modeli komut dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="9217a-120">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="9217a-121">Windows PowerShell ISE nesne modeli başvurusu</span><span class="sxs-lookup"><span data-stu-id="9217a-121">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="9217a-122">ISE nesne modeli hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="9217a-122">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
