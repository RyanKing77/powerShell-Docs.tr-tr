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
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="a9d37-103">ISEMenuItemCollection Nesnesi</span><span class="sxs-lookup"><span data-stu-id="a9d37-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="a9d37-104">Bir **Isemenuıtemcollection** nesnedir koleksiyonu **Isemenuıtem** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="a9d37-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="a9d37-105">Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection sınıfının bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="a9d37-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="a9d37-106">Bir örnek **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** özelleştirmek için kullanılan nesne **eklenti** menü, Windows PowerShell® Tümleşik komut dosyası ortamı (ISE).</span><span class="sxs-lookup"><span data-stu-id="a9d37-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="a9d37-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a9d37-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="a9d37-108">Ekleme\(DisplayName, System.Management.Automation.ScriptBlock eylem System.Windows.Input.KeyGesture kısayol dize \)</span><span class="sxs-lookup"><span data-stu-id="a9d37-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="a9d37-109">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a9d37-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="a9d37-110">Bir menü öğesi koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="a9d37-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="a9d37-111">**DisplayName** eklenecek menüsünde görünen adı.</span><span class="sxs-lookup"><span data-stu-id="a9d37-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="a9d37-112">**Eylem** **System.Management.Automation.ScriptBlock** nesnesini bu menü öğesiyle ilişkili eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9d37-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="a9d37-113">**Kısayol** eylemi için klavye kısayol.</span><span class="sxs-lookup"><span data-stu-id="a9d37-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="a9d37-114">**Döndürür** yeni eklenenler Isemenuıtem nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a9d37-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="a9d37-115">Temizle\(\)</span><span class="sxs-lookup"><span data-stu-id="a9d37-115">Clear\(\)</span></span>

<span data-ttu-id="a9d37-116">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a9d37-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="a9d37-117">Tüm alt menü öğesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a9d37-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="a9d37-118">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a9d37-118">See Also</span></span>

- [<span data-ttu-id="a9d37-119">Isemenuıtem nesnesi</span><span class="sxs-lookup"><span data-stu-id="a9d37-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="a9d37-120">Windows PowerShell ISE betik oluşturma nesne modelinin amacı</span><span class="sxs-lookup"><span data-stu-id="a9d37-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="a9d37-121">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="a9d37-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
