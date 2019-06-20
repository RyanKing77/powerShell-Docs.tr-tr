---
title: Uzaktan düzenleme ve hata ayıklama için Visual Studio Code’u kullanma
description: Uzaktan düzenleme ve hata ayıklama için Visual Studio Code’u kullanma
ms.date: 06/13/2019
ms.openlocfilehash: ae3b7a3709498fcd547a48d0849b0dc880217225
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263956"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="37b9b-103">Uzaktan düzenleme ve hata ayıklama için Visual Studio Code’u kullanma</span><span class="sxs-lookup"><span data-stu-id="37b9b-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="37b9b-104">Bu, işe ile ilgili bilgi sahibi olduğunuz, çalıştırabilir, hatırlayabilirsiniz `psedit file.ps1` dosyaları - yerel veya uzak - açmak için tümleşik konsoldan ISE'de sağ.</span><span class="sxs-lookup"><span data-stu-id="37b9b-104">For those of you that are familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="37b9b-105">Bu özellik, VSCode için PowerShell uzantısı'nda da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="37b9b-105">This feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="37b9b-106">Bu kılavuz nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="37b9b-106">This guide shows you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="37b9b-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="37b9b-107">Prerequisites</span></span>

<span data-ttu-id="37b9b-108">Bu kılavuz, olduğunu varsayar:</span><span class="sxs-lookup"><span data-stu-id="37b9b-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="37b9b-109">Uzak Kaynak (örn: bir kapsayıcı bir VM) erişimi olmasını</span><span class="sxs-lookup"><span data-stu-id="37b9b-109">A remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="37b9b-110">Bu ve ana makine üzerinde çalışan PowerShell</span><span class="sxs-lookup"><span data-stu-id="37b9b-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="37b9b-111">VSCode ve VSCode için PowerShell uzantısı</span><span class="sxs-lookup"><span data-stu-id="37b9b-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="37b9b-112">Bu özellik, Windows PowerShell ve PowerShell Core üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="37b9b-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="37b9b-113">Bu özellik, uzak bir makinede WinRM, PowerShell Direct veya SSH üzerinden bağlanırken de çalışır.</span><span class="sxs-lookup"><span data-stu-id="37b9b-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="37b9b-114">SSH kullanmak istediğiniz, ancak Windows kullanıyorsanız, kullanıma [SSH Win32 sürümünü](https://github.com/PowerShell/Win32-OpenSSH)!</span><span class="sxs-lookup"><span data-stu-id="37b9b-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="37b9b-115">`Open-EditorFile` Ve `psedit` komutları yalnızca iş **PowerShell tümleştirilmiş bir konsol** VSCode için PowerShell uzantısı tarafından oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="37b9b-115">The `Open-EditorFile` and `psedit` commands only work in the **PowerShell Integrated Console** created by the PowerShell extension for VSCode.</span></span>

## <a name="usage-examples"></a><span data-ttu-id="37b9b-116">Kullanım örnekleri</span><span class="sxs-lookup"><span data-stu-id="37b9b-116">Usage examples</span></span>

<span data-ttu-id="37b9b-117">Bu örnekler, Azure'da çalışan düzenleme ve bir MacBook Pro Ubuntu sanal makinesi için hata ayıklama uzak gösterir.</span><span class="sxs-lookup"><span data-stu-id="37b9b-117">These examples show remote editing and debugging from a MacBook Pro to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="37b9b-118">Windows üzerinde işlem aynıdır.</span><span class="sxs-lookup"><span data-stu-id="37b9b-118">The process is identical on Windows.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="37b9b-119">Yerel dosya açık EditorFile ile düzenleme</span><span class="sxs-lookup"><span data-stu-id="37b9b-119">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="37b9b-120">PowerShell uzantısıyla VSCode çalışmaya ve PowerShell tümleştirilmiş bir konsol açıldı, biz yazabilirsiniz `Open-EditorFile foo.ps1` veya `psedit foo.ps1` yerel foo.ps1 dosyanızı doğrudan düzenleyicide açın.</span><span class="sxs-lookup"><span data-stu-id="37b9b-120">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Açık EditorFile foo.ps1 yerel olarak çalışır](images/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> <span data-ttu-id="37b9b-122">Dosya `foo.ps1` zaten mevcut olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="37b9b-122">The file `foo.ps1` must already exist.</span></span>

<span data-ttu-id="37b9b-123">Burada, şunları yapabiliriz:</span><span class="sxs-lookup"><span data-stu-id="37b9b-123">From there, we can:</span></span>

- <span data-ttu-id="37b9b-124">Kesme noktası cilt payını için ekleyin</span><span class="sxs-lookup"><span data-stu-id="37b9b-124">Add breakpoints to the gutter</span></span>

  ![kanalını için kesme noktası ekleme](images/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- <span data-ttu-id="37b9b-126">PowerShell komut dosyası hata ayıklamak için F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="37b9b-126">Hit F5 to debug the PowerShell script.</span></span>

  ![Yerel PowerShell betik hata ayıklama](images/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

<span data-ttu-id="37b9b-128">Hata ayıklarken hata ayıklama konsol ile etkileşemeyebilirsiniz, sol tarafta, hata ayıklama araçları diğer standart kapsam içinde değişkenlere göz atın.</span><span class="sxs-lookup"><span data-stu-id="37b9b-128">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="37b9b-129">Uzak dosya açık EditorFile ile düzenleme</span><span class="sxs-lookup"><span data-stu-id="37b9b-129">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="37b9b-130">Şimdi düzenleme ve hata ayıklama uzak dosya geçelim.</span><span class="sxs-lookup"><span data-stu-id="37b9b-130">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="37b9b-131">Adımlar neredeyse aynıdır, tek şey ihtiyacımız öncelikle-uzak sunucuya bizim PowerShell oturumu girin.</span><span class="sxs-lookup"><span data-stu-id="37b9b-131">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="37b9b-132">Bunu yapmak için bir cmdlet için yoktur.</span><span class="sxs-lookup"><span data-stu-id="37b9b-132">There's a cmdlet for to do so.</span></span> <span data-ttu-id="37b9b-133">Çağrıldığı `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="37b9b-133">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="37b9b-134">Cmdlet'ini aşağı watered açıklaması verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="37b9b-134">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="37b9b-135">`Enter-PSSession -ComputerName foo` WinRM aracılığıyla bir oturumu başlatır</span><span class="sxs-lookup"><span data-stu-id="37b9b-135">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="37b9b-136">`Enter-PSSession -ContainerId foo` ve `Enter-PSSession -VmId foo` PowerShell Direct aracılığıyla bir oturumu başlatın</span><span class="sxs-lookup"><span data-stu-id="37b9b-136">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="37b9b-137">`Enter-PSSession -HostName foo` SSH aracılığıyla bir oturumu başlatır</span><span class="sxs-lookup"><span data-stu-id="37b9b-137">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="37b9b-138">Daha fazla bilgi için belgelerine bakın [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="37b9b-138">For more information, see the documentation for [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span></span>

<span data-ttu-id="37b9b-139">MacOS azure'daki bir Ubuntu sanal kullanacağız olduğundan, uzaktan iletişim için SSH kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="37b9b-139">Since we are going from macOS to an Ubuntu VM in Azure, we are using SSH for remoting.</span></span>

<span data-ttu-id="37b9b-140">İlk olarak, tümleşik konsolda Çalıştır `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="37b9b-140">First, in the Integrated Console, run `Enter-PSSession`.</span></span> <span data-ttu-id="37b9b-141">Uzak oturuma bağlı olduğunuz zaman `[<hostname>]` isteminiz soluna kadar gösterir.</span><span class="sxs-lookup"><span data-stu-id="37b9b-141">You're connected to the remote session when `[<hostname>]` shows up to the left of your prompt.</span></span>

![Enter-PSSession çağrısı](images/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

<span data-ttu-id="37b9b-143">Şimdi, biz bir yerel komut dosyasını düzenliyorsanız gibi aynı adımları yapabiliriz.</span><span class="sxs-lookup"><span data-stu-id="37b9b-143">Now, we can do the same steps as if we are editing a local script.</span></span>

1. <span data-ttu-id="37b9b-144">Çalıştırma `Open-EditorFile test.ps1` veya `psedit test.ps1` uzak açmak için `test.ps1` dosyası</span><span class="sxs-lookup"><span data-stu-id="37b9b-144">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file</span></span>

  ![Açık-EditorFile test.ps1 dosyası](images/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. <span data-ttu-id="37b9b-146">Dosya/set kesme noktaları Düzenle</span><span class="sxs-lookup"><span data-stu-id="37b9b-146">Edit the file/set breakpoints</span></span>

   ![düzenleme, kesme noktaları ayarlama](images/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. <span data-ttu-id="37b9b-148">Uzak dosyanın (F5) hata ayıklamayı Başlat</span><span class="sxs-lookup"><span data-stu-id="37b9b-148">Start debugging (F5) the remote file</span></span>

   ![Uzak dosyanın hata ayıklama](images/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

<span data-ttu-id="37b9b-150">Herhangi bir sorun varsa, sorunları açabileceğiniz [GitHub deposunu](https://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="37b9b-150">If you have any problems, you can open issues in the [GitHub repo](https://github.com/powershell/vscode-powershell).</span></span>
