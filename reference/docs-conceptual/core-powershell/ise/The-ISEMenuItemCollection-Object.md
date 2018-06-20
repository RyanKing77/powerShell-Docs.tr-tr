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
ms.locfileid: "30954713"
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="b0d49-103">ISEMenuItemCollection Nesnesi</span><span class="sxs-lookup"><span data-stu-id="b0d49-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="b0d49-104">Bir **ISEMenuItemCollection** nesnesidir koleksiyonu **ISEMenuItem** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b0d49-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="b0d49-105">Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection sınıfının bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="b0d49-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="b0d49-106">Örnek **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** özelleştirmek için kullanılan nesne **eklenti** menü içinde Windows PowerShell® Tümleşik komut dosyası ortamı (ISE).</span><span class="sxs-lookup"><span data-stu-id="b0d49-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="b0d49-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b0d49-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="b0d49-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span><span class="sxs-lookup"><span data-stu-id="b0d49-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="b0d49-109">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b0d49-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b0d49-110">Menü öğesi koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="b0d49-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="b0d49-111">**DisplayName** eklenmesi için menüsünde görünen adı.</span><span class="sxs-lookup"><span data-stu-id="b0d49-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="b0d49-112">**Eylem** **System.Management.Automation.ScriptBlock** nesne bu menü öğesiyle ilişkili eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0d49-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="b0d49-113">**Kısayol** eylemi için klavye kısayolu.</span><span class="sxs-lookup"><span data-stu-id="b0d49-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="b0d49-114">**Döndürür** yeni eklediğiniz ISEMenuItem nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b0d49-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="b0d49-115">Temizle\(\)</span><span class="sxs-lookup"><span data-stu-id="b0d49-115">Clear\(\)</span></span>

<span data-ttu-id="b0d49-116">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b0d49-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b0d49-117">Tüm alt menüler menü öğesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b0d49-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="b0d49-118">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="b0d49-118">See Also</span></span>

- [<span data-ttu-id="b0d49-119">ISEMenuItem nesnesi</span><span class="sxs-lookup"><span data-stu-id="b0d49-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="b0d49-120">Nesne modeli komut dosyası Windows PowerShell ISE amacı</span><span class="sxs-lookup"><span data-stu-id="b0d49-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="b0d49-121">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="b0d49-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)