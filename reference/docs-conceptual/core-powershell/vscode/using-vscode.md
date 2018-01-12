# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="fd754-101">PowerShell geliştirme için Visual Studio Code kullanma</span><span class="sxs-lookup"><span data-stu-id="fd754-101">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="fd754-102">Ek olarak [PowerShell ISE][ise], PowerShell Visual Studio kodda iyi desteklenen de.</span><span class="sxs-lookup"><span data-stu-id="fd754-102">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="fd754-103">Visual Studio Code PowerShell çekirdek için tüm platformlarda (Windows, macOS ve Linux) destekleniyorsa Ayrıca, işe PowerShell çekirdek ile desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="fd754-103">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="fd754-104">Visual Studio Code Windows PowerShell sürüm 5 ile Windows 10 veya yükleyerek kullanabilirsiniz [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) için alt düzey Windows OSs (örneğin Windows 8.1, vb.).</span><span class="sxs-lookup"><span data-stu-id="fd754-104">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="fd754-105">Başlamadan önce lütfen PowerShell sisteminizde bulunduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="fd754-105">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="fd754-106">Windows, macOS ve Linux modern iş yükleri için bkz:</span><span class="sxs-lookup"><span data-stu-id="fd754-106">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="fd754-107">[PowerShell çekirdek yüklemek macOS ve Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="fd754-107">[Installing PowerShell Core on macOS and Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="fd754-108">[Windows PowerShell çekirdek yükleniyor][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="fd754-108">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="fd754-109">Geleneksel Windows PowerShell iş yükleri için bkz: [Windows PowerShell'i yükleme][install-winps].</span><span class="sxs-lookup"><span data-stu-id="fd754-109">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="fd754-110">Visual Studio Code ile düzenleme</span><span class="sxs-lookup"><span data-stu-id="fd754-110">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="fd754-111">1. Visual Studio Code yükleme</span><span class="sxs-lookup"><span data-stu-id="fd754-111">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="fd754-112">**Linux**: yükleme yönergelerini izleyin [Linux üzerinde çalışan VS kodu](https://code.visualstudio.com/docs/setup/linux) sayfası</span><span class="sxs-lookup"><span data-stu-id="fd754-112">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="fd754-113">**macOS**: yükleme yönergelerini izleyin [macOS üzerinde çalışan VS kodu](https://code.visualstudio.com/docs/setup/mac) sayfası</span><span class="sxs-lookup"><span data-stu-id="fd754-113">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd754-114">MacOS üzerinde düzgün çalışması için OpenSSL PowerShell uzantısı yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd754-114">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
> <span data-ttu-id="fd754-115">Bunu yapmanın en kolay yolu yüklemektir [Homebrew](http://brew.sh/) ve ardından çalıştırın `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="fd754-115">The easiest way to accomplish this is to install [Homebrew](http://brew.sh/) and then run `brew install openssl`.</span></span>
> <span data-ttu-id="fd754-116">PowerShell uzantısı artık başarıyla yüklemek mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fd754-116">The PowerShell extension will now be able to load successfully.</span></span>

- <span data-ttu-id="fd754-117">**Windows**: yükleme yönergelerini izleyin [Windows üzerinde çalışan VS kodu](https://code.visualstudio.com/docs/setup/windows) sayfası</span><span class="sxs-lookup"><span data-stu-id="fd754-117">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="fd754-118">2. PowerShell uzantısı yükleme</span><span class="sxs-lookup"><span data-stu-id="fd754-118">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="fd754-119">Visual Studio Code uygulama tarafından başlatma:</span><span class="sxs-lookup"><span data-stu-id="fd754-119">Launch the Visual Studio Code app by:</span></span>
    - <span data-ttu-id="fd754-120">**Windows**: yazarak `code` PowerShell oturumunuzda</span><span class="sxs-lookup"><span data-stu-id="fd754-120">**Windows**: typing `code` in your PowerShell session</span></span>
    - <span data-ttu-id="fd754-121">**Linux**: yazarak `code` terminalinizde</span><span class="sxs-lookup"><span data-stu-id="fd754-121">**Linux**: typing `code` in your terminal</span></span>
    - <span data-ttu-id="fd754-122">**macOS**: yazarak `code` terminalinizde</span><span class="sxs-lookup"><span data-stu-id="fd754-122">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="fd754-123">Başlatma **hızlı açık** basarak **Ctrl + P** (**Cmd + P** Mac üzerinde).</span><span class="sxs-lookup"><span data-stu-id="fd754-123">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="fd754-124">Hızlı Aç yazın `ext install powershell` ve isabet **Enter**.</span><span class="sxs-lookup"><span data-stu-id="fd754-124">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="fd754-125">**Uzantıları** görünümü yan çubuğunda açın.</span><span class="sxs-lookup"><span data-stu-id="fd754-125">The **Extensions** view will open on the Side Bar.</span></span> <span data-ttu-id="fd754-126">PowerShell uzantısı Microsoft'tan seçin.</span><span class="sxs-lookup"><span data-stu-id="fd754-126">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="fd754-127">Bir şey görürsünüz aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="fd754-127">You will see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="fd754-129">Tıklatın **yükleme** Microsoft PowerShell uzantısından düğmesinde.</span><span class="sxs-lookup"><span data-stu-id="fd754-129">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="fd754-130">Yüklemeden sonra görürsünüz **yükleme** düğmesini döndüğüne **yeniden**.</span><span class="sxs-lookup"><span data-stu-id="fd754-130">After the install, you will see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="fd754-131">Tıklayın **yeniden**.</span><span class="sxs-lookup"><span data-stu-id="fd754-131">Click on **Reload**.</span></span>
- <span data-ttu-id="fd754-132">Visual Studio Code yeniden sahip olduktan sonra düzenleme için hazır olursunuz.</span><span class="sxs-lookup"><span data-stu-id="fd754-132">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="fd754-133">Örneğin, yeni bir dosya oluşturmak için tıklatın **Dosya -> Yeni**.</span><span class="sxs-lookup"><span data-stu-id="fd754-133">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="fd754-134">Dosyayı kaydetmek için tıklatın **Dosya -> Kaydet** ve ardından, bir dosya adı şimdi deyin sağlayın `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="fd754-134">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="fd754-135">Dosyayı kapatın, dosya adının yanındaki "x"'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fd754-135">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="fd754-136">Visual Studio Code, çıkmak için **Dosya -> çıkış**.</span><span class="sxs-lookup"><span data-stu-id="fd754-136">To exit Visual Studio Code, **File->Exit**.</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="fd754-137">Belirli bir yüklü sürümünü PowerShell kullanma</span><span class="sxs-lookup"><span data-stu-id="fd754-137">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="fd754-138">Visual Studio Code ile belirli bir PowerShell yüklemesini kullanmak istiyorsanız, kullanıcı ayarları dosyanız için yeni bir değişken eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd754-138">If you wish to use a specific installation of PowerShell with Visual Studio Code, you will need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="fd754-139">Tıklatın **dosya Tercihler -> Ayarlar ->**</span><span class="sxs-lookup"><span data-stu-id="fd754-139">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="fd754-140">İki Düzenleyicisi bölmeleri görünür.</span><span class="sxs-lookup"><span data-stu-id="fd754-140">Two editor panes will appear.</span></span>
   <span data-ttu-id="fd754-141">En sağdaki bölmede (`settings.json`), aşağıdaki ayar Ekle iki süslü ayraçlar arasında bir yerde, işletim sistemi için uygun (`{` ve `}`) ve değiştirme  *<version>*  yüklü ile PowerShell sürümü:</span><span class="sxs-lookup"><span data-stu-id="fd754-141">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace *<version>* with the installed PowerShell version:</span></span>

  ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
  ```
1. <span data-ttu-id="fd754-142">Yürütülebilir istenen PowerShell yoluyla ayarını değiştirin</span><span class="sxs-lookup"><span data-stu-id="fd754-142">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="fd754-143">Ayarlar dosyasını kaydedin ve Visual Studio Code yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="fd754-143">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="fd754-144">Visual Studio Code için yapılandırma ayarları</span><span class="sxs-lookup"><span data-stu-id="fd754-144">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="fd754-145">Önceki paragrafta adımları kullanarak yapılandırma ayarlarında ekleyebilirsiniz `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="fd754-145">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="fd754-146">Visual Studio Code aşağıdaki yapılandırma ayarları öneririz:</span><span class="sxs-lookup"><span data-stu-id="fd754-146">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="fd754-147">Visual Studio Code ile hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="fd754-147">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="fd754-148">Hayır-çalışma hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="fd754-148">No-workspace debugging</span></span>

<span data-ttu-id="fd754-149">Visual Studio Code sürüm 1.9 itibariyle PowerShell komut dosyasını içeren klasörü açmak zorunda kalmadan PowerShell komut dosyaları ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd754-149">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span>
<span data-ttu-id="fd754-150">PowerShell komut dosyası ile açmanız yeterlidir **Dosya -> Dosya Aç...** , bir satırı (F9 tuşuna basın) bir kesme noktası ayarlayın ve ardından hata ayıklamayı başlatmak için F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="fd754-150">Simply open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span>
<span data-ttu-id="fd754-151">Hata ayıklayıcı, adım, devam ettirme ve durdurma hata ayıklama bölün sağlayan görünen hata ayıklama eylemler bölmesini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="fd754-151">You will see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="fd754-152">Çalışma hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="fd754-152">Workspace debugging</span></span>

<span data-ttu-id="fd754-153">Hata ayıklama çalışma başvuruyor Visual Studio Code kullanarak açtığınız bir klasör bağlamında hata ayıklama için **Klasör Aç...**  gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="fd754-153">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="fd754-154">Açtığınız genellikle PowerShell proje klasörünüzdeki ve/veya Git deponuzu kökündeki klasörüdür.</span><span class="sxs-lookup"><span data-stu-id="fd754-154">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="fd754-155">Bu modda bile F5'e basarak şu anda seçili PowerShell komut dosyası hata ayıklama başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd754-155">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="fd754-156">Ancak, çalışma hata ayıklama yalnızca şu anda açık olan dosyayla hata ayıklama dışında birden çok hata ayıklama yapılandırmaları tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fd754-156">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="fd754-157">Örneğin, bir yapılandırmaları ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fd754-157">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="fd754-158">Hata ayıklayıcı Pester testlerinde başlatma</span><span class="sxs-lookup"><span data-stu-id="fd754-158">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="fd754-159">Hata ayıklayıcı bağımsız değişkenlerle belirli bir dosya başlatma</span><span class="sxs-lookup"><span data-stu-id="fd754-159">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="fd754-160">Hata ayıklayıcı etkileşimli oturum başlatma</span><span class="sxs-lookup"><span data-stu-id="fd754-160">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="fd754-161">PowerShell ana bilgisayar işlemi için hata ayıklayıcıyı Ekle</span><span class="sxs-lookup"><span data-stu-id="fd754-161">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="fd754-162">Hata ayıklama yapılandırma dosyası oluşturmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="fd754-162">Follow these steps to create your debug configuration file:</span></span>

1. <span data-ttu-id="fd754-163">Açık **hata ayıklama** basarak Görünüm **Ctrl + Shift + D** (**Cmd + SHIFT + D** Mac üzerinde).</span><span class="sxs-lookup"><span data-stu-id="fd754-163">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
1. <span data-ttu-id="fd754-164">Tuşuna **yapılandırma** araç çubuğunda dişli simgesi.</span><span class="sxs-lookup"><span data-stu-id="fd754-164">Press the **Configure** gear icon in the toolbar.</span></span>
1. <span data-ttu-id="fd754-165">Visual Studio Code size sorar **seçin ortamı**.</span><span class="sxs-lookup"><span data-stu-id="fd754-165">Visual Studio Code will prompt you to **Select Environment**.</span></span>
   <span data-ttu-id="fd754-166">Seçin **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="fd754-166">Choose **PowerShell**.</span></span>

   <span data-ttu-id="fd754-167">Bunu yaparken, Visual Studio Code çalışma klasörünüze kök dizininde bir dizin ve dosya ".vscode\launch.json" oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fd754-167">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
   <span data-ttu-id="fd754-168">Bu, hata ayıklama yapılandırmasını depolandığı yerdir.</span><span class="sxs-lookup"><span data-stu-id="fd754-168">This is where your debug configuration is stored.</span></span> <span data-ttu-id="fd754-169">Dosyalarınızı Git deposunda varsa, genellikle Launch.json'u dosya Yürüt istersiniz.</span><span class="sxs-lookup"><span data-stu-id="fd754-169">If your files are in a Git repository, you will typically want to commit the launch.json file.</span></span>
   <span data-ttu-id="fd754-170">Launch.json'u dosyasının içeriğini şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fd754-170">The contents of the launch.json file are:</span></span>

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Launch (current file)",
            "script": "${file}",
            "args": [],
            "cwd": "${file}"
        },
        {
            "type": "PowerShell",
            "request": "attach",
            "name": "PowerShell Attach to Host Process",
            "processId": "${command.PickPSHostProcess}",
            "runspaceId": 1
        },
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Interactive Session",
            "cwd": "${workspaceRoot}"
        }
    ]
}
```

<span data-ttu-id="fd754-171">Bu hata ayıklama senaryoları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fd754-171">This represents the common debug scenarios.</span></span>
<span data-ttu-id="fd754-172">Ancak, bu dosyayı düzenleyicide açtığınızda göreceğiniz bir **Yapılandırması Ekle...**  düğmesi.</span><span class="sxs-lookup"><span data-stu-id="fd754-172">However, when you open this file in the editor, you will see an **Add Configuration...** button.</span></span>
<span data-ttu-id="fd754-173">Daha fazla PowerShell hata ayıklama yapılandırmaları eklemek için bu düğmeyi basabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd754-173">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="fd754-174">Eklemek için kullanışlı bir yapılandırma **PowerShell: başlatma komut dosyası**.</span><span class="sxs-lookup"><span data-stu-id="fd754-174">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
<span data-ttu-id="fd754-175">Bu yapılandırma ile hangi dosya Düzenleyicisi'nde şu anda etkin olan geçtiğinden bağımsız F5'e basın her başlatılması gereken isteğe bağlı bağımsız değişkenler ile belirli bir dosya belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd754-175">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="fd754-176">Hata ayıklama yapılandırmasını kurulduktan sonra bir hata ayıklama oturumu sırasında bir hata ayıklama yapılandırmasını açılan listesinde seçerek kullanmak istediğiniz yapılandırma seçebilirsiniz **hata ayıklama** görünümünün araç.</span><span class="sxs-lookup"><span data-stu-id="fd754-176">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="fd754-177">Visual Studio Code için PowerShell uzantısını kullanarak başlamanıza yardımcı olmak kullanışlı olabilecek birkaç bloglar vardır</span><span class="sxs-lookup"><span data-stu-id="fd754-177">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code</span></span>

- <span data-ttu-id="fd754-178">Visual Studio Code: [PowerShell uzantısı][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="fd754-178">Visual Studio Code: [PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="fd754-179">[Yazma ve PowerShell betikleri Visual Studio kodda hata ayıklama][debug]</span><span class="sxs-lookup"><span data-stu-id="fd754-179">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="fd754-180">[Visual Studio kod Kılavuzu hata ayıklama][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="fd754-180">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="fd754-181">[PowerShell Visual Studio kodda hata ayıklama][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="fd754-181">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="fd754-182">[Visual Studio Code PowerShell geliştirme kullanmaya başlama][getting-started]</span><span class="sxs-lookup"><span data-stu-id="fd754-182">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="fd754-183">[Visual Studio Code PowerShell geliştirme – 1. bölüm özelliklerini düzenleme][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="fd754-183">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="fd754-184">[Visual Studio Code PowerShell geliştirme – Kısım 2 özelliklerini düzenleme][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="fd754-184">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="fd754-185">[Visual Studio Code – Kısım 1 PowerShell komut dosyası hata ayıklaması][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="fd754-185">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="fd754-186">[Visual Studio Code – Kısım 2 PowerShell komut dosyası hata ayıklaması][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="fd754-186">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise-guide.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-macOS-and-Linux.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]:https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]:https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]:https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]:https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]:https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="fd754-187">Visual Studio Code için PowerShell uzantısı</span><span class="sxs-lookup"><span data-stu-id="fd754-187">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="fd754-188">PowerShell uzantının kaynak kodu bulunabilir [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="fd754-188">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
