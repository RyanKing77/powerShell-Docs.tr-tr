# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="5c9fc-101">PowerShell geliştirme için Visual Studio Code kullanma</span><span class="sxs-lookup"><span data-stu-id="5c9fc-101">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="5c9fc-102">Ek olarak [PowerShell ISE][ise], PowerShell Visual Studio kodda iyi desteklenen de.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-102">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="5c9fc-103">Visual Studio Code PowerShell çekirdek için tüm platformlarda (Windows, macOS ve Linux) destekleniyorsa Ayrıca, işe PowerShell çekirdek ile desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="5c9fc-103">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="5c9fc-104">Visual Studio Code Windows PowerShell sürüm 5 ile Windows 10 veya yükleyerek kullanabilirsiniz [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) için alt düzey Windows OSs (örneğin Windows 8.1, vb.).</span><span class="sxs-lookup"><span data-stu-id="5c9fc-104">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="5c9fc-105">Başlamadan önce lütfen PowerShell sisteminizde bulunduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-105">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="5c9fc-106">Windows, macOS ve Linux modern iş yükleri için bkz:</span><span class="sxs-lookup"><span data-stu-id="5c9fc-106">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="5c9fc-107">[PowerShell çekirdek Linux'ta yükleme][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="5c9fc-107">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="5c9fc-108">[PowerShell çekirdeği üzerinde macOS yükleme][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="5c9fc-108">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="5c9fc-109">[Windows PowerShell çekirdek yükleniyor][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="5c9fc-109">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="5c9fc-110">Geleneksel Windows PowerShell iş yükleri için bkz: [Windows PowerShell'i yükleme][install-winps].</span><span class="sxs-lookup"><span data-stu-id="5c9fc-110">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="5c9fc-111">Visual Studio Code ile düzenleme</span><span class="sxs-lookup"><span data-stu-id="5c9fc-111">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="5c9fc-112">1. Visual Studio Code yükleme</span><span class="sxs-lookup"><span data-stu-id="5c9fc-112">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="5c9fc-113">**Linux**: yükleme yönergelerini izleyin [Linux üzerinde çalışan VS kodu](https://code.visualstudio.com/docs/setup/linux) sayfası</span><span class="sxs-lookup"><span data-stu-id="5c9fc-113">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="5c9fc-114">**macOS**: yükleme yönergelerini izleyin [macOS üzerinde çalışan VS kodu](https://code.visualstudio.com/docs/setup/mac) sayfası</span><span class="sxs-lookup"><span data-stu-id="5c9fc-114">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5c9fc-115">MacOS üzerinde düzgün çalışması için OpenSSL PowerShell uzantısı yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-115">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
> <span data-ttu-id="5c9fc-116">Bunu yapmanın en kolay yolu yüklemektir [Homebrew](http://brew.sh/) ve ardından çalıştırın `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-116">The easiest way to accomplish this is to install [Homebrew](http://brew.sh/) and then run `brew install openssl`.</span></span>
> <span data-ttu-id="5c9fc-117">VS Code şimdi yükleyebilirsiniz PowerShell uzantısı başarıyla.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-117">VS Code can now load the the PowerShell extension successfully.</span></span>

- <span data-ttu-id="5c9fc-118">**Windows**: yükleme yönergelerini izleyin [Windows üzerinde çalışan VS kodu](https://code.visualstudio.com/docs/setup/windows) sayfası</span><span class="sxs-lookup"><span data-stu-id="5c9fc-118">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="5c9fc-119">2. PowerShell uzantısı yükleme</span><span class="sxs-lookup"><span data-stu-id="5c9fc-119">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="5c9fc-120">Visual Studio Code uygulama tarafından başlatma:</span><span class="sxs-lookup"><span data-stu-id="5c9fc-120">Launch the Visual Studio Code app by:</span></span>
    - <span data-ttu-id="5c9fc-121">**Windows**: yazarak `code` PowerShell oturumunuzda</span><span class="sxs-lookup"><span data-stu-id="5c9fc-121">**Windows**: typing `code` in your PowerShell session</span></span>
    - <span data-ttu-id="5c9fc-122">**Linux**: yazarak `code` terminalinizde</span><span class="sxs-lookup"><span data-stu-id="5c9fc-122">**Linux**: typing `code` in your terminal</span></span>
    - <span data-ttu-id="5c9fc-123">**macOS**: yazarak `code` terminalinizde</span><span class="sxs-lookup"><span data-stu-id="5c9fc-123">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="5c9fc-124">Başlatma **hızlı açık** basarak **Ctrl + P** (**Cmd + P** Mac üzerinde).</span><span class="sxs-lookup"><span data-stu-id="5c9fc-124">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="5c9fc-125">Hızlı Aç yazın `ext install powershell` ve isabet **Enter**.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-125">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="5c9fc-126">**Uzantıları** yan çubuğunda görünümünü açar.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-126">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="5c9fc-127">PowerShell uzantısı Microsoft'tan seçin.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-127">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="5c9fc-128">Bir şey görmeniz gerekir aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="5c9fc-128">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="5c9fc-130">Tıklatın **yükleme** Microsoft PowerShell uzantısından düğmesinde.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-130">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="5c9fc-131">Yüklemeyi tamamladıktan sonra gördüğünüz **yüklemek** düğmesini döndüğüne **yeniden**.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-131">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="5c9fc-132">Tıklayın **yeniden**.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-132">Click on **Reload**.</span></span>
- <span data-ttu-id="5c9fc-133">Visual Studio Code yeniden sahip olduktan sonra düzenleme için hazır olursunuz.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-133">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="5c9fc-134">Örneğin, yeni bir dosya oluşturmak için tıklatın **Dosya -> Yeni**.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-134">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="5c9fc-135">Dosyayı kaydetmek için tıklatın **Dosya -> Kaydet** ve ardından, bir dosya adı şimdi deyin sağlayın `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-135">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="5c9fc-136">Dosyayı kapatın, dosya adının yanındaki "x"'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-136">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="5c9fc-137">Visual Studio Code, çıkmak için **Dosya -> çıkış**.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-137">To exit Visual Studio Code, **File->Exit**.</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="5c9fc-138">Belirli bir yüklü sürümünü PowerShell kullanma</span><span class="sxs-lookup"><span data-stu-id="5c9fc-138">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="5c9fc-139">Visual Studio Code ile belirli bir PowerShell yüklemesini kullanmak istiyorsanız, kullanıcı ayarları dosyanız için yeni bir değişken eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-139">If you wish to use a specific installation of PowerShell with Visual Studio Code, you need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="5c9fc-140">Tıklatın **dosya Tercihler -> Ayarlar ->**</span><span class="sxs-lookup"><span data-stu-id="5c9fc-140">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="5c9fc-141">İki Düzenleyicisi bölmeleri görünür.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-141">Two editor panes appear.</span></span>
   <span data-ttu-id="5c9fc-142">En sağdaki bölmede (`settings.json`), aşağıdaki ayar Ekle iki süslü ayraçlar arasında bir yerde, işletim sistemi için uygun (`{` ve `}`) ve değiştirme *<version>* yüklü ile PowerShell sürümü:</span><span class="sxs-lookup"><span data-stu-id="5c9fc-142">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace *<version>* with the installed PowerShell version:</span></span>

  ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
  ```
1. <span data-ttu-id="5c9fc-143">Yürütülebilir istenen PowerShell yoluyla ayarını değiştirin</span><span class="sxs-lookup"><span data-stu-id="5c9fc-143">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="5c9fc-144">Ayarlar dosyasını kaydedin ve Visual Studio Code yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="5c9fc-144">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="5c9fc-145">Visual Studio Code için yapılandırma ayarları</span><span class="sxs-lookup"><span data-stu-id="5c9fc-145">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="5c9fc-146">Önceki paragrafta adımları kullanarak yapılandırma ayarlarında ekleyebilirsiniz `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-146">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="5c9fc-147">Visual Studio Code aşağıdaki yapılandırma ayarları öneririz:</span><span class="sxs-lookup"><span data-stu-id="5c9fc-147">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="5c9fc-148">Visual Studio Code ile hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="5c9fc-148">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="5c9fc-149">Hayır-çalışma hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="5c9fc-149">No-workspace debugging</span></span>

<span data-ttu-id="5c9fc-150">Visual Studio Code sürüm 1.9 itibariyle PowerShell komut dosyasını içeren klasörü açmak zorunda kalmadan PowerShell komut dosyaları ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-150">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span>
<span data-ttu-id="5c9fc-151">PowerShell komut dosyası ile açmanız yeterlidir **Dosya -> Dosya Aç...** , bir satırı (F9 tuşuna basın) bir kesme noktası ayarlayın ve ardından hata ayıklamayı başlatmak için F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-151">Simply open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span>
<span data-ttu-id="5c9fc-152">Hata ayıklayıcı, adım, devam ettirme ve durdurma hata ayıklama bölün sağlayan görünür ve hata ayıklama Eylemler bölmesinde görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-152">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="5c9fc-153">Çalışma hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="5c9fc-153">Workspace debugging</span></span>

<span data-ttu-id="5c9fc-154">Hata ayıklama çalışma başvuruyor Visual Studio Code kullanarak açtığınız bir klasör bağlamında hata ayıklama için **Klasör Aç...**  gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-154">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="5c9fc-155">Açtığınız genellikle PowerShell proje klasörünüzdeki ve/veya Git deponuzu kökündeki klasörüdür.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-155">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="5c9fc-156">Bu modda bile F5'e basarak şu anda seçili PowerShell komut dosyası hata ayıklama başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-156">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="5c9fc-157">Ancak, çalışma hata ayıklama yalnızca şu anda açık olan dosyayla hata ayıklama dışında birden çok hata ayıklama yapılandırmaları tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-157">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="5c9fc-158">Örneğin, bir yapılandırmaları ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5c9fc-158">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="5c9fc-159">Hata ayıklayıcı Pester testlerinde başlatma</span><span class="sxs-lookup"><span data-stu-id="5c9fc-159">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="5c9fc-160">Hata ayıklayıcı bağımsız değişkenlerle belirli bir dosya başlatma</span><span class="sxs-lookup"><span data-stu-id="5c9fc-160">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="5c9fc-161">Hata ayıklayıcı etkileşimli oturum başlatma</span><span class="sxs-lookup"><span data-stu-id="5c9fc-161">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="5c9fc-162">PowerShell ana bilgisayar işlemi için hata ayıklayıcıyı Ekle</span><span class="sxs-lookup"><span data-stu-id="5c9fc-162">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="5c9fc-163">Hata ayıklama yapılandırma dosyası oluşturmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="5c9fc-163">Follow these steps to create your debug configuration file:</span></span>

1. <span data-ttu-id="5c9fc-164">Açık **hata ayıklama** basarak Görünüm **Ctrl + Shift + D** (**Cmd + SHIFT + D** Mac üzerinde).</span><span class="sxs-lookup"><span data-stu-id="5c9fc-164">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
1. <span data-ttu-id="5c9fc-165">Tuşuna **yapılandırma** araç çubuğunda dişli simgesi.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-165">Press the **Configure** gear icon in the toolbar.</span></span>
1. <span data-ttu-id="5c9fc-166">Visual Studio Code ister **seçin ortamı**.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-166">Visual Studio Code prompts you to **Select Environment**.</span></span>
   <span data-ttu-id="5c9fc-167">Seçin **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-167">Choose **PowerShell**.</span></span>

   <span data-ttu-id="5c9fc-168">Bunu yaparken, Visual Studio Code çalışma klasörünüze kök dizininde bir dizin ve dosya ".vscode\launch.json" oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-168">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
   <span data-ttu-id="5c9fc-169">Bu, hata ayıklama yapılandırmasını depolandığı yerdir.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-169">This is where your debug configuration is stored.</span></span> <span data-ttu-id="5c9fc-170">Dosyalarınızı Git deposunda varsa, genellikle Launch.json'u dosyasını kaydetmek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-170">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
   <span data-ttu-id="5c9fc-171">Launch.json'u dosyasının içeriğini şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5c9fc-171">The contents of the launch.json file are:</span></span>

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

<span data-ttu-id="5c9fc-172">Bu hata ayıklama senaryoları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-172">This represents the common debug scenarios.</span></span>
<span data-ttu-id="5c9fc-173">Ancak, bu dosyayı düzenleyicide açtığınızda gördüğünüz bir **Yapılandırması Ekle...**  düğmesi.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-173">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
<span data-ttu-id="5c9fc-174">Daha fazla PowerShell hata ayıklama yapılandırmaları eklemek için bu düğmeyi basabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-174">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="5c9fc-175">Eklemek için kullanışlı bir yapılandırma **PowerShell: başlatma komut dosyası**.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-175">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
<span data-ttu-id="5c9fc-176">Bu yapılandırma ile hangi dosya Düzenleyicisi'nde şu anda etkin olan geçtiğinden bağımsız F5'e basın her başlatılması gereken isteğe bağlı bağımsız değişkenler ile belirli bir dosya belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-176">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="5c9fc-177">Hata ayıklama yapılandırmasını kurulduktan sonra bir hata ayıklama oturumu sırasında bir hata ayıklama yapılandırmasını açılan listesinde seçerek kullanmak istediğiniz yapılandırma seçebilirsiniz **hata ayıklama** görünümünün araç.</span><span class="sxs-lookup"><span data-stu-id="5c9fc-177">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="5c9fc-178">Visual Studio Code için PowerShell uzantısını kullanarak başlamanıza yardımcı olmak kullanışlı olabilecek birkaç bloglar vardır</span><span class="sxs-lookup"><span data-stu-id="5c9fc-178">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code</span></span>

- <span data-ttu-id="5c9fc-179">Visual Studio Code: [PowerShell uzantısı][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="5c9fc-179">Visual Studio Code: [PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="5c9fc-180">[Yazma ve PowerShell betikleri Visual Studio kodda hata ayıklama][debug]</span><span class="sxs-lookup"><span data-stu-id="5c9fc-180">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="5c9fc-181">[Visual Studio kod Kılavuzu hata ayıklama][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="5c9fc-181">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="5c9fc-182">[PowerShell Visual Studio kodda hata ayıklama][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="5c9fc-182">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="5c9fc-183">[Visual Studio Code PowerShell geliştirme kullanmaya başlama][getting-started]</span><span class="sxs-lookup"><span data-stu-id="5c9fc-183">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="5c9fc-184">[Visual Studio Code PowerShell geliştirme – 1. bölüm özelliklerini düzenleme][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="5c9fc-184">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="5c9fc-185">[Visual Studio Code PowerShell geliştirme – Kısım 2 özelliklerini düzenleme][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="5c9fc-185">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="5c9fc-186">[Visual Studio Code – Kısım 1 PowerShell komut dosyası hata ayıklaması][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="5c9fc-186">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="5c9fc-187">[Visual Studio Code – Kısım 2 PowerShell komut dosyası hata ayıklaması][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="5c9fc-187">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise-guide.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
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

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="5c9fc-188">Visual Studio Code için PowerShell uzantısı</span><span class="sxs-lookup"><span data-stu-id="5c9fc-188">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="5c9fc-189">PowerShell uzantının kaynak kodu bulunabilir [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="5c9fc-189">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
