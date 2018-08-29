---
ms.date: 08/14/2018
keywords: PowerShell cmdlet'i
title: PowerShell.exe Komut Satırı Yardımı
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: c7f35511e876e8e5189d8a2b949555603d43f731
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133824"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="85f28-103">PowerShell.exe komut satırı Yardımı</span><span class="sxs-lookup"><span data-stu-id="85f28-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="85f28-104">Cmd.exe gibi başka bir aracının komut satırı bir PowerShell oturumu başlatmak için PowerShell.exe kullanın veya yeni bir oturum başlatmak için PowerShell komut satırında kullanın.</span><span class="sxs-lookup"><span data-stu-id="85f28-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="85f28-105">Oturum özelleştirmek için parametreleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="85f28-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="85f28-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85f28-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="85f28-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="85f28-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="85f28-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="85f28-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="85f28-109">Bir komut base-64 kodlu dize sürümünü kabul eder.</span><span class="sxs-lookup"><span data-stu-id="85f28-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="85f28-110">Karmaşık tırnak işaretleri veya küme ayraçları gerektiren PowerShell komutları göndermek için bu parametreyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="85f28-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="85f28-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="85f28-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="85f28-112">Geçerli oturum için varsayılan yürütme ilkesini ayarlar ve içinde $env kaydeder: PSExecutionPolicyPreference ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="85f28-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="85f28-113">Bu parametre, kayıt defterinde ayarlanan PowerShell yürütme İlkesi değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="85f28-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="85f28-114">Geçerli değerler listesi dahil olmak üzere PowerShell yürütme ilkeleri hakkında daha fazla bilgi için bkz. [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="85f28-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="85f28-115">-Dosya <FilePath> \[ <Parameters>]</span><span class="sxs-lookup"><span data-stu-id="85f28-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="85f28-116">Geçerli oturumda betik değişkenleri ve işlevleri kullanılabilir olacak şekilde belirtilen betik ("dot kaynaklı"), yerel kapsamda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="85f28-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="85f28-117">Betik dosyası yolu ve herhangi bir parametre girin.</span><span class="sxs-lookup"><span data-stu-id="85f28-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="85f28-118">**Dosya** komutta son parametre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="85f28-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="85f28-119">Sonra yazılan tüm değerleri **-dosya** parametresi betik olarak yorumlanır dosyası yolu ve parametreleri bu betiğe geçirilen.</span><span class="sxs-lookup"><span data-stu-id="85f28-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="85f28-120">Komut dosyasına iletilen parametreler (yorumu geçerli kabuk tarafından sonra) değişmez değer dizeleri geçirilir.</span><span class="sxs-lookup"><span data-stu-id="85f28-120">Parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span> <span data-ttu-id="85f28-121">Örneğin, cmd.exe içinde olan ve bir ortam değişken değerini geçirmek istiyorsanız cmd.exe sözdizimini kullanırsınız: `powershell -File .\test.ps1 -Sample %windir%` Bu örnekte, komut dosyası sabit dizesini alır. `$env:windir` ve bu ortam değişkeninin değerini değil: `powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="85f28-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` In this example, the script receives the literal string `$env:windir` and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="85f28-122">\-InputFormat {metin | XML}</span><span class="sxs-lookup"><span data-stu-id="85f28-122">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="85f28-123">PowerShell için gönderilen veri biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="85f28-123">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="85f28-124">Geçerli değerler "Metin" (metin dizelerini) veya "XML" (CLIXML biçimi) olmalı.</span><span class="sxs-lookup"><span data-stu-id="85f28-124">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="85f28-125">-Mta</span><span class="sxs-lookup"><span data-stu-id="85f28-125">-Mta</span></span>

<span data-ttu-id="85f28-126">PowerShell kullanarak bir çok iş parçacıklı grup başlatır.</span><span class="sxs-lookup"><span data-stu-id="85f28-126">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="85f28-127">Bu parametre PowerShell 3. 0 ' kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="85f28-127">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="85f28-128">PowerShell 3. 0'da, tek iş parçacıklı grup (STA) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="85f28-128">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="85f28-129">PowerShell 2. 0'da, çok iş parçacıklı grup (MTA) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="85f28-129">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="85f28-130">-NoExit</span><span class="sxs-lookup"><span data-stu-id="85f28-130">-NoExit</span></span>

<span data-ttu-id="85f28-131">Başlangıç komutları çalıştırdıktan sonra çıkmak değil.</span><span class="sxs-lookup"><span data-stu-id="85f28-131">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="85f28-132">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="85f28-132">-NoLogo</span></span>

<span data-ttu-id="85f28-133">Telif hakkı başlığını başlangıçta gizler.</span><span class="sxs-lookup"><span data-stu-id="85f28-133">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="85f28-134">-Etkileşimsiz</span><span class="sxs-lookup"><span data-stu-id="85f28-134">-NonInteractive</span></span>

<span data-ttu-id="85f28-135">Etkileşimli bir istemi kullanıcı için mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="85f28-135">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="85f28-136">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="85f28-136">-NoProfile</span></span>

<span data-ttu-id="85f28-137">PowerShell profili yüklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="85f28-137">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="85f28-138">-OutputFormat {metin | XML}</span><span class="sxs-lookup"><span data-stu-id="85f28-138">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="85f28-139">PowerShell çıkışı nasıl biçimlendirildiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="85f28-139">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="85f28-140">Geçerli değerler "Metin" (metin dizelerini) veya "XML" (CLIXML biçimi) olmalı.</span><span class="sxs-lookup"><span data-stu-id="85f28-140">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="85f28-141">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="85f28-141">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="85f28-142">Belirtilen bir PowerShell Konsolu dosya yükler.</span><span class="sxs-lookup"><span data-stu-id="85f28-142">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="85f28-143">Konsol dosyasının adını ve yolunu girin.</span><span class="sxs-lookup"><span data-stu-id="85f28-143">Enter the path and name of the console file.</span></span> <span data-ttu-id="85f28-144">Bir konsol dosyası oluşturmak için kullanın [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) PowerShell cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="85f28-144">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="85f28-145">-Sta</span><span class="sxs-lookup"><span data-stu-id="85f28-145">-Sta</span></span>

<span data-ttu-id="85f28-146">PowerShell kullanarak tek kullanımlık apartman başlatır.</span><span class="sxs-lookup"><span data-stu-id="85f28-146">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="85f28-147">PowerShell 3. 0'da, tek iş parçacıklı grup (STA) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="85f28-147">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="85f28-148">PowerShell 2. 0'da, çok iş parçacıklı grup (MTA) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="85f28-148">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="85f28-149">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="85f28-149">-Version <PowerShell Version></span></span>

<span data-ttu-id="85f28-150">Belirtilen PowerShell sürümünü başlatır.</span><span class="sxs-lookup"><span data-stu-id="85f28-150">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="85f28-151">Sistemde, belirttiğiniz sürümü yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="85f28-151">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="85f28-152">PowerShell 3.0, bilgisayarda yüklü değilse, geçerli değerler şunlardır: "2.0" ve "3.0".</span><span class="sxs-lookup"><span data-stu-id="85f28-152">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="85f28-153">"3.0" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="85f28-153">The default value is "3.0".</span></span>

<span data-ttu-id="85f28-154">PowerShell 3.0 yüklü değilse, yalnızca geçerli "2.0" değeridir.</span><span class="sxs-lookup"><span data-stu-id="85f28-154">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="85f28-155">Diğer değerleri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="85f28-155">Other values are ignored.</span></span>

<span data-ttu-id="85f28-156">Daha fazla bilgi için [Windows PowerShell'i yükleme](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="85f28-156">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="85f28-157">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="85f28-157">-WindowStyle <Window style></span></span>

<span data-ttu-id="85f28-158">Oturum için pencere stilini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="85f28-158">Sets the window style for the session.</span></span> <span data-ttu-id="85f28-159">Geçerli değerler şunlardır: Normal, küçültülmüş, ekranı kaplamış ve gizli.</span><span class="sxs-lookup"><span data-stu-id="85f28-159">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="85f28-160">-Komutu</span><span class="sxs-lookup"><span data-stu-id="85f28-160">-Command</span></span>

<span data-ttu-id="85f28-161">PowerShell komut isteminde türü belirtilmiş gibi sorgulamanıza (herhangi bir parametre ile) belirtilen komutları yürütür.</span><span class="sxs-lookup"><span data-stu-id="85f28-161">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span> <span data-ttu-id="85f28-162">Yürütmeden sonra PowerShell sürece çıkar `-NoExit` parametre belirtildi.</span><span class="sxs-lookup"><span data-stu-id="85f28-162">After execution, PowerShell exits unless the `-NoExit` parameter is specified.</span></span>
<span data-ttu-id="85f28-163">Sonra herhangi bir metin `-Command` PowerShell tek bir komut satırı gönderilir.</span><span class="sxs-lookup"><span data-stu-id="85f28-163">Any text after `-Command` is sent as a single command line to PowerShell.</span></span> <span data-ttu-id="85f28-164">Bu nasıl farklı `-File` parametreleri için bir komut dosyası gönderilen işler.</span><span class="sxs-lookup"><span data-stu-id="85f28-164">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="85f28-165">Komut değeri olabilir "-", bir dize.</span><span class="sxs-lookup"><span data-stu-id="85f28-165">The value of Command can be "-", a string.</span></span> <span data-ttu-id="85f28-166">veya bir betik bloğu.</span><span class="sxs-lookup"><span data-stu-id="85f28-166">or a script block.</span></span> <span data-ttu-id="85f28-167">Komut değerini ise "-", Standart girdiden okunan komut metni.</span><span class="sxs-lookup"><span data-stu-id="85f28-167">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="85f28-168">Komut dosyası blokları küme ayraçları içine alınmalıdır ({}).</span><span class="sxs-lookup"><span data-stu-id="85f28-168">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="85f28-169">PowerShell.exe PowerShell'de çalıştırırken bir betik bloğu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85f28-169">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="85f28-170">Betik sonuçlarını üst kabuğa değil Canlı nesneleri seri durumdan çıkarılmış XML nesneler olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="85f28-170">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="85f28-171">Komut değeri bir dize ise **komut** komutu yorumlanır sonra komut bağımsız herhangi bir karakter yazdığınızdan komutta, son parametre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="85f28-171">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="85f28-172">Bir PowerShell komutu çalışan bir dize yazmak için biçimi kullanın:</span><span class="sxs-lookup"><span data-stu-id="85f28-172">To write a string that runs a PowerShell command, use the format:</span></span>

```powershell
"& {<command>}"
```

<span data-ttu-id="85f28-173">Tırnak işaretleri dize ve Invoke işleci (&) yürütülecek komut neden olur.</span><span class="sxs-lookup"><span data-stu-id="85f28-173">The quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="85f28-174">-Help-?, /?</span><span class="sxs-lookup"><span data-stu-id="85f28-174">-Help, -?, /?</span></span>

<span data-ttu-id="85f28-175">Powershell.exe söz dizimi görülmektedir.</span><span class="sxs-lookup"><span data-stu-id="85f28-175">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="85f28-176">PowerShell.exe komut PowerShell'de yazıyorsanız, kısa çizgi (-) değil ters eğik çizgi (/) komutunu parametrelerle önüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="85f28-176">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="85f28-177">Bir tire veya eğik Cmd.exe içinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85f28-177">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="85f28-178">Sorun giderme notu: PowerShell 2. 0'da, bazı Windows PowerShell konsol programlarda 0xc0000142'bir LastExitCode ile başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="85f28-178">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="85f28-179">ÖRNEKLERİ</span><span class="sxs-lookup"><span data-stu-id="85f28-179">EXAMPLES</span></span>

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
