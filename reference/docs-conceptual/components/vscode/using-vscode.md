---
title: PowerShell geliştirme için Visual Studio Code'u kullanma
description: PowerShell geliştirme için Visual Studio Code'u kullanma
ms.date: 08/06/2018
ms.openlocfilehash: 5badffd49252e0d72ae2c20d3147ad4b1e92d5ed
ms.sourcegitcommit: cf1a281cce9f7239c440c90f8b2798d32a13778d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882568"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="e5297-103">PowerShell geliştirme için Visual Studio Code'u kullanma</span><span class="sxs-lookup"><span data-stu-id="e5297-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="e5297-104">Ek olarak [PowerShell ISE][ise], PowerShell Visual Studio Code'da iyi desteklenen de.</span><span class="sxs-lookup"><span data-stu-id="e5297-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="e5297-105">Visual Studio Code için PowerShell Core (Windows, macOS ve Linux) tüm platformlarda desteklenir ancak Ayrıca, işe PowerShell Core ile desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="e5297-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="e5297-106">Visual Studio Code Windows PowerShell sürüm 5 ile Windows 10 veya yükleyerek kullanabileceğinizi [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) için alt düzey Windows OSs (örneğin Windows 8.1, vb.).</span><span class="sxs-lookup"><span data-stu-id="e5297-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="e5297-107">Başlamadan önce lütfen PowerShell sisteminizde mevcut olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e5297-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="e5297-108">Windows, macOS ve Linux'ta modern iş yükleri için bkz:</span><span class="sxs-lookup"><span data-stu-id="e5297-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="e5297-109">[Linux'ta PowerShell Core yükleme][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="e5297-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="e5297-110">[Macos'ta PowerShell Core yükleme][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="e5297-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="e5297-111">[Üzerinde Windows PowerShell Core yükleme][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="e5297-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="e5297-112">Geleneksel Windows PowerShell iş yükleri için bkz: [Windows PowerShell'i yükleme][install-winps].</span><span class="sxs-lookup"><span data-stu-id="e5297-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="e5297-113">Visual Studio kodu ile düzenleme</span><span class="sxs-lookup"><span data-stu-id="e5297-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="e5297-114">1. Visual Studio Code yükleme</span><span class="sxs-lookup"><span data-stu-id="e5297-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="e5297-115">**Linux**: yükleme yönergelerini izleyin [Linux üzerinde çalışan VS Code](https://code.visualstudio.com/docs/setup/linux) sayfası</span><span class="sxs-lookup"><span data-stu-id="e5297-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="e5297-116">**macOS**: yükleme yönergelerini izleyin [macOS üzerinde çalışan VS Code](https://code.visualstudio.com/docs/setup/mac) sayfası</span><span class="sxs-lookup"><span data-stu-id="e5297-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="e5297-117">MacOS üzerinde doğru çalışması için PowerShell uzantısı için OpenSSL yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5297-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="e5297-118">Bunu yapmanın en kolay yolu yüklemektir [Homebrew](https://brew.sh/) ve ardından çalıştırın `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="e5297-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="e5297-119">VS Code PowerShell uzantısı şimdi başarıyla yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5297-119">VS Code can now load the PowerShell extension successfully.</span></span>

- <span data-ttu-id="e5297-120">**Windows**: yükleme yönergelerini izleyin [Windows üzerinde çalışan VS Code](https://code.visualstudio.com/docs/setup/windows) sayfası</span><span class="sxs-lookup"><span data-stu-id="e5297-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="e5297-121">2. PowerShell uzantısı yükleniyor</span><span class="sxs-lookup"><span data-stu-id="e5297-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="e5297-122">Visual Studio Code tarafından uygulama başlatma:</span><span class="sxs-lookup"><span data-stu-id="e5297-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="e5297-123">**Windows**: yazarak `code` PowerShell oturumunuzda</span><span class="sxs-lookup"><span data-stu-id="e5297-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="e5297-124">**Linux**: yazarak `code` , Terminal</span><span class="sxs-lookup"><span data-stu-id="e5297-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="e5297-125">**macOS**: yazarak `code` , Terminal</span><span class="sxs-lookup"><span data-stu-id="e5297-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="e5297-126">Başlatma **Quick Open** tuşuna basarak **Ctrl + P** (**Cmd + P** Mac üzerinde).</span><span class="sxs-lookup"><span data-stu-id="e5297-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="e5297-127">Hızlı Aç yazın `ext install powershell` ve isabet **Enter**.</span><span class="sxs-lookup"><span data-stu-id="e5297-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="e5297-128">**Uzantıları** taraftaki çubukta görünümü açılır.</span><span class="sxs-lookup"><span data-stu-id="e5297-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="e5297-129">Microsoft PowerShell uzantıyı seçin.</span><span class="sxs-lookup"><span data-stu-id="e5297-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="e5297-130">Bir şey görmeniz gerekir aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="e5297-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="e5297-132">Tıklayın **yükleme** Microsoft gelen PowerShell uzantısında düğmesi.</span><span class="sxs-lookup"><span data-stu-id="e5297-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="e5297-133">Yüklemeyi tamamladıktan sonra gördüğünüz **yükleme** düğmesi dönüşür **yeniden**.</span><span class="sxs-lookup"><span data-stu-id="e5297-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="e5297-134">Tıklayarak **yeniden**.</span><span class="sxs-lookup"><span data-stu-id="e5297-134">Click on **Reload**.</span></span>
- <span data-ttu-id="e5297-135">Visual Studio Code yeniden sahip olduktan sonra düzenleme için hazır olursunuz.</span><span class="sxs-lookup"><span data-stu-id="e5297-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="e5297-136">Örneğin, yeni bir dosya oluşturmak için tıklayın **Dosya -> Yeni**.</span><span class="sxs-lookup"><span data-stu-id="e5297-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="e5297-137">Bunu kaydetmek için tıklatın **Dosya -> Kaydet** ve ardından bir dosya adı, şimdi deyin sağlayın `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="e5297-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="e5297-138">Dosyayı kapatmak için dosya adının yanındaki "x" tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e5297-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="e5297-139">Visual Studio Code, çıkmak için **Dosya -> çıkış**.</span><span class="sxs-lookup"><span data-stu-id="e5297-139">To exit Visual Studio Code, **File->Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="e5297-140">Kısıtlı sistemlerde PowerShell uzantısı yükleniyor</span><span class="sxs-lookup"><span data-stu-id="e5297-140">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="e5297-141">Bazı sistemler, tüm kod imzası gözden geçirilmesini gerektirir ve bu nedenle PowerShell Düzenleyicisi Services'ı el ile sistem üzerinde çalışacak şekilde onaylanması gerekir şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e5297-141">Some systems are set up in a way that requires all code signatures to be checked and thus requires PowerShell Editor Services to be manually approved to run on the system.</span></span>
<span data-ttu-id="e5297-142">PowerShell uzantısı yüklü ancak gibi bir hata ulaşıyor yürütme İlkesi değiştiren bir Grup İlkesi güncelleştirmesini olası bir nedeni:</span><span class="sxs-lookup"><span data-stu-id="e5297-142">A Group Policy update that changes execution policy is a likely cause if you have installed the PowerShell extension but are reaching an error like:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="e5297-143">El ile onaylamanız için bir PowerShell istemi ve çalışma PowerShell Düzenleyicisi Hizmetleri ve bu nedenle VSCode için PowerShell uzantısı açın:</span><span class="sxs-lookup"><span data-stu-id="e5297-143">To manually approve PowerShell Editor Services and thus the PowerShell extension for VSCode open a PowerShell prompt and run:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="e5297-144">"Yazılım bu güvenilmeyen yayımcıdan çalıştırmak istediğiniz yapmak ile?" istenir.</span><span class="sxs-lookup"><span data-stu-id="e5297-144">You are prompted with "Do you want to run software from this untrusted publisher?"</span></span>
<span data-ttu-id="e5297-145">Tür `R` dosyayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e5297-145">Type `R` to run the file.</span></span> <span data-ttu-id="e5297-146">Ardından, Visual Studio Code'u açın ve PowerShell uzantısı düzgün çalışıp çalışmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e5297-146">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="e5297-147">Başlarken konuları hala varsa, üzerinde bize [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="e5297-147">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="e5297-148">Bir uzantıyla kullanılmak üzere PowerShell sürümü seçme</span><span class="sxs-lookup"><span data-stu-id="e5297-148">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="e5297-149">PowerShell Core Windows PowerShell ile yan yana yükleme, artık PowerShell uzantısıyla PowerShell belirli bir sürümünü kullanmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e5297-149">With PowerShell Core installing side-by-side with Windows PowerShell, is it now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="e5297-150">Aşağıdaki sürüm seçmek için aşağıdaki adımları kullanın:</span><span class="sxs-lookup"><span data-stu-id="e5297-150">Use the following these steps to choose the version:</span></span>

1. <span data-ttu-id="e5297-151">Komut paleti açın (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> Windows ve Linux <kbd>Cmd</kbd> + <kbd>Shift</kbd>+<kbd>P</kbd> MacOS).</span><span class="sxs-lookup"><span data-stu-id="e5297-151">Open the command pallet (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on Windows & Linux, <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS).</span></span>
1. <span data-ttu-id="e5297-152">"Oturumu" arayın.</span><span class="sxs-lookup"><span data-stu-id="e5297-152">Search for "Session".</span></span>
1. <span data-ttu-id="e5297-153">Tıklayın "PowerShell: Oturum menüsünü göster:".</span><span class="sxs-lookup"><span data-stu-id="e5297-153">Click on "PowerShell: Show Session Menu".</span></span>
1. <span data-ttu-id="e5297-154">Listeden - Örneğin, "PowerShell Core" kullanmak istediğiniz PowerShell sürümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="e5297-154">Choose the version of PowerShell you want to use from the list - for example, "PowerShell Core".</span></span>

>[!IMPORTANT]
> <span data-ttu-id="e5297-155">Bu özellik, bazı iyi bilinen yollarında farklı işletim PowerShell yükleme konumlarını bulmak için sistemlerinde arar.</span><span class="sxs-lookup"><span data-stu-id="e5297-155">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="e5297-156">PowerShell normal olmayan bir konuma yüklediyseniz, bu ilk oturum menüsünde gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="e5297-156">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="e5297-157">Oturum menüsü tarafından genişletebileceğiniz [kendi özel yollar ekleme](#adding-your-own-powershell-paths-to-the-session-menu) aşağıda açıklandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="e5297-157">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="e5297-158">Oturum menüsüne ulaşmak için başka bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="e5297-158">There is another way to get to the session menu.</span></span> <span data-ttu-id="e5297-159">Bir PowerShell dosyasını, düzenleyicide açık olduğunda, sağ alt bir yeşil sürüm numarası bakın.</span><span class="sxs-lookup"><span data-stu-id="e5297-159">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="e5297-160">Bu sürüm numarası tıklayarak oturum menüsüne çıkarır.</span><span class="sxs-lookup"><span data-stu-id="e5297-160">Clicking this version number will bring you to the session menu.</span></span>

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="e5297-161">Kendi PowerShell yolları oturumu menü ekleme</span><span class="sxs-lookup"><span data-stu-id="e5297-161">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="e5297-162">Bir VS Code ayarı ile oturum menüsüne diğer PowerShell yürütülebilir yollar ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5297-162">You can add other PowerShell executable paths to the session menu through a VS Code setting.</span></span>

<span data-ttu-id="e5297-163">Bir öğeyi listeye eklemek `powershell.powerShellAdditionalExePaths` veya içinde yoksa bir liste oluşturun, `settings.json`:</span><span class="sxs-lookup"><span data-stu-id="e5297-163">Add an item to the list  `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],
    
    // other settings...
}
```

<span data-ttu-id="e5297-164">Her bir öğe olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="e5297-164">Each item must have:</span></span>

* <span data-ttu-id="e5297-165">`exePath`: Yolu `pwsh` veya `powershell` yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="e5297-165">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="e5297-166">`versionName`: Oturum menüde görünür metin.</span><span class="sxs-lookup"><span data-stu-id="e5297-166">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="e5297-167">Kullanarak kullanılacak varsayılan PowerShell sürümünü ayarlayabilirsiniz `powershell.powerShellDefaultVersion` ayarını, bu metinde görünür oturumu menüde (diğer adıyla `versionName` son ayarı):</span><span class="sxs-lookup"><span data-stu-id="e5297-167">You can set the default PowerShell version to use using the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (aka the `versionName` in the last setting):</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],
    
    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",
    
    // other settings...
}
```

<span data-ttu-id="e5297-168">Bu ayar ayarladıktan sonra Visual Studio Code'u yeniden başlatın veya kullanın "Geliştirici: Geçerli vscode pencereyi yeniden penceresi yeniden"komut paleti eylem.</span><span class="sxs-lookup"><span data-stu-id="e5297-168">Once you've set this setting, restart Visual Studio Code or use the the "Developer: Reload Window" command pallet action to reload the current vscode window.</span></span>

<span data-ttu-id="e5297-169">Oturum menüsünü açın, ek PowerShell sürümü artık görürsünüz!</span><span class="sxs-lookup"><span data-stu-id="e5297-169">If you open the session menu, you will now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="e5297-170">Kaynak Powershell'den derleme yaparsanız, yerel PowerShell yapımı test etmek için harika bir yolu budur.</span><span class="sxs-lookup"><span data-stu-id="e5297-170">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="e5297-171">Visual Studio Code için yapılandırma ayarları</span><span class="sxs-lookup"><span data-stu-id="e5297-171">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="e5297-172">Önceki paragrafta adımları kullanarak, yapılandırma ayarlarında ekleyebilirsiniz `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="e5297-172">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="e5297-173">Visual Studio Code için aşağıdaki yapılandırma ayarları öneririz:</span><span class="sxs-lookup"><span data-stu-id="e5297-173">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="e5297-174">Bu ayarlar, tüm dosya türlerini etkilemesini istemiyorsanız VSCode dil başına yapılandırmaları da sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5297-174">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="e5297-175">Ayarları koyarak belirli bir dil ayarı oluşturma bir `[<language-name>]` alan.</span><span class="sxs-lookup"><span data-stu-id="e5297-175">Create a language specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="e5297-176">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e5297-176">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="e5297-177">VS Code'da kodlama dosya hakkında daha fazla bilgi için bkz: [dosya kodlama anlama](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="e5297-177">For more information about file encoding in VS Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="e5297-178">Visual Studio kodu ile hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e5297-178">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="e5297-179">Hayır-çalışma hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e5297-179">No-workspace debugging</span></span>

<span data-ttu-id="e5297-180">Visual Studio Code sürümü 1.9 itibarıyla PowerShell komut dosyasını içeren klasörü açmak zorunda kalmadan PowerShell betikleri hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5297-180">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span> <span data-ttu-id="e5297-181">PowerShell betik dosyasını açın **Dosya -> Dosya Aç...** satırında (F9 tuşuna basın) bir kesme noktası ayarlayın ve ardından hata ayıklamayı başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e5297-181">Open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span> <span data-ttu-id="e5297-182">Hata ayıklayıcı, adım, sürdürme ve hata ayıklamayı durdurmak sonu sağlayan görünen hata ayıklama Eylemler bölmesinde görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5297-182">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="e5297-183">Çalışma hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e5297-183">Workspace debugging</span></span>

<span data-ttu-id="e5297-184">Çalışma hata ayıklama başvuruyor Visual Studio Code kullanarak açılan bir klasörü bağlamında hata ayıklama için **Klasör Aç...**  gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="e5297-184">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="e5297-185">Açtığınız genellikle PowerShell proje klasörünüze ve/veya Git deponuzun kök klasördür.</span><span class="sxs-lookup"><span data-stu-id="e5297-185">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="e5297-186">Bu modda da F5'e basarak o anda seçili PowerShell betik hata ayıklama başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5297-186">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="e5297-187">Ancak, çalışma hata ayıklama, şu anda açık dosya yalnızca hata ayıklama dışında birden çok hata ayıklama yapılandırmaları tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5297-187">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="e5297-188">Örneğin, bir yapılandırmalarına ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e5297-188">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="e5297-189">Hata ayıklayıcı Pester testlerinde başlatın</span><span class="sxs-lookup"><span data-stu-id="e5297-189">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="e5297-190">Belirli bir dosya hata ayıklayıcı bağımsız değişkenleriyle Başlat</span><span class="sxs-lookup"><span data-stu-id="e5297-190">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="e5297-191">Hata ayıklayıcı etkileşimli bir oturum başlatın</span><span class="sxs-lookup"><span data-stu-id="e5297-191">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="e5297-192">Bir PowerShell ana bilgisayar işlemi için hata ayıklayıcının</span><span class="sxs-lookup"><span data-stu-id="e5297-192">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="e5297-193">Hata ayıklama yapılandırma dosyanızı oluşturmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="e5297-193">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="e5297-194">Açık **hata ayıklama** tuşuna basarak görünümü **Ctrl + SHIFT + D** (**Cmd + SHIFT + D** Mac üzerinde).</span><span class="sxs-lookup"><span data-stu-id="e5297-194">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="e5297-195">Tuşuna **yapılandırma** araç çubuğundaki dişli simgesi.</span><span class="sxs-lookup"><span data-stu-id="e5297-195">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="e5297-196">Visual Studio Code ister **ortamı seçin**.</span><span class="sxs-lookup"><span data-stu-id="e5297-196">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="e5297-197">Seçin **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="e5297-197">Choose **PowerShell**.</span></span>

  <span data-ttu-id="e5297-198">Bunu yaptığınızda, Visual Studio Code kullanarak çalışma klasörünüzde kök dizininde bir dizin ve dosya ".vscode\launch.json" oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e5297-198">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="e5297-199">Bu, hata ayıklama yapılandırması depolandığı yerdir.</span><span class="sxs-lookup"><span data-stu-id="e5297-199">This is where your debug configuration is stored.</span></span> <span data-ttu-id="e5297-200">Dosyalarınızı Git deposunda ise genellikle launch.json dosyası işleme istersiniz.</span><span class="sxs-lookup"><span data-stu-id="e5297-200">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="e5297-201">Launch.json dosyasının içeriğini şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e5297-201">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="e5297-202">Bu, hata ayıklama senaryoları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e5297-202">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="e5297-203">Ancak, bu dosya Düzenleyicisi'nde açtığınızda, gördüğünüz bir **Yapılandırması Ekle...**  düğmesi.</span><span class="sxs-lookup"><span data-stu-id="e5297-203">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="e5297-204">Daha fazla PowerShell hata ayıklama yapılandırmaları eklemek için bu düğmeyi basabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5297-204">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="e5297-205">Eklemek için kullanışlı bir yapılandırma **PowerShell: Betiği Başlat**.</span><span class="sxs-lookup"><span data-stu-id="e5297-205">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="e5297-206">Bu yapılandırma ile hangi dosya düzenleyicide şu anda etkin olursa olsun F5 tuşuna basarak her başlatılacak isteğe bağlı bağımsız değişkenler ile belirli bir dosyayı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5297-206">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="e5297-207">Hata ayıklama yapılandırması kurulduktan sonra hata ayıklama oturumu sırasında bir hata ayıklama yapılandırması açılan listesinde seçerek kullanmak istediğiniz yapılandırmayı seçebilirsiniz **hata ayıklama** görünümünün araç çubuğu.</span><span class="sxs-lookup"><span data-stu-id="e5297-207">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="e5297-208">Visual Studio Code için PowerShell uzantısını kullanarak başlamanıza yardımcı olmak yardımcı olabilecek birkaç blogları vardır:</span><span class="sxs-lookup"><span data-stu-id="e5297-208">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="e5297-209">[PowerShell uzantısı][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="e5297-209">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="e5297-210">[Yazma ve PowerShell betikleri Visual Studio code'da Hata Ayıkla][debug]</span><span class="sxs-lookup"><span data-stu-id="e5297-210">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="e5297-211">[Hata ayıklama Visual Studio kod Kılavuzu][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="e5297-211">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="e5297-212">[Visual Studio code'da hata ayıklama PowerShell][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="e5297-212">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="e5297-213">[Visual Studio code'da PowerShell geliştirme ile çalışmaya başlama][getting-started]</span><span class="sxs-lookup"><span data-stu-id="e5297-213">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="e5297-214">[Düzenleme özellikleri PowerShell geliştirme – bölüm 1 için Visual Studio Code][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="e5297-214">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="e5297-215">[Visual Studio kod düzenleme özellikleri PowerShell geliştirme – bölüm 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="e5297-215">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="e5297-216">[Visual Studio Code – bölüm 1 PowerShell betik hata ayıklama][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="e5297-216">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="e5297-217">[Visual Studio Code – bölüm 2 PowerShell betik hata ayıklama][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="e5297-217">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
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

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="e5297-218">Visual Studio Code için PowerShell uzantısı</span><span class="sxs-lookup"><span data-stu-id="e5297-218">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="e5297-219">PowerShell uzantının kaynak kodu bulunabilir [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="e5297-219">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
