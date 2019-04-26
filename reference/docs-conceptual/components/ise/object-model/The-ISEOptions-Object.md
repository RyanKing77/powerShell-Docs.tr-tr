---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISEOptions Nesnesi
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: e756da21aaa5465f7fa6a90563b4180f0c89e87b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057783"
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="570d4-103">ISEOptions Nesnesi</span><span class="sxs-lookup"><span data-stu-id="570d4-103">The ISEOptions Object</span></span>

<span data-ttu-id="570d4-104">**Iseoptions** nesnesi, Windows PowerShell ISE için çeşitli ayarlar'ı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="570d4-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="570d4-105">Bir örneğidir **Microsoft.PowerShell.Host.ISE.ISEOptions** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="570d4-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

<span data-ttu-id="570d4-106">**Iseoptions** nesnesi, aşağıdaki yöntemleri ve özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="570d4-106">The **ISEOptions** object provides the following methods and properties.</span></span>

## <a name="methods"></a><span data-ttu-id="570d4-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="570d4-107">Methods</span></span>

### <a name="restoredefaultconsoletokencolors"></a><span data-ttu-id="570d4-108">RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="570d4-108">RestoreDefaultConsoleTokenColors\(\)</span></span>

<span data-ttu-id="570d4-109">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="570d4-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="570d4-110">Konsol bölmesinde belirteç renkleri için varsayılan değerleri yükler.</span><span class="sxs-lookup"><span data-stu-id="570d4-110">Restores the default values of the token colors in the Console pane.</span></span>

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a><span data-ttu-id="570d4-111">RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="570d4-111">RestoreDefaults\(\)</span></span>

<span data-ttu-id="570d4-112">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="570d4-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="570d4-113">Konsol bölmesinde tüm seçenekleri ayarlar için varsayılan değerleri yükler.</span><span class="sxs-lookup"><span data-stu-id="570d4-113">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="570d4-114">Ayrıca, ileti yeniden gösterilen önlemek için standart onay kutusunu sağlayan çeşitli uyarı iletilerini davranışını sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="570d4-114">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a><span data-ttu-id="570d4-115">RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="570d4-115">RestoreDefaultTokenColors\(\)</span></span>

<span data-ttu-id="570d4-116">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="570d4-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="570d4-117">Betik bölmesini simge renkleri için varsayılan değerleri yükler.</span><span class="sxs-lookup"><span data-stu-id="570d4-117">Restores the default values of the token colors in the Script pane.</span></span>

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a><span data-ttu-id="570d4-118">RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="570d4-118">RestoreDefaultXmlTokenColors\(\)</span></span>

<span data-ttu-id="570d4-119">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="570d4-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="570d4-120">Windows PowerShell ISE'de görüntülenen XML öğeleri için belirteç renkleri için varsayılan değerleri yükler.</span><span class="sxs-lookup"><span data-stu-id="570d4-120">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="570d4-121">Ayrıca bkz: [XmlTokenColors](#xmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="570d4-121">Also see [XmlTokenColors](#xmltokencolors).</span></span>

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="570d4-122">Özellikler</span><span class="sxs-lookup"><span data-stu-id="570d4-122">Properties</span></span>

### <a name="autosaveminuteinterval"></a><span data-ttu-id="570d4-123">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="570d4-123">AutoSaveMinuteInterval</span></span>

<span data-ttu-id="570d4-124">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="570d4-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="570d4-125">Windows PowerShell ISE tarafından dosyalarınızın otomatik kaydetme işlemleri arasındaki dakika sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-125">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="570d4-126">Varsayılan değer 2 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="570d4-126">The default value is 2 minutes.</span></span> <span data-ttu-id="570d4-127">Bir tamsayı değerdir.</span><span class="sxs-lookup"><span data-stu-id="570d4-127">The value is an integer.</span></span>

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a><span data-ttu-id="570d4-128">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="570d4-128">CommandPaneBackgroundColor</span></span>

<span data-ttu-id="570d4-129">Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerde yeniden adlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="570d4-129">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="570d4-130">Sonraki sürümleri için bkz: [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="570d4-130">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="570d4-131">Komut bölmesi için arka plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-131">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="570d4-132">Bir örneğidir **System.Windows.Media.Color** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="570d4-132">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a><span data-ttu-id="570d4-133">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="570d4-133">CommandPaneUp</span></span>

<span data-ttu-id="570d4-134">Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerde yeniden adlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="570d4-134">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

<span data-ttu-id="570d4-135">Komut bölmesi çıkış Bölmesi ' bulunup bulunmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-135">Specifies whether the Command pane is located above the Output pane.</span></span>

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a><span data-ttu-id="570d4-136">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="570d4-136">ConsolePaneBackgroundColor</span></span>

<span data-ttu-id="570d4-137">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="570d4-137">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="570d4-138">Konsol bölmesinde arka plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-138">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="570d4-139">Bir örneğidir **System.Windows.Media.Color** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="570d4-139">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a><span data-ttu-id="570d4-140">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="570d4-140">ConsolePaneForegroundColor</span></span>

<span data-ttu-id="570d4-141">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="570d4-141">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="570d4-142">Konsol bölmesinde metin ön plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-142">Specifies the foreground color of the text in the Console pane.</span></span>

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a><span data-ttu-id="570d4-143">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="570d4-143">ConsolePaneTextBackgroundColor</span></span>

<span data-ttu-id="570d4-144">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="570d4-144">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="570d4-145">Konsol bölmesinde metin arka plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-145">Specifies the background color of the text in the Console pane.</span></span>

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a><span data-ttu-id="570d4-146">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="570d4-146">ConsoleTokenColors</span></span>

<span data-ttu-id="570d4-147">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="570d4-147">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="570d4-148">Windows PowerShell ISE Konsol bölmesinde IntelliSense belirteçleri rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-148">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="570d4-149">Bu özellik belirteç türleri ve konsol bölmesinde renkleri ad/değer çiftleri içeren bir sözlük nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="570d4-149">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="570d4-150">Betik bölmesindeki IntelliSense belirteçlerin renkleri değiştirmek için bkz: [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="570d4-150">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tokencolors).</span></span> <span data-ttu-id="570d4-151">Renkleri varsayılan değerlere sıfırlamak için bkz: [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="570d4-151">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span></span> <span data-ttu-id="570d4-152">Belirteç renkleri, aşağıdakiler için ayarlanabilir: Öznitelik, komut, CommandArgument, CommandParameter, açıklama, GroupEnd, GroupStart, anahtar sözcüğü, LineContinuation, LoopLabel, üye, yeni satır, sayı, işleci, konum, StatementSeparator, dize, türü, bilinmeyen, değişken.</span><span class="sxs-lookup"><span data-stu-id="570d4-152">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a><span data-ttu-id="570d4-153">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="570d4-153">DebugBackgroundColor</span></span>

<span data-ttu-id="570d4-154">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="570d4-154">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="570d4-155">Konsol bölmesinde görüntülenen hata ayıklama metin arka plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-155">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="570d4-156">Bir örneğidir **System.Windows.Media.Color** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="570d4-156">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a><span data-ttu-id="570d4-157">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="570d4-157">DebugForegroundColor</span></span>

<span data-ttu-id="570d4-158">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="570d4-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="570d4-159">Konsol bölmesinde görüntülenen hata ayıklama metin ön plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-159">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="570d4-160">Bir örneğidir **System.Windows.Media.Color** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="570d4-160">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a><span data-ttu-id="570d4-161">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="570d4-161">DefaultOptions</span></span>

<span data-ttu-id="570d4-162">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="570d4-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="570d4-163">Yöntemleri sıfırlama kullanıldığında kullanılacak varsayılan değerleri belirten özellikleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="570d4-163">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

```powershell
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions

SelectedScriptPaneState                   : Top
ShowDefaultSnippets                       : True
ShowToolBar                               : True
ShowOutlining                             : True
ShowLineNumbers                           : True
TokenColors                               : {[Attribute, #FF00BFFF], [Command, #FF0000FF], [CommandArgument, #FF8A2BE2], [CommandParameter, #FF000080]...}
ConsoleTokenColors                        : {[Attribute, #FFB0C4DE], [Command, #FFE0FFFF], [CommandArgument, #FFEE82EE], [CommandParameter, #FFFFE4B5]...}
XmlTokenColors                            : {[Comment, #FF006400], [CommentDelimiter, #FF008000], [ElementName, #FF8B0000], [MarkupExtension, #FFFF8C00]...}
DefaultOptions                            : Microsoft.PowerShell.Host.ISE.ISEOptions
FontSize                                  : 9
Zoom                                      : 100
FontName                                  : Lucida Console
ErrorForegroundColor                      : #FFFF0000
ErrorBackgroundColor                      : #00FFFFFF
WarningForegroundColor                    : #FFFF8C00
WarningBackgroundColor                    : #00FFFFFF
VerboseForegroundColor                    : #FF00FFFF
VerboseBackgroundColor                    : #00FFFFFF
DebugForegroundColor                      : #FF00FFFF
DebugBackgroundColor                      : #00FFFFFF
ConsolePaneBackgroundColor                : #FF012456
ConsolePaneTextBackgroundColor            : #FF012456
ConsolePaneForegroundColor                : #FFF5F5F5
ScriptPaneBackgroundColor                 : #FFFFFFFF
ScriptPaneForegroundColor                 : #FF000000
ShowWarningForDuplicateFiles              : True
ShowWarningBeforeSavingOnRun              : True
UseLocalHelp                              : True
AutoSaveMinuteInterval                    : 2
MruCount                                  : 10
ShowIntellisenseInConsolePane             : True
ShowIntellisenseInScriptPane              : True
UseEnterToSelectInConsolePaneIntellisense : True
UseEnterToSelectInScriptPaneIntellisense  : True
IntellisenseTimeoutInSeconds              : 3
```

### <a name="errorbackgroundcolor"></a><span data-ttu-id="570d4-164">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="570d4-164">ErrorBackgroundColor</span></span>

<span data-ttu-id="570d4-165">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="570d4-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="570d4-166">Konsol bölmesinde görüntülenen hata metni arka plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-166">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="570d4-167">Bir örneğidir **System.Windows.Media.Color** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="570d4-167">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a><span data-ttu-id="570d4-168">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="570d4-168">ErrorForegroundColor</span></span>

<span data-ttu-id="570d4-169">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="570d4-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="570d4-170">Konsol bölmesinde görünen hata metin ön plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-170">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="570d4-171">Bir örneğidir **System.Windows.Media.Color** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="570d4-171">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a><span data-ttu-id="570d4-172">FontName</span><span class="sxs-lookup"><span data-stu-id="570d4-172">FontName</span></span>

<span data-ttu-id="570d4-173">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="570d4-173">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="570d4-174">Yazı tipi adı şu anda betik bölmesi ve konsol bölmesinde hem belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-174">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a><span data-ttu-id="570d4-175">FontSize</span><span class="sxs-lookup"><span data-stu-id="570d4-175">FontSize</span></span>

<span data-ttu-id="570d4-176">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="570d4-176">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="570d4-177">Bir tamsayı olarak yazı tipi boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-177">Specifies the font size as an integer.</span></span> <span data-ttu-id="570d4-178">Bu betik bölmesine, komut bölmesi ve çıkış Bölmesi ' kullanılır.</span><span class="sxs-lookup"><span data-stu-id="570d4-178">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="570d4-179">Değerlerinin geçerli aralığı 8 ile 32 ' dir.</span><span class="sxs-lookup"><span data-stu-id="570d4-179">The valid range of values is 8 through 32.</span></span>

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a><span data-ttu-id="570d4-180">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="570d4-180">IntellisenseTimeoutInSeconds</span></span>

<span data-ttu-id="570d4-181">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="570d4-181">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="570d4-182">Şu anda karakterlerine çözümlemeyi denemek için IntelliSense kullanan saniye sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-182">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="570d4-183">Bu kadar saniye sonra IntelliSense zaman aşımına uğrar ve yazmaya devam etmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="570d4-183">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="570d4-184">Varsayılan değer 3 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="570d4-184">The default value is 3 seconds.</span></span> <span data-ttu-id="570d4-185">Bir tamsayı değerdir.</span><span class="sxs-lookup"><span data-stu-id="570d4-185">The value is an integer.</span></span>

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a><span data-ttu-id="570d4-186">MruCount</span><span class="sxs-lookup"><span data-stu-id="570d4-186">MruCount</span></span>

<span data-ttu-id="570d4-187">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="570d4-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="570d4-188">Windows PowerShell ISE izler ve alt kısmında görüntüler en son açılan dosyaları belirtir **Dosya Aç** menüsü.</span><span class="sxs-lookup"><span data-stu-id="570d4-188">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="570d4-189">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="570d4-189">The default value is 10.</span></span> <span data-ttu-id="570d4-190">Bir tamsayı değerdir.</span><span class="sxs-lookup"><span data-stu-id="570d4-190">The value is an integer.</span></span>

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a><span data-ttu-id="570d4-191">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="570d4-191">OutputPaneBackgroundColor</span></span>

<span data-ttu-id="570d4-192">Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerde yeniden adlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="570d4-192">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="570d4-193">Sonraki sürümleri için bkz: [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="570d4-193">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="570d4-194">Çıkış bölmesi için arka plan rengini alır veya ayarlar okuma/yazma özelliği.</span><span class="sxs-lookup"><span data-stu-id="570d4-194">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="570d4-195">Bir örneğidir **System.Windows.Media.Color** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="570d4-195">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a><span data-ttu-id="570d4-196">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="570d4-196">OutputPaneTextForegroundColor</span></span>

<span data-ttu-id="570d4-197">Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerde yeniden adlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="570d4-197">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="570d4-198">Sonraki sürümleri için bkz: [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span><span class="sxs-lookup"><span data-stu-id="570d4-198">For later versions, see [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span></span>

<span data-ttu-id="570d4-199">Windows PowerShell ISE 2.0 çıkış bölmesinde metin ön plan rengini değiştiren okuma/yazma özelliği.</span><span class="sxs-lookup"><span data-stu-id="570d4-199">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a><span data-ttu-id="570d4-200">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="570d4-200">OutputPaneTextBackgroundColor</span></span>

<span data-ttu-id="570d4-201">Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerde yeniden adlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="570d4-201">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="570d4-202">Sonraki sürümleri için bkz: [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="570d4-202">For later versions, see [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span></span>

<span data-ttu-id="570d4-203">Metin çıkışı bölmesindeki arka plan rengi değişir okuma/yazma özelliği.</span><span class="sxs-lookup"><span data-stu-id="570d4-203">The read/write property that changes the background color of the text in the Output pane.</span></span>

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a><span data-ttu-id="570d4-204">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="570d4-204">ScriptPaneBackgroundColor</span></span>

<span data-ttu-id="570d4-205">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="570d4-205">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="570d4-206">Dosyaları için arka plan rengini alır veya ayarlar okuma/yazma özelliği.</span><span class="sxs-lookup"><span data-stu-id="570d4-206">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="570d4-207">Bir örneğidir **System.Windows.Media.Color** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="570d4-207">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a><span data-ttu-id="570d4-208">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="570d4-208">ScriptPaneForegroundColor</span></span>

<span data-ttu-id="570d4-209">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="570d4-209">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="570d4-210">Alır veya betik bölmesinde olmayan komut dosyalarını ön plan rengini ayarlar okuma/yazma özelliği.</span><span class="sxs-lookup"><span data-stu-id="570d4-210">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="570d4-211">Komut dosyalarını ön plan rengini ayarlamak için kullanın [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="570d4-211">To set the foreground color for script files, use the [TokenColors](#tokencolors).</span></span>

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a><span data-ttu-id="570d4-212">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="570d4-212">SelectedScriptPaneState</span></span>

<span data-ttu-id="570d4-213">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="570d4-213">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="570d4-214">Ekranda betik bölmesini konumunu ayarlar veya alır okuma/yazma özelliği.</span><span class="sxs-lookup"><span data-stu-id="570d4-214">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="570d4-215">Bir dize olabilir 'Maximized', 'Top' veya 'Right'.</span><span class="sxs-lookup"><span data-stu-id="570d4-215">The string can be either 'Maximized', 'Top', or 'Right'.</span></span>

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a><span data-ttu-id="570d4-216">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="570d4-216">ShowDefaultSnippets</span></span>

<span data-ttu-id="570d4-217">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="570d4-217">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="570d4-218">Belirtir olup olmadığını **CTRL + J** parçacıkları listesi Windows PowerShell'de dahil başlangıç kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="570d4-218">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="570d4-219">Ayarlandığında **$false**, yalnızca kullanıcı tarafından tanımlanan kod parçacıkları görünür **CTRL + J** listesi.</span><span class="sxs-lookup"><span data-stu-id="570d4-219">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="570d4-220">Varsayılan değer **$true**.</span><span class="sxs-lookup"><span data-stu-id="570d4-220">The default value is **$true**.</span></span>

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a><span data-ttu-id="570d4-221">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="570d4-221">ShowIntellisenseInConsolePane</span></span>

<span data-ttu-id="570d4-222">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="570d4-222">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="570d4-223">IntelliSense, sözdizimi, parametre ve konsol bölmesinde değer önerileri sunup sunmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-223">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="570d4-224">Varsayılan değer **$true**.</span><span class="sxs-lookup"><span data-stu-id="570d4-224">The default value is **$true**.</span></span>

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a><span data-ttu-id="570d4-225">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="570d4-225">ShowIntellisenseInScriptPane</span></span>

<span data-ttu-id="570d4-226">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="570d4-226">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="570d4-227">IntelliSense sözdizimi, parametre ve betik bölmesine değer önerileri sunup belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-227">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="570d4-228">Varsayılan değer **$true**.</span><span class="sxs-lookup"><span data-stu-id="570d4-228">The default value is **$true**.</span></span>

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a><span data-ttu-id="570d4-229">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="570d4-229">ShowLineNumbers</span></span>

<span data-ttu-id="570d4-230">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="570d4-230">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="570d4-231">Betik bölmesi sol kenar boşluğunda satır numaralarını görüntülenip görüntülenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-231">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="570d4-232">Varsayılan değer **$true**.</span><span class="sxs-lookup"><span data-stu-id="570d4-232">The default value is **$true**.</span></span>

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a><span data-ttu-id="570d4-233">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="570d4-233">ShowOutlining</span></span>

<span data-ttu-id="570d4-234">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="570d4-234">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="570d4-235">Betik bölmesi sol kenar boşluğunda kod bölümlerini yanındaki köşeli ayraçlar genişletilebilen ve daraltılabilen görüntülenip görüntülenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-235">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="570d4-236">Görüntülendiğinde, eksi tıklayabilirsiniz \( - \) simgeler yanındaki artı işaretine tıklayın veya daraltılabilir metin bloğu \( + \) simgesini metin bloğu genişletin.</span><span class="sxs-lookup"><span data-stu-id="570d4-236">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="570d4-237">Varsayılan değer **$true**.</span><span class="sxs-lookup"><span data-stu-id="570d4-237">The default value is **$true**.</span></span>

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a><span data-ttu-id="570d4-238">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="570d4-238">ShowToolBar</span></span>

<span data-ttu-id="570d4-239">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="570d4-239">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="570d4-240">ISE araç Windows PowerShell ISE penceresi üstündeki görüntülenip görüntülenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-240">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="570d4-241">Varsayılan değer **$true**.</span><span class="sxs-lookup"><span data-stu-id="570d4-241">The default value is **$true**.</span></span>

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a><span data-ttu-id="570d4-242">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="570d4-242">ShowWarningBeforeSavingOnRun</span></span>

<span data-ttu-id="570d4-243">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="570d4-243">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="570d4-244">Bunu çalıştırılmadan önce bir komut dosyası otomatik olarak kaydedildiğinde bir uyarı iletisi görünür olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-244">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="570d4-245">Varsayılan değer **$true**.</span><span class="sxs-lookup"><span data-stu-id="570d4-245">The default value is **$true**.</span></span>

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a><span data-ttu-id="570d4-246">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="570d4-246">ShowWarningForDuplicateFiles</span></span>

<span data-ttu-id="570d4-247">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="570d4-247">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="570d4-248">Aynı dosyanın farklı PowerShell sekmelerde açıldığında bir uyarı iletisi görünür olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-248">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="570d4-249">Varsa kümesine **$true**aynı dosyanın birden çok sekme görüntüler bu iletiyi açmak için: "Bu dosyanın bir kopyasını başka bir Windows PowerShell sekmeyi açık durumdadır. Bu dosyada yapılan değişiklikler tüm açık kopyaları etkiler."</span><span class="sxs-lookup"><span data-stu-id="570d4-249">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab. Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="570d4-250">Varsayılan değer **$true**.</span><span class="sxs-lookup"><span data-stu-id="570d4-250">The default value is **$true**.</span></span>

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a><span data-ttu-id="570d4-251">TokenColors</span><span class="sxs-lookup"><span data-stu-id="570d4-251">TokenColors</span></span>

<span data-ttu-id="570d4-252">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="570d4-252">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="570d4-253">Windows PowerShell ISE betik bölmesinde IntelliSense belirteçleri rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-253">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="570d4-254">Bu betik bölmesine için renkleri ve belirteç türleri ad/değer çiftleri içeren bir sözlük nesnesi özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="570d4-254">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="570d4-255">Konsol bölmesinde IntelliSense belirteçlerin renkleri değiştirmek için bkz: [ConsoleTokenColors](#consoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="570d4-255">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#consoletokencolors).</span></span> <span data-ttu-id="570d4-256">Renkleri varsayılan değerlere sıfırlamak için bkz: [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span><span class="sxs-lookup"><span data-stu-id="570d4-256">To reset the colors to the default values, see [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span></span> <span data-ttu-id="570d4-257">Belirteç renkleri, aşağıdakiler için ayarlanabilir: Öznitelik, komut, CommandArgument, CommandParameter, açıklama, GroupEnd, GroupStart, anahtar sözcüğü, LineContinuation, LoopLabel, üye, yeni satır, sayı, işleci, konum, StatementSeparator, dize, türü, bilinmeyen, değişken.</span><span class="sxs-lookup"><span data-stu-id="570d4-257">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a><span data-ttu-id="570d4-258">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="570d4-258">UseEnterToSelectInConsolePaneIntellisense</span></span>

<span data-ttu-id="570d4-259">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="570d4-259">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="570d4-260">Konsol bölmesinde seçeneği sağlanan bir IntelliSense seçmek için Enter tuşunu kullanabilirsiniz olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-260">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="570d4-261">Varsayılan değer **$true**.</span><span class="sxs-lookup"><span data-stu-id="570d4-261">The default value is **$true**.</span></span>

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a><span data-ttu-id="570d4-262">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="570d4-262">UseEnterToSelectInScriptPaneIntellisense</span></span>

<span data-ttu-id="570d4-263">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="570d4-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="570d4-264">IntelliSense tarafından sağlanan bir seçenek betik bölmesinde seçmek için Enter tuşunu kullanabilirsiniz olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-264">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="570d4-265">Varsayılan değer **$true**.</span><span class="sxs-lookup"><span data-stu-id="570d4-265">The default value is **$true**.</span></span>

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a><span data-ttu-id="570d4-266">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="570d4-266">UseLocalHelp</span></span>

<span data-ttu-id="570d4-267">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="570d4-267">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="570d4-268">Bir anahtar sözcük bulunan imleç ile F1 tuşuna bastığınızda yerel olarak yüklenmiş Yardım veya çevrimiçi TechNet Kitaplığı Yardım görüntülenip görüntülenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-268">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="570d4-269">Varsa kümesine **$true**, sonra da bir açılır pencere yerel olarak yüklenmiş Yardım içerik gösterir.</span><span class="sxs-lookup"><span data-stu-id="570d4-269">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="570d4-270">Yardım dosyaları çalıştırarak yükleyebilirsiniz `Update-Help` komutu.</span><span class="sxs-lookup"><span data-stu-id="570d4-270">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="570d4-271">Varsa kümesine **$false**, TechNet Kitaplığı'nda bir sayfa için tarayıcınızı açar.</span><span class="sxs-lookup"><span data-stu-id="570d4-271">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a><span data-ttu-id="570d4-272">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="570d4-272">VerboseBackgroundColor</span></span>

<span data-ttu-id="570d4-273">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="570d4-273">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="570d4-274">Konsol bölmesinde görünen ayrıntılı metin arka plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-274">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="570d4-275">Bu bir **System.Windows.Media.Color** nesne.</span><span class="sxs-lookup"><span data-stu-id="570d4-275">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a><span data-ttu-id="570d4-276">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="570d4-276">VerboseForegroundColor</span></span>

<span data-ttu-id="570d4-277">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="570d4-277">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="570d4-278">Konsol bölmesinde görünen ayrıntılı metin ön plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-278">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="570d4-279">Bu bir **System.Windows.Media.Color** nesne.</span><span class="sxs-lookup"><span data-stu-id="570d4-279">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a><span data-ttu-id="570d4-280">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="570d4-280">WarningBackgroundColor</span></span>

<span data-ttu-id="570d4-281">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="570d4-281">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="570d4-282">Konsol bölmesinde görüntülenen uyarı metni arka plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-282">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="570d4-283">Bu bir **System.Windows.Media.Color** nesne.</span><span class="sxs-lookup"><span data-stu-id="570d4-283">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a><span data-ttu-id="570d4-284">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="570d4-284">WarningForegroundColor</span></span>

<span data-ttu-id="570d4-285">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="570d4-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="570d4-286">Çıkış Bölmesi'nde görüntülenen uyarı metni ön plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-286">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="570d4-287">Bu bir **System.Windows.Media.Color** nesne.</span><span class="sxs-lookup"><span data-stu-id="570d4-287">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a><span data-ttu-id="570d4-288">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="570d4-288">XmlTokenColors</span></span>

<span data-ttu-id="570d4-289">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="570d4-289">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="570d4-290">Windows PowerShell ISE'de görüntülenen XML içeriği için renkleri ve belirteç türleri ad/değer çiftleri içeren bir sözlük nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-290">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="570d4-291">Belirteç renkleri, aşağıdakiler için ayarlanabilir: Öznitelik, komut, CommandArgument, CommandParameter, açıklama, GroupEnd, GroupStart, anahtar sözcüğü, LineContinuation, LoopLabel, üye, yeni satır, sayı, işleci, konum, StatementSeparator, dize, türü, bilinmeyen, değişken.</span><span class="sxs-lookup"><span data-stu-id="570d4-291">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="570d4-292">Ayrıca bkz: [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="570d4-292">Also see [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span></span>

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a><span data-ttu-id="570d4-293">Yakınlaştır</span><span class="sxs-lookup"><span data-stu-id="570d4-293">Zoom</span></span>

<span data-ttu-id="570d4-294">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="570d4-294">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="570d4-295">Hem konsol hem de betik bölmelerinde metin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="570d4-295">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="570d4-296">Varsayılan değer 100’dür.</span><span class="sxs-lookup"><span data-stu-id="570d4-296">The default value is 100.</span></span> <span data-ttu-id="570d4-297">Daha küçük değerler metni büyük görüntülenecek metin daha büyük sayılar neden olurken daha küçük görünür için Windows PowerShell ISE'de neden olur.</span><span class="sxs-lookup"><span data-stu-id="570d4-297">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="570d4-298">20'den 400 arasında bir tamsayı değerdir.</span><span class="sxs-lookup"><span data-stu-id="570d4-298">The value is an integer that ranges from 20 to 400.</span></span>

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="570d4-299">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="570d4-299">See Also</span></span>

- [<span data-ttu-id="570d4-300">Windows PowerShell ISE betik oluşturma nesne modelinin amacı</span><span class="sxs-lookup"><span data-stu-id="570d4-300">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="570d4-301">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="570d4-301">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)