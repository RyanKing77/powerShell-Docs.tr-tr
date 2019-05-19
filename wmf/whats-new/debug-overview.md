---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: PowerShell Betik Hata Ayıklama İyileştirmeleri
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856178"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="8d8d2-103">PowerShell Betik Hata Ayıklama İyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="8d8d2-103">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="8d8d2-104">PowerShell 5.0, hata ayıklama deneyimini geliştiren çeşitli iyileştirmeler içerir.</span><span class="sxs-lookup"><span data-stu-id="8d8d2-104">PowerShell 5.0 includes several improvements that enhance the debugging experience.</span></span>

## <a name="break-all"></a><span data-ttu-id="8d8d2-105">Tümünü Kes</span><span class="sxs-lookup"><span data-stu-id="8d8d2-105">Break All</span></span>

<span data-ttu-id="8d8d2-106">PowerShell ISE ve PowerShell konsolunu artık komut dosyaları çalıştırmak için hata ayıklayıcıyı durdurmak için izin verin.</span><span class="sxs-lookup"><span data-stu-id="8d8d2-106">The PowerShell console and PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="8d8d2-107">Bu, hem yerel hem de uzak oturumlarda çalışır.</span><span class="sxs-lookup"><span data-stu-id="8d8d2-107">This works in both local and remote sessions.</span></span>

<span data-ttu-id="8d8d2-108">Konsolda, basın <kbd>Ctrl</kbd>+<kbd>sonu</kbd>.</span><span class="sxs-lookup"><span data-stu-id="8d8d2-108">In the console, press <kbd>Ctrl</kbd>+<kbd>Break</kbd>.</span></span>

<span data-ttu-id="8d8d2-109">ISE'de basın <kbd>Ctrl</kbd>+<kbd>B</kbd>, veya **hata ayıklama -> Tümünü Kes** menü komutu.</span><span class="sxs-lookup"><span data-stu-id="8d8d2-109">In ISE, press <kbd>Ctrl</kbd>+<kbd>B</kbd>, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a><span data-ttu-id="8d8d2-110">Uzaktan hata ayıklama ve PowerShell ISE'de uzaktan dosya düzenleme</span><span class="sxs-lookup"><span data-stu-id="8d8d2-110">Remote debugging and remote file editing in PowerShell ISE</span></span>

<span data-ttu-id="8d8d2-111">PowerShell ISE'de artık, dosyaları açabilir ve uzak bir oturumda PSEdit komutuna çalıştırarak düzenleyebilirsiniz olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8d8d2-111">PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="8d8d2-112">Örneğin, komut satırından aşağıdaki gibi uzak bir oturumda düzenlemek için bir dosya açabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8d8d2-112">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="8d8d2-113">Ayrıca, artık düzenleyebilir ve değişiklikleri bir kesme noktasına ulaştığınızda, PowerShell ISE'de otomatik olarak açılmış uzak bir dosyaya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="8d8d2-113">In addition, you can now edit and save changes in a remote file that is automatically opened in PowerShell ISE when you hit a breakpoint.</span></span> <span data-ttu-id="8d8d2-114">Şimdi, uzak bir bilgisayarda çalışan bir komut dosyası hata ayıklama, ortaya çıkan hata düzeltildi ve değiştirilmiş betiği yeniden dosyasını düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="8d8d2-114">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="8d8d2-115">Gelişmiş komut dosyası hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="8d8d2-115">Advanced Script Debugging</span></span>

<span data-ttu-id="8d8d2-116">PowerShell yüklü herhangi bir yerel bilgisayar işleme eklemesine ve rastgele çalışma alanları bu işlemde hata ayıklama izin veren yeni, Gelişmiş hata ayıklama özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="8d8d2-116">There are new, advanced debugging features that let you attach to any local computer process that has loaded PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="8d8d2-117">Çalışma hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="8d8d2-117">Runspace Debugging</span></span>

<span data-ttu-id="8d8d2-118">İşlemin geçerli çalışma alanlarını listelemek ve betik hata ayıklama için bu çalışma PowerShell konsolu veya PowerShell ISE hata ayıklayıcı iliştirmek izin veren yeni cmdlet'ler eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="8d8d2-118">New cmdlets have been added that let you list current runspaces in a process, and attach the PowerShell console or PowerShell ISE debugger to that runspace for script debugging:</span></span>

- <span data-ttu-id="8d8d2-119">Get-çalışma</span><span class="sxs-lookup"><span data-stu-id="8d8d2-119">Get-Runspace</span></span>
- <span data-ttu-id="8d8d2-120">Hata ayıklama çalışma</span><span class="sxs-lookup"><span data-stu-id="8d8d2-120">Debug-Runspace</span></span>
- <span data-ttu-id="8d8d2-121">RunspaceDebug etkinleştir</span><span class="sxs-lookup"><span data-stu-id="8d8d2-121">Enable-RunspaceDebug</span></span>
- <span data-ttu-id="8d8d2-122">RunspaceDebug devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="8d8d2-122">Disable-RunspaceDebug</span></span>
- <span data-ttu-id="8d8d2-123">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="8d8d2-123">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="8d8d2-124">PowerShell barındırma işleme</span><span class="sxs-lookup"><span data-stu-id="8d8d2-124">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="8d8d2-125">Artık PowerShell yüklü olan herhangi bir bilgisayar işleme iliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d8d2-125">You can now attach to any computer process that has PowerShell loaded.</span></span> <span data-ttu-id="8d8d2-126">Ana bilgisayar işlemi ile etkileşimli bir oturum içine girerek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d8d2-126">You do this by entering into an interactive session with the host process.</span></span> <span data-ttu-id="8d8d2-127">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="8d8d2-127">For more information, see:</span></span>

- [<span data-ttu-id="8d8d2-128">PSHostProcess girin</span><span class="sxs-lookup"><span data-stu-id="8d8d2-128">Enter-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [<span data-ttu-id="8d8d2-129">Çıkış PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="8d8d2-129">Exit-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
