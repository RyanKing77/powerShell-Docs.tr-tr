---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISEEditor Nesnesi
ms.openlocfilehash: 2d4c3d941035384c591ca57e809c0e3a9b852f5c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405951"
---
# <a name="the-iseeditor-object"></a>ISEEditor Nesnesi

Bir **Iseeditor** nesnedir Microsoft.PowerShell.Host.ISE.ISEEditor sınıfının örneği. Konsolunda bölmesinin bir **Iseeditor** nesne. Her [Isefile](The-ISEFile-Object.md) nesnesinde ilişkili bir **Iseeditor** nesne. Aşağıdaki bölümlerde yöntemleri ve özellikleri listelemek bir **Iseeditor** nesne.

## <a name="methods"></a>Yöntemler

### <a name="clear"></a>Temizle\(\)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Düzenleyicide metni temizler.

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a>EnsureVisible\(int lineNumber\)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Düzenleyici böylece satır için karşılık gelen kayan belirtilen **lineNumber** parametre değeri olduğu görünür. Belirtilen satır numarası geçerli satır numaralarını tanımlayan 1, son satır numarası aralığı dışında ise bir özel durum oluşturur.

**lineNumber** görünür yapılacak satır sayısı.

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a>Odağı\(\)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Odağı düzenleyiciye ayarlar.

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a>GetLineLength\(int lineNumber \)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Satır uzunluğu, satır numarası tarafından belirtilen satır için bir tamsayı olarak alır.

**lineNumber** uzunluğu alınacağı, satır sayısı.

**Döndürür** belirtilen satır numarası satırı için satır uzunluğu.

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a>GoToMatch\(\)

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Giriş işaretini eşleşen karaktere taşıyan **CanGoToMatch** Düzenleyicisi nesnenin özellik **$true**, giriş işaretini hemen bir açma parantezi, köşeli ayraç veya küme ayracı - önce olduğunda gerçekleşir \(,\[, {- veya hemen sonra bir kapatma ayracı, köşeli ayraç veya küme ayracı - \),\],}.  Giriş işaretini bir açılış karakterden önce veya sonra bir kapatma karakteri yer alır. Varsa **CanGoToMatch** özelliği **$false**, sonra da bu yöntemi hiçbir şey yapmaz.

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a>E:System.Windows.Forms.Control.Click\( metin \)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Seçimi metinle değiştirir veya metni geçerli giriş işareti konumuna ekler.

**metin** -eklemek için metin dizesi.

Bkz: [örnek komut dosyası](#scripting-example) bu konuda.

### <a name="select-startline-startcolumn-endline-endcolumn-"></a>Seçin\( startLine, startColumn, endLine, endColumn \)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Metinden seçer **startLine**, **startColumn**, **endLine**, ve **endColumn** parametreleri.

**startLine** -seçimi başladığı satırın tamsayı.

**startColumn** -tamsayı seçimi başladığı başlangıç satırı içindeki sütun.

**endLine** -sona ereceği Seçimi satırın tamsayı.

**endColumn** -sütun seçimi sona ereceği satır sonu içinde tamsayı.

Bkz: [örnek komut dosyası](#scripting-example) bu konuda.

### <a name="selectcaretline"></a>SelectCaretLine\(\)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Şu anda giriş işaretini içeren metin tüm satırı seçer.

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a>SetCaretPosition\( lineNumber, columnNumber \)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Giriş işareti konumunu, satır numarası ve sütun sayısını ayarlar. Giriş işaretini satır numarası ya da giriş işaretini sütun numarası, ilgili geçerli aralık dışında ise bir özel durum oluşturur.

**lineNumber** -tamsayı giriş işaretini satır numarası.

**columnNumber** -tamsayı giriş işaretini sütun numarası.

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a>ToggleOutliningExpansion\(\)

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Genişletmek veya daraltmak tüm ana hattı bölümleri neden olur.

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a>Özellikler

### <a name="cangotomatch"></a>CanGoToMatch

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Giriş işaretini bir parantez, köşeli ayraç veya küme ayracı - yanındaki olup olmadığını belirtmek için salt okunur Boolean özelliği \( \), \[ \], {}. Giriş işaretini açılış karakterden hemen önce bir çift kapatma karakterini hemen sonra mı sonra bu özellik değeri **$true**. Aksi halde **$false**.

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a>CaretColumn

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Sütun numarası, salt okunur özelliği giriş işareti konumuna karşılık gelir.

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a>CaretLine

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Giriş işaretini içeren satırı sayısını alır salt okunur özellik.

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a>CaretLineText

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Giriş işaretini içeren metin tam satırının alan salt okunur özelliği.

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a>LineCount

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Satır sayısı Düzenleyicisi'nden alır salt okunur özellik.

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a>Metin

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Seçili metin Düzenleyicisi'nden alır salt okunur özellik.

Bkz: [örnek komut dosyası](#scripting-example) bu konuda.

### <a name="text"></a>Metin

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Alır veya metin düzenleyicide ayarlar okuma/yazma özelliği.

Bkz: [örnek komut dosyası](#scripting-example) bu konuda.

## <a name="scripting-example"></a>Örnek betik

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
$endColumn = $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1, 1, 3, $endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a>Ayrıca bkz:

- [Isefile nesnesi](The-ISEFile-Object.md)
- [PowerShellTab nesnesi](The-PowerShellTab-Object.md)
- [Windows PowerShell ISE betik oluşturma nesne modelinin amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)