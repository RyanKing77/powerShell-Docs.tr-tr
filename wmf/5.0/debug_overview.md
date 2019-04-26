---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 22a027ebc97e15075980bc77ce272d8ecdae0b5f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058675"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="bfb60-102">PowerShell Betik Hata Ayıklama İyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="bfb60-102">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="bfb60-103">Hata ayıklama deneyimini geliştirmek için PowerShell 5. 0'iyileştirmeler yapılmıştır:</span><span class="sxs-lookup"><span data-stu-id="bfb60-103">A number of improvements were made in PowerShell 5.0 to enhance the debugging experience:</span></span>

## <a name="break-all"></a><span data-ttu-id="bfb60-104">Tümünü Kes</span><span class="sxs-lookup"><span data-stu-id="bfb60-104">Break All</span></span>

<span data-ttu-id="bfb60-105">Artık PowerShell konsolunu ve Windows PowerShell ISE, komut dosyaları çalıştırmak için hata ayıklayıcıya girdikten olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="bfb60-105">The PowerShell console and Windows PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="bfb60-106">Bu, hem yerel hem de uzak oturumlarda çalışır.</span><span class="sxs-lookup"><span data-stu-id="bfb60-106">This works in both local and remote sessions.</span></span>

<span data-ttu-id="bfb60-107">Konsolda, basın **Ctrl + Break**.</span><span class="sxs-lookup"><span data-stu-id="bfb60-107">In the console, press **Ctrl+Break**.</span></span>

<span data-ttu-id="bfb60-108">ISE'de basın **Ctrl + B**, veya **hata ayıklama -> Tümünü Kes** menü komutu.</span><span class="sxs-lookup"><span data-stu-id="bfb60-108">In ISE, press **Ctrl+B**, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a><span data-ttu-id="bfb60-109">Uzaktan hata ayıklama ve Windows PowerShell ISE'de uzaktan dosya düzenleme</span><span class="sxs-lookup"><span data-stu-id="bfb60-109">Remote debugging and remote file editing in Windows PowerShell ISE</span></span>

<span data-ttu-id="bfb60-110">Windows PowerShell ISE'de artık, dosyaları açabilir ve uzak bir oturumda PSEdit komutuna çalıştırarak düzenleyebilirsiniz olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="bfb60-110">Windows PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="bfb60-111">Örneğin, komut satırından aşağıdaki gibi uzak bir oturumda düzenlemek için bir dosya açabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bfb60-111">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="bfb60-112">Ayrıca, artık düzenleyebilir ve değişiklikleri bir kesme noktasına ulaştığınızda, Windows PowerShell ISE'de otomatik olarak açılmış uzak bir dosyaya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="bfb60-112">In addition, you can now edit and save changes in a remote file that is automatically opened in Windows PowerShell ISE when you hit a breakpoint.</span></span>
<span data-ttu-id="bfb60-113">Şimdi, uzak bir bilgisayarda çalışan bir komut dosyası hata ayıklama, ortaya çıkan hata düzeltildi ve değiştirilmiş betiği yeniden dosyasını düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="bfb60-113">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="bfb60-114">Gelişmiş komut dosyası hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="bfb60-114">Advanced Script Debugging</span></span>

<span data-ttu-id="bfb60-115">Windows PowerShell yüklü herhangi bir yerel bilgisayar işleme eklemesine ve rastgele çalışma alanları bu işlemde hata ayıklama izin veren yeni, Gelişmiş hata ayıklama özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="bfb60-115">There are new, advanced debugging features that let you attach to any local computer process that has loaded Windows PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="bfb60-116">Çalışma hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="bfb60-116">Runspace Debugging</span></span>

<span data-ttu-id="bfb60-117">İşlemin geçerli çalışma alanlarını listelemek ve ISE hata ayıklayıcı ve Windows PowerShell Konsolu komut dosyası hata ayıklama için bu çalışma alanı ekleme izin veren yeni cmdlet'ler eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="bfb60-117">New cmdlets have been added that let you list current runspaces in a process, and attach the Windows PowerShell console or ISE debugger to that runspace for script debugging:</span></span>

-   <span data-ttu-id="bfb60-118">Get-çalışma</span><span class="sxs-lookup"><span data-stu-id="bfb60-118">Get-Runspace</span></span>
-   <span data-ttu-id="bfb60-119">Hata ayıklama çalışma</span><span class="sxs-lookup"><span data-stu-id="bfb60-119">Debug-Runspace</span></span>
-   <span data-ttu-id="bfb60-120">RunspaceDebug etkinleştir</span><span class="sxs-lookup"><span data-stu-id="bfb60-120">Enable-RunspaceDebug</span></span>
-   <span data-ttu-id="bfb60-121">RunspaceDebug devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="bfb60-121">Disable-RunspaceDebug</span></span>
-   <span data-ttu-id="bfb60-122">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="bfb60-122">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="bfb60-123">PowerShell barındırma işleme</span><span class="sxs-lookup"><span data-stu-id="bfb60-123">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="bfb60-124">Artık Windows PowerShell yüklü olan herhangi bir bilgisayar işleme iliştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="bfb60-124">You can now attach to any computer process that has Windows PowerShell loaded.</span></span> <span data-ttu-id="bfb60-125">Bunun için etkileşimli bir oturum ile nasıl Enter-PSSession cmdlet'i çalıştırarak etkileşimli bir uzak oturuma girmek için benzer şekilde, işlem içine girerek:</span><span class="sxs-lookup"><span data-stu-id="bfb60-125">You do this by entering into an interactive session with the process, similarly to how you enter into an interactive remote session by running the Enter-PSSession cmdlet:</span></span>

-   <span data-ttu-id="bfb60-126">PSHostProcess girin</span><span class="sxs-lookup"><span data-stu-id="bfb60-126">Enter-PSHostProcess</span></span>
-   <span data-ttu-id="bfb60-127">Çıkış PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="bfb60-127">Exit-PSHostProcess</span></span>
