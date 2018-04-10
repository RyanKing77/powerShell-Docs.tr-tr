---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISEEditor Nesnesi
ms.openlocfilehash: 2d4c3d941035384c591ca57e809c0e3a9b852f5c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="ec039-103">ISEEditor Nesnesi</span><span class="sxs-lookup"><span data-stu-id="ec039-103">The ISEEditor Object</span></span>

<span data-ttu-id="ec039-104">Bir **ISEEditor** nesnesidir Microsoft.PowerShell.Host.ISE.ISEEditor sınıfının bir örneği.</span><span class="sxs-lookup"><span data-stu-id="ec039-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="ec039-105">Konsol bölmesinde bir **ISEEditor** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ec039-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="ec039-106">Her [ISEFile](The-ISEFile-Object.md) nesne olan ilişkili bir **ISEEditor** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ec039-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="ec039-107">Aşağıdaki bölümlerde yöntemleri ve özellikleri listelenmektedir bir **ISEEditor** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ec039-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="ec039-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ec039-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="ec039-109">Temizle\(\)</span><span class="sxs-lookup"><span data-stu-id="ec039-109">Clear\(\)</span></span>

<span data-ttu-id="ec039-110">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ec039-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ec039-111">Metin Düzenleyicisi'nde temizler.</span><span class="sxs-lookup"><span data-stu-id="ec039-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="ec039-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="ec039-112">EnsureVisible\(int lineNumber\)</span></span>

<span data-ttu-id="ec039-113">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ec039-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ec039-114">Böylece satır için karşılık gelen düzenleyicisi kayar belirtilen **lineNumber** parametre değeri görülebilir.</span><span class="sxs-lookup"><span data-stu-id="ec039-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="ec039-115">Belirtilen satır numarası geçerli satır numaralarını tanımlayan 1, son satır numarası, aralığının dışında olması durumunda bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ec039-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

<span data-ttu-id="ec039-116">**lineNumber** görünür duruma getirilecek satır sayısı.</span><span class="sxs-lookup"><span data-stu-id="ec039-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="ec039-117">Odağı\(\)</span><span class="sxs-lookup"><span data-stu-id="ec039-117">Focus\(\)</span></span>

<span data-ttu-id="ec039-118">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ec039-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ec039-119">Odağı düzenleyiciye ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ec039-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="ec039-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="ec039-120">GetLineLength\(int lineNumber \)</span></span>

<span data-ttu-id="ec039-121">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ec039-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ec039-122">Satır uzunluğu bir tamsayı olarak satır sayısı ile belirtilen satır alır.</span><span class="sxs-lookup"><span data-stu-id="ec039-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

<span data-ttu-id="ec039-123">**lineNumber** de uzunluğu almak satır sayısı.</span><span class="sxs-lookup"><span data-stu-id="ec039-123">**lineNumber** The number of the line of which to get the length.</span></span>

<span data-ttu-id="ec039-124">**Döndürür** belirtilen satır numarası satırında satır uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="ec039-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="ec039-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="ec039-125">GoToMatch\(\)</span></span>

<span data-ttu-id="ec039-126">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="ec039-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="ec039-127">Şapka eşleşen karakter taşınır **CanGoToMatch** editor nesnesi özelliği **$true**, düzeltme işareti hemen bir açma ayracı, köşeli ayraç veya parantezi - önce olduğunda oluşur \(,\[, {- veya hemen sonra bir kapanış parantezi, köşeli ayraç ya da küme parantezi - \),\],}.</span><span class="sxs-lookup"><span data-stu-id="ec039-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="ec039-128">Düzeltme işareti bir açılış karakter önce veya sonra kapatma karakterini yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ec039-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="ec039-129">Varsa **CanGoToMatch** özelliği **$false**, sonra da bu yöntem hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="ec039-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span>

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a><span data-ttu-id="ec039-130">E:System.Windows.Forms.Control.Click\( metin \)</span><span class="sxs-lookup"><span data-stu-id="ec039-130">InsertText\( text \)</span></span>

<span data-ttu-id="ec039-131">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ec039-131">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ec039-132">Seçimi metinle değiştirir veya metni geçerli düzeltme işareti konumuna ekler.</span><span class="sxs-lookup"><span data-stu-id="ec039-132">Replaces the selection with text or inserts text at the current caret position.</span></span>

<span data-ttu-id="ec039-133">**metin** -eklemek için metin dizesi.</span><span class="sxs-lookup"><span data-stu-id="ec039-133">**text** - String The text to insert.</span></span>

<span data-ttu-id="ec039-134">Bkz: [örnek komut dosyası](#scripting-example) bu konuda daha sonra.</span><span class="sxs-lookup"><span data-stu-id="ec039-134">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="ec039-135">Seçin\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="ec039-135">Select\( startLine, startColumn, endLine, endColumn \)</span></span>

<span data-ttu-id="ec039-136">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ec039-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ec039-137">Metinden seçer **startLine**, **startColumn**, **endLine**, ve **endColumn** parametreleri.</span><span class="sxs-lookup"><span data-stu-id="ec039-137">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

<span data-ttu-id="ec039-138">**startLine** -tamsayı seçimi başladığı satır.</span><span class="sxs-lookup"><span data-stu-id="ec039-138">**startLine** - Integer The line where the selection starts.</span></span>

<span data-ttu-id="ec039-139">**startColumn** -tamsayı sütunu seçimi başladığı başlangıç satırı içinde.</span><span class="sxs-lookup"><span data-stu-id="ec039-139">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

<span data-ttu-id="ec039-140">**endLine** -tamsayı seçimi bittiği satır.</span><span class="sxs-lookup"><span data-stu-id="ec039-140">**endLine** - Integer The line where the selection ends.</span></span>

<span data-ttu-id="ec039-141">**endColumn** -tamsayı sütunu satır sonu seçimi bittiği içinde.</span><span class="sxs-lookup"><span data-stu-id="ec039-141">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

<span data-ttu-id="ec039-142">Bkz: [örnek komut dosyası](#scripting-example) bu konuda daha sonra.</span><span class="sxs-lookup"><span data-stu-id="ec039-142">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="ec039-143">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="ec039-143">SelectCaretLine\(\)</span></span>

<span data-ttu-id="ec039-144">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ec039-144">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ec039-145">Şu anda düzeltme işareti içeren metin satırının tamamına seçer.</span><span class="sxs-lookup"><span data-stu-id="ec039-145">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="ec039-146">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="ec039-146">SetCaretPosition\( lineNumber, columnNumber \)</span></span>

<span data-ttu-id="ec039-147">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ec039-147">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ec039-148">İmleç konumunu satır numarasını ve sütun sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ec039-148">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="ec039-149">Şapka satır numarası ya da düzeltme işareti sütun numarası kendi ilgili geçerli aralıklar dışında olması durumunda bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ec039-149">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

<span data-ttu-id="ec039-150">**lineNumber** -tamsayı şapka satır numarası.</span><span class="sxs-lookup"><span data-stu-id="ec039-150">**lineNumber** - Integer The caret line number.</span></span>

<span data-ttu-id="ec039-151">**columnNumber** -tamsayı şapka sütun numarası.</span><span class="sxs-lookup"><span data-stu-id="ec039-151">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="ec039-152">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="ec039-152">ToggleOutliningExpansion\(\)</span></span>

<span data-ttu-id="ec039-153">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="ec039-153">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="ec039-154">Genişletmek veya daraltmak tüm anahat bölümleri neden olur.</span><span class="sxs-lookup"><span data-stu-id="ec039-154">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="ec039-155">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ec039-155">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="ec039-156">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="ec039-156">CanGoToMatch</span></span>

<span data-ttu-id="ec039-157">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="ec039-157">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="ec039-158">Şapka parantez, köşeli ayraç veya parantezi - yanındaki olup olmadığını belirtmek için salt okunur Boolean özelliği \( \), \[ \], {}.</span><span class="sxs-lookup"><span data-stu-id="ec039-158">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="ec039-159">Şapka açılış karakter hemen önce bir çift kapanış karakterinin hemen sonra mı sonra bu özellik değeri **$true**.</span><span class="sxs-lookup"><span data-stu-id="ec039-159">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="ec039-160">Aksi takdirde, değer **$false**.</span><span class="sxs-lookup"><span data-stu-id="ec039-160">Otherwise, it is **$false**.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="ec039-161">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="ec039-161">CaretColumn</span></span>

<span data-ttu-id="ec039-162">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ec039-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ec039-163">Sütun sayısını alır salt okunur özelliği şapka konuma karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="ec039-163">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="ec039-164">CaretLine</span><span class="sxs-lookup"><span data-stu-id="ec039-164">CaretLine</span></span>

<span data-ttu-id="ec039-165">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ec039-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ec039-166">Düzeltme işareti içeren satırı sayısını alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="ec039-166">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="ec039-167">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="ec039-167">CaretLineText</span></span>

<span data-ttu-id="ec039-168">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ec039-168">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ec039-169">Tam metin satırının alır salt okunur özellik şapka içerir.</span><span class="sxs-lookup"><span data-stu-id="ec039-169">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="ec039-170">LineCount</span><span class="sxs-lookup"><span data-stu-id="ec039-170">LineCount</span></span>

<span data-ttu-id="ec039-171">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ec039-171">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ec039-172">Satır sayısı Düzenleyicisi'nden alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="ec039-172">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="ec039-173">SelectedText</span><span class="sxs-lookup"><span data-stu-id="ec039-173">SelectedText</span></span>

<span data-ttu-id="ec039-174">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ec039-174">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ec039-175">Seçili metni Düzenleyicisi'nden alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="ec039-175">The read-only property that gets the selected text from the editor.</span></span>

<span data-ttu-id="ec039-176">Bkz: [örnek komut dosyası](#scripting-example) bu konuda daha sonra.</span><span class="sxs-lookup"><span data-stu-id="ec039-176">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="ec039-177">Metin</span><span class="sxs-lookup"><span data-stu-id="ec039-177">Text</span></span>

<span data-ttu-id="ec039-178">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ec039-178">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ec039-179">Alır veya metin düzenleyicide ayarlar okuma/yazma özelliği.</span><span class="sxs-lookup"><span data-stu-id="ec039-179">The read/write property that gets or sets the text in the editor.</span></span>

<span data-ttu-id="ec039-180">Bkz: [örnek komut dosyası](#scripting-example) bu konuda daha sonra.</span><span class="sxs-lookup"><span data-stu-id="ec039-180">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="ec039-181">Örnek komut dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="ec039-181">Scripting Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ec039-182">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ec039-182">See Also</span></span>

- [<span data-ttu-id="ec039-183">The ISEFile Object</span><span class="sxs-lookup"><span data-stu-id="ec039-183">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="ec039-184">The PowerShellTab Object</span><span class="sxs-lookup"><span data-stu-id="ec039-184">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="ec039-185">Nesne modeli komut dosyası Windows PowerShell ISE amacı</span><span class="sxs-lookup"><span data-stu-id="ec039-185">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="ec039-186">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="ec039-186">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)