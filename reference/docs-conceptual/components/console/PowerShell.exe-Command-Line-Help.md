---
ms.date: 08/14/2018
keywords: PowerShell cmdlet'i
title: PowerShell.exe Komut Satırı Yardımı
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058522"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="078ee-103">PowerShell.exe komut satırı Yardımı</span><span class="sxs-lookup"><span data-stu-id="078ee-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="078ee-104">Cmd.exe gibi başka bir aracının komut satırı bir PowerShell oturumu başlatmak için PowerShell.exe kullanın veya yeni bir oturum başlatmak için PowerShell komut satırında kullanın.</span><span class="sxs-lookup"><span data-stu-id="078ee-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="078ee-105">Oturum özelleştirmek için parametreleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="078ee-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="078ee-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="078ee-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="078ee-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="078ee-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="078ee-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="078ee-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="078ee-109">Bir komut base-64 kodlu dize sürümünü kabul eder.</span><span class="sxs-lookup"><span data-stu-id="078ee-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="078ee-110">Karmaşık tırnak işaretleri veya küme ayraçları gerektiren PowerShell komutları göndermek için bu parametreyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="078ee-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="078ee-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="078ee-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="078ee-112">Geçerli oturum için varsayılan yürütme ilkesini ayarlar ve içinde $env kaydeder: PSExecutionPolicyPreference ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="078ee-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="078ee-113">Bu parametre, kayıt defterinde ayarlanan PowerShell yürütme İlkesi değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="078ee-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="078ee-114">Geçerli değerler listesi dahil olmak üzere PowerShell yürütme ilkeleri hakkında daha fazla bilgi için bkz. [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="078ee-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="078ee-115">-Dosya <FilePath> \[ <Parameters>]</span><span class="sxs-lookup"><span data-stu-id="078ee-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="078ee-116">Geçerli oturumda betik değişkenleri ve işlevleri kullanılabilir olacak şekilde belirtilen betik ("dot kaynaklı"), yerel kapsamda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="078ee-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="078ee-117">Betik dosyası yolu ve herhangi bir parametre girin.</span><span class="sxs-lookup"><span data-stu-id="078ee-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="078ee-118">**Dosya** komutta son parametre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="078ee-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="078ee-119">Sonra yazılan tüm değerleri **-dosya** parametresi betik olarak yorumlanır dosyası yolu ve parametreleri bu betiğe geçirilen.</span><span class="sxs-lookup"><span data-stu-id="078ee-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="078ee-120">Betiğe geçirilen parametreler geçerli kabuk tarafından yorumu sonra değişmez değer dizeleri geçirilir.</span><span class="sxs-lookup"><span data-stu-id="078ee-120">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="078ee-121">Örneğin, cmd.exe içinde olan ve bir ortam değişken değerini geçirmek istiyorsanız cmd.exe söz dizimini kullanın: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="078ee-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="078ee-122">Buna karşılık, çalışan `powershell.exe -File .\test.ps1 -TestParam $env:windir` sabit dizesini alma betiği cmd.exe sonucu `$env:windir` çünkü geçerli cmd.exe Kabuğu özel bir anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="078ee-122">In contrast, running `powershell.exe -File .\test.ps1 -TestParam $env:windir` in cmd.exe results in the script receiving the literal string `$env:windir` because it has no special meaning to the current cmd.exe shell.</span></span>
<span data-ttu-id="078ee-123">`$env:windir` Ortam değişkeni başvurusu stilini _olabilir_ içinde kullanılabilir bir `-Command` var. PowerShell kodu olarak yorumlanacaktır olduğundan parametre.</span><span class="sxs-lookup"><span data-stu-id="078ee-123">The `$env:windir` style of environment variable reference _can_ be used inside a `-Command` parameter, since there it will be interpreted as PowerShell code.</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="078ee-124">\-InputFormat {metin | XML}</span><span class="sxs-lookup"><span data-stu-id="078ee-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="078ee-125">PowerShell için gönderilen veri biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="078ee-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="078ee-126">Geçerli değerler "Metin" (metin dizelerini) veya "XML" (CLIXML biçimi) olmalı.</span><span class="sxs-lookup"><span data-stu-id="078ee-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="078ee-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="078ee-127">-Mta</span></span>

<span data-ttu-id="078ee-128">PowerShell kullanarak bir çok iş parçacıklı grup başlatır.</span><span class="sxs-lookup"><span data-stu-id="078ee-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="078ee-129">Bu parametre PowerShell 3. 0 ' kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="078ee-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="078ee-130">PowerShell 3. 0'da, tek iş parçacıklı grup (STA) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="078ee-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="078ee-131">PowerShell 2. 0'da, çok iş parçacıklı grup (MTA) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="078ee-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="078ee-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="078ee-132">-NoExit</span></span>

<span data-ttu-id="078ee-133">Başlangıç komutları çalıştırdıktan sonra çıkmak değil.</span><span class="sxs-lookup"><span data-stu-id="078ee-133">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="078ee-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="078ee-134">-NoLogo</span></span>

<span data-ttu-id="078ee-135">Telif hakkı başlığını başlangıçta gizler.</span><span class="sxs-lookup"><span data-stu-id="078ee-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="078ee-136">-Etkileşimsiz</span><span class="sxs-lookup"><span data-stu-id="078ee-136">-NonInteractive</span></span>

<span data-ttu-id="078ee-137">Etkileşimli bir istemi kullanıcı için mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="078ee-137">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="078ee-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="078ee-138">-NoProfile</span></span>

<span data-ttu-id="078ee-139">PowerShell profili yüklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="078ee-139">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="078ee-140">-OutputFormat {metin | XML}</span><span class="sxs-lookup"><span data-stu-id="078ee-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="078ee-141">PowerShell çıkışı nasıl biçimlendirildiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="078ee-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="078ee-142">Geçerli değerler "Metin" (metin dizelerini) veya "XML" (CLIXML biçimi) olmalı.</span><span class="sxs-lookup"><span data-stu-id="078ee-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="078ee-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="078ee-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="078ee-144">Belirtilen bir PowerShell Konsolu dosya yükler.</span><span class="sxs-lookup"><span data-stu-id="078ee-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="078ee-145">Konsol dosyasının adını ve yolunu girin.</span><span class="sxs-lookup"><span data-stu-id="078ee-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="078ee-146">Bir konsol dosyası oluşturmak için kullanın [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) PowerShell cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="078ee-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="078ee-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="078ee-147">-Sta</span></span>

<span data-ttu-id="078ee-148">PowerShell kullanarak tek kullanımlık apartman başlatır.</span><span class="sxs-lookup"><span data-stu-id="078ee-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="078ee-149">PowerShell 3. 0'da, tek iş parçacıklı grup (STA) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="078ee-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="078ee-150">PowerShell 2. 0'da, çok iş parçacıklı grup (MTA) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="078ee-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="078ee-151">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="078ee-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="078ee-152">Belirtilen PowerShell sürümünü başlatır.</span><span class="sxs-lookup"><span data-stu-id="078ee-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="078ee-153">Sistemde, belirttiğiniz sürümü yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="078ee-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="078ee-154">PowerShell 3.0, bilgisayarda yüklü değilse, geçerli değerler şunlardır: "2.0" ve "3.0".</span><span class="sxs-lookup"><span data-stu-id="078ee-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="078ee-155">"3.0" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="078ee-155">The default value is "3.0".</span></span>

<span data-ttu-id="078ee-156">PowerShell 3.0 yüklü değilse, yalnızca geçerli "2.0" değeridir.</span><span class="sxs-lookup"><span data-stu-id="078ee-156">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="078ee-157">Diğer değerleri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="078ee-157">Other values are ignored.</span></span>

<span data-ttu-id="078ee-158">Daha fazla bilgi için [Windows PowerShell'i yükleme](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="078ee-158">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="078ee-159">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="078ee-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="078ee-160">Oturum için pencere stilini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="078ee-160">Sets the window style for the session.</span></span> <span data-ttu-id="078ee-161">Geçerli değerler şunlardır: Normal, küçültülmüş, ekranı kaplamış ve gizli.</span><span class="sxs-lookup"><span data-stu-id="078ee-161">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="078ee-162">-Komutu</span><span class="sxs-lookup"><span data-stu-id="078ee-162">-Command</span></span>

<span data-ttu-id="078ee-163">PowerShell komut isteminde türü belirtilmiş gibi sorgulamanıza (herhangi bir parametre ile) belirtilen komutları yürütür.</span><span class="sxs-lookup"><span data-stu-id="078ee-163">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span>
<span data-ttu-id="078ee-164">Yürütmeden sonra PowerShell sürece çıkar **NoExit** parametre belirtildi.</span><span class="sxs-lookup"><span data-stu-id="078ee-164">After execution, PowerShell exits unless the **NoExit** parameter is specified.</span></span>
<span data-ttu-id="078ee-165">Sonra herhangi bir metin `-Command` PowerShell tek bir komut satırı gönderilir.</span><span class="sxs-lookup"><span data-stu-id="078ee-165">Any text after `-Command` is sent as a single command line to PowerShell.</span></span>
<span data-ttu-id="078ee-166">Bu nasıl farklı `-File` parametreleri için bir komut dosyası gönderilen işler.</span><span class="sxs-lookup"><span data-stu-id="078ee-166">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="078ee-167">Değerini `-Command` olabilir "-", bir dize veya bir betik bloğu.</span><span class="sxs-lookup"><span data-stu-id="078ee-167">The value of `-Command` can be "-", a string, or a script block.</span></span>
<span data-ttu-id="078ee-168">Komutun sonuçlarını üst kabuğa değil Canlı nesneleri seri durumdan çıkarılmış XML nesneler olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="078ee-168">The results of the command are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="078ee-169">Varsa değerini `-Command` olan "-", Standart girdiden okunan komut metni.</span><span class="sxs-lookup"><span data-stu-id="078ee-169">If the value of `-Command` is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="078ee-170">Zaman değerini `-Command` bir dizedir, **komut** _gerekir_ komutu yorumlanır sonra komut bağımsız herhangi bir karakter türü belirtilmiş olduğundan belirtilen son parametre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="078ee-170">When the value of `-Command` is a string, **Command** _must_ be the last parameter specified because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="078ee-171">**Komut** parametresi için geçirilen değer tanıyabilmesi zaman yürütme için bir betik bloğu yalnızca kabul `-Command` ScriptBlock türü.</span><span class="sxs-lookup"><span data-stu-id="078ee-171">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to `-Command` as a ScriptBlock type.</span></span>
<span data-ttu-id="078ee-172">Bu _yalnızca_ PowerShell.exe başka bir PowerShell konaktan çalıştırırken mümkün.</span><span class="sxs-lookup"><span data-stu-id="078ee-172">This is _only_ possible when running PowerShell.exe from another PowerShell host.</span></span>
<span data-ttu-id="078ee-173">Türü yer almalıdır bir değişken, bir ifadeden döndürülen veya PowerShell ayrıştırılmış varolan ScriptBlock konak küme ayraçları içine alınmış bir değişmez değer betik bloğu olarak `{}`PowerShell.exe iletilmeden önce.</span><span class="sxs-lookup"><span data-stu-id="078ee-173">The ScriptBlock type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces `{}`, before being passed to PowerShell.exe.</span></span>

<span data-ttu-id="078ee-174">Cmd.exe içinde yoktur de bir betik bloğu (veya Scriptblock'u türü), bu nedenle için geçirilen değer **komut** olacak _her zaman_ bir dize olması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="078ee-174">In cmd.exe, there is no such thing as a script block (or ScriptBlock type), so the value passed to **Command** will _always_ be a string.</span></span>
<span data-ttu-id="078ee-175">Bir betik bloğu içinde dize yazabilirsiniz, ancak yürütülen yerine, tam olarak davranacak tipik bir PowerShell isteminde yazılı olarak da, komut dosyasının içeriğini yazdırma bloke geri için.</span><span class="sxs-lookup"><span data-stu-id="078ee-175">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="078ee-176">Geçirilen bir dize `-Command` betik blok küme ayraçları ilk başta cmd.exe çalışırken gerekli genellikle olmadıklarından yine de PowerShell yürütülür.</span><span class="sxs-lookup"><span data-stu-id="078ee-176">A string passed to `-Command` will still be executed as PowerShell, so the script block curly braces are often not required in the first place when running from cmd.exe.</span></span>
<span data-ttu-id="078ee-177">Bir dize içinde tanımlanan bir satır içi betik bloğu yürütülecek [çağrısı işleci](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="078ee-177">To execute an inline script block defined inside a string, the [call operator](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` can be used:</span></span>

```console
"& {<command>}"
```

### <a name="-help---"></a><span data-ttu-id="078ee-178">-Help-?, /?</span><span class="sxs-lookup"><span data-stu-id="078ee-178">-Help, -?, /?</span></span>

<span data-ttu-id="078ee-179">Powershell.exe söz dizimi görülmektedir.</span><span class="sxs-lookup"><span data-stu-id="078ee-179">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="078ee-180">PowerShell.exe komut PowerShell'de yazıyorsanız, kısa çizgi (-) değil ters eğik çizgi (/) komutunu parametrelerle önüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="078ee-180">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="078ee-181">Bir tire veya eğik Cmd.exe içinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="078ee-181">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="078ee-182">Sorun giderme notu: PowerShell 2. 0'da, bazı Windows PowerShell konsol programlarda 0xc0000142'bir LastExitCode ile başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="078ee-182">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="078ee-183">ÖRNEKLERİ</span><span class="sxs-lookup"><span data-stu-id="078ee-183">EXAMPLES</span></span>

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
