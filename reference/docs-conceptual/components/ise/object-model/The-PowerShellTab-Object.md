---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: PowerShellTab Nesnesi
ms.openlocfilehash: bfa11b553f97b7b27b974855ff4e8f1a48c33fea
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028913"
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="615ea-103">PowerShellTab Nesnesi</span><span class="sxs-lookup"><span data-stu-id="615ea-103">The PowerShellTab Object</span></span>

<span data-ttu-id="615ea-104">**PowerShellTab** nesnesi, bir Windows PowerShell çalışma zamanı ortamı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="615ea-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="615ea-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="615ea-105">Methods</span></span>

### <a name="invoke-script-"></a><span data-ttu-id="615ea-106">Çağırma\( betiği \)</span><span class="sxs-lookup"><span data-stu-id="615ea-106">Invoke\( Script \)</span></span>

<span data-ttu-id="615ea-107">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="615ea-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="615ea-108">PowerShell sekmede belirtilen komut dosyasını çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="615ea-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="615ea-109">Bu yöntem, yalnızca diğer PowerShell sekmelerde değil, çalıştırıldığı PowerShell sekme çalışır.</span><span class="sxs-lookup"><span data-stu-id="615ea-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="615ea-110">Herhangi bir nesne veya değer döndürmez.</span><span class="sxs-lookup"><span data-stu-id="615ea-110">It does not return any object or value.</span></span> <span data-ttu-id="615ea-111">Herhangi bir değişken kodunu değiştirir, bu değişiklikleri karşı komut çağrıldı sekmesinde kalıcı.</span><span class="sxs-lookup"><span data-stu-id="615ea-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

<span data-ttu-id="615ea-112">**Betik** -System.Management.Automation.ScriptBlock veya dize çalıştırılacak betik bloğu.</span><span class="sxs-lookup"><span data-stu-id="615ea-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="615ea-113">InvokeSynchronous\( betiğini \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="615ea-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>

<span data-ttu-id="615ea-114">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="615ea-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="615ea-115">PowerShell sekmede belirtilen komut dosyasını çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="615ea-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="615ea-116">Bu yöntem, yalnızca diğer PowerShell sekmelerde değil, çalıştırıldığı PowerShell sekme çalışır.</span><span class="sxs-lookup"><span data-stu-id="615ea-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="615ea-117">Betik bloğundaki çalıştırın ve komut'ni çağrılan çalıştırma ortamını betikten döndürülen herhangi bir değer döndürülür.</span><span class="sxs-lookup"><span data-stu-id="615ea-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="615ea-118">Komut daha çalışması daha uzun sürerse **millesecondsTimeout** değerini belirtir ve ardından komut bir özel durum ile başarısız olur: "İşlemi zaman aşımına uğradı."</span><span class="sxs-lookup"><span data-stu-id="615ea-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

<span data-ttu-id="615ea-119">**Betik** -System.Management.Automation.ScriptBlock veya dize çalıştırılacak betik bloğu.</span><span class="sxs-lookup"><span data-stu-id="615ea-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

<span data-ttu-id="615ea-120">**\[useNewScope\]**  -isteğe bağlı, varsayılan olarak Boole **$true** varsa kümesine **$true**, sonra da yeni bir kapsam içinde komutu çalıştırmak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="615ea-120">**\[useNewScope\]** -  Optional Boolean that defaults to **$true** If set to **$true**, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="615ea-121">Çalışma zamanı ortamı komutu tarafından belirtilir PowerShell sekmesinin değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="615ea-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

<span data-ttu-id="615ea-122">**\[millisecondsTimeout\]**  -varsayılan olarak, isteğe bağlı tamsayı **500**.</span><span class="sxs-lookup"><span data-stu-id="615ea-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="615ea-123">Komut, belirtilen süre içinde sonlanmaz sonra komut oluşturur. bir **TimeoutException** iletisiyle "işlemi zaman aşımına uğradı."</span><span class="sxs-lookup"><span data-stu-id="615ea-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

```powershell
# Create a new PowerShell tab and then switch back to the first
$psISE.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0])

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1', $false)
# You can switch to the other tab and type '$x' to see that the value is saved there.

# This example sets a value in the other tab (in a different scope)
# and returns it through the pipeline to this tab to store in $a
$a = $psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z')
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
Measure-Command {$psISE.PowerShellTabs[1].InvokeSynchronous('sleep 10', $false, 5000)}
```

## <a name="properties"></a><span data-ttu-id="615ea-124">Özellikler</span><span class="sxs-lookup"><span data-stu-id="615ea-124">Properties</span></span>

### <a name="addonsmenu"></a><span data-ttu-id="615ea-125">AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="615ea-125">AddOnsMenu</span></span>

<span data-ttu-id="615ea-126">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="615ea-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="615ea-127">PowerShell sekme için eklentiler menüsü alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="615ea-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

```powershell
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

### <a name="caninvoke"></a><span data-ttu-id="615ea-128">CanInvoke</span><span class="sxs-lookup"><span data-stu-id="615ea-128">CanInvoke</span></span>

<span data-ttu-id="615ea-129">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="615ea-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="615ea-130">Döndürür salt okunur Boolean özelliği bir **$true** bir betik ile çağrılabilir değeri [Invoke (betik)](#invoke-script-) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="615ea-130">The read-only Boolean property that returns a **$true** value if a script can be invoked with the [Invoke( Script )](#invoke-script-) method.</span></span>

```powershell
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab.
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psISE.PowerShellTabs[1]
$secondTab.CanInvoke
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke
```

### <a name="consolepane"></a><span data-ttu-id="615ea-131">Consolepane</span><span class="sxs-lookup"><span data-stu-id="615ea-131">Consolepane</span></span>

<span data-ttu-id="615ea-132">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="615ea-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>  <span data-ttu-id="615ea-133">Bu Windows PowerShell ISE 2. 0'taşıyordu **CommandPane**.</span><span class="sxs-lookup"><span data-stu-id="615ea-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

<span data-ttu-id="615ea-134">Konsol bölmesinde salt okunur özelliği [Düzenleyicisi](The-ISEEditor-Object.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="615ea-134">The read-only property that gets the Console pane [editor](The-ISEEditor-Object.md) object.</span></span>

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a><span data-ttu-id="615ea-135">Görünen Ad</span><span class="sxs-lookup"><span data-stu-id="615ea-135">DisplayName</span></span>

<span data-ttu-id="615ea-136">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="615ea-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="615ea-137">PowerShell sekmesinde görüntülenen metni alır veya ayarlar okuma-yazma özelliği. Varsayılan olarak, sekmeleri adlandırılır "PowerShell #", # temsil ettiği bir sayı.</span><span class="sxs-lookup"><span data-stu-id="615ea-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab. By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a><span data-ttu-id="615ea-138">ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="615ea-138">ExpandedScript</span></span>

<span data-ttu-id="615ea-139">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="615ea-139">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="615ea-140">Okuma-yazma betik bölmesini genişletilmiş veya gizli olup olmadığını belirleyen bir Boolean özelliği.</span><span class="sxs-lookup"><span data-stu-id="615ea-140">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a><span data-ttu-id="615ea-141">Dosyalar</span><span class="sxs-lookup"><span data-stu-id="615ea-141">Files</span></span>

<span data-ttu-id="615ea-142">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="615ea-142">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="615ea-143">Salt okunur özelliği [komut dosyaları koleksiyonu](The-ISEFileCollection-Object.md) olan PowerShell sekmesini açın.</span><span class="sxs-lookup"><span data-stu-id="615ea-143">The read-only property that gets the [collection of script files](The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a><span data-ttu-id="615ea-144">Çıktı</span><span class="sxs-lookup"><span data-stu-id="615ea-144">Output</span></span>

<span data-ttu-id="615ea-145">Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerde yeniden adlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="615ea-145">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="615ea-146">Windows PowerShell ISE sonraki sürümlerinde kullanabileceğiniz **ConsolePane** aynı amaçlar için nesne.</span><span class="sxs-lookup"><span data-stu-id="615ea-146">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

<span data-ttu-id="615ea-147">Çıkış Bölmesi'geçerli alan salt okunur özelliği [Düzenleyicisi](The-ISEEditor-Object.md).</span><span class="sxs-lookup"><span data-stu-id="615ea-147">The read-only property that gets the Output pane of the current [editor](The-ISEEditor-Object.md).</span></span>

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a><span data-ttu-id="615ea-148">İstem</span><span class="sxs-lookup"><span data-stu-id="615ea-148">Prompt</span></span>

<span data-ttu-id="615ea-149">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="615ea-149">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="615ea-150">Geçerli istem metnini alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="615ea-150">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="615ea-151">Not: **istemi** işlevi kullanıcı tarafından geçersiz kılınabilir '™ s profili.</span><span class="sxs-lookup"><span data-stu-id="615ea-151">Note: the **Prompt** function can be overridden by the user'™s profile.</span></span> <span data-ttu-id="615ea-152">Sonuç dışında basit bir dize ise, bu özellik nothing döndürür.</span><span class="sxs-lookup"><span data-stu-id="615ea-152">If the result is other than a simple string, then this property returns nothing.</span></span>

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a><span data-ttu-id="615ea-153">ShowCommands</span><span class="sxs-lookup"><span data-stu-id="615ea-153">ShowCommands</span></span>

<span data-ttu-id="615ea-154">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="615ea-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="615ea-155">Komutları bölmesinde şu anda gösterilip gösterilmediğini gösterir okuma-yazma özelliği.</span><span class="sxs-lookup"><span data-stu-id="615ea-155">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a><span data-ttu-id="615ea-156">StatusText</span><span class="sxs-lookup"><span data-stu-id="615ea-156">StatusText</span></span>

<span data-ttu-id="615ea-157">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="615ea-157">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="615ea-158">Salt okunur özelliği **PowerShellTab** durum metni.</span><span class="sxs-lookup"><span data-stu-id="615ea-158">The read-only property that gets the **PowerShellTab** status text.</span></span>

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a><span data-ttu-id="615ea-159">HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="615ea-159">HorizontalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="615ea-160">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="615ea-160">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="615ea-161">Yatay eklentileri araç bölmesini şu anda açık olup olmadığını belirten salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="615ea-161">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a><span data-ttu-id="615ea-162">VerticalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="615ea-162">VerticalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="615ea-163">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="615ea-163">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="615ea-164">Dikey eklentileri araç bölmesini şu anda açık olup olmadığını belirten salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="615ea-164">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="615ea-165">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="615ea-165">See Also</span></span>

- [<span data-ttu-id="615ea-166">PowerShellTabCollection nesnesi</span><span class="sxs-lookup"><span data-stu-id="615ea-166">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md)
- [<span data-ttu-id="615ea-167">Windows PowerShell ISE betik oluşturma nesne modelinin amacı</span><span class="sxs-lookup"><span data-stu-id="615ea-167">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="615ea-168">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="615ea-168">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
