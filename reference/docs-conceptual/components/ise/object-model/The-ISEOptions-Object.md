---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISEOptions Nesnesi
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: e756da21aaa5465f7fa6a90563b4180f0c89e87b
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405928"
---
# <a name="the-iseoptions-object"></a>ISEOptions Nesnesi

**Iseoptions** nesnesi, Windows PowerShell ISE için çeşitli ayarlar'ı temsil eder. Bir örneğidir **Microsoft.PowerShell.Host.ISE.ISEOptions** sınıfı.

**Iseoptions** nesnesi, aşağıdaki yöntemleri ve özellikleri sağlar.

## <a name="methods"></a>Yöntemler

### <a name="restoredefaultconsoletokencolors"></a>RestoreDefaultConsoleTokenColors\(\)

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Konsol bölmesinde belirteç renkleri için varsayılan değerleri yükler.

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a>RestoreDefaults\(\)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Konsol bölmesinde tüm seçenekleri ayarlar için varsayılan değerleri yükler. Ayrıca, ileti yeniden gösterilen önlemek için standart onay kutusunu sağlayan çeşitli uyarı iletilerini davranışını sıfırlar.

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a>RestoreDefaultTokenColors\(\)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Betik bölmesini simge renkleri için varsayılan değerleri yükler.

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a>RestoreDefaultXmlTokenColors\(\)

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Windows PowerShell ISE'de görüntülenen XML öğeleri için belirteç renkleri için varsayılan değerleri yükler. Ayrıca bkz: [XmlTokenColors](#xmltokencolors).

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a>Özellikler

### <a name="autosaveminuteinterval"></a>AutoSaveMinuteInterval

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Windows PowerShell ISE tarafından dosyalarınızın otomatik kaydetme işlemleri arasındaki dakika sayısını belirtir. Varsayılan değer 2 dakikadır. Bir tamsayı değerdir.

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a>CommandPaneBackgroundColor

Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerde yeniden adlandırıldı.  Sonraki sürümleri için bkz: [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).

Komut bölmesi için arka plan rengini belirtir. Bir örneğidir **System.Windows.Media.Color** sınıfı.

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a>CommandPaneUp

Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerde yeniden adlandırıldı.

Komut bölmesi çıkış Bölmesi ' bulunup bulunmadığını belirtir.

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a>ConsolePaneBackgroundColor

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Konsol bölmesinde arka plan rengini belirtir. Bir örneğidir **System.Windows.Media.Color** sınıfı.

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a>ConsolePaneForegroundColor

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Konsol bölmesinde metin ön plan rengini belirtir.

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a>ConsolePaneTextBackgroundColor

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Konsol bölmesinde metin arka plan rengini belirtir.

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a>ConsoleTokenColors

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Windows PowerShell ISE Konsol bölmesinde IntelliSense belirteçleri rengini belirtir. Bu özellik belirteç türleri ve konsol bölmesinde renkleri ad/değer çiftleri içeren bir sözlük nesnesidir. Betik bölmesindeki IntelliSense belirteçlerin renkleri değiştirmek için bkz: [TokenColors](#tokencolors). Renkleri varsayılan değerlere sıfırlamak için bkz: [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors). Belirteç renkleri, aşağıdakiler için ayarlanabilir: Öznitelik, komut, CommandArgument, CommandParameter, açıklama, GroupEnd, GroupStart, anahtar sözcüğü, LineContinuation, LoopLabel, üye, yeni satır, sayı, işleci, konum, StatementSeparator, dize, türü, bilinmeyen, değişken.

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a>DebugBackgroundColor

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Konsol bölmesinde görüntülenen hata ayıklama metin arka plan rengini belirtir. Bir örneğidir **System.Windows.Media.Color** sınıfı.

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a>DebugForegroundColor

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Konsol bölmesinde görüntülenen hata ayıklama metin ön plan rengini belirtir. Bir örneğidir **System.Windows.Media.Color** sınıfı.

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a>DefaultOptions

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Yöntemleri sıfırlama kullanıldığında kullanılacak varsayılan değerleri belirten özellikleri koleksiyonu.

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

### <a name="errorbackgroundcolor"></a>ErrorBackgroundColor

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Konsol bölmesinde görüntülenen hata metni arka plan rengini belirtir. Bir örneğidir **System.Windows.Media.Color** sınıfı.

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a>ErrorForegroundColor

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Konsol bölmesinde görünen hata metin ön plan rengini belirtir. Bir örneğidir **System.Windows.Media.Color** sınıfı.

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a>FontName

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Yazı tipi adı şu anda betik bölmesi ve konsol bölmesinde hem belirtir.

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a>FontSize

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Bir tamsayı olarak yazı tipi boyutunu belirtir. Bu betik bölmesine, komut bölmesi ve çıkış Bölmesi ' kullanılır. Değerlerinin geçerli aralığı 8 ile 32 ' dir.

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a>IntellisenseTimeoutInSeconds

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Şu anda karakterlerine çözümlemeyi denemek için IntelliSense kullanan saniye sayısını belirtir. Bu kadar saniye sonra IntelliSense zaman aşımına uğrar ve yazmaya devam etmenize olanak sağlar. Varsayılan değer 3 saniyedir. Bir tamsayı değerdir.

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a>MruCount

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Windows PowerShell ISE izler ve alt kısmında görüntüler en son açılan dosyaları belirtir **Dosya Aç** menüsü. Varsayılan değer 10'dur. Bir tamsayı değerdir.

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a>OutputPaneBackgroundColor

Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerde yeniden adlandırıldı.  Sonraki sürümleri için bkz: [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).

Çıkış bölmesi için arka plan rengini alır veya ayarlar okuma/yazma özelliği. Bir örneğidir **System.Windows.Media.Color** sınıfı.

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a>OutputPaneTextForegroundColor

Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerde yeniden adlandırıldı.  Sonraki sürümleri için bkz: [ConsolePaneForegroundColor](#consolepaneforegroundcolor).

Windows PowerShell ISE 2.0 çıkış bölmesinde metin ön plan rengini değiştiren okuma/yazma özelliği.

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a>OutputPaneTextBackgroundColor

Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerde yeniden adlandırıldı.  Sonraki sürümleri için bkz: [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).

Metin çıkışı bölmesindeki arka plan rengi değişir okuma/yazma özelliği.

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a>ScriptPaneBackgroundColor

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Dosyaları için arka plan rengini alır veya ayarlar okuma/yazma özelliği. Bir örneğidir **System.Windows.Media.Color** sınıfı.

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a>ScriptPaneForegroundColor

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Alır veya betik bölmesinde olmayan komut dosyalarını ön plan rengini ayarlar okuma/yazma özelliği.
Komut dosyalarını ön plan rengini ayarlamak için kullanın [TokenColors](#tokencolors).

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a>SelectedScriptPaneState

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Ekranda betik bölmesini konumunu ayarlar veya alır okuma/yazma özelliği. Bir dize olabilir 'Maximized', 'Top' veya 'Right'.

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a>ShowDefaultSnippets

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Belirtir olup olmadığını **CTRL + J** parçacıkları listesi Windows PowerShell'de dahil başlangıç kümesi içerir. Ayarlandığında **$false**, yalnızca kullanıcı tarafından tanımlanan kod parçacıkları görünür **CTRL + J** listesi. Varsayılan değer **$true**.

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a>ShowIntellisenseInConsolePane

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

IntelliSense, sözdizimi, parametre ve konsol bölmesinde değer önerileri sunup sunmadığını belirtir. Varsayılan değer **$true**.

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a>ShowIntellisenseInScriptPane

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

IntelliSense sözdizimi, parametre ve betik bölmesine değer önerileri sunup belirtir. Varsayılan değer **$true**.

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a>ShowLineNumbers

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Betik bölmesi sol kenar boşluğunda satır numaralarını görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer **$true**.

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a>ShowOutlining

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Betik bölmesi sol kenar boşluğunda kod bölümlerini yanındaki köşeli ayraçlar genişletilebilen ve daraltılabilen görüntülenip görüntülenmeyeceğini belirtir. Görüntülendiğinde, eksi tıklayabilirsiniz \( - \) simgeler yanındaki artı işaretine tıklayın veya daraltılabilir metin bloğu \( + \) simgesini metin bloğu genişletin. Varsayılan değer **$true**.

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a>ShowToolBar

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

ISE araç Windows PowerShell ISE penceresi üstündeki görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer **$true**.

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a>ShowWarningBeforeSavingOnRun

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Bunu çalıştırılmadan önce bir komut dosyası otomatik olarak kaydedildiğinde bir uyarı iletisi görünür olup olmadığını belirtir. Varsayılan değer **$true**.

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a>ShowWarningForDuplicateFiles

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Aynı dosyanın farklı PowerShell sekmelerde açıldığında bir uyarı iletisi görünür olup olmadığını belirtir. Varsa kümesine **$true**aynı dosyanın birden çok sekme görüntüler bu iletiyi açmak için: "Bu dosyanın bir kopyasını başka bir Windows PowerShell sekmeyi açık durumdadır. Bu dosyada yapılan değişiklikler tüm açık kopyaları etkiler." Varsayılan değer **$true**.

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a>TokenColors

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Windows PowerShell ISE betik bölmesinde IntelliSense belirteçleri rengini belirtir. Bu betik bölmesine için renkleri ve belirteç türleri ad/değer çiftleri içeren bir sözlük nesnesi özelliğidir. Konsol bölmesinde IntelliSense belirteçlerin renkleri değiştirmek için bkz: [ConsoleTokenColors](#consoletokencolors). Renkleri varsayılan değerlere sıfırlamak için bkz: [RestoreDefaultTokenColors](#restoredefaulttokencolors). Belirteç renkleri, aşağıdakiler için ayarlanabilir: Öznitelik, komut, CommandArgument, CommandParameter, açıklama, GroupEnd, GroupStart, anahtar sözcüğü, LineContinuation, LoopLabel, üye, yeni satır, sayı, işleci, konum, StatementSeparator, dize, türü, bilinmeyen, değişken.

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a>UseEnterToSelectInConsolePaneIntellisense

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Konsol bölmesinde seçeneği sağlanan bir IntelliSense seçmek için Enter tuşunu kullanabilirsiniz olup olmadığını belirtir. Varsayılan değer **$true**.

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a>UseEnterToSelectInScriptPaneIntellisense

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

IntelliSense tarafından sağlanan bir seçenek betik bölmesinde seçmek için Enter tuşunu kullanabilirsiniz olup olmadığını belirtir. Varsayılan değer **$true**.

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a>UseLocalHelp

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Bir anahtar sözcük bulunan imleç ile F1 tuşuna bastığınızda yerel olarak yüklenmiş Yardım veya çevrimiçi TechNet Kitaplığı Yardım görüntülenip görüntülenmeyeceğini belirtir. Varsa kümesine **$true**, sonra da bir açılır pencere yerel olarak yüklenmiş Yardım içerik gösterir. Yardım dosyaları çalıştırarak yükleyebilirsiniz `Update-Help` komutu. Varsa kümesine **$false**, TechNet Kitaplığı'nda bir sayfa için tarayıcınızı açar.

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a>VerboseBackgroundColor

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Konsol bölmesinde görünen ayrıntılı metin arka plan rengini belirtir. Bu bir **System.Windows.Media.Color** nesne.

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a>VerboseForegroundColor

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Konsol bölmesinde görünen ayrıntılı metin ön plan rengini belirtir. Bu bir **System.Windows.Media.Color** nesne.

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a>WarningBackgroundColor

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Konsol bölmesinde görüntülenen uyarı metni arka plan rengini belirtir. Bu bir **System.Windows.Media.Color** nesne.

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a>WarningForegroundColor

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Çıkış Bölmesi'nde görüntülenen uyarı metni ön plan rengini belirtir. Bu bir **System.Windows.Media.Color** nesne.

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a>XmlTokenColors

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Windows PowerShell ISE'de görüntülenen XML içeriği için renkleri ve belirteç türleri ad/değer çiftleri içeren bir sözlük nesnesini belirtir. Belirteç renkleri, aşağıdakiler için ayarlanabilir: Öznitelik, komut, CommandArgument, CommandParameter, açıklama, GroupEnd, GroupStart, anahtar sözcüğü, LineContinuation, LoopLabel, üye, yeni satır, sayı, işleci, konum, StatementSeparator, dize, türü, bilinmeyen, değişken. Ayrıca bkz: [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a>Yakınlaştırma

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Hem konsol hem de betik bölmelerinde metin boyutunu belirtir. Varsayılan değer 100'dür. Daha küçük değerler metni büyük görüntülenecek metin daha büyük sayılar neden olurken daha küçük görünür için Windows PowerShell ISE'de neden olur. 20'den 400 arasında bir tamsayı değerdir.

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a>Ayrıca bkz:

- [Windows PowerShell ISE betik oluşturma nesne modelinin amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)