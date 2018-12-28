---
title: Visual Studio code'da ISE deneyimi çoğaltma
description: Visual Studio code'da ISE deneyimi çoğaltma
ms.date: 08/06/2018
ms.openlocfilehash: 0ac38985a842a0dfc6118d0ae7116d12e1579daf
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655538"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="c1482-103">Visual Studio code'da ISE deneyimi çoğaltma</span><span class="sxs-lookup"><span data-stu-id="c1482-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="c1482-104">VSCode için PowerShell uzantısı tam özellik eşliği PowerShell ISE ile arama değildir, ancak özellikler mevcuttur VSCode deneyimi ISE kullanıcılar için daha doğal hale getirmek için bir yerde.</span><span class="sxs-lookup"><span data-stu-id="c1482-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="c1482-105">Bu belge, kullanıcı deneyimini ISE'ye kıyasla biraz daha tanıdık yapmak için VSCode yapılandırabileceğiniz listesi ayarları dener.</span><span class="sxs-lookup"><span data-stu-id="c1482-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="c1482-106">Tuş bağlamaları</span><span class="sxs-lookup"><span data-stu-id="c1482-106">Key bindings</span></span>

| <span data-ttu-id="c1482-107">İşlev</span><span class="sxs-lookup"><span data-stu-id="c1482-107">Function</span></span>                              | <span data-ttu-id="c1482-108">ISE bağlama</span><span class="sxs-lookup"><span data-stu-id="c1482-108">ISE Binding</span></span>                  | <span data-ttu-id="c1482-109">VSCode bağlama</span><span class="sxs-lookup"><span data-stu-id="c1482-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="c1482-110">Kesme ve hata ayıklayıcı kesme</span><span class="sxs-lookup"><span data-stu-id="c1482-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="c1482-111"><kbd>CTRL</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="c1482-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="c1482-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="c1482-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="c1482-113">Geçerli satır ve vurgulanan metin yürütün</span><span class="sxs-lookup"><span data-stu-id="c1482-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="c1482-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="c1482-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="c1482-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="c1482-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="c1482-116">Kullanılabilir kod parçacıkları listesi</span><span class="sxs-lookup"><span data-stu-id="c1482-116">List available snippets</span></span>               | <span data-ttu-id="c1482-117"><kbd>CTRL</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="c1482-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="c1482-118"><kbd>CTRL</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="c1482-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="c1482-119">Özel anahtar bağlamaları</span><span class="sxs-lookup"><span data-stu-id="c1482-119">Custom Key bindings</span></span>

<span data-ttu-id="c1482-120">Yapabilecekleriniz [kendi tuş bağlamaları yapılandırma](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) de VSCode içinde.</span><span class="sxs-lookup"><span data-stu-id="c1482-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="c1482-121">Sekme tamamlama</span><span class="sxs-lookup"><span data-stu-id="c1482-121">Tab completion</span></span>

<span data-ttu-id="c1482-122">Daha fazla ISE benzeri sekme tamamlamayı etkinleştirmek için bu ayarı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c1482-122">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> <span data-ttu-id="c1482-123">Bu ayar, doğrudan VSCode (yerine uzantısında) eklendi.</span><span class="sxs-lookup"><span data-stu-id="c1482-123">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="c1482-124">Davranışını VSCode tarafından doğrudan belirlenir ve uzantısı tarafından değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="c1482-124">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="c1482-125">Hiçbir yürütülürken konsol odaklanır</span><span class="sxs-lookup"><span data-stu-id="c1482-125">No focus on console when executing</span></span>

<span data-ttu-id="c1482-126">İle yürütürken odağı düzenleyiciye tutmak <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="c1482-126">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="c1482-127">Varsayılan değer `true` erişilebilmesi için.</span><span class="sxs-lookup"><span data-stu-id="c1482-127">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="c1482-128">Tümleşik bir konsol başlangıçta başlatma</span><span class="sxs-lookup"><span data-stu-id="c1482-128">Don't start integrated console on startup</span></span>

<span data-ttu-id="c1482-129">Başlatma sırasında tümleşik bir konsol durdurmak için aşağıdakileri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="c1482-129">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="c1482-130">Arka plan PowerShell işlem hala sağlayan bu yana IntelliSense, kod analizi, sembol gezintisini vb. başlar. Ancak, konsolda gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="c1482-130">The background PowerShell process will still start since that provides intellisense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="c1482-131">Dosyalar varsayılan olarak PowerShell olduğu varsayılır</span><span class="sxs-lookup"><span data-stu-id="c1482-131">Assume files are PowerShell by default</span></span>

<span data-ttu-id="c1482-132">Yeni/adsız dosyaları hale getirmek için varsayılan PowerShell kaydedin:</span><span class="sxs-lookup"><span data-stu-id="c1482-132">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a><span data-ttu-id="c1482-133">Renk şeması</span><span class="sxs-lookup"><span data-stu-id="c1482-133">Color scheme</span></span>

<span data-ttu-id="c1482-134">ISE Temalar sayısı ISE gibi çok daha düzenleyiciniz VSCode için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c1482-134">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="c1482-135">İçinde [komut paleti] türü `theme` almak için `Preferences: Color Theme` basın <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="c1482-135">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="c1482-136">Aşağı açılan listesinde seçin `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="c1482-136">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="c1482-137">Bu tema ayarlarla ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c1482-137">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="c1482-138">PowerShell komut Gezgini</span><span class="sxs-lookup"><span data-stu-id="c1482-138">PowerShell Command Explorer</span></span>

<span data-ttu-id="c1482-139">Çalışması sayesinde [ @corbob ](https://github.com/corbob), kendi komut explorer'ın beginnings PowerShell uzantısına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c1482-139">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="c1482-140">İçinde [komut paleti], girin `PowerShell Command Explorer` basın <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="c1482-140">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="c1482-141">ISE Aç</span><span class="sxs-lookup"><span data-stu-id="c1482-141">Open in the ISE</span></span>

<span data-ttu-id="c1482-142">Yine de ISE'de bir dosyayı açmaya isteyen gerekmesi halinde kullanabileceğiniz <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="c1482-142">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="c1482-143">Diğer kaynaklar</span><span class="sxs-lookup"><span data-stu-id="c1482-143">Other resources</span></span>

- <span data-ttu-id="c1482-144">4sysops sahip [harika bir makale](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) VSCode ISE gibi daha fazla olacak şekilde yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="c1482-144">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="c1482-145">Mike F Robbins sahip [harika bir gönderi](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) VSCode ayarlama.</span><span class="sxs-lookup"><span data-stu-id="c1482-145">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="c1482-146">PowerShell sahip öğrenin [yukarı mükemmel bir yazma](https://www.learnpwsh.com/setup-vs-code-for-powershell/) VSCode Forms'dan kurulumu için PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1482-146">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="c1482-147">Daha fazla ayar</span><span class="sxs-lookup"><span data-stu-id="c1482-147">More settings</span></span>

<span data-ttu-id="c1482-148">ISE kullanıcılar için daha tanıdık gelmeli VSCode yapmak için daha fazla şekilde biliyorsanız, bu belge için katkıda bulunur. Aradığınız bir uyumluluk yapılandırma yoktur ancak bunu etkinleştirmek için herhangi bir şekilde bulunamıyor [bir sorun açın](https://github.com/PowerShell/vscode-powershell/issues/new/choose) hemen isteyin!</span><span class="sxs-lookup"><span data-stu-id="c1482-148">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="c1482-149">Her zaman çekme istekleri ve Katkıları da kabul olmaktan mutluluk duyarız!</span><span class="sxs-lookup"><span data-stu-id="c1482-149">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="c1482-150">VSCode ipuçları</span><span class="sxs-lookup"><span data-stu-id="c1482-150">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="c1482-151">Komut paleti</span><span class="sxs-lookup"><span data-stu-id="c1482-151">Command Palette</span></span>

<span data-ttu-id="c1482-152"><kbd>F1</kbd> veya <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> Kaydırma</kbd>+<kbd>P</kbd> macOS üzerinde)</span><span class="sxs-lookup"><span data-stu-id="c1482-152"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="c1482-153">VSCode içinde komut yürütmenin kurmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1482-153">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="c1482-154">Daha fazla bilgi için [VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="c1482-154">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Komut paleti]: #command-palette
[Command Palette]: #command-palette
