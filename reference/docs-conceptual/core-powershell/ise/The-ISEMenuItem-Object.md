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
# <a name="the-isemenuitem-object"></a><span data-ttu-id="b90ef-103">ISEMenuItem nesnesi</span><span class="sxs-lookup"><span data-stu-id="b90ef-103">The ISEMenuItem Object</span></span>
  <span data-ttu-id="b90ef-104">Bir **ISEMenuItem** nesnesidir Microsoft.PowerShell.Host.ISE.ISEMenuItem sınıfının bir örneği.</span><span class="sxs-lookup"><span data-stu-id="b90ef-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="b90ef-105">Tüm menü nesnelerde **eklentileri** menü örnekleridir **Microsoft.PowerShell.Host.ISE.ISEMenuItem** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b90ef-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="b90ef-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b90ef-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="b90ef-107">Görünen Ad</span><span class="sxs-lookup"><span data-stu-id="b90ef-107">DisplayName</span></span>
  <span data-ttu-id="b90ef-108">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b90ef-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b90ef-109">Menü öğesi görünen adını alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="b90ef-109">The read-only property that gets the display name of the menu item.</span></span>

```
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName

```

### <a name="action"></a><span data-ttu-id="b90ef-110">Eylem</span><span class="sxs-lookup"><span data-stu-id="b90ef-110">Action</span></span>
  <span data-ttu-id="b90ef-111">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b90ef-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b90ef-112">Komut dosyası bloğunda alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="b90ef-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="b90ef-113">Menü öğesini tıklattığınızda eylemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="b90ef-113">It invokes the action when you click the menu item.</span></span>

```
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item 
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="b90ef-114">Kısayol</span><span class="sxs-lookup"><span data-stu-id="b90ef-114">Shortcut</span></span>
  <span data-ttu-id="b90ef-115">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b90ef-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b90ef-116">Windows alır salt okunur özellik klavye kısayol menü öğesi için girin.</span><span class="sxs-lookup"><span data-stu-id="b90ef-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="b90ef-117">Alt menüler</span><span class="sxs-lookup"><span data-stu-id="b90ef-117">Submenus</span></span>
  <span data-ttu-id="b90ef-118">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b90ef-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="b90ef-119">Alır salt okunur özellik [alt menüler listesi](The-ISEMenuItemCollection-Object.md) menü öğesinin.</span><span class="sxs-lookup"><span data-stu-id="b90ef-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="b90ef-120">Komut dosyası örneği</span><span class="sxs-lookup"><span data-stu-id="b90ef-120">Scripting example</span></span>
 <span data-ttu-id="b90ef-121">Eklentiler menü ve kodlanabilir özelliklerini kullanımını daha iyi anlamak için aşağıdaki komut dosyası örneği okuyun.</span><span class="sxs-lookup"><span data-stu-id="b90ef-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b90ef-122">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="b90ef-122">See Also</span></span>
- [<span data-ttu-id="b90ef-123">ISEMenuItemCollection nesnesi</span><span class="sxs-lookup"><span data-stu-id="b90ef-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md) 
- [<span data-ttu-id="b90ef-124">Windows PowerShell ISE nesne modeli komut dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="b90ef-124">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="b90ef-125">Windows PowerShell ISE nesne modeli başvurusu</span><span class="sxs-lookup"><span data-stu-id="b90ef-125">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="b90ef-126">ISE nesne modeli hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="b90ef-126">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
