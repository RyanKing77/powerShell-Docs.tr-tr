---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: PowerShellTab nesnesi
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: 15d9a7474e4c2cf2a9ff8edb88802106489cdba1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="the-powershelltab-object"></a>PowerShellTab nesnesi
  **PowerShellTab** nesnesi, bir Windows PowerShell çalışma zamanı ortamı temsil eder.

## <a name="methods"></a>Yöntemler

### <a name="invoke-script-"></a>Çağırma\( komut dosyası\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Belirtilen komut dosyası PowerShell sekmesindeki çalışır.

> [!NOTE]
> Bu yöntem, diğer PowerShell sekmelerde değil, çalıştırıldığı PowerShell sekmesi yalnızca çalışır. Herhangi bir nesne veya değer döndürmüyor. Kod herhangi bir değişken değiştirirse, bu değişiklikleri göre komutu çağrıldı sekmesinde kalıcı olmasını sağlar.

 **Komut dosyası** -System.Management.Automation.ScriptBlock veya dize çalıştırmak için betik bloğu.

```
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psise.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a>InvokeSynchronous\( komut dosyası, \[useNewScope\], millisecondsTimeout\)
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil. 

 Belirtilen komut dosyası PowerShell sekmesindeki çalışır.

> [!NOTE]
> Bu yöntem, diğer PowerShell sekmelerde değil, çalıştırıldığı PowerShell sekmesi yalnızca çalışır. Betik bloğu çalıştırın ve komut çağrılan çalışma ortamı betikten döndürülen herhangi bir değer döndürdü. Komut daha çalışması daha uzun sürerse **millesecondsTimeout** değerini belirtir, sonra komutu bir özel durum ile başarısız olur: "işlemi zaman aşımına uğradı."

 **Komut dosyası** -System.Management.Automation.ScriptBlock veya dize çalıştırmak için betik bloğu.

 **\[useNewScope\]**  -isteğe bağlı, varsayılan olarak Boolean **$true** varsa kümesine **$true**, sonra da yeni bir kapsam içinde komutu çalıştırmak oluşturulur. PowerShell sekmenin komutu tarafından belirtilen çalışma zamanı ortamı değiştirmez.

 **\[millisecondsTimeout\]**  -varsayılan olarak isteğe bağlı tamsayı **500**.
Komut belirtilen süre içinde tamamlanmıyor sonra komut üretir bir **TimeoutException** iletiyle "işlemi zaman aşımına uğradı."

```
# create a new PowerShell tab and then switch back to the first
$PSise.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0]) 

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1',$false)
# You can switch to the other tab and type 'œ$x' to see that the value is saved there.

# This example sets a value in the other tab (in a different scope) 
# and returns it through the pipeline to this tab to store in $a
$a=$psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z') 
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
measure-command {$psISE.PowerShellTabs[1].InvokeSynchronous("sleep 10",$false,5000)}

```

## <a name="properties"></a>Özellikler

### <a name="addonsmenu"></a>AddOnsMenu
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 PowerShell sekmesini eklentileri menü alır salt okunur özellik.

```
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

### <a name="caninvoke"></a>CanInvoke
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Döndürür salt okunur Boolean özelliği bir **$true** bir betik ile çağrılabilir değeri [Invoke (komut)](#invoke-script-) yöntemi.

```
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab. 
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psise.PowerShellTabs[1] 
$secondTab.CanInvoke 
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke

```

### <a name="consolepane"></a>Consolepane
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.  Windows PowerShell ISE 2. 0 ' Bu taşıyordu **CommandPane**.

 Konsol bölmesinde alır salt okunur özellik [Düzenleyicisi](../ise/The-ISEEditor-Object.md) nesnesi.

```
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane

```

### <a name="displayname"></a>Görünen Ad
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 PowerShell sekmesinde görüntülenen metni alır veya ayarlar okuma-yazma özelliği. Varsayılan olarak, sekmeler adlı "PowerShell #", burada # bir sayıyı gösterir.

```
$newTab = $psise.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

### <a name="expandedscript"></a>ExpandedScript
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Okuma-yazma betik bölmesine genişletilmiş veya gizli olup olmadığını belirleyen bir Boolean özelliği.

```
# Toggle the expanded script property to see its effect.
$PSise.CurrentPowerShellTab.ExpandedScript=!$PSise.CurrentPowerShellTab.ExpandedScript

```

### <a name="files"></a>Dosyalar
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Alır salt okunur özellik [komut dosyaları koleksiyonunu](../ise/The-ISEFileCollection-Object.md) , PowerShell sekmede aç.

```
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb" 
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a>Çıktı
  Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerini yeniden adlandırıldı.  Windows PowerShell ISE sonraki sürümlerinde, kullandığınız **ConsolePane** aynı amaçlar için nesnesi.

 Çıkış Bölmesi ' geçerli alır salt okunur özellik [Düzenleyicisi](../ise/The-ISEEditor-Object.md).

```
# Clears the text in the Output pane.
$psise.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a>istemi
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Geçerli komut istemi metni alır salt okunur özellik. Not: **komut istemi** işlevi kullanıcı tarafından geçersiz '™ s profili. Sonuç dışında basit bir dize ise, bu özellik hiçbir şey döndürür.

```
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a>ShowCommands
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil. 

 Komutları bölmesi görüntülenmekte olmadığını belirten okuma-yazma özelliği.

```
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $True
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands=$True}
```

### <a name="statustext"></a>StatusText
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Alır salt okunur özellik **PowerShellTab** durum metni.

```
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a>HorizontalAddOnToolsPaneOpened
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil. 

 Yatay eklentileri araç bölmesini açık olup olmadığını belirten salt okunur özellik.

```
# Gets the current state of the horizontal Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a>VerticalAddOnToolsPaneOpened
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil. 

 Dikey eklentileri araç bölmesini açık olup olmadığını belirten salt okunur özellik.

```
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands=$True
# Gets the current state of the vertical Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a>Ayrıca bkz:
- [PowerShellTabCollection nesnesi](The-PowerShellTabCollection-Object.md) 
- [Windows PowerShell ISE nesne modeli komut dosyası oluşturma](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE nesne modeli başvurusu](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [ISE nesne modeli hiyerarşisi](../ise/The-ISE-Object-Model-Hierarchy.md)

  
