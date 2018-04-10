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
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="bfe4f-103">PowerShell.exe Command-Line Help</span><span class="sxs-lookup"><span data-stu-id="bfe4f-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="bfe4f-104">Cmd.exe gibi başka bir aracı komut satırından bir PowerShell oturumu başlatmak için PowerShell.exe kullanın veya yeni bir oturum başlatmak için PowerShell komut satırında kullanın.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="bfe4f-105">Parametreleri oturum özelleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="bfe4f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bfe4f-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="bfe4f-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bfe4f-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="bfe4f-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="bfe4f-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="bfe4f-109">Bir komut base-64 olarak kodlanmış dize sürümü kabul eder.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="bfe4f-110">Karmaşık tırnak işaretleri veya süslü ayraçlar kullanılmasını gerektiren PowerShell komutlarına göndermek için bu parametreyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="bfe4f-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="bfe4f-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="bfe4f-112">Geçerli oturum için varsayılan yürütme ilkesini ayarlar ve $env kaydeder: PSExecutionPolicyPreference ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="bfe4f-113">Bu parametre kayıt defterinde ayarlama PowerShell yürütme İlkesi değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-113">This parameter does not change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="bfe4f-114">Geçerli bir değer listesi dahil olmak üzere, PowerShell yürütme ilkeleri hakkında bilgi için bkz: [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="bfe4f-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="bfe4f-115">-Dosya <FilePath> \[ <Parameters>]</span><span class="sxs-lookup"><span data-stu-id="bfe4f-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="bfe4f-116">İşlevleri ve komut dosyası oluşturur değişkenler geçerli oturumda kullanılabilir olacak şekilde, belirtilen komut dosyası ("nokta-kaynaklanan"), yerel kapsamdaki çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="bfe4f-117">Betik dosyası yolu ve parametreleri girin.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="bfe4f-118">**Dosya** sonra yazılan tüm karakterleri komutta, son parametre olmalıdır **dosya** parametre adı, ardından betik parametrelerini ve değerlerini komut dosyası yolunu olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-118">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="bfe4f-119">Bir komut dosyası ve parametre değerlerini parametrelerinin değerinde içerebilir **dosya** parametresi.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-119">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="bfe4f-120">Örneğin: `-File .\Get-Script.ps1 -Domain Central` komut dosyasına iletilen parametreler sabit değer olarak geçirilir Not dizeleri (sonra yorumu geçerli kabuk tarafından).</span><span class="sxs-lookup"><span data-stu-id="bfe4f-120">For example: `-File .\Get-Script.ps1 -Domain Central` Note that parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span>
<span data-ttu-id="bfe4f-121">Örneğin, cmd.exe içinde olan ve bir ortam değişkeni değeri geçirmek istiyorsanız cmd.exe sözdizimini kullanırsınız: `powershell -File .\test.ps1 -Sample %windir%` PowerShell söz dizimi kullanmak için bundan sonra bu örnekte, komut dosyası değişmez değeri alacağı "$env: windir" ve değil, değeri ortam değişkeni: `powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="bfe4f-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` If you were to use PowerShell syntax, then in this example your script would receive the literal "$env:windir" and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

<span data-ttu-id="bfe4f-122">Genellikle, bir komut dosyası anahtar parametrelerinin dahil atlanmış ya.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-122">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="bfe4f-123">Örneğin, aşağıdaki kullanan komut **tüm** Get-Script.ps1 komut dosyasının parametre: `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="bfe4f-123">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="bfe4f-124">\-InputFormat {metin | XML}</span><span class="sxs-lookup"><span data-stu-id="bfe4f-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="bfe4f-125">PowerShell için gönderilen veri biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="bfe4f-126">Geçerli değerler "Metin" (metin dizelerini) veya "XML" (serileştirilmiş CLIXML biçimi) değerleridir.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="bfe4f-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="bfe4f-127">-Mta</span></span>

<span data-ttu-id="bfe4f-128">Çoklu iş parçacıklı kullanarak PowerShell başlatır.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="bfe4f-129">Bu parametre, PowerShell 3.0 sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="bfe4f-130">PowerShell 3. 0'da, tek iş parçacıklı (STA) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="bfe4f-131">PowerShell 2. 0'da, birden çok iş parçacıklı (MTA) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="bfe4f-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="bfe4f-132">-NoExit</span></span>

<span data-ttu-id="bfe4f-133">Başlangıç komutları çalıştırdıktan sonra mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-133">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="bfe4f-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="bfe4f-134">-NoLogo</span></span>

<span data-ttu-id="bfe4f-135">Telif hakkı başlığını başlangıçta gizler.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="bfe4f-136">-Etkileşimsiz</span><span class="sxs-lookup"><span data-stu-id="bfe4f-136">-NonInteractive</span></span>

<span data-ttu-id="bfe4f-137">Etkileşimli bir istem kullanıcıyı sunmaz.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-137">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="bfe4f-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="bfe4f-138">-NoProfile</span></span>

<span data-ttu-id="bfe4f-139">PowerShell profili yüklemez.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-139">Does not load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="bfe4f-140">-OutputFormat {metin | XML}</span><span class="sxs-lookup"><span data-stu-id="bfe4f-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="bfe4f-141">PowerShell çıkışı nasıl biçimlendirilmiş belirler.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="bfe4f-142">Geçerli değerler "Metin" (metin dizelerini) veya "XML" (serileştirilmiş CLIXML biçimi) değerleridir.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="bfe4f-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="bfe4f-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="bfe4f-144">Belirtilen PowerShell konsol dosyasını yükler.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="bfe4f-145">Konsol dosyasının adını ve yolunu girin.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="bfe4f-146">Bir konsol dosyası oluşturmak için kullanmak [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) PowerShell cmdlet'ini.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="bfe4f-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="bfe4f-147">-Sta</span></span>

<span data-ttu-id="bfe4f-148">PowerShell kullanarak bir tek iş parçacıklı başlatır.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="bfe4f-149">PowerShell 3. 0'da, tek iş parçacıklı (STA) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="bfe4f-150">PowerShell 2. 0'da, birden çok iş parçacıklı (MTA) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="bfe4f-151">-Sürüm <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="bfe4f-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="bfe4f-152">PowerShell belirtilen sürümünü başlatır.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="bfe4f-153">Belirttiğiniz sürümden sistemde yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="bfe4f-154">PowerShell 3.0 bilgisayarda yüklüyse, geçerli değerleri "2.0" ve "3.0" şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="bfe4f-155">Varsayılan değer "3.0" dir.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-155">The default value is "3.0".</span></span>

<span data-ttu-id="bfe4f-156">PowerShell 3.0 yüklü değilse, tek geçerli değer "2.0" dır.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-156">If PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="bfe4f-157">Diğer değerler göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-157">Other values are ignored.</span></span>

<span data-ttu-id="bfe4f-158">Daha fazla bilgi için "[Windows PowerShell'i yükleme](../../setup/installing-windows-powershell.md)".</span><span class="sxs-lookup"><span data-stu-id="bfe4f-158">For more information, see "[Installing Windows PowerShell](../../setup/installing-windows-powershell.md)".</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="bfe4f-159">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="bfe4f-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="bfe4f-160">Pencere stili oturum için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-160">Sets the window style for the session.</span></span> <span data-ttu-id="bfe4f-161">Geçerli değerler, Normal, simge durumuna küçültülmüş, ekranı kaplamış ve gizli arasındadır.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-161">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="bfe4f-162">-Komutu</span><span class="sxs-lookup"><span data-stu-id="bfe4f-162">-Command</span></span>

<span data-ttu-id="bfe4f-163">PowerShell komut isteminde yazılan ve çıkar, gibi sorgulamanıza NoExit parametresi belirtilmediğinde belirtilen komutların (ve parametreleri) yürütür.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-163">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>
<span data-ttu-id="bfe4f-164">Esas olarak, herhangi bir metin sonra `-Command` tek bir komut satırı için PowerShell gönderilen (Bunu nasıl farklı `-File` parametreleri bir komut dosyasına gönderilen işler).</span><span class="sxs-lookup"><span data-stu-id="bfe4f-164">Essentially, any text after `-Command` is sent as a single command line to PowerShell (this is different from how `-File` handles parameters sent to a script).</span></span>

<span data-ttu-id="bfe4f-165">Komut değeri olabilir "-", bir dize.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-165">The value of Command can be "-", a string.</span></span> <span data-ttu-id="bfe4f-166">veya bir betik bloğu.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-166">or a script block.</span></span> <span data-ttu-id="bfe4f-167">Komut değerini ise "-", standart girişten komut metni okuyun.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-167">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="bfe4f-168">Komut dosyası blokları ({}) ayraç içine alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-168">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="bfe4f-169">Yalnızca PowerShell.exe PowerShell'de çalışırken bir betik bloğu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-169">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="bfe4f-170">Komut dosyası sonuçlarını üst Kabuk değil Canlı nesneleri seri durumdan çıkarılmış XML nesneler döndürülür.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-170">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="bfe4f-171">Komut değeri bir dize ise **komutu** komutu yorumlanacağını sonra komut bağımsız herhangi bir karakter yazdığınızdan komutta, son parametre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-171">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="bfe4f-172">Bir PowerShell komut çalıştıran bir dize yazmak için biçimi kullanın:</span><span class="sxs-lookup"><span data-stu-id="bfe4f-172">To write a string that runs a PowerShell command, use the format:</span></span>

```powershell
"& {<command>}"
```

<span data-ttu-id="bfe4f-173">Burada tırnak işaretleri dize ve Invoke işleci belirtin (&) yürütülecek komut neden olur.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-173">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="bfe4f-174">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="bfe4f-174">-Help, -?, /?</span></span>

<span data-ttu-id="bfe4f-175">Bu ileti gösterir.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-175">Shows this message.</span></span> <span data-ttu-id="bfe4f-176">PowerShell'de PowerShell.exe komutu yazıyorsanız, bir tire (-) değil ters eğik çizgi (/) ile komut parametreleri önüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-176">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="bfe4f-177">Bir tire veya eğik Cmd.exe içinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-177">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="bfe4f-178">Sorun giderme notu: PowerShell 2. 0'da, bazı programlar konsol başarısız Windows PowerShell'de bir 0xc0000142 LastExitCode ile başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-178">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="bfe4f-179">ÖRNEKLER</span><span class="sxs-lookup"><span data-stu-id="bfe4f-179">EXAMPLES</span></span>

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