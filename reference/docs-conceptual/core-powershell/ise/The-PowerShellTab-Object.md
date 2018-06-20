---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: PowerShellTab Nesnesi
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: c10f9106e31bb05828f1e76554ebe40ddb778340
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952520"
---
# <a name="the-powershelltab-object"></a>PowerShellTab Nesnesi

**PowerShellTab** nesnesi, bir Windows PowerShell çalışma zamanı ortamı temsil eder.

## <a name="methods"></a>Yöntemler

### <a name="invoke-script-"></a>Çağırma\( komut dosyası \)

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Belirtilen komut dosyası PowerShell sekmesindeki çalışır.

> [!NOTE]
> Bu yöntem, diğer PowerShell sekmelerde değil, çalıştırıldığı PowerShell sekmesi yalnızca çalışır. Herhangi bir nesne veya değer döndürmüyor. Kod herhangi bir değişken değiştirirse, bu değişiklikleri göre komutu çağrıldı sekmesinde kalıcı olmasını sağlar.

**Komut dosyası** -System.Management.Automation.ScriptBlock veya dize çalıştırmak için betik bloğu.

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a>InvokeSynchronous\( komut dosyası, \[useNewScope\], millisecondsTimeout \)

Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

Belirtilen komut dosyası PowerShell sekmesindeki çalışır.

> [!NOTE]
> Bu yöntem, diğer PowerShell sekmelerde değil, çalıştırıldığı PowerShell sekmesi yalnızca çalışır. Betik bloğu çalıştırın ve komut çağrılan çalışma ortamı betikten döndürülen herhangi bir değer döndürdü. Komut daha çalışması daha uzun sürerse **millesecondsTimeout** değerini belirtir, sonra komutu bir özel durum ile başarısız olur: "işlemi zaman aşımına uğradı."

**Komut dosyası** -System.Management.Automation.ScriptBlock veya dize çalıştırmak için betik bloğu.

**\[useNewScope\]**  -isteğe bağlı, varsayılan olarak Boolean **$true** varsa kümesine **$true**, sonra da yeni bir kapsam içinde komutu çalıştırmak oluşturulur. PowerShell sekmenin komutu tarafından belirtilen çalışma zamanı ortamı değiştirmez.

**\[millisecondsTimeout\]**  -varsayılan olarak isteğe bağlı tamsayı **500**.
Komut belirtilen süre içinde tamamlanmıyor sonra komut üretir bir **TimeoutException** iletiyle "işlemi zaman aşımına uğradı."

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

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

PowerShell sekmesini eklentileri menü alır salt okunur özellik.

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

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Döndürür salt okunur Boolean özelliği bir **$true** bir betik ile çağrılabilir değeri [Invoke (komut)](#invoke-script-) yöntemi.

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

Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.  Windows PowerShell ISE 2. 0 ' Bu taşıyordu **CommandPane**.

Konsol bölmesinde alır salt okunur özellik [Düzenleyicisi](../ise/The-ISEEditor-Object.md) nesnesi.

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a>Görünen Ad

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

PowerShell sekmesinde görüntülenen metni alır veya ayarlar okuma-yazma özelliği. Varsayılan olarak, sekmeler adlı "PowerShell #", burada # bir sayıyı gösterir.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a>ExpandedScript

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Okuma-yazma betik bölmesine genişletilmiş veya gizli olup olmadığını belirleyen bir Boolean özelliği.

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a>Dosyalar

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Alır salt okunur özellik [komut dosyaları koleksiyonunu](../ise/The-ISEFileCollection-Object.md) , PowerShell sekmede aç.

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a>Çıktı

Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerini yeniden adlandırıldı.  Windows PowerShell ISE sonraki sürümlerinde, kullandığınız **ConsolePane** aynı amaçlar için nesnesi.

Çıkış Bölmesi ' geçerli alır salt okunur özellik [Düzenleyicisi](../ise/The-ISEEditor-Object.md).

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a>Prompt

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Geçerli komut istemi metni alır salt okunur özellik. Not: **komut istemi** işlevi kullanıcı tarafından geçersiz '™ s profili. Sonuç dışında basit bir dize ise, bu özellik hiçbir şey döndürür.

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a>ShowCommands

Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

Komutları bölmesi görüntülenmekte olmadığını belirten okuma-yazma özelliği.

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a>StatusText

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Alır salt okunur özellik **PowerShellTab** durum metni.

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a>HorizontalAddOnToolsPaneOpened

Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

Yatay eklentileri araç bölmesini açık olup olmadığını belirten salt okunur özellik.

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a>VerticalAddOnToolsPaneOpened

Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

Dikey eklentileri araç bölmesini açık olup olmadığını belirten salt okunur özellik.

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a>Ayrıca bkz:

- [PowerShellTabCollection nesnesi](The-PowerShellTabCollection-Object.md)
- [Nesne modeli komut dosyası Windows PowerShell ISE amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)