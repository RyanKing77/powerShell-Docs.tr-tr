---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9ead27fd5d4f146e9062488c1c8cc22a073b922e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187111"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="bdf3e-102">PowerShell Betik Hata Ayıklama İyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="bdf3e-102">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="bdf3e-103">Bazı geliştirmeler, hata ayıklama deneyimini geliştirmek için PowerShell 5. 0 ' yapıldı:</span><span class="sxs-lookup"><span data-stu-id="bdf3e-103">A number of improvements were made in PowerShell 5.0 to enhance the debugging experience:</span></span>

## <a name="break-all"></a><span data-ttu-id="bdf3e-104">Tüm bölün</span><span class="sxs-lookup"><span data-stu-id="bdf3e-104">Break All</span></span>

<span data-ttu-id="bdf3e-105">PowerShell konsolunda ve Windows PowerShell ISE artık betikleri çalıştırmak için hata ayıklayıcısında araya girmektir olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="bdf3e-105">The PowerShell console and Windows PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="bdf3e-106">Bu, hem yerel hem de uzak oturumlarda çalışır.</span><span class="sxs-lookup"><span data-stu-id="bdf3e-106">This works in both local and remote sessions.</span></span>

<span data-ttu-id="bdf3e-107">Konsolda basın **Ctrl + Break**.</span><span class="sxs-lookup"><span data-stu-id="bdf3e-107">In the console, press **Ctrl+Break**.</span></span>

<span data-ttu-id="bdf3e-108">ISE içinde basın **Ctrl + B**, veya kullanmak **hata ayıklama -> bölün tüm** menü komutu.</span><span class="sxs-lookup"><span data-stu-id="bdf3e-108">In ISE, press **Ctrl+B**, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a><span data-ttu-id="bdf3e-109">Uzaktan hata ayıklama ve Windows PowerShell ISE uzaktan dosya düzenleme</span><span class="sxs-lookup"><span data-stu-id="bdf3e-109">Remote debugging and remote file editing in Windows PowerShell ISE</span></span>

<span data-ttu-id="bdf3e-110">Windows PowerShell ISE şimdi açın ve PSEdit komutunu çalıştırarak uzak bir oturumda dosyaları düzenlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="bdf3e-110">Windows PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="bdf3e-111">Örneğin, komut satırından aşağıdaki gibi uzak bir oturumda düzenlemek için bir dosya açabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bdf3e-111">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="bdf3e-112">Ayrıca, artık düzenleyebilir ve değişiklikleri bir kesme noktası isabet yükleyen Windows PowerShell ISE açıldığında otomatik olarak uzak bir dosyaya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="bdf3e-112">In addition, you can now edit and save changes in a remote file that is automatically opened in Windows PowerShell ISE when you hit a breakpoint.</span></span>
<span data-ttu-id="bdf3e-113">Şimdi, uzak bir bilgisayarda çalışan bir komut dosyası hata ayıklama, hata düzeltme ve değiştirilen komut dosyası yeniden dosyasını düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="bdf3e-113">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="bdf3e-114">Gelişmiş komut dosyası hata ayıklaması</span><span class="sxs-lookup"><span data-stu-id="bdf3e-114">Advanced Script Debugging</span></span>

<span data-ttu-id="bdf3e-115">Windows PowerShell yükledi herhangi bir yerel bilgisayarda işlem ekleyin ve bu işlem rasgele alanlarında hata ayıklama izin veren yeni, Gelişmiş hata ayıklama özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="bdf3e-115">There are new, advanced debugging features that let you attach to any local computer process that has loaded Windows PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="bdf3e-116">Çalışma hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="bdf3e-116">Runspace Debugging</span></span>

<span data-ttu-id="bdf3e-117">İşlemin geçerli çalışma alanlarını listelemek ve komut dosyası hata ayıklama için bu çalışma alanı Windows PowerShell konsolu veya işe hata ayıklayıcı ekleme imkan sağlayan yeni cmdlet'ler eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="bdf3e-117">New cmdlets have been added that let you list current runspaces in a process, and attach the Windows PowerShell console or ISE debugger to that runspace for script debugging:</span></span>

-   <span data-ttu-id="bdf3e-118">Get-çalışma</span><span class="sxs-lookup"><span data-stu-id="bdf3e-118">Get-Runspace</span></span>
-   <span data-ttu-id="bdf3e-119">Hata ayıklama çalışma</span><span class="sxs-lookup"><span data-stu-id="bdf3e-119">Debug-Runspace</span></span>
-   <span data-ttu-id="bdf3e-120">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="bdf3e-120">Enable-RunspaceDebug</span></span>
-   <span data-ttu-id="bdf3e-121">RunspaceDebug devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="bdf3e-121">Disable-RunspaceDebug</span></span>
-   <span data-ttu-id="bdf3e-122">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="bdf3e-122">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="bdf3e-123">PowerShell barındırma işlem ekleme</span><span class="sxs-lookup"><span data-stu-id="bdf3e-123">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="bdf3e-124">Windows PowerShell yüklü olan herhangi bir bilgisayarda işlem şimdi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdf3e-124">You can now attach to any computer process that has Windows PowerShell loaded.</span></span> <span data-ttu-id="bdf3e-125">Etkileşimli oturum işlemine nasıl Enter-PSSession cmdlet'i çalıştırarak etkileşimli bir uzak oturuma girin benzer şekilde, içine girerek yapın:</span><span class="sxs-lookup"><span data-stu-id="bdf3e-125">You do this by entering into an interactive session with the process, similarly to how you enter into an interactive remote session by running the Enter-PSSession cmdlet:</span></span>

-   <span data-ttu-id="bdf3e-126">Girin PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="bdf3e-126">Enter-PSHostProcess</span></span>
-   <span data-ttu-id="bdf3e-127">Çıkış PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="bdf3e-127">Exit-PSHostProcess</span></span>
