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
# <a name="the-iseeditor-object"></a><span data-ttu-id="e4c2e-103">ISEEditor Nesnesi</span><span class="sxs-lookup"><span data-stu-id="e4c2e-103">The ISEEditor Object</span></span>

<span data-ttu-id="e4c2e-104">Bir **Iseeditor** nesnedir Microsoft.PowerShell.Host.ISE.ISEEditor sınıfının örneği.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="e4c2e-105">Konsolunda bölmesinin bir **Iseeditor** nesne.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="e4c2e-106">Her [Isefile](The-ISEFile-Object.md) nesnesinde ilişkili bir **Iseeditor** nesne.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="e4c2e-107">Aşağıdaki bölümlerde yöntemleri ve özellikleri listelemek bir **Iseeditor** nesne.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="e4c2e-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e4c2e-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="e4c2e-109">Temizle\(\)</span><span class="sxs-lookup"><span data-stu-id="e4c2e-109">Clear\(\)</span></span>

<span data-ttu-id="e4c2e-110">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e4c2e-111">Düzenleyicide metni temizler.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="e4c2e-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="e4c2e-112">EnsureVisible\(int lineNumber\)</span></span>

<span data-ttu-id="e4c2e-113">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e4c2e-114">Düzenleyici böylece satır için karşılık gelen kayan belirtilen **lineNumber** parametre değeri olduğu görünür.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="e4c2e-115">Belirtilen satır numarası geçerli satır numaralarını tanımlayan 1, son satır numarası aralığı dışında ise bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

<span data-ttu-id="e4c2e-116">**lineNumber** görünür yapılacak satır sayısı.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="e4c2e-117">Odağı\(\)</span><span class="sxs-lookup"><span data-stu-id="e4c2e-117">Focus\(\)</span></span>

<span data-ttu-id="e4c2e-118">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e4c2e-119">Odağı düzenleyiciye ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="e4c2e-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="e4c2e-120">GetLineLength\(int lineNumber \)</span></span>

<span data-ttu-id="e4c2e-121">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e4c2e-122">Satır uzunluğu, satır numarası tarafından belirtilen satır için bir tamsayı olarak alır.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

<span data-ttu-id="e4c2e-123">**lineNumber** uzunluğu alınacağı, satır sayısı.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-123">**lineNumber** The number of the line of which to get the length.</span></span>

<span data-ttu-id="e4c2e-124">**Döndürür** belirtilen satır numarası satırı için satır uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="e4c2e-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="e4c2e-125">GoToMatch\(\)</span></span>

<span data-ttu-id="e4c2e-126">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e4c2e-127">Giriş işaretini eşleşen karaktere taşıyan **CanGoToMatch** Düzenleyicisi nesnenin özellik **$true**, giriş işaretini hemen bir açma parantezi, köşeli ayraç veya küme ayracı - önce olduğunda gerçekleşir \(,\[, {- veya hemen sonra bir kapatma ayracı, köşeli ayraç veya küme ayracı - \),\],}.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="e4c2e-128">Giriş işaretini bir açılış karakterden önce veya sonra bir kapatma karakteri yer alır.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="e4c2e-129">Varsa **CanGoToMatch** özelliği **$false**, sonra da bu yöntemi hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span>

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a><span data-ttu-id="e4c2e-130">E:System.Windows.Forms.Control.Click\( metin \)</span><span class="sxs-lookup"><span data-stu-id="e4c2e-130">InsertText\( text \)</span></span>

<span data-ttu-id="e4c2e-131">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-131">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e4c2e-132">Seçimi metinle değiştirir veya metni geçerli giriş işareti konumuna ekler.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-132">Replaces the selection with text or inserts text at the current caret position.</span></span>

<span data-ttu-id="e4c2e-133">**metin** -eklemek için metin dizesi.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-133">**text** - String The text to insert.</span></span>

<span data-ttu-id="e4c2e-134">Bkz: [örnek komut dosyası](#scripting-example) bu konuda.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-134">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="e4c2e-135">Seçin\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="e4c2e-135">Select\( startLine, startColumn, endLine, endColumn \)</span></span>

<span data-ttu-id="e4c2e-136">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e4c2e-137">Metinden seçer **startLine**, **startColumn**, **endLine**, ve **endColumn** parametreleri.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-137">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

<span data-ttu-id="e4c2e-138">**startLine** -seçimi başladığı satırın tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-138">**startLine** - Integer The line where the selection starts.</span></span>

<span data-ttu-id="e4c2e-139">**startColumn** -tamsayı seçimi başladığı başlangıç satırı içindeki sütun.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-139">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

<span data-ttu-id="e4c2e-140">**endLine** -sona ereceği Seçimi satırın tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-140">**endLine** - Integer The line where the selection ends.</span></span>

<span data-ttu-id="e4c2e-141">**endColumn** -sütun seçimi sona ereceği satır sonu içinde tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-141">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

<span data-ttu-id="e4c2e-142">Bkz: [örnek komut dosyası](#scripting-example) bu konuda.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-142">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="e4c2e-143">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="e4c2e-143">SelectCaretLine\(\)</span></span>

<span data-ttu-id="e4c2e-144">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-144">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e4c2e-145">Şu anda giriş işaretini içeren metin tüm satırı seçer.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-145">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="e4c2e-146">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="e4c2e-146">SetCaretPosition\( lineNumber, columnNumber \)</span></span>

<span data-ttu-id="e4c2e-147">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-147">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e4c2e-148">Giriş işareti konumunu, satır numarası ve sütun sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-148">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="e4c2e-149">Giriş işaretini satır numarası ya da giriş işaretini sütun numarası, ilgili geçerli aralık dışında ise bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-149">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

<span data-ttu-id="e4c2e-150">**lineNumber** -tamsayı giriş işaretini satır numarası.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-150">**lineNumber** - Integer The caret line number.</span></span>

<span data-ttu-id="e4c2e-151">**columnNumber** -tamsayı giriş işaretini sütun numarası.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-151">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="e4c2e-152">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="e4c2e-152">ToggleOutliningExpansion\(\)</span></span>

<span data-ttu-id="e4c2e-153">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-153">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e4c2e-154">Genişletmek veya daraltmak tüm ana hattı bölümleri neden olur.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-154">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="e4c2e-155">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e4c2e-155">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="e4c2e-156">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="e4c2e-156">CanGoToMatch</span></span>

<span data-ttu-id="e4c2e-157">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-157">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e4c2e-158">Giriş işaretini bir parantez, köşeli ayraç veya küme ayracı - yanındaki olup olmadığını belirtmek için salt okunur Boolean özelliği \( \), \[ \], {}.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-158">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="e4c2e-159">Giriş işaretini açılış karakterden hemen önce bir çift kapatma karakterini hemen sonra mı sonra bu özellik değeri **$true**.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-159">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="e4c2e-160">Aksi halde **$false**.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-160">Otherwise, it is **$false**.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="e4c2e-161">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="e4c2e-161">CaretColumn</span></span>

<span data-ttu-id="e4c2e-162">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e4c2e-163">Sütun numarası, salt okunur özelliği giriş işareti konumuna karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-163">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="e4c2e-164">CaretLine</span><span class="sxs-lookup"><span data-stu-id="e4c2e-164">CaretLine</span></span>

<span data-ttu-id="e4c2e-165">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e4c2e-166">Giriş işaretini içeren satırı sayısını alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-166">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="e4c2e-167">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="e4c2e-167">CaretLineText</span></span>

<span data-ttu-id="e4c2e-168">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-168">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e4c2e-169">Giriş işaretini içeren metin tam satırının alan salt okunur özelliği.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-169">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="e4c2e-170">LineCount</span><span class="sxs-lookup"><span data-stu-id="e4c2e-170">LineCount</span></span>

<span data-ttu-id="e4c2e-171">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-171">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e4c2e-172">Satır sayısı Düzenleyicisi'nden alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-172">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="e4c2e-173">Metin</span><span class="sxs-lookup"><span data-stu-id="e4c2e-173">SelectedText</span></span>

<span data-ttu-id="e4c2e-174">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-174">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e4c2e-175">Seçili metin Düzenleyicisi'nden alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-175">The read-only property that gets the selected text from the editor.</span></span>

<span data-ttu-id="e4c2e-176">Bkz: [örnek komut dosyası](#scripting-example) bu konuda.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-176">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="e4c2e-177">Metin</span><span class="sxs-lookup"><span data-stu-id="e4c2e-177">Text</span></span>

<span data-ttu-id="e4c2e-178">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-178">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e4c2e-179">Alır veya metin düzenleyicide ayarlar okuma/yazma özelliği.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-179">The read/write property that gets or sets the text in the editor.</span></span>

<span data-ttu-id="e4c2e-180">Bkz: [örnek komut dosyası](#scripting-example) bu konuda.</span><span class="sxs-lookup"><span data-stu-id="e4c2e-180">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="e4c2e-181">Örnek betik</span><span class="sxs-lookup"><span data-stu-id="e4c2e-181">Scripting Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e4c2e-182">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e4c2e-182">See Also</span></span>

- [<span data-ttu-id="e4c2e-183">Isefile nesnesi</span><span class="sxs-lookup"><span data-stu-id="e4c2e-183">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="e4c2e-184">PowerShellTab nesnesi</span><span class="sxs-lookup"><span data-stu-id="e4c2e-184">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="e4c2e-185">Windows PowerShell ISE betik oluşturma nesne modelinin amacı</span><span class="sxs-lookup"><span data-stu-id="e4c2e-185">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="e4c2e-186">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="e4c2e-186">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)