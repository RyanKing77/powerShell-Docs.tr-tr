---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: ISEEditor nesnesi
ms.openlocfilehash: c593eeebf0b9a94769841efd2aa78f84a3829ca5
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2017
---
# <a name="the-iseeditor-object"></a>ISEEditor nesnesi
  Bir **ISEEditor** nesnesidir Microsoft.PowerShell.Host.ISE.ISEEditor sınıfının bir örneği. Konsol bölmesinde bir **ISEEditor** nesnesi. Her [ISEFile](The-ISEFile-Object.md) nesne olan ilişkili bir **ISEEditor** nesnesi. Aşağıdaki bölümlerde yöntemleri ve özellikleri listelenmektedir bir **ISEEditor** nesnesi.

## <a name="methods"></a>Yöntemler

### <a name="clear"></a>Temizle\(\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Metin Düzenleyicisi'nde temizler.

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a>EnsureVisible\(int lineNumber\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Böylece satır için karşılık gelen düzenleyicisi kayar belirtilen **lineNumber** parametre değeri görülebilir. Belirtilen satır numarası geçerli satır numaralarını tanımlayan 1, son satır numarası, aralığının dışında olması durumunda bir özel durum oluşturur.

 **lineNumber** görünür duruma getirilecek satır sayısı.

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view. 
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a>Odağı\(\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Odağı düzenleyiciye ayarlar.

```powershell
# Sets focus to the Console pane. 
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a>GetLineLength\(int lineNumber\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Satır uzunluğu bir tamsayı olarak satır sayısı ile belirtilen satır alır.

 **lineNumber** de uzunluğu almak satır sayısı.

 **Döndürür** belirtilen satır numarası satırında satır uzunluğu.

```powershell
# Gets the length of the first line in the text of the Command pane. 
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a>GoToMatch\(\)
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil. 

 Şapka eşleşen karakter taşınır **CanGoToMatch** editor nesnesi özelliği **$true**, düzeltme işareti hemen bir açma ayracı, köşeli ayraç veya parantezi - önce olduğunda oluşur \(,\[, {- veya hemen sonra bir kapanış parantezi, köşeli ayraç ya da küme parantezi - \),\],}.  Düzeltme işareti bir açılış karakter önce veya sonra kapatma karakterini yerleştirilir. Varsa **CanGoToMatch** özelliği **$false**, sonra da bu yöntem hiçbir şey yapmaz.

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace.
```

### <a name="inserttext-text-"></a>E:System.Windows.Forms.Control.Click\( metin\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Seçimi metinle değiştirir veya metni geçerli düzeltme işareti konumuna ekler.

 **metin** -eklemek için metin dizesi.

 Bkz: [örnek komut dosyası](#scripting-example) bu konuda daha sonra.

### <a name="select-startline-startcolumn-endline-endcolumn-"></a>Seçin\( startLine, startColumn, endLine, endColumn\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Metinden seçer **startLine**, **startColumn**, **endLine**, ve **endColumn** parametreleri.

 **startLine** -tamsayı seçimi başladığı satır.

 **startColumn** -tamsayı sütunu seçimi başladığı başlangıç satırı içinde.

 **endLine** -tamsayı seçimi bittiği satır.

 **endColumn** -tamsayı sütunu satır sonu seçimi bittiği içinde.

 Bkz: [örnek komut dosyası](#scripting-example) bu konuda daha sonra.

### <a name="selectcaretline"></a>SelectCaretLine\(\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Şu anda düzeltme işareti içeren metin satırının tamamına seçer.

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1) 
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a>SetCaretPosition\( lineNumber, columnNumber\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 İmleç konumunu satır numarasını ve sütun sayısını ayarlar. Şapka satır numarası ya da düzeltme işareti sütun numarası kendi ilgili geçerli aralıklar dışında olması durumunda bir özel durum oluşturur.

 **lineNumber** -tamsayı şapka satır numarası.

 **columnNumber** -tamsayı şapka sütun numarası.

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a>ToggleOutliningExpansion\(\)
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil. 

 Genişletmek veya daraltmak tüm anahat bölümleri neden olur.

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a>Özellikler

### <a name="cangotomatch"></a>CanGoToMatch
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil. 

 Şapka parantez, köşeli ayraç veya parantezi - yanındaki olup olmadığını belirtmek için salt okunur Boolean özelliği \( \), \[ \], {}. Şapka açılış karakter hemen önce bir çift kapanış karakterinin hemen sonra mı sonra bu özellik değeri **$true**. Aksi takdirde, değer **$false**.

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a>CaretColumn
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Sütun sayısını alır salt okunur özelliği şapka konuma karşılık gelir.

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a>CaretLine
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Düzeltme işareti içeren satırı sayısını alır salt okunur özellik.

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a>CaretLineText
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Tam metin satırının alır salt okunur özellik şapka içerir.

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a>LineCount
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Satır sayısı Düzenleyicisi'nden alır salt okunur özellik.

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a>Metin
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Seçili metni Düzenleyicisi'nden alır salt okunur özellik.

 Bkz: [örnek komut dosyası](#scripting-example) bu konuda daha sonra.

### <a name="text"></a>Metin
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Alır veya metin düzenleyicide ayarlar okuma/yazma özelliği.

 Bkz: [örnek komut dosyası](#scripting-example) bu konuda daha sonra.

## <a name="scripting-example"></a>Örnek komut dosyası oluşturma

```powershell
# This illustrates how you can use the length of a line to
# select the entire line and shows how you can make it lowercase. 
# You must run this in the Console pane. It will not run in the Script pane.
# Begin by getting a variable that points to the editor.
$myEditor = $psISE.CurrentFile.Editor
# Clear the text in the current file editor.
$myEditor.Clear()

# Make sure the file has five lines of text.
$myEditor.InsertText("LINE1 `n")
$myEditor.InsertText("LINE2 `n")
$myEditor.InsertText("LINE3 `n")
$myEditor.InsertText("LINE4 `n")
$myEditor.InsertText("LINE5 `n")

# Use the GetLineLength method to get the length of the third line. 
$endColumn= $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1,1,3,$endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a>Ayrıca bkz:
- [ISEFile nesnesi](The-ISEFile-Object.md) 
- [PowerShellTab nesnesi](The-PowerShellTab-Object.md) 
- [Windows PowerShell ISE nesne modeli komut dosyası oluşturma](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE nesne modeli başvurusu](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [ISE nesne modeli hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)

  
