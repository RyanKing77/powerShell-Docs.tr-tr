---
ms.date: 08/14/2018
keywords: PowerShell cmdlet'i
title: PowerShell.exe Komut Satırı Yardımı
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: 03c7672ee72698fe88a73e99702ceaadf87e702f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51691839"
---
# <a name="powershellexe-command-line-help"></a>PowerShell.exe komut satırı Yardımı

Cmd.exe gibi başka bir aracının komut satırı bir PowerShell oturumu başlatmak için PowerShell.exe kullanın veya yeni bir oturum başlatmak için PowerShell komut satırında kullanın. Oturum özelleştirmek için parametreleri kullanın.

## <a name="syntax"></a>Sözdizimi

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}]
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive]
       [-NoProfile]
       [-OutputFormat {Text | XML}]
       [-PSConsoleFile <FilePath> | -Version <PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a>Parametreler

### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand <Base64EncodedCommand>

Bir komut base-64 kodlu dize sürümünü kabul eder. Karmaşık tırnak işaretleri veya küme ayraçları gerektiren PowerShell komutları göndermek için bu parametreyi kullanın.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>

Geçerli oturum için varsayılan yürütme ilkesini ayarlar ve içinde $env kaydeder: PSExecutionPolicyPreference ortam değişkeni. Bu parametre, kayıt defterinde ayarlanan PowerShell yürütme İlkesi değiştirmez. Geçerli değerler listesi dahil olmak üzere PowerShell yürütme ilkeleri hakkında daha fazla bilgi için bkz. [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

### <a name="-file-filepath-parameters"></a>-Dosya <FilePath> \[ <Parameters>]

Geçerli oturumda betik değişkenleri ve işlevleri kullanılabilir olacak şekilde belirtilen betik ("dot kaynaklı"), yerel kapsamda çalıştırır. Betik dosyası yolu ve herhangi bir parametre girin. **Dosya** komutta son parametre olmalıdır. Sonra yazılan tüm değerleri **-dosya** parametresi betik olarak yorumlanır dosyası yolu ve parametreleri bu betiğe geçirilen.

Betiğe geçirilen parametreler geçerli kabuk tarafından yorumu sonra değişmez değer dizeleri geçirilir. Örneğin, cmd.exe içinde olan ve bir ortam değişken değerini geçirmek istiyorsanız cmd.exe söz dizimini kullanın: `powershell.exe -File .\test.ps1 -TestParam %windir%`

Buna karşılık, çalışan `powershell.exe -File .\test.ps1 -TestParam $env:windir` sabit dizesini alma betiği cmd.exe sonucu `$env:windir` çünkü geçerli cmd.exe Kabuğu özel bir anlamı yoktur.
`$env:windir` Ortam değişkeni başvurusu stilini _olabilir_ içinde kullanılabilir bir `-Command` var. PowerShell kodu olarak yorumlanacaktır olduğundan parametre.

### <a name="-inputformat-text--xml"></a>\-InputFormat {metin | XML}

PowerShell için gönderilen veri biçimini tanımlar. Geçerli değerler "Metin" (metin dizelerini) veya "XML" (CLIXML biçimi) olmalı.

### <a name="-mta"></a>-Mta

PowerShell kullanarak bir çok iş parçacıklı grup başlatır. Bu parametre PowerShell 3. 0 ' kullanıma sunulmuştur. PowerShell 3. 0'da, tek iş parçacıklı grup (STA) varsayılandır. PowerShell 2. 0'da, çok iş parçacıklı grup (MTA) varsayılandır.

### <a name="-noexit"></a>-NoExit

Başlangıç komutları çalıştırdıktan sonra çıkmak değil.

### <a name="-nologo"></a>-NoLogo

Telif hakkı başlığını başlangıçta gizler.

### <a name="-noninteractive"></a>-Etkileşimsiz

Etkileşimli bir istemi kullanıcı için mevcut değil.

### <a name="-noprofile"></a>-NoProfile

PowerShell profili yüklenmiyor.

### <a name="-outputformat-text--xml"></a>-OutputFormat {metin | XML}

PowerShell çıkışı nasıl biçimlendirildiğini belirler. Geçerli değerler "Metin" (metin dizelerini) veya "XML" (CLIXML biçimi) olmalı.

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>

Belirtilen bir PowerShell Konsolu dosya yükler. Konsol dosyasının adını ve yolunu girin. Bir konsol dosyası oluşturmak için kullanın [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) PowerShell cmdlet'i.

### <a name="-sta"></a>-Sta

PowerShell kullanarak tek kullanımlık apartman başlatır. PowerShell 3. 0'da, tek iş parçacıklı grup (STA) varsayılandır. PowerShell 2. 0'da, çok iş parçacıklı grup (MTA) varsayılandır.

### <a name="-version-powershell-version"></a>-Version <PowerShell Version>

Belirtilen PowerShell sürümünü başlatır. Sistemde, belirttiğiniz sürümü yüklenmelidir. PowerShell 3.0, bilgisayarda yüklü değilse, geçerli değerler şunlardır: "2.0" ve "3.0". "3.0" varsayılan değerdir.

PowerShell 3.0 yüklü değilse, yalnızca geçerli "2.0" değeridir. Diğer değerleri yok sayılır.

Daha fazla bilgi için [Windows PowerShell'i yükleme](../../setup/installing-windows-powershell.md).

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>

Oturum için pencere stilini ayarlar. Geçerli değerler şunlardır: Normal, küçültülmüş, ekranı kaplamış ve gizli.

### <a name="-command"></a>-Komutu

PowerShell komut isteminde türü belirtilmiş gibi sorgulamanıza (herhangi bir parametre ile) belirtilen komutları yürütür.
Yürütmeden sonra PowerShell sürece çıkar **NoExit** parametre belirtildi.
Sonra herhangi bir metin `-Command` PowerShell tek bir komut satırı gönderilir.
Bu nasıl farklı `-File` parametreleri için bir komut dosyası gönderilen işler.

Değerini `-Command` olabilir "-", bir dize veya bir betik bloğu.
Komutun sonuçlarını üst kabuğa değil Canlı nesneleri seri durumdan çıkarılmış XML nesneler olarak döndürülür.

Varsa değerini `-Command` olan "-", Standart girdiden okunan komut metni.

Zaman değerini `-Command` bir dizedir, **komut** _gerekir_ komutu yorumlanır sonra komut bağımsız herhangi bir karakter türü belirtilmiş olduğundan belirtilen son parametre olmalıdır.

**Komut** parametresi için geçirilen değer tanıyabilmesi zaman yürütme için bir betik bloğu yalnızca kabul `-Command` ScriptBlock türü.
Bu _yalnızca_ PowerShell.exe başka bir PowerShell konaktan çalıştırırken mümkün.
Türü yer almalıdır bir değişken, bir ifadeden döndürülen veya PowerShell ayrıştırılmış varolan ScriptBlock konak küme ayraçları içine alınmış bir değişmez değer betik bloğu olarak `{}`PowerShell.exe iletilmeden önce.

Cmd.exe içinde yoktur de bir betik bloğu (veya Scriptblock'u türü), bu nedenle için geçirilen değer **komut** olacak _her zaman_ bir dize olması gerekiyor.
Bir betik bloğu içinde dize yazabilirsiniz, ancak yürütülen yerine, tam olarak davranacak tipik bir PowerShell isteminde yazılı olarak da, komut dosyasının içeriğini yazdırma bloke geri için.

Geçirilen bir dize `-Command` betik blok küme ayraçları ilk başta cmd.exe çalışırken gerekli genellikle olmadıklarından yine de PowerShell yürütülür.
Bir dize içinde tanımlanan bir satır içi betik bloğu yürütülecek [çağrısı işleci](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` kullanılabilir:

```console
"& {<command>}"
```

### <a name="-help---"></a>-Help-?, /?

Powershell.exe söz dizimi görülmektedir. PowerShell.exe komut PowerShell'de yazıyorsanız, kısa çizgi (-) değil ters eğik çizgi (/) komutunu parametrelerle önüne ekleyin. Bir tire veya eğik Cmd.exe içinde kullanabilirsiniz.

> [!NOTE]
> Sorun giderme notu: PowerShell 2. 0'da, bazı Windows PowerShell konsol programlarda 0xc0000142'bir LastExitCode ile başlatılıyor.

## <a name="examples"></a>ÖRNEKLERİ

```powershell
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a PowerShell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate way to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```
