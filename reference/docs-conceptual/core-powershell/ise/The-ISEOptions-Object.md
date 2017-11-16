---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: ISEOptions nesnesi
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: 5e04adeebacfb9214bf39d9ec9c5f0e01f5729ee
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="the-iseoptions-object"></a>ISEOptions nesnesi
  **ISEOptions** nesnesi, Windows PowerShell ISE için çeşitli ayarlar'ı temsil eder. Örneği olan **Microsoft.PowerShell.Host.ISE.ISEOptions** sınıfı.

 **ISEOptions** nesnesi, aşağıdaki yöntemleri ve özellikleri sağlar.

## <a name="methods"></a>Yöntemler

### <a name="restoredefaultconsoletokencolors"></a>RestoreDefaultConsoleTokenColors\(\)
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

 Konsol bölmesinde belirteç renkleri varsayılan değerini geri yükler.

```
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = "red"
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a>RestoreDefaults\(\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 Konsol bölmesinde tüm seçenekleri ayarlarının varsayılan değerleri geri yükler. Ayrıca, yeniden gösterilen iletinin önlemek için standart onay kutusu sağlama çeşitli uyarı iletilerini davranışını sıfırlar.

```
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = "orange"
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a>RestoreDefaultTokenColors\(\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 Betik bölmesine belirteci renkleri varsayılan değerini geri yükler.

```
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a>RestoreDefaultXmlTokenColors\(\)
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

 Windows PowerShell ISE görüntülenen XML öğeleri için belirteç renkleri varsayılan değerlerini geri yükler. Ayrıca bkz. [XmlTokenColors](#xmltokencolors).

```
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a>Özellikler

### <a name="autosaveminuteinterval"></a>AutoSaveMinuteInterval
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

 Windows PowerShell ISE göre dosyalarınıza yönelik otomatik kaydetme işlemleri arasındaki dakika sayısını belirtir. Varsayılan değer 2 dakikadır. Bir tamsayı değerdir.

```
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a>CommandPaneBackgroundColor
  Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerini yeniden adlandırıldı.  Sonraki sürümleri için bkz: [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).

 Komut bölmesi arka plan rengini belirtir. Örneği olan **System.Windows.Media.Color** sınıfı.

```
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = "orange"
```

### <a name="commandpaneup"></a>CommandPaneUp
  Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerini yeniden adlandırıldı.

 Komut bölmesi çıkış Bölmesi ' bulunup bulunmadığını belirtir.

```
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true

```

### <a name="consolepanebackgroundcolor"></a>ConsolePaneBackgroundColor
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

 Konsol bölmesinde arka plan rengini belirtir. Örneği olan **System.Windows.Media.Color** sınıfı.

```
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = "red"
```

### <a name="consolepaneforegroundcolor"></a>ConsolePaneForegroundColor
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

 Konsol bölmesinde metin ön plan rengini belirtir.

```
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = "yellow"

```

### <a name="consolepanetextbackgroundcolor"></a>ConsolePaneTextBackgroundColor
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

 Konsol bölmesinde metin arka plan rengini belirtir.

```
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = "pink"
```

### <a name="consoletokencolors"></a>ConsoleTokenColors
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

 Windows PowerShell ISE Konsol bölmesinde IntelliSense belirteçleri rengini belirtir. Bu özellik, belirteç türleri ve konsol bölmesinde renklerini ad/değer çiftleri içeren bir sözlük nesnesidir. Betik bölmesine IntelliSense belirteçleri renkleri değiştirmek için bkz: [TokenColors](#tokencolors). Renkleri varsayılan değerlere sıfırla için bkz: [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors). Belirteç renkler için aşağıdakileri ayarlayabilirsiniz: özniteliği, komutu, CommandArgument, CommandParameter, açıklama, GroupEnd, GroupStart, anahtar sözcüğü, LineContinuation, LoopLabel, üye, yeni satır, sayı, işleci, konum, StatementSeparator, dize, türü Bilinmiyor, değişkeni'ni tıklatın.

```
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = "magenta"

```

### <a name="debugbackgroundcolor"></a>DebugBackgroundColor
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 Konsol bölmesinde görüntülenen hata ayıklama metin arka plan rengini belirtir. Örneği olan **System.Windows.Media.Color** sınıfı.

```
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor ='#0000FF'
```

### <a name="debugforegroundcolor"></a>DebugForegroundColor
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 Konsol bölmesinde görüntülenen hata ayıklama metni ön plan rengini belirtir. Örneği olan **System.Windows.Media.Color** sınıfı.

```
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor ="yellow"
```

### <a name="defaultoptions"></a>DefaultOptions
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 Reset yöntemleri kullanılırken kullanılacak varsayılan değerler belirten özellikleri koleksiyonu.

```
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
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 Konsol bölmesinde görüntülenen hata metni arka plan rengini belirtir. Örneği olan **System.Windows.Media.Color** sınıfı.

```
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor="black"
```

### <a name="errorforegroundcolor"></a>ErrorForegroundColor
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 Konsol bölmesinde görüntülenen hata metni ön plan rengini belirtir. Örneği olan **System.Windows.Media.Color** sınıfı.

```
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor ="green"
```

### <a name="fontname"></a>FontName
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 Yazı tipi adı şu anda kullanımda betik bölmesine ve konsol bölmesinde belirtir.

```
# Changes the font used in both panes.
$psISE.Options.FontName = "courier new"
```

### <a name="fontsize"></a>FontSize
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 Yazı tipi boyutu tamsayı olarak belirtir. Betik bölmesine, komut bölmesi ve çıkış bölmesinde kullanılır. Geçerli değerlerin 8 ila 32 arasındadır.

```
# Changes the font size in all panes.
$psISE.Options.FontSize = 20

```

### <a name="intellisensetimeoutinseconds"></a>IntellisenseTimeoutInSeconds
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

 Şu anda karakterlerine çözmeye IntelliSense kullanan saniye sayısını belirtir. Saniye sayısı sonra IntelliSense zaman aşımına uğradı ve yazmaya devam etmenizi sağlar. Varsayılan değer 3 saniyedir. Bir tamsayı değerdir.

```
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a>MruCount
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

 Windows PowerShell ISE izler ve alt kısmındaki görüntüleyen en son açılan dosyaların sayısını belirtir **Dosya Aç** menüsü. Varsayılan değer 10'dur. Bir tamsayı değerdir.

```
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a>OutputPaneBackgroundColor
  Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerini yeniden adlandırıldı.  Sonraki sürümleri için bkz: [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).

 Çıkış bölmesi için arka plan rengini alır veya ayarlar okuma/yazma özelliği. Örneği olan **System.Windows.Media.Color** sınıfı.

```
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = "gold"

```

### <a name="outputpanetextforegroundcolor"></a>OutputPaneTextForegroundColor
  Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerini yeniden adlandırıldı.  Sonraki sürümleri için bkz: [ConsolePaneForegroundColor](#consolepaneforegroundcolor).

 Çıkış Bölmesi'nde Windows PowerShell ISE 2.0 metinde ön plan rengini değiştirir okuma/yazma özelliği.

```
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = "blue"

```

### <a name="outputpanetextbackgroundcolor"></a>OutputPaneTextBackgroundColor
  Bu özellik Windows PowerShell ISE 2. 0'da, mevcut ancak kaldırıldı veya işe sonraki sürümlerini yeniden adlandırıldı.  Sonraki sürümleri için bkz: [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).

 Çıkış bölmesinde metin arka plan rengini değiştirir okuma/yazma özelliği.

```
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = "pink"
```

### <a name="scriptpanebackgroundcolor"></a>ScriptPaneBackgroundColor
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 Dosyalar için arka plan rengini alır veya ayarlar okuma/yazma özelliği. Örneği olan **System.Windows.Media.Color** sınıfı.

```

# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'

```

### <a name="scriptpaneforegroundcolor"></a>ScriptPaneForegroundColor
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 Alır veya betik bölmesinde betik olmayan dosyaları ön plan rengini ayarlar okuma/yazma özelliği.
Komut dosyaları ön plan rengini ayarlamak için kullanın [TokenColors](#tokencolors).

```
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = "green"

```

### <a name="selectedscriptpanestate"></a>SelectedScriptPaneState
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 Alır veya ekranda betik bölmesine konumunu ayarlar okuma/yazma özelliği. Bir dize olabilir "Maximized", "Üst" veya "Sağ".

```
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = "Top"
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = "Right"
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = "Maximized"

```

### <a name="showdefaultsnippets"></a>ShowDefaultSnippets
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

 Belirtir olup olmadığını **CTRL + J** parçacıkları listesini Windows PowerShell'de dahil starter kümesi içerir. Ayarlandığında **$false**, yalnızca kullanıcı tanımlı parçacıkları görünür **CTRL + J** listesi. Varsayılan değer **$true**.

```
# Hide the default snippets from the CTRL+J list.
$psISe.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a>ShowIntellisenseInConsolePane
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

 IntelliSense sözdizimi, parametre ve konsol bölmesinde değer önerileri sunar olup olmadığını belirtir. Varsayılan değer **$true**.

```
# Turn off IntelliSense in the console pane.
$psISe.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a>ShowIntellisenseInScriptPane
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

 IntelliSense sözdizimi, parametre ve betik bölmesine değer önerileri sunar olup olmadığını belirtir. Varsayılan değer **$true**.

```
# Turn off IntelliSense in the Script pane.
$psISe.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a>ShowLineNumbers
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

 Betik bölmesine sol kenar boşluğunda satır numaralarını görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer **$true**.

```
# Turn off line numbers in the Script pane.
$psISe.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a>ShowOutlining
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

 Betik bölmesine sol kenar boşluğunda genişletilebilir ve daraltılabilir köşeli kodun bölümlerini yanındaki görüntülenip görüntülenmeyeceğini belirtir. Görüntülendiğinde, eksi tıklatabilirsiniz \( - \) artı tıklayın veya daraltılabilir metin bloğunu yanındaki simge \( + \) bir metin bloğunu genişletmek için simge. Varsayılan değer **$true**.

```
# Turn off outlining in the Script pane.
$psISe.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a>ShowToolBar
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 ISE araç Windows PowerShell ISE penceresinin en üstünde görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer **$true**.

```
# Show the toolbar.
$psISe.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a>ShowWarningBeforeSavingOnRun
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 Bunu çalıştırılmadan önce bir komut dosyası otomatik olarak yeniden kaydedildiğinde bir uyarı iletisi görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer **$true**.

```
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun=$true

```

### <a name="showwarningforduplicatefiles"></a>ShowWarningForDuplicateFiles
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 Aynı dosyanın farklı PowerShell sekmelerde açıldığında bir uyarı iletisi görüntülenip görüntülenmeyeceğini belirtir. Varsa kümesine **$true**, bu iletiyi birden çok sekme görüntüler aynı dosyayı açmaya: "Bu dosyanın bir kopyasını başka bir Windows PowerShell sekmesinde açıktır. Bu dosyada yapılan değişiklikler tüm açık kopyaları etkiler." Varsayılan değer **$true**.

```
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true

```

### <a name="tokencolors"></a>TokenColors
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 Windows PowerShell ISE betik bölmesinde IntelliSense belirteçleri rengini belirtir. Bu özellik, belirteç türleri ve betik bölmesine renklerini ad/değer çiftleri içeren bir sözlük nesnesidir. Konsol bölmesinde IntelliSense belirteçleri renkleri değiştirmek için bkz: [ConsoleTokenColors](#consoletokencolors). Renkleri varsayılan değerlere sıfırla için bkz: [RestoreDefaultTokenColors](#restoredefaulttokencolors). Belirteç renkler için aşağıdakileri ayarlayabilirsiniz: özniteliği, komutu, CommandArgument, CommandParameter, açıklama, GroupEnd, GroupStart, anahtar sözcüğü, LineContinuation, LoopLabel, üye, yeni satır, sayı, işleci, konum, StatementSeparator, dize, türü Bilinmiyor, değişkeni'ni tıklatın.

```
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"

```

### <a name="useentertoselectinconsolepaneintellisense"></a>UseEnterToSelectInConsolePaneIntellisense
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

 Konsol bölmesinde seçeneği sağlanan IntelliSense seçmek için Enter tuşuna kullanabilirsiniz olup olmadığını belirtir. Varsayılan değer **$true**.

```
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$false

```

### <a name="useentertoselectinscriptpaneintellisense"></a>UseEnterToSelectInScriptPaneIntellisense
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

 Bir IntelliSense tarafından sağlanan betik bölmesinde seçeneği için Enter tuşuna kullanıp kullanmayacağınızı belirtir. Varsayılan değer **$true**.

```
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$true

```

### <a name="uselocalhelp"></a>UseLocalHelp
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

 Bir anahtar sözcük bulunan imleç ile F1 tuşuna bastığınızda, yerel olarak yüklenmiş Yardım veya çevrimiçi TechNet Kitaplığı Yardım görüntülenip görüntülenmeyeceğini belirtir. Varsa kümesine **$true**, sonra da bir açılır pencere yerel olarak yüklenmiş Yardım içerik gösterir. Yardım dosyalarını çalıştırarak yükleyebilirsiniz `Update-Help` komutu. Varsa kümesine **$false**, sonra da tarayıcınızı TechNet Kitaplığı'nda bir sayfa açar.

```
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp=$false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp=$true

```

### <a name="verbosebackgroundcolor"></a>VerboseBackgroundColor
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 Konsol bölmesinde görüntülenen ayrıntılı metin arka plan rengini belirtir. Bu bir **System.Windows.Media.Color** nesnesi.

```
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a>VerboseForegroundColor
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 Konsol bölmesinde görüntülenen ayrıntılı metin ön plan rengini belirtir. Bu bir **System.Windows.Media.Color** nesnesi.

```
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor ='yellow'
```

### <a name="warningbackgroundcolor"></a>WarningBackgroundColor
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 Konsol bölmesinde görüntülenen uyarı metni arka plan rengini belirtir. Bu bir **System.Windows.Media.Color** nesnesi.

```
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor ='#0000FF'
```

### <a name="warningforegroundcolor"></a>WarningForegroundColor
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 Çıkış Bölmesi'nde görüntülenen uyarı metni ön plan rengini belirtir. Bu bir **System.Windows.Media.Color** nesnesi.

```
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor ='yellow'
```

### <a name="xmltokencolors"></a>XmlTokenColors
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

 Belirteç türleri ve Windows PowerShell ISE görüntülenen XML içeriği için renk ad/değer çiftleri içeren bir sözlük nesnesi belirtir. Belirteç renkler için aşağıdakileri ayarlayabilirsiniz: özniteliği, komutu, CommandArgument, CommandParameter, açıklama, GroupEnd, GroupStart, anahtar sözcüğü, LineContinuation, LoopLabel, üye, yeni satır, sayı, işleci, konum, StatementSeparator, dize, türü Bilinmiyor, değişkeni'ni tıklatın. Ayrıca bkz. [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).

```
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = "green"
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = "magenta"

```

### <a name="zoom"></a>Yakınlaştır
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

 Metin göreli boyutunu hem Konsol hem de betik bölmelerinde belirtir. Varsayılan değer 100'dür. Daha küçük değerler metni büyük görüntülenecek metni büyük sayılar neden olurken küçük görünmesini Windows PowerShell ISE'de neden olur. 20 400 aralıkları bir tamsayı değerdir.

```
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a>Ayrıca bkz:
- [Windows PowerShell ISE nesne modeli komut dosyası oluşturma](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Windows PowerShell ISE nesne modeli başvurusu](Windows-PowerShell-ISE-Object-Model-Reference.md)

