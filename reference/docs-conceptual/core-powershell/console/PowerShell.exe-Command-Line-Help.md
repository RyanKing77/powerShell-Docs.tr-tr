---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "PowerShell.exe komut satırı Yardımı"
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 262c21e44e509746314ed44d91bb3de16a4b854b
ms.sourcegitcommit: 4807ab554d55fdee499980835bcc279368b1df68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2017
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="48880-103">PowerShell.exe komut satırı Yardımı</span><span class="sxs-lookup"><span data-stu-id="48880-103">PowerShell.exe Command-Line Help</span></span>
<span data-ttu-id="48880-104">bir Windows PowerShell oturumu.</span><span class="sxs-lookup"><span data-stu-id="48880-104">a Windows PowerShell session.</span></span> <span data-ttu-id="48880-105">Cmd.exe gibi başka bir aracı komut satırından bir PowerShell oturumu başlatmak için PowerShell.exe kullanın veya yeni bir oturum başlatmak için PowerShell komut satırında kullanın.</span><span class="sxs-lookup"><span data-stu-id="48880-105">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="48880-106">Parametreleri oturum özelleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="48880-106">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="48880-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48880-107">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="48880-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="48880-108">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="48880-109">-EncodedCommand<Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="48880-109">-EncodedCommand <Base64EncodedCommand></span></span>
<span data-ttu-id="48880-110">Bir komut base-64 olarak kodlanmış dize sürümü kabul eder.</span><span class="sxs-lookup"><span data-stu-id="48880-110">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="48880-111">Karmaşık tırnak işaretleri veya süslü ayraçlar kullanılmasını gerektiren PowerShell komutlarına göndermek için bu parametreyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="48880-111">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="48880-112">-ExecutionPolicy<ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="48880-112">-ExecutionPolicy <ExecutionPolicy></span></span>
<span data-ttu-id="48880-113">Geçerli oturum için varsayılan yürütme ilkesini ayarlar ve $env kaydeder: PSExecutionPolicyPreference ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="48880-113">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="48880-114">Bu parametre kayıt defterinde ayarlama PowerShell yürütme İlkesi değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="48880-114">This parameter does not change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="48880-115">Geçerli bir değer listesi dahil olmak üzere, PowerShell yürütme ilkeleri hakkında bilgi için about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170) bakın.</span><span class="sxs-lookup"><span data-stu-id="48880-115">For information about PowerShell execution policies, including a list of valid values, see about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="48880-116">-Dosya <FilePath> \[ <Parameters>]</span><span class="sxs-lookup"><span data-stu-id="48880-116">-File <FilePath> \[<Parameters>]</span></span>
<span data-ttu-id="48880-117">İşlevleri ve komut dosyası oluşturur değişkenler geçerli oturumda kullanılabilir olacak şekilde, belirtilen komut dosyası ("nokta-kaynaklanan"), yerel kapsamdaki çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="48880-117">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="48880-118">Betik dosyası yolu ve parametreleri girin.</span><span class="sxs-lookup"><span data-stu-id="48880-118">Enter the script file path and any parameters.</span></span> <span data-ttu-id="48880-119">**Dosya** sonra yazılan tüm karakterleri komutta, son parametre olmalıdır **dosya** parametre adı, ardından betik parametrelerini ve değerlerini komut dosyası yolunu olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="48880-119">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="48880-120">Bir komut dosyası ve parametre değerlerini parametrelerinin değerinde içerebilir **dosya** parametresi.</span><span class="sxs-lookup"><span data-stu-id="48880-120">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="48880-121">Örneğin: `-File .\Get-Script.ps1 -Domain Central` komut dosyasına iletilen parametreler sabit değer olarak geçirilir Not dizeleri (sonra yorumu geçerli kabuk tarafından).</span><span class="sxs-lookup"><span data-stu-id="48880-121">For example: `-File .\Get-Script.ps1 -Domain Central` Note that parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span>
<span data-ttu-id="48880-122">Örneğin, cmd.exe içinde olan ve bir ortam değişkeni değeri geçirmek istiyorsanız cmd.exe sözdizimini kullanırsınız: `powershell -File .\test.ps1 -Sample %windir%` PowerShell söz dizimi kullanmak için bundan sonra bu örnekte, komut dosyası değişmez değeri alacağı "$env: windir" ve değil, değeri ortam değişkeni:`powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="48880-122">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` If you were to use PowerShell syntax, then in this example your script would receive the literal "$env:windir" and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

<span data-ttu-id="48880-123">Genellikle, bir komut dosyası anahtar parametrelerinin dahil atlanmış ya.</span><span class="sxs-lookup"><span data-stu-id="48880-123">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="48880-124">Örneğin, aşağıdaki kullanan komut **tüm** Get-Script.ps1 komut dosyasının parametre:`-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="48880-124">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="48880-125">\-InputFormat {metin | XML}</span><span class="sxs-lookup"><span data-stu-id="48880-125">\-InputFormat {Text | XML}</span></span>
<span data-ttu-id="48880-126">PowerShell için gönderilen veri biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="48880-126">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="48880-127">Geçerli değerler "Metin" (metin dizelerini) veya "XML" (serileştirilmiş CLIXML biçimi) değerleridir.</span><span class="sxs-lookup"><span data-stu-id="48880-127">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="48880-128">-Mta</span><span class="sxs-lookup"><span data-stu-id="48880-128">-Mta</span></span>
<span data-ttu-id="48880-129">Çoklu iş parçacıklı kullanarak PowerShell başlatır.</span><span class="sxs-lookup"><span data-stu-id="48880-129">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="48880-130">Bu parametre, PowerShell 3.0 sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="48880-130">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="48880-131">PowerShell 3. 0'da, tek iş parçacıklı (STA) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="48880-131">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="48880-132">PowerShell 2. 0'da, birden çok iş parçacıklı (MTA) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="48880-132">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="48880-133">-NoExit</span><span class="sxs-lookup"><span data-stu-id="48880-133">-NoExit</span></span>
<span data-ttu-id="48880-134">Başlangıç komutları çalıştırdıktan sonra mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="48880-134">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="48880-135">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="48880-135">-NoLogo</span></span>
<span data-ttu-id="48880-136">Telif hakkı başlığını başlangıçta gizler.</span><span class="sxs-lookup"><span data-stu-id="48880-136">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="48880-137">-Etkileşimsiz</span><span class="sxs-lookup"><span data-stu-id="48880-137">-NonInteractive</span></span>
<span data-ttu-id="48880-138">Etkileşimli bir istem kullanıcıyı sunmaz.</span><span class="sxs-lookup"><span data-stu-id="48880-138">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="48880-139">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="48880-139">-NoProfile</span></span>
<span data-ttu-id="48880-140">PowerShell profili yüklemez.</span><span class="sxs-lookup"><span data-stu-id="48880-140">Does not load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="48880-141">-OutputFormat {metin | XML}</span><span class="sxs-lookup"><span data-stu-id="48880-141">-OutputFormat {Text | XML}</span></span>
<span data-ttu-id="48880-142">PowerShell çıkışı nasıl biçimlendirilmiş belirler.</span><span class="sxs-lookup"><span data-stu-id="48880-142">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="48880-143">Geçerli değerler "Metin" (metin dizelerini) veya "XML" (serileştirilmiş CLIXML biçimi) değerleridir.</span><span class="sxs-lookup"><span data-stu-id="48880-143">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="48880-144">-PSConsoleFile<FilePath></span><span class="sxs-lookup"><span data-stu-id="48880-144">-PSConsoleFile <FilePath></span></span>
<span data-ttu-id="48880-145">Belirtilen PowerShell konsol dosyasını yükler.</span><span class="sxs-lookup"><span data-stu-id="48880-145">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="48880-146">Konsol dosyasının adını ve yolunu girin.</span><span class="sxs-lookup"><span data-stu-id="48880-146">Enter the path and name of the console file.</span></span> <span data-ttu-id="48880-147">Bir konsol dosyası oluşturmak için kullanmak [verme konsol](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) PowerShell cmdlet'ini.</span><span class="sxs-lookup"><span data-stu-id="48880-147">To create a console file, use the [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="48880-148">-Sta</span><span class="sxs-lookup"><span data-stu-id="48880-148">-Sta</span></span>
<span data-ttu-id="48880-149">PowerShell kullanarak bir tek iş parçacıklı başlatır.</span><span class="sxs-lookup"><span data-stu-id="48880-149">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="48880-150">PowerShell 3. 0'da, tek iş parçacıklı (STA) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="48880-150">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="48880-151">PowerShell 2. 0'da, birden çok iş parçacıklı (MTA) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="48880-151">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="48880-152">-Sürüm<PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="48880-152">-Version <PowerShell Version></span></span>
<span data-ttu-id="48880-153">PowerShell belirtilen sürümünü başlatır.</span><span class="sxs-lookup"><span data-stu-id="48880-153">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="48880-154">Belirttiğiniz sürümden sistemde yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="48880-154">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="48880-155">PowerShell 3.0 bilgisayarda yüklüyse, geçerli değerleri "2.0" ve "3.0" şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="48880-155">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="48880-156">Varsayılan değer "3.0" dir.</span><span class="sxs-lookup"><span data-stu-id="48880-156">The default value is "3.0".</span></span>

<span data-ttu-id="48880-157">PowerShell 3.0 yüklü değilse, tek geçerli değer "2.0" dır.</span><span class="sxs-lookup"><span data-stu-id="48880-157">If PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="48880-158">Diğer değerler göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="48880-158">Other values are ignored.</span></span>

<span data-ttu-id="48880-159">Daha fazla bilgi için "PowerShell'i yükleme" konusuna bakın. [PowerShell [eski MSDN] ile çalışmaya başlama](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span><span class="sxs-lookup"><span data-stu-id="48880-159">For more information, see "Installing PowerShell" in the [Getting Started with PowerShell [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="48880-160">-WindowStyle<Window style></span><span class="sxs-lookup"><span data-stu-id="48880-160">-WindowStyle <Window style></span></span>
<span data-ttu-id="48880-161">Pencere stili oturum için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="48880-161">Sets the window style for the session.</span></span> <span data-ttu-id="48880-162">Geçerli değerler, Normal, simge durumuna küçültülmüş, ekranı kaplamış ve gizli arasındadır.</span><span class="sxs-lookup"><span data-stu-id="48880-162">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="48880-163">-Komutu</span><span class="sxs-lookup"><span data-stu-id="48880-163">-Command</span></span>
<span data-ttu-id="48880-164">PowerShell komut isteminde yazılan ve çıkar, gibi sorgulamanıza NoExit parametresi belirtilmediğinde belirtilen komutların (ve parametreleri) yürütür.</span><span class="sxs-lookup"><span data-stu-id="48880-164">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>
<span data-ttu-id="48880-165">Esas olarak, herhangi bir metin sonra `-Command` tek bir komut satırı için PowerShell gönderilen (Bunu nasıl farklı `-File` parametreleri bir komut dosyasına gönderilen işler).</span><span class="sxs-lookup"><span data-stu-id="48880-165">Essentially, any text after `-Command` is sent as a single command line to PowerShell (this is different from how `-File` handles parameters sent to a script).</span></span>

<span data-ttu-id="48880-166">Komut değeri olabilir "-", bir dize.</span><span class="sxs-lookup"><span data-stu-id="48880-166">The value of Command can be "-", a string.</span></span> <span data-ttu-id="48880-167">veya bir betik bloğu.</span><span class="sxs-lookup"><span data-stu-id="48880-167">or a script block.</span></span> <span data-ttu-id="48880-168">Komut değerini ise "-", standart girişten komut metni okuyun.</span><span class="sxs-lookup"><span data-stu-id="48880-168">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="48880-169">Komut dosyası blokları ({}) ayraç içine alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="48880-169">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="48880-170">Yalnızca PowerShell.exe PowerShell'de çalışırken bir betik bloğu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48880-170">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="48880-171">Komut dosyası sonuçlarını üst Kabuk değil Canlı nesneleri seri durumdan çıkarılmış XML nesneler döndürülür.</span><span class="sxs-lookup"><span data-stu-id="48880-171">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="48880-172">Komut değeri bir dize ise **komutu** komutu yorumlanacağını sonra komut bağımsız herhangi bir karakter yazdığınızdan komutta, son parametre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="48880-172">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="48880-173">Bir PowerShell komut çalıştıran bir dize yazmak için biçimi kullanın:</span><span class="sxs-lookup"><span data-stu-id="48880-173">To write a string that runs a PowerShell command, use the format:</span></span>

```
"& {<command>}"
```

<span data-ttu-id="48880-174">Burada tırnak işaretleri dize ve Invoke işleci belirtin (&) yürütülecek komut neden olur.</span><span class="sxs-lookup"><span data-stu-id="48880-174">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="48880-175">-Help,-?, /?</span><span class="sxs-lookup"><span data-stu-id="48880-175">-Help, -?, /?</span></span>
<span data-ttu-id="48880-176">Bu ileti gösterir.</span><span class="sxs-lookup"><span data-stu-id="48880-176">Shows this message.</span></span> <span data-ttu-id="48880-177">PowerShell'de PowerShell.exe komutu yazıyorsanız, bir tire (-) değil ters eğik çizgi (/) ile komut parametreleri önüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="48880-177">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="48880-178">Bir tire veya eğik Cmd.exe içinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48880-178">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="48880-179">Sorun giderme notu: PowerShell 2. 0'da, bazı programlar konsol başarısız Windows PowerShell'de bir 0xc0000142 LastExitCode ile başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="48880-179">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="48880-180">ÖRNEKLER</span><span class="sxs-lookup"><span data-stu-id="48880-180">EXAMPLES</span></span>

```
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a Powerhell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate wayh to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```

