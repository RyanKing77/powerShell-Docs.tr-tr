---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: PowerShell.exe Komut Satırı Yardımı
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 60b6a7e310821a4092b0972b7abbdae0e2d5f738
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="powershellexe-command-line-help"></a>PowerShell.exe Command-Line Help

Cmd.exe gibi başka bir aracı komut satırından bir PowerShell oturumu başlatmak için PowerShell.exe kullanın veya yeni bir oturum başlatmak için PowerShell komut satırında kullanın. Parametreleri oturum özelleştirmek için kullanın.

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

Bir komut base-64 olarak kodlanmış dize sürümü kabul eder. Karmaşık tırnak işaretleri veya süslü ayraçlar kullanılmasını gerektiren PowerShell komutlarına göndermek için bu parametreyi kullanın.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>

Geçerli oturum için varsayılan yürütme ilkesini ayarlar ve $env kaydeder: PSExecutionPolicyPreference ortam değişkeni. Bu parametre kayıt defterinde ayarlama PowerShell yürütme İlkesi değiştirmez. Geçerli bir değer listesi dahil olmak üzere, PowerShell yürütme ilkeleri hakkında bilgi için bkz: [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

### <a name="-file-filepath-parameters"></a>-Dosya <FilePath> \[ <Parameters>]

İşlevleri ve komut dosyası oluşturur değişkenler geçerli oturumda kullanılabilir olacak şekilde, belirtilen komut dosyası ("nokta-kaynaklanan"), yerel kapsamdaki çalıştırır. Betik dosyası yolu ve parametreleri girin. **Dosya** sonra yazılan tüm karakterleri komutta, son parametre olmalıdır **dosya** parametre adı, ardından betik parametrelerini ve değerlerini komut dosyası yolunu olarak yorumlanır.

Bir komut dosyası ve parametre değerlerini parametrelerinin değerinde içerebilir **dosya** parametresi. Örneğin: `-File .\Get-Script.ps1 -Domain Central` komut dosyasına iletilen parametreler sabit değer olarak geçirilir Not dizeleri (sonra yorumu geçerli kabuk tarafından).
Örneğin, cmd.exe içinde olan ve bir ortam değişkeni değeri geçirmek istiyorsanız cmd.exe sözdizimini kullanırsınız: `powershell -File .\test.ps1 -Sample %windir%` PowerShell söz dizimi kullanmak için bundan sonra bu örnekte, komut dosyası değişmez değeri alacağı "$env: windir" ve değil, değeri ortam değişkeni: `powershell -File .\test.ps1 -Sample $env:windir`

Genellikle, bir komut dosyası anahtar parametrelerinin dahil atlanmış ya. Örneğin, aşağıdaki kullanan komut **tüm** Get-Script.ps1 komut dosyasının parametre: `-File .\Get-Script.ps1 -All`

### <a name="-inputformat-text--xml"></a>\-InputFormat {metin | XML}

PowerShell için gönderilen veri biçimini tanımlar. Geçerli değerler "Metin" (metin dizelerini) veya "XML" (serileştirilmiş CLIXML biçimi) değerleridir.

### <a name="-mta"></a>-Mta

Çoklu iş parçacıklı kullanarak PowerShell başlatır. Bu parametre, PowerShell 3.0 sunulmuştur. PowerShell 3. 0'da, tek iş parçacıklı (STA) varsayılandır. PowerShell 2. 0'da, birden çok iş parçacıklı (MTA) varsayılandır.

### <a name="-noexit"></a>-NoExit

Başlangıç komutları çalıştırdıktan sonra mevcut değil.

### <a name="-nologo"></a>-NoLogo

Telif hakkı başlığını başlangıçta gizler.

### <a name="-noninteractive"></a>-Etkileşimsiz

Etkileşimli bir istem kullanıcıyı sunmaz.

### <a name="-noprofile"></a>-NoProfile

PowerShell profili yüklemez.

### <a name="-outputformat-text--xml"></a>-OutputFormat {metin | XML}

PowerShell çıkışı nasıl biçimlendirilmiş belirler. Geçerli değerler "Metin" (metin dizelerini) veya "XML" (serileştirilmiş CLIXML biçimi) değerleridir.

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>

Belirtilen PowerShell konsol dosyasını yükler. Konsol dosyasının adını ve yolunu girin. Bir konsol dosyası oluşturmak için kullanmak [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) PowerShell cmdlet'ini.

### <a name="-sta"></a>-Sta

PowerShell kullanarak bir tek iş parçacıklı başlatır. PowerShell 3. 0'da, tek iş parçacıklı (STA) varsayılandır. PowerShell 2. 0'da, birden çok iş parçacıklı (MTA) varsayılandır.

### <a name="-version-powershell-version"></a>-Sürüm <PowerShell Version>

PowerShell belirtilen sürümünü başlatır. Belirttiğiniz sürümden sistemde yüklü olmalıdır. PowerShell 3.0 bilgisayarda yüklüyse, geçerli değerleri "2.0" ve "3.0" şeklindedir. Varsayılan değer "3.0" dir.

PowerShell 3.0 yüklü değilse, tek geçerli değer "2.0" dır. Diğer değerler göz ardı edilir.

Daha fazla bilgi için "[Windows PowerShell'i yükleme](../../setup/installing-windows-powershell.md)".

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>

Pencere stili oturum için ayarlar. Geçerli değerler, Normal, simge durumuna küçültülmüş, ekranı kaplamış ve gizli arasındadır.

### <a name="-command"></a>-Komutu

PowerShell komut isteminde yazılan ve çıkar, gibi sorgulamanıza NoExit parametresi belirtilmediğinde belirtilen komutların (ve parametreleri) yürütür.
Esas olarak, herhangi bir metin sonra `-Command` tek bir komut satırı için PowerShell gönderilen (Bunu nasıl farklı `-File` parametreleri bir komut dosyasına gönderilen işler).

Komut değeri olabilir "-", bir dize. veya bir betik bloğu. Komut değerini ise "-", standart girişten komut metni okuyun.

Komut dosyası blokları ({}) ayraç içine alınması gerekir. Yalnızca PowerShell.exe PowerShell'de çalışırken bir betik bloğu belirtebilirsiniz. Komut dosyası sonuçlarını üst Kabuk değil Canlı nesneleri seri durumdan çıkarılmış XML nesneler döndürülür.

Komut değeri bir dize ise **komutu** komutu yorumlanacağını sonra komut bağımsız herhangi bir karakter yazdığınızdan komutta, son parametre olmalıdır.

Bir PowerShell komut çalıştıran bir dize yazmak için biçimi kullanın:

```powershell
"& {<command>}"
```

Burada tırnak işaretleri dize ve Invoke işleci belirtin (&) yürütülecek komut neden olur.

### <a name="-help---"></a>-Help, -?, /?

Bu ileti gösterir. PowerShell'de PowerShell.exe komutu yazıyorsanız, bir tire (-) değil ters eğik çizgi (/) ile komut parametreleri önüne ekleyin. Bir tire veya eğik Cmd.exe içinde kullanabilirsiniz.

> [!NOTE]
> Sorun giderme notu: PowerShell 2. 0'da, bazı programlar konsol başarısız Windows PowerShell'de bir 0xc0000142 LastExitCode ile başlatılıyor.

## <a name="examples"></a>ÖRNEKLER

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