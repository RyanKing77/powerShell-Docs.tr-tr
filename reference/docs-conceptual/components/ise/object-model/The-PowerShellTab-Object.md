---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: PowerShellTab Nesnesi
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: 577e2aaaddf3071801816d9ae91dbf0006dd5072
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057681"
---
# <a name="the-powershelltab-object"></a>PowerShellTab Nesnesi

**PowerShellTab** nesnesi, bir Windows PowerShell çalışma zamanı ortamı temsil eder.

## <a name="methods"></a>Yöntemler

### <a name="invoke-script-"></a>Çağırma\( betiği \)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

PowerShell sekmede belirtilen komut dosyasını çalıştırır.

> [!NOTE]
> Bu yöntem, yalnızca diğer PowerShell sekmelerde değil, çalıştırıldığı PowerShell sekme çalışır. Herhangi bir nesne veya değer döndürmez. Herhangi bir değişken kodunu değiştirir, bu değişiklikleri karşı komut çağrıldı sekmesinde kalıcı.

**Betik** -System.Management.Automation.ScriptBlock veya dize çalıştırılacak betik bloğu.

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a>InvokeSynchronous\( betiğini \[useNewScope\], millisecondsTimeout \)

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

PowerShell sekmede belirtilen komut dosyasını çalıştırır.

> [!NOTE]
> Bu yöntem, yalnızca diğer PowerShell sekmelerde değil, çalıştırıldığı PowerShell sekme çalışır. Betik bloğundaki çalıştırın ve komut'ni çağrılan çalıştırma ortamını betikten döndürülen herhangi bir değer döndürülür. Komut daha çalışması daha uzun sürerse **millesecondsTimeout** değerini belirtir ve ardından komut bir özel durum ile başarısız olur: "İşlemi zaman aşımına uğradı."

**Betik** -System.Management.Automation.ScriptBlock veya dize çalıştırılacak betik bloğu.

**\[useNewScope\]**  -isteğe bağlı, varsayılan olarak Boole **$true** varsa kümesine **$true**, sonra da yeni bir kapsam içinde komutu çalıştırmak oluşturulur. Çalışma zamanı ortamı komutu tarafından belirtilir PowerShell sekmesinin değiştirmez.

**\[millisecondsTimeout\]**  -varsayılan olarak, isteğe bağlı tamsayı **500**.
Komut, belirtilen süre içinde sonlanmaz sonra komut oluşturur. bir **TimeoutException** iletisiyle "işlemi zaman aşımına uğradı."

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

## <a name="properties"></a>Özellikler

### <a name="addonsmenu"></a>AddOnsMenu

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

PowerShell sekme için eklentiler menüsü alır salt okunur özellik.

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

### <a name="caninvoke"></a>CanInvoke

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Döndürür salt okunur Boolean özelliği bir **$true** bir betik ile çağrılabilir değeri [Invoke (betik)](#invoke-script-) yöntemi.

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

### <a name="consolepane"></a>Consolepane

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.  Bu Windows PowerShell ISE 2. 0'taşıyordu **CommandPane**.

Konsol bölmesinde salt okunur özelliği [Düzenleyicisi](The-ISEEditor-Object.md) nesne.

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a>Görünen Ad

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

PowerShell sekmesinde görüntülenen metni alır veya ayarlar okuma-yazma özelliği. Varsayılan olarak, sekmeleri adlandırılır "PowerShell #", # temsil ettiği bir sayı.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a>ExpandedScript

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Okuma-yazma betik bölmesini genişletilmiş veya gizli olup olmadığını belirleyen bir Boolean özelliği.

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a>Dosyalar

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Salt okunur özelliği [komut dosyaları koleksiyonu](The-ISEFileCollection-Object.md) olan PowerShell sekmesini açın.

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a>Çıktı

Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerde yeniden adlandırıldı.  Windows PowerShell ISE sonraki sürümlerinde kullanabileceğiniz **ConsolePane** aynı amaçlar için nesne.

Çıkış Bölmesi'geçerli alan salt okunur özelliği [Düzenleyicisi](The-ISEEditor-Object.md).

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a>İstem

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Geçerli istem metnini alır salt okunur özellik. Not: **istemi** işlevi kullanıcı tarafından geçersiz kılınabilir '™ s profili. Sonuç dışında basit bir dize ise, bu özellik nothing döndürür.

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a>ShowCommands

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Komutları bölmesinde şu anda gösterilip gösterilmediğini gösterir okuma-yazma özelliği.

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a>StatusText

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Salt okunur özelliği **PowerShellTab** durum metni.

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a>HorizontalAddOnToolsPaneOpened

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Yatay eklentileri araç bölmesini şu anda açık olup olmadığını belirten salt okunur özellik.

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a>VerticalAddOnToolsPaneOpened

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Dikey eklentileri araç bölmesini şu anda açık olup olmadığını belirten salt okunur özellik.

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a>Ayrıca bkz:

- [PowerShellTabCollection nesnesi](The-PowerShellTabCollection-Object.md)
- [Windows PowerShell ISE betik oluşturma nesne modelinin amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)