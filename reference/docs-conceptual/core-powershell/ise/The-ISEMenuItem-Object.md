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
# <a name="the-isemenuitem-object"></a><span data-ttu-id="b34fa-103">ISEMenuItem Nesnesi</span><span class="sxs-lookup"><span data-stu-id="b34fa-103">The ISEMenuItem Object</span></span>

<span data-ttu-id="b34fa-104">Bir **ISEMenuItem** nesnesidir Microsoft.PowerShell.Host.ISE.ISEMenuItem sınıfının bir örneği.</span><span class="sxs-lookup"><span data-stu-id="b34fa-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="b34fa-105">Tüm menü nesnelerde **eklentileri** menü örnekleridir **Microsoft.PowerShell.Host.ISE.ISEMenuItem** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b34fa-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="b34fa-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b34fa-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="b34fa-107">Görünen Ad</span><span class="sxs-lookup"><span data-stu-id="b34fa-107">DisplayName</span></span>

<span data-ttu-id="b34fa-108">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b34fa-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b34fa-109">Menü öğesi görünen adını alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="b34fa-109">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="b34fa-110">Eylem</span><span class="sxs-lookup"><span data-stu-id="b34fa-110">Action</span></span>

<span data-ttu-id="b34fa-111">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b34fa-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b34fa-112">Komut dosyası bloğunda alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="b34fa-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="b34fa-113">Menü öğesini tıklattığınızda eylemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="b34fa-113">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="b34fa-114">Kısayol</span><span class="sxs-lookup"><span data-stu-id="b34fa-114">Shortcut</span></span>

<span data-ttu-id="b34fa-115">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b34fa-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b34fa-116">Windows alır salt okunur özellik klavye kısayol menü öğesi için girin.</span><span class="sxs-lookup"><span data-stu-id="b34fa-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="b34fa-117">Alt menüler</span><span class="sxs-lookup"><span data-stu-id="b34fa-117">Submenus</span></span>

<span data-ttu-id="b34fa-118">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b34fa-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b34fa-119">Alır salt okunur özellik [alt menüler listesi](The-ISEMenuItemCollection-Object.md) menü öğesinin.</span><span class="sxs-lookup"><span data-stu-id="b34fa-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="b34fa-120">Komut dosyası örneği</span><span class="sxs-lookup"><span data-stu-id="b34fa-120">Scripting example</span></span>

<span data-ttu-id="b34fa-121">Eklentiler menü ve kodlanabilir özelliklerini kullanımını daha iyi anlamak için aşağıdaki komut dosyası örneği okuyun.</span><span class="sxs-lookup"><span data-stu-id="b34fa-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b34fa-122">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="b34fa-122">See Also</span></span>

- [<span data-ttu-id="b34fa-123">ISEMenuItemCollection nesnesi</span><span class="sxs-lookup"><span data-stu-id="b34fa-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="b34fa-124">Nesne modeli komut dosyası Windows PowerShell ISE amacı</span><span class="sxs-lookup"><span data-stu-id="b34fa-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="b34fa-125">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="b34fa-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)