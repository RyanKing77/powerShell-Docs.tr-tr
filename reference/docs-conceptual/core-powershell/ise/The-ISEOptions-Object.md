---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISEOptions Nesnesi
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: e756da21aaa5465f7fa6a90563b4180f0c89e87b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="53e19-103">ISEOptions Nesnesi</span><span class="sxs-lookup"><span data-stu-id="53e19-103">The ISEOptions Object</span></span>

<span data-ttu-id="53e19-104">**ISEOptions** nesnesi, Windows PowerShell ISE için çeşitli ayarlar'ı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="53e19-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="53e19-105">Örneği olan **Microsoft.PowerShell.Host.ISE.ISEOptions** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="53e19-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

<span data-ttu-id="53e19-106">**ISEOptions** nesnesi, aşağıdaki yöntemleri ve özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="53e19-106">The **ISEOptions** object provides the following methods and properties.</span></span>

## <a name="methods"></a><span data-ttu-id="53e19-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="53e19-107">Methods</span></span>

### <a name="restoredefaultconsoletokencolors"></a><span data-ttu-id="53e19-108">RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="53e19-108">RestoreDefaultConsoleTokenColors\(\)</span></span>

<span data-ttu-id="53e19-109">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="53e19-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="53e19-110">Konsol bölmesinde belirteç renkleri varsayılan değerini geri yükler.</span><span class="sxs-lookup"><span data-stu-id="53e19-110">Restores the default values of the token colors in the Console pane.</span></span>

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a><span data-ttu-id="53e19-111">RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="53e19-111">RestoreDefaults\(\)</span></span>

<span data-ttu-id="53e19-112">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="53e19-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="53e19-113">Konsol bölmesinde tüm seçenekleri ayarlarının varsayılan değerleri geri yükler.</span><span class="sxs-lookup"><span data-stu-id="53e19-113">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="53e19-114">Ayrıca, yeniden gösterilen iletinin önlemek için standart onay kutusu sağlama çeşitli uyarı iletilerini davranışını sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="53e19-114">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a><span data-ttu-id="53e19-115">RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="53e19-115">RestoreDefaultTokenColors\(\)</span></span>

<span data-ttu-id="53e19-116">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="53e19-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="53e19-117">Betik bölmesine belirteci renkleri varsayılan değerini geri yükler.</span><span class="sxs-lookup"><span data-stu-id="53e19-117">Restores the default values of the token colors in the Script pane.</span></span>

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a><span data-ttu-id="53e19-118">RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="53e19-118">RestoreDefaultXmlTokenColors\(\)</span></span>

<span data-ttu-id="53e19-119">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="53e19-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="53e19-120">Windows PowerShell ISE görüntülenen XML öğeleri için belirteç renkleri varsayılan değerlerini geri yükler.</span><span class="sxs-lookup"><span data-stu-id="53e19-120">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="53e19-121">Ayrıca bkz. [XmlTokenColors](#xmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="53e19-121">Also see [XmlTokenColors](#xmltokencolors).</span></span>

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="53e19-122">Özellikler</span><span class="sxs-lookup"><span data-stu-id="53e19-122">Properties</span></span>

### <a name="autosaveminuteinterval"></a><span data-ttu-id="53e19-123">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="53e19-123">AutoSaveMinuteInterval</span></span>

<span data-ttu-id="53e19-124">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="53e19-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="53e19-125">Windows PowerShell ISE göre dosyalarınıza yönelik otomatik kaydetme işlemleri arasındaki dakika sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-125">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="53e19-126">Varsayılan değer 2 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="53e19-126">The default value is 2 minutes.</span></span> <span data-ttu-id="53e19-127">Bir tamsayı değerdir.</span><span class="sxs-lookup"><span data-stu-id="53e19-127">The value is an integer.</span></span>

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a><span data-ttu-id="53e19-128">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="53e19-128">CommandPaneBackgroundColor</span></span>

<span data-ttu-id="53e19-129">Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerini yeniden adlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="53e19-129">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="53e19-130">Sonraki sürümleri için bkz: [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="53e19-130">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="53e19-131">Komut bölmesi arka plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-131">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="53e19-132">Örneği olan **System.Windows.Media.Color** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="53e19-132">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a><span data-ttu-id="53e19-133">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="53e19-133">CommandPaneUp</span></span>

<span data-ttu-id="53e19-134">Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerini yeniden adlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="53e19-134">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

<span data-ttu-id="53e19-135">Komut bölmesi çıkış Bölmesi ' bulunup bulunmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-135">Specifies whether the Command pane is located above the Output pane.</span></span>

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a><span data-ttu-id="53e19-136">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="53e19-136">ConsolePaneBackgroundColor</span></span>

<span data-ttu-id="53e19-137">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="53e19-137">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="53e19-138">Konsol bölmesinde arka plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-138">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="53e19-139">Örneği olan **System.Windows.Media.Color** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="53e19-139">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a><span data-ttu-id="53e19-140">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="53e19-140">ConsolePaneForegroundColor</span></span>

<span data-ttu-id="53e19-141">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="53e19-141">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="53e19-142">Konsol bölmesinde metin ön plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-142">Specifies the foreground color of the text in the Console pane.</span></span>

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a><span data-ttu-id="53e19-143">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="53e19-143">ConsolePaneTextBackgroundColor</span></span>

<span data-ttu-id="53e19-144">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="53e19-144">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="53e19-145">Konsol bölmesinde metin arka plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-145">Specifies the background color of the text in the Console pane.</span></span>

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a><span data-ttu-id="53e19-146">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="53e19-146">ConsoleTokenColors</span></span>

<span data-ttu-id="53e19-147">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="53e19-147">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="53e19-148">Windows PowerShell ISE Konsol bölmesinde IntelliSense belirteçleri rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-148">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="53e19-149">Bu özellik, belirteç türleri ve konsol bölmesinde renklerini ad/değer çiftleri içeren bir sözlük nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="53e19-149">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="53e19-150">Betik bölmesine IntelliSense belirteçleri renkleri değiştirmek için bkz: [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="53e19-150">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tokencolors).</span></span> <span data-ttu-id="53e19-151">Renkleri varsayılan değerlere sıfırla için bkz: [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="53e19-151">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span></span> <span data-ttu-id="53e19-152">Belirteç renkler için aşağıdakileri ayarlayabilirsiniz: özniteliği, komutu, CommandArgument, CommandParameter, açıklama, GroupEnd, GroupStart, anahtar sözcüğü, LineContinuation, LoopLabel, üye, yeni satır, sayı, işleci, konum, StatementSeparator, dize, türü Bilinmiyor, değişkeni'ni tıklatın.</span><span class="sxs-lookup"><span data-stu-id="53e19-152">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a><span data-ttu-id="53e19-153">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="53e19-153">DebugBackgroundColor</span></span>

<span data-ttu-id="53e19-154">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="53e19-154">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="53e19-155">Konsol bölmesinde görüntülenen hata ayıklama metin arka plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-155">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="53e19-156">Örneği olan **System.Windows.Media.Color** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="53e19-156">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a><span data-ttu-id="53e19-157">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="53e19-157">DebugForegroundColor</span></span>

<span data-ttu-id="53e19-158">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="53e19-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="53e19-159">Konsol bölmesinde görüntülenen hata ayıklama metni ön plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-159">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="53e19-160">Örneği olan **System.Windows.Media.Color** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="53e19-160">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a><span data-ttu-id="53e19-161">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="53e19-161">DefaultOptions</span></span>

<span data-ttu-id="53e19-162">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="53e19-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="53e19-163">Reset yöntemleri kullanılırken kullanılacak varsayılan değerler belirten özellikleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="53e19-163">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

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

### <a name="errorbackgroundcolor"></a><span data-ttu-id="53e19-164">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="53e19-164">ErrorBackgroundColor</span></span>

<span data-ttu-id="53e19-165">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="53e19-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="53e19-166">Konsol bölmesinde görüntülenen hata metni arka plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-166">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="53e19-167">Örneği olan **System.Windows.Media.Color** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="53e19-167">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a><span data-ttu-id="53e19-168">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="53e19-168">ErrorForegroundColor</span></span>

<span data-ttu-id="53e19-169">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="53e19-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="53e19-170">Konsol bölmesinde görüntülenen hata metni ön plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-170">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="53e19-171">Örneği olan **System.Windows.Media.Color** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="53e19-171">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a><span data-ttu-id="53e19-172">FontName</span><span class="sxs-lookup"><span data-stu-id="53e19-172">FontName</span></span>

<span data-ttu-id="53e19-173">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="53e19-173">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="53e19-174">Yazı tipi adı şu anda kullanımda betik bölmesine ve konsol bölmesinde belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-174">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a><span data-ttu-id="53e19-175">FontSize</span><span class="sxs-lookup"><span data-stu-id="53e19-175">FontSize</span></span>

<span data-ttu-id="53e19-176">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="53e19-176">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="53e19-177">Yazı tipi boyutu tamsayı olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-177">Specifies the font size as an integer.</span></span> <span data-ttu-id="53e19-178">Betik bölmesine, komut bölmesi ve çıkış bölmesinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="53e19-178">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="53e19-179">Geçerli değerlerin 8 ila 32 arasındadır.</span><span class="sxs-lookup"><span data-stu-id="53e19-179">The valid range of values is 8 through 32.</span></span>

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a><span data-ttu-id="53e19-180">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="53e19-180">IntellisenseTimeoutInSeconds</span></span>

<span data-ttu-id="53e19-181">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="53e19-181">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="53e19-182">Şu anda karakterlerine çözmeye IntelliSense kullanan saniye sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-182">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="53e19-183">Saniye sayısı sonra IntelliSense zaman aşımına uğradı ve yazmaya devam etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="53e19-183">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="53e19-184">Varsayılan değer 3 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="53e19-184">The default value is 3 seconds.</span></span> <span data-ttu-id="53e19-185">Bir tamsayı değerdir.</span><span class="sxs-lookup"><span data-stu-id="53e19-185">The value is an integer.</span></span>

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a><span data-ttu-id="53e19-186">MruCount</span><span class="sxs-lookup"><span data-stu-id="53e19-186">MruCount</span></span>

<span data-ttu-id="53e19-187">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="53e19-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="53e19-188">Windows PowerShell ISE izler ve alt kısmındaki görüntüleyen en son açılan dosyaların sayısını belirtir **Dosya Aç** menüsü.</span><span class="sxs-lookup"><span data-stu-id="53e19-188">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="53e19-189">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="53e19-189">The default value is 10.</span></span> <span data-ttu-id="53e19-190">Bir tamsayı değerdir.</span><span class="sxs-lookup"><span data-stu-id="53e19-190">The value is an integer.</span></span>

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a><span data-ttu-id="53e19-191">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="53e19-191">OutputPaneBackgroundColor</span></span>

<span data-ttu-id="53e19-192">Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerini yeniden adlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="53e19-192">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="53e19-193">Sonraki sürümleri için bkz: [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="53e19-193">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="53e19-194">Çıkış bölmesi için arka plan rengini alır veya ayarlar okuma/yazma özelliği.</span><span class="sxs-lookup"><span data-stu-id="53e19-194">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="53e19-195">Örneği olan **System.Windows.Media.Color** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="53e19-195">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a><span data-ttu-id="53e19-196">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="53e19-196">OutputPaneTextForegroundColor</span></span>

<span data-ttu-id="53e19-197">Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerini yeniden adlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="53e19-197">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="53e19-198">Sonraki sürümleri için bkz: [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span><span class="sxs-lookup"><span data-stu-id="53e19-198">For later versions, see [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span></span>

<span data-ttu-id="53e19-199">Çıkış Bölmesi'nde Windows PowerShell ISE 2.0 metinde ön plan rengini değiştirir okuma/yazma özelliği.</span><span class="sxs-lookup"><span data-stu-id="53e19-199">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a><span data-ttu-id="53e19-200">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="53e19-200">OutputPaneTextBackgroundColor</span></span>

<span data-ttu-id="53e19-201">Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerini yeniden adlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="53e19-201">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="53e19-202">Sonraki sürümleri için bkz: [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="53e19-202">For later versions, see [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span></span>

<span data-ttu-id="53e19-203">Çıkış bölmesinde metin arka plan rengini değiştirir okuma/yazma özelliği.</span><span class="sxs-lookup"><span data-stu-id="53e19-203">The read/write property that changes the background color of the text in the Output pane.</span></span>

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a><span data-ttu-id="53e19-204">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="53e19-204">ScriptPaneBackgroundColor</span></span>

<span data-ttu-id="53e19-205">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="53e19-205">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="53e19-206">Dosyalar için arka plan rengini alır veya ayarlar okuma/yazma özelliği.</span><span class="sxs-lookup"><span data-stu-id="53e19-206">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="53e19-207">Örneği olan **System.Windows.Media.Color** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="53e19-207">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a><span data-ttu-id="53e19-208">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="53e19-208">ScriptPaneForegroundColor</span></span>

<span data-ttu-id="53e19-209">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="53e19-209">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="53e19-210">Alır veya betik bölmesinde betik olmayan dosyaları ön plan rengini ayarlar okuma/yazma özelliği.</span><span class="sxs-lookup"><span data-stu-id="53e19-210">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="53e19-211">Komut dosyaları ön plan rengini ayarlamak için kullanın [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="53e19-211">To set the foreground color for script files, use the [TokenColors](#tokencolors).</span></span>

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a><span data-ttu-id="53e19-212">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="53e19-212">SelectedScriptPaneState</span></span>

<span data-ttu-id="53e19-213">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="53e19-213">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="53e19-214">Alır veya ekranda betik bölmesine konumunu ayarlar okuma/yazma özelliği.</span><span class="sxs-lookup"><span data-stu-id="53e19-214">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="53e19-215">Bir dize olabilir 'Maximized', 'Top' veya 'Right'.</span><span class="sxs-lookup"><span data-stu-id="53e19-215">The string can be either 'Maximized', 'Top', or 'Right'.</span></span>

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a><span data-ttu-id="53e19-216">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="53e19-216">ShowDefaultSnippets</span></span>

<span data-ttu-id="53e19-217">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="53e19-217">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="53e19-218">Belirtir olup olmadığını **CTRL + J** parçacıkları listesini Windows PowerShell'de dahil starter kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="53e19-218">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="53e19-219">Ayarlandığında **$false**, yalnızca kullanıcı tanımlı parçacıkları görünür **CTRL + J** listesi.</span><span class="sxs-lookup"><span data-stu-id="53e19-219">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="53e19-220">Varsayılan değer **$true**.</span><span class="sxs-lookup"><span data-stu-id="53e19-220">The default value is **$true**.</span></span>

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a><span data-ttu-id="53e19-221">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="53e19-221">ShowIntellisenseInConsolePane</span></span>

<span data-ttu-id="53e19-222">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="53e19-222">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="53e19-223">IntelliSense sözdizimi, parametre ve konsol bölmesinde değer önerileri sunar olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-223">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="53e19-224">Varsayılan değer **$true**.</span><span class="sxs-lookup"><span data-stu-id="53e19-224">The default value is **$true**.</span></span>

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a><span data-ttu-id="53e19-225">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="53e19-225">ShowIntellisenseInScriptPane</span></span>

<span data-ttu-id="53e19-226">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="53e19-226">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="53e19-227">IntelliSense sözdizimi, parametre ve betik bölmesine değer önerileri sunar olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-227">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="53e19-228">Varsayılan değer **$true**.</span><span class="sxs-lookup"><span data-stu-id="53e19-228">The default value is **$true**.</span></span>

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a><span data-ttu-id="53e19-229">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="53e19-229">ShowLineNumbers</span></span>

<span data-ttu-id="53e19-230">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="53e19-230">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="53e19-231">Betik bölmesine sol kenar boşluğunda satır numaralarını görüntülenip görüntülenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-231">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="53e19-232">Varsayılan değer **$true**.</span><span class="sxs-lookup"><span data-stu-id="53e19-232">The default value is **$true**.</span></span>

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a><span data-ttu-id="53e19-233">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="53e19-233">ShowOutlining</span></span>

<span data-ttu-id="53e19-234">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="53e19-234">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="53e19-235">Betik bölmesine sol kenar boşluğunda genişletilebilir ve daraltılabilir köşeli kodun bölümlerini yanındaki görüntülenip görüntülenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-235">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="53e19-236">Görüntülendiğinde, eksi tıklatabilirsiniz \( - \) artı tıklayın veya daraltılabilir metin bloğunu yanındaki simge \( + \) bir metin bloğunu genişletmek için simge.</span><span class="sxs-lookup"><span data-stu-id="53e19-236">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="53e19-237">Varsayılan değer **$true**.</span><span class="sxs-lookup"><span data-stu-id="53e19-237">The default value is **$true**.</span></span>

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a><span data-ttu-id="53e19-238">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="53e19-238">ShowToolBar</span></span>

<span data-ttu-id="53e19-239">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="53e19-239">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="53e19-240">ISE araç Windows PowerShell ISE penceresinin en üstünde görüntülenip görüntülenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-240">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="53e19-241">Varsayılan değer **$true**.</span><span class="sxs-lookup"><span data-stu-id="53e19-241">The default value is **$true**.</span></span>

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a><span data-ttu-id="53e19-242">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="53e19-242">ShowWarningBeforeSavingOnRun</span></span>

<span data-ttu-id="53e19-243">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="53e19-243">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="53e19-244">Bunu çalıştırılmadan önce bir komut dosyası otomatik olarak yeniden kaydedildiğinde bir uyarı iletisi görüntülenip görüntülenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-244">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="53e19-245">Varsayılan değer **$true**.</span><span class="sxs-lookup"><span data-stu-id="53e19-245">The default value is **$true**.</span></span>

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a><span data-ttu-id="53e19-246">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="53e19-246">ShowWarningForDuplicateFiles</span></span>

<span data-ttu-id="53e19-247">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="53e19-247">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="53e19-248">Aynı dosyanın farklı PowerShell sekmelerde açıldığında bir uyarı iletisi görüntülenip görüntülenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-248">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="53e19-249">Varsa kümesine **$true**, bu iletiyi birden çok sekme görüntüler aynı dosyayı açmaya: "Bu dosyanın bir kopyasını başka bir Windows PowerShell sekmesinde açıktır. Bu dosyada yapılan değişiklikler tüm açık kopyaları etkiler."</span><span class="sxs-lookup"><span data-stu-id="53e19-249">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab. Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="53e19-250">Varsayılan değer **$true**.</span><span class="sxs-lookup"><span data-stu-id="53e19-250">The default value is **$true**.</span></span>

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a><span data-ttu-id="53e19-251">TokenColors</span><span class="sxs-lookup"><span data-stu-id="53e19-251">TokenColors</span></span>

<span data-ttu-id="53e19-252">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="53e19-252">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="53e19-253">Windows PowerShell ISE betik bölmesinde IntelliSense belirteçleri rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-253">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="53e19-254">Bu özellik, belirteç türleri ve betik bölmesine renklerini ad/değer çiftleri içeren bir sözlük nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="53e19-254">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="53e19-255">Konsol bölmesinde IntelliSense belirteçleri renkleri değiştirmek için bkz: [ConsoleTokenColors](#consoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="53e19-255">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#consoletokencolors).</span></span> <span data-ttu-id="53e19-256">Renkleri varsayılan değerlere sıfırla için bkz: [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span><span class="sxs-lookup"><span data-stu-id="53e19-256">To reset the colors to the default values, see [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span></span> <span data-ttu-id="53e19-257">Belirteç renkler için aşağıdakileri ayarlayabilirsiniz: özniteliği, komutu, CommandArgument, CommandParameter, açıklama, GroupEnd, GroupStart, anahtar sözcüğü, LineContinuation, LoopLabel, üye, yeni satır, sayı, işleci, konum, StatementSeparator, dize, türü Bilinmiyor, değişkeni'ni tıklatın.</span><span class="sxs-lookup"><span data-stu-id="53e19-257">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a><span data-ttu-id="53e19-258">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="53e19-258">UseEnterToSelectInConsolePaneIntellisense</span></span>

<span data-ttu-id="53e19-259">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="53e19-259">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="53e19-260">Konsol bölmesinde seçeneği sağlanan IntelliSense seçmek için Enter tuşuna kullanabilirsiniz olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-260">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="53e19-261">Varsayılan değer **$true**.</span><span class="sxs-lookup"><span data-stu-id="53e19-261">The default value is **$true**.</span></span>

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a><span data-ttu-id="53e19-262">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="53e19-262">UseEnterToSelectInScriptPaneIntellisense</span></span>

<span data-ttu-id="53e19-263">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="53e19-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="53e19-264">Bir IntelliSense tarafından sağlanan betik bölmesinde seçeneği için Enter tuşuna kullanıp kullanmayacağınızı belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-264">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="53e19-265">Varsayılan değer **$true**.</span><span class="sxs-lookup"><span data-stu-id="53e19-265">The default value is **$true**.</span></span>

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a><span data-ttu-id="53e19-266">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="53e19-266">UseLocalHelp</span></span>

<span data-ttu-id="53e19-267">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="53e19-267">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="53e19-268">Bir anahtar sözcük bulunan imleç ile F1 tuşuna bastığınızda, yerel olarak yüklenmiş Yardım veya çevrimiçi TechNet Kitaplığı Yardım görüntülenip görüntülenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-268">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="53e19-269">Varsa kümesine **$true**, sonra da bir açılır pencere yerel olarak yüklenmiş Yardım içerik gösterir.</span><span class="sxs-lookup"><span data-stu-id="53e19-269">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="53e19-270">Yardım dosyalarını çalıştırarak yükleyebilirsiniz `Update-Help` komutu.</span><span class="sxs-lookup"><span data-stu-id="53e19-270">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="53e19-271">Varsa kümesine **$false**, sonra da tarayıcınızı TechNet Kitaplığı'nda bir sayfa açar.</span><span class="sxs-lookup"><span data-stu-id="53e19-271">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a><span data-ttu-id="53e19-272">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="53e19-272">VerboseBackgroundColor</span></span>

<span data-ttu-id="53e19-273">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="53e19-273">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="53e19-274">Konsol bölmesinde görüntülenen ayrıntılı metin arka plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-274">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="53e19-275">Bu bir **System.Windows.Media.Color** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="53e19-275">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a><span data-ttu-id="53e19-276">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="53e19-276">VerboseForegroundColor</span></span>

<span data-ttu-id="53e19-277">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="53e19-277">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="53e19-278">Konsol bölmesinde görüntülenen ayrıntılı metin ön plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-278">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="53e19-279">Bu bir **System.Windows.Media.Color** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="53e19-279">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a><span data-ttu-id="53e19-280">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="53e19-280">WarningBackgroundColor</span></span>

<span data-ttu-id="53e19-281">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="53e19-281">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="53e19-282">Konsol bölmesinde görüntülenen uyarı metni arka plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-282">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="53e19-283">Bu bir **System.Windows.Media.Color** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="53e19-283">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a><span data-ttu-id="53e19-284">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="53e19-284">WarningForegroundColor</span></span>

<span data-ttu-id="53e19-285">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="53e19-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="53e19-286">Çıkış Bölmesi'nde görüntülenen uyarı metni ön plan rengini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-286">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="53e19-287">Bu bir **System.Windows.Media.Color** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="53e19-287">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a><span data-ttu-id="53e19-288">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="53e19-288">XmlTokenColors</span></span>

<span data-ttu-id="53e19-289">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="53e19-289">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="53e19-290">Belirteç türleri ve Windows PowerShell ISE görüntülenen XML içeriği için renk ad/değer çiftleri içeren bir sözlük nesnesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-290">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="53e19-291">Belirteç renkler için aşağıdakileri ayarlayabilirsiniz: özniteliği, komutu, CommandArgument, CommandParameter, açıklama, GroupEnd, GroupStart, anahtar sözcüğü, LineContinuation, LoopLabel, üye, yeni satır, sayı, işleci, konum, StatementSeparator, dize, türü Bilinmiyor, değişkeni'ni tıklatın.</span><span class="sxs-lookup"><span data-stu-id="53e19-291">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="53e19-292">Ayrıca bkz. [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="53e19-292">Also see [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span></span>

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a><span data-ttu-id="53e19-293">Yakınlaştır</span><span class="sxs-lookup"><span data-stu-id="53e19-293">Zoom</span></span>

<span data-ttu-id="53e19-294">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="53e19-294">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="53e19-295">Metin göreli boyutunu hem Konsol hem de betik bölmelerinde belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e19-295">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="53e19-296">Varsayılan değer 100'dür.</span><span class="sxs-lookup"><span data-stu-id="53e19-296">The default value is 100.</span></span> <span data-ttu-id="53e19-297">Daha küçük değerler metni büyük görüntülenecek metni büyük sayılar neden olurken küçük görünmesini Windows PowerShell ISE'de neden olur.</span><span class="sxs-lookup"><span data-stu-id="53e19-297">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="53e19-298">20 400 aralıkları bir tamsayı değerdir.</span><span class="sxs-lookup"><span data-stu-id="53e19-298">The value is an integer that ranges from 20 to 400.</span></span>

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="53e19-299">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="53e19-299">See Also</span></span>

- [<span data-ttu-id="53e19-300">Nesne modeli komut dosyası Windows PowerShell ISE amacı</span><span class="sxs-lookup"><span data-stu-id="53e19-300">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="53e19-301">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="53e19-301">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)