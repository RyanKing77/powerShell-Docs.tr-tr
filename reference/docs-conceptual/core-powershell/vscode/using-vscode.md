---
title: PowerShell geliştirme için Visual Studio Code'u kullanma
description: PowerShell geliştirme için Visual Studio Code'u kullanma
ms.date: 08/06/2018
ms.openlocfilehash: 9c06ce72c39d08e75fcb7e5cf9d5f92ae5dd8ed9
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225803"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="eeb10-103">PowerShell geliştirme için Visual Studio Code'u kullanma</span><span class="sxs-lookup"><span data-stu-id="eeb10-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="eeb10-104">Ek olarak [PowerShell ISE][ise], PowerShell Visual Studio Code'da iyi desteklenen de.</span><span class="sxs-lookup"><span data-stu-id="eeb10-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="eeb10-105">Visual Studio Code için PowerShell Core (Windows, macOS ve Linux) tüm platformlarda desteklenir ancak Ayrıca, işe PowerShell Core ile desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="eeb10-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="eeb10-106">Visual Studio Code Windows PowerShell sürüm 5 ile Windows 10 veya yükleyerek kullanabileceğinizi [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) için alt düzey Windows OSs (örneğin Windows 8.1, vb.).</span><span class="sxs-lookup"><span data-stu-id="eeb10-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="eeb10-107">Başlamadan önce lütfen PowerShell sisteminizde mevcut olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="eeb10-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="eeb10-108">Windows, macOS ve Linux'ta modern iş yükleri için bkz:</span><span class="sxs-lookup"><span data-stu-id="eeb10-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="eeb10-109">[Linux'ta PowerShell Core yükleme][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="eeb10-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="eeb10-110">[Macos'ta PowerShell Core yükleme][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="eeb10-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="eeb10-111">[Üzerinde Windows PowerShell Core yükleme][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="eeb10-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="eeb10-112">Geleneksel Windows PowerShell iş yükleri için bkz: [Windows PowerShell'i yükleme][install-winps].</span><span class="sxs-lookup"><span data-stu-id="eeb10-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="eeb10-113">Visual Studio kodu ile düzenleme</span><span class="sxs-lookup"><span data-stu-id="eeb10-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="eeb10-114">1. Visual Studio Code yükleme</span><span class="sxs-lookup"><span data-stu-id="eeb10-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="eeb10-115">**Linux**: yükleme yönergelerini izleyin [Linux üzerinde çalışan VS Code](https://code.visualstudio.com/docs/setup/linux) sayfası</span><span class="sxs-lookup"><span data-stu-id="eeb10-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="eeb10-116">**macOS**: yükleme yönergelerini izleyin [macOS üzerinde çalışan VS Code](https://code.visualstudio.com/docs/setup/mac) sayfası</span><span class="sxs-lookup"><span data-stu-id="eeb10-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="eeb10-117">MacOS üzerinde doğru çalışması için PowerShell uzantısı için OpenSSL yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eeb10-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="eeb10-118">Bunu yapmanın en kolay yolu yüklemektir [Homebrew](http://brew.sh/) ve ardından çalıştırın `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="eeb10-118">The easiest way to accomplish this is to install [Homebrew](http://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="eeb10-119">VS Code PowerShell uzantısı şimdi başarıyla yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eeb10-119">VS Code can now load the PowerShell extension successfully.</span></span>

- <span data-ttu-id="eeb10-120">**Windows**: yükleme yönergelerini izleyin [Windows üzerinde çalışan VS Code](https://code.visualstudio.com/docs/setup/windows) sayfası</span><span class="sxs-lookup"><span data-stu-id="eeb10-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="eeb10-121">2. PowerShell uzantısı yükleniyor</span><span class="sxs-lookup"><span data-stu-id="eeb10-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="eeb10-122">Visual Studio Code tarafından uygulama başlatma:</span><span class="sxs-lookup"><span data-stu-id="eeb10-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="eeb10-123">**Windows**: yazarak `code` PowerShell oturumunuzda</span><span class="sxs-lookup"><span data-stu-id="eeb10-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="eeb10-124">**Linux**: yazarak `code` , Terminal</span><span class="sxs-lookup"><span data-stu-id="eeb10-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="eeb10-125">**macOS**: yazarak `code` , Terminal</span><span class="sxs-lookup"><span data-stu-id="eeb10-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="eeb10-126">Başlatma **Quick Open** tuşuna basarak **Ctrl + P** (**Cmd + P** Mac üzerinde).</span><span class="sxs-lookup"><span data-stu-id="eeb10-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="eeb10-127">Hızlı Aç yazın `ext install powershell` ve isabet **Enter**.</span><span class="sxs-lookup"><span data-stu-id="eeb10-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="eeb10-128">**Uzantıları** taraftaki çubukta görünümü açılır.</span><span class="sxs-lookup"><span data-stu-id="eeb10-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="eeb10-129">Microsoft PowerShell uzantıyı seçin.</span><span class="sxs-lookup"><span data-stu-id="eeb10-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="eeb10-130">Bir şey görmeniz gerekir aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="eeb10-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="eeb10-132">Tıklayın **yükleme** Microsoft gelen PowerShell uzantısında düğmesi.</span><span class="sxs-lookup"><span data-stu-id="eeb10-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="eeb10-133">Yüklemeyi tamamladıktan sonra gördüğünüz **yükleme** düğmesi dönüşür **yeniden**.</span><span class="sxs-lookup"><span data-stu-id="eeb10-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="eeb10-134">Tıklayarak **yeniden**.</span><span class="sxs-lookup"><span data-stu-id="eeb10-134">Click on **Reload**.</span></span>
- <span data-ttu-id="eeb10-135">Visual Studio Code yeniden sahip olduktan sonra düzenleme için hazır olursunuz.</span><span class="sxs-lookup"><span data-stu-id="eeb10-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="eeb10-136">Örneğin, yeni bir dosya oluşturmak için tıklayın **Dosya -> Yeni**.</span><span class="sxs-lookup"><span data-stu-id="eeb10-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="eeb10-137">Bunu kaydetmek için tıklatın **Dosya -> Kaydet** ve ardından bir dosya adı, şimdi deyin sağlayın `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="eeb10-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="eeb10-138">Dosyayı kapatmak için dosya adının yanındaki "x" tıklayın.</span><span class="sxs-lookup"><span data-stu-id="eeb10-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="eeb10-139">Visual Studio Code, çıkmak için **Dosya -> çıkış**.</span><span class="sxs-lookup"><span data-stu-id="eeb10-139">To exit Visual Studio Code, **File->Exit**.</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="eeb10-140">Belirli yüklü PowerShell sürümü kullanıyor</span><span class="sxs-lookup"><span data-stu-id="eeb10-140">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="eeb10-141">Visual Studio Code ile belirli bir PowerShell yüklemesi kullanmak istiyorsanız, yeni bir değişken, kullanıcı ayarları dosyanıza ekleme gerekir.</span><span class="sxs-lookup"><span data-stu-id="eeb10-141">If you wish to use a specific installation of PowerShell with Visual Studio Code, you need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="eeb10-142">Tıklayın **dosya Tercihler -> Ayarlar ->**</span><span class="sxs-lookup"><span data-stu-id="eeb10-142">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="eeb10-143">İki Düzenleyici bölme görünür.</span><span class="sxs-lookup"><span data-stu-id="eeb10-143">Two editor panes appear.</span></span>
   <span data-ttu-id="eeb10-144">En sağdaki bölmede (`settings.json`), aşağıdaki ayar Ekle iki süslü ayraçlar arasında bir yerde, işletim sistemi için uygun (`{` ve `}`) ve yerine **\<sürüm\>** yüklü PowerShell sürümü ile:</span><span class="sxs-lookup"><span data-stu-id="eeb10-144">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace **\<version\>** with the installed PowerShell version:</span></span>

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. <span data-ttu-id="eeb10-145">Yürütülebilir istenen PowerShell yoluyla ayarını değiştirin</span><span class="sxs-lookup"><span data-stu-id="eeb10-145">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="eeb10-146">Ayarlar dosyasını kaydedin ve Visual Studio Code'u yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="eeb10-146">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="eeb10-147">Visual Studio Code için yapılandırma ayarları</span><span class="sxs-lookup"><span data-stu-id="eeb10-147">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="eeb10-148">Önceki paragrafta adımları kullanarak, yapılandırma ayarlarında ekleyebilirsiniz `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="eeb10-148">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="eeb10-149">Visual Studio Code için aşağıdaki yapılandırma ayarları öneririz:</span><span class="sxs-lookup"><span data-stu-id="eeb10-149">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="eeb10-150">Visual Studio kodu ile hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="eeb10-150">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="eeb10-151">Hayır-çalışma hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="eeb10-151">No-workspace debugging</span></span>

<span data-ttu-id="eeb10-152">Visual Studio Code sürümü 1.9 itibarıyla PowerShell komut dosyasını içeren klasörü açmak zorunda kalmadan PowerShell betikleri hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eeb10-152">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span>
<span data-ttu-id="eeb10-153">PowerShell komut dosyasıyla açmanız yeterlidir **Dosya -> Dosya Aç...** satırında (F9 tuşuna basın) bir kesme noktası ayarlayın ve ardından hata ayıklamayı başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="eeb10-153">Simply open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span>
<span data-ttu-id="eeb10-154">Hata ayıklayıcı, adım, sürdürme ve hata ayıklamayı durdurmak sonu sağlayan görünen hata ayıklama Eylemler bölmesinde görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eeb10-154">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="eeb10-155">Çalışma hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="eeb10-155">Workspace debugging</span></span>

<span data-ttu-id="eeb10-156">Çalışma hata ayıklama başvuruyor Visual Studio Code kullanarak açılan bir klasörü bağlamında hata ayıklama için **Klasör Aç...**  gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="eeb10-156">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="eeb10-157">Açtığınız genellikle PowerShell proje klasörünüze ve/veya Git deponuzun kök klasördür.</span><span class="sxs-lookup"><span data-stu-id="eeb10-157">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="eeb10-158">Bu modda da F5'e basarak o anda seçili PowerShell betik hata ayıklama başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eeb10-158">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="eeb10-159">Ancak, çalışma hata ayıklama, şu anda açık dosya yalnızca hata ayıklama dışında birden çok hata ayıklama yapılandırmaları tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="eeb10-159">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="eeb10-160">Örneğin, bir yapılandırmalarına ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="eeb10-160">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="eeb10-161">Hata ayıklayıcı Pester testlerinde başlatın</span><span class="sxs-lookup"><span data-stu-id="eeb10-161">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="eeb10-162">Belirli bir dosya hata ayıklayıcı bağımsız değişkenleriyle Başlat</span><span class="sxs-lookup"><span data-stu-id="eeb10-162">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="eeb10-163">Hata ayıklayıcı etkileşimli bir oturum başlatın</span><span class="sxs-lookup"><span data-stu-id="eeb10-163">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="eeb10-164">Bir PowerShell ana bilgisayar işlemi için hata ayıklayıcının</span><span class="sxs-lookup"><span data-stu-id="eeb10-164">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="eeb10-165">Hata ayıklama yapılandırma dosyanızı oluşturmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="eeb10-165">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="eeb10-166">Açık **hata ayıklama** tuşuna basarak görünümü **Ctrl + SHIFT + D** (**Cmd + SHIFT + D** Mac üzerinde).</span><span class="sxs-lookup"><span data-stu-id="eeb10-166">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="eeb10-167">Tuşuna **yapılandırma** araç çubuğundaki dişli simgesi.</span><span class="sxs-lookup"><span data-stu-id="eeb10-167">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="eeb10-168">Visual Studio Code ister **ortamı seçin**.</span><span class="sxs-lookup"><span data-stu-id="eeb10-168">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="eeb10-169">Seçin **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="eeb10-169">Choose **PowerShell**.</span></span>

  <span data-ttu-id="eeb10-170">Bunu yaptığınızda, Visual Studio Code kullanarak çalışma klasörünüzde kök dizininde bir dizin ve dosya ".vscode\launch.json" oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eeb10-170">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="eeb10-171">Bu, hata ayıklama yapılandırması depolandığı yerdir.</span><span class="sxs-lookup"><span data-stu-id="eeb10-171">This is where your debug configuration is stored.</span></span> <span data-ttu-id="eeb10-172">Dosyalarınızı Git deposunda ise genellikle launch.json dosyası işleme istersiniz.</span><span class="sxs-lookup"><span data-stu-id="eeb10-172">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="eeb10-173">Launch.json dosyasının içeriğini şunlardır:</span><span class="sxs-lookup"><span data-stu-id="eeb10-173">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="eeb10-174">Bu, hata ayıklama senaryoları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="eeb10-174">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="eeb10-175">Ancak, bu dosya Düzenleyicisi'nde açtığınızda, gördüğünüz bir **Yapılandırması Ekle...**  düğmesi.</span><span class="sxs-lookup"><span data-stu-id="eeb10-175">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="eeb10-176">Daha fazla PowerShell hata ayıklama yapılandırmaları eklemek için bu düğmeyi basabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eeb10-176">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="eeb10-177">Eklemek için kullanışlı bir yapılandırma **PowerShell: başlatma betiği**.</span><span class="sxs-lookup"><span data-stu-id="eeb10-177">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="eeb10-178">Bu yapılandırma ile hangi dosya düzenleyicide şu anda etkin olursa olsun F5 tuşuna basarak her başlatılacak isteğe bağlı bağımsız değişkenler ile belirli bir dosyayı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eeb10-178">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="eeb10-179">Hata ayıklama yapılandırması kurulduktan sonra hata ayıklama oturumu sırasında bir hata ayıklama yapılandırması açılan listesinde seçerek kullanmak istediğiniz yapılandırmayı seçebilirsiniz **hata ayıklama** görünümünün araç çubuğu.</span><span class="sxs-lookup"><span data-stu-id="eeb10-179">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="eeb10-180">Visual Studio Code için PowerShell uzantısını kullanarak başlamanıza yardımcı olmak yardımcı olabilecek birkaç blogları vardır:</span><span class="sxs-lookup"><span data-stu-id="eeb10-180">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="eeb10-181">[PowerShell uzantısı][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="eeb10-181">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="eeb10-182">[Yazma ve PowerShell betikleri Visual Studio code'da Hata Ayıkla][debug]</span><span class="sxs-lookup"><span data-stu-id="eeb10-182">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="eeb10-183">[Hata ayıklama Visual Studio kod Kılavuzu][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="eeb10-183">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="eeb10-184">[Visual Studio code'da hata ayıklama PowerShell][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="eeb10-184">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="eeb10-185">[Visual Studio code'da PowerShell geliştirme ile çalışmaya başlama][getting-started]</span><span class="sxs-lookup"><span data-stu-id="eeb10-185">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="eeb10-186">[Düzenleme özellikleri PowerShell geliştirme – bölüm 1 için Visual Studio Code][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="eeb10-186">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="eeb10-187">[Visual Studio kod düzenleme özellikleri PowerShell geliştirme – bölüm 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="eeb10-187">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="eeb10-188">[Visual Studio Code – bölüm 1 PowerShell betik hata ayıklama][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="eeb10-188">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="eeb10-189">[Visual Studio Code – bölüm 2 PowerShell betik hata ayıklama][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="eeb10-189">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise-guide.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="eeb10-190">Visual Studio Code için PowerShell uzantısı</span><span class="sxs-lookup"><span data-stu-id="eeb10-190">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="eeb10-191">PowerShell uzantının kaynak kodu bulunabilir [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="eeb10-191">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
