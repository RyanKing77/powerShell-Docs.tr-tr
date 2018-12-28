---
title: Uzaktan düzenleme ve hata ayıklama için Visual Studio Code kullanarak
description: Uzaktan düzenleme ve hata ayıklama için Visual Studio Code kullanarak
ms.date: 08/06/2018
ms.openlocfilehash: bab1a629a7e9dafd5957cf93025abb18b8a4f326
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655545"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="c2258-103">Uzaktan düzenleme ve hata ayıklama için Visual Studio Code kullanarak</span><span class="sxs-lookup"><span data-stu-id="c2258-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="c2258-104">Bu işe ile ilgili bilgi sahibi olduğunuz, çalıştırabilir, hatırlayabilirsiniz `psedit file.ps1` dosyaları - yerel veya uzak - açmak için tümleşik konsoldan ISE'de sağ.</span><span class="sxs-lookup"><span data-stu-id="c2258-104">For those of you that were familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="c2258-105">Bu özellik ayrıca ortaya çıkmıştır gibi PowerShell uzantısı VSCode için kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="c2258-105">As it turns out, this feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="c2258-106">Bu kılavuz, nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c2258-106">This guide will show you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c2258-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c2258-107">Prerequisites</span></span>

<span data-ttu-id="c2258-108">Bu kılavuz, olduğunu varsayar:</span><span class="sxs-lookup"><span data-stu-id="c2258-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="c2258-109">Uzak Kaynak (örn: bir kapsayıcı bir VM) erişimi olmasını</span><span class="sxs-lookup"><span data-stu-id="c2258-109">a remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="c2258-110">Bu ve ana makine üzerinde çalışan PowerShell</span><span class="sxs-lookup"><span data-stu-id="c2258-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="c2258-111">VSCode ve VSCode için PowerShell uzantısı</span><span class="sxs-lookup"><span data-stu-id="c2258-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="c2258-112">Bu özellik, Windows PowerShell ve PowerShell Core üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="c2258-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="c2258-113">Bu özellik, uzak bir makinede WinRM, PowerShell Direct veya SSH üzerinden bağlanırken de çalışır.</span><span class="sxs-lookup"><span data-stu-id="c2258-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="c2258-114">SSH kullanmak istediğiniz, ancak Windows kullanıyorsanız, kullanıma [SSH Win32 sürümünü](https://github.com/PowerShell/Win32-OpenSSH)!</span><span class="sxs-lookup"><span data-stu-id="c2258-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

## <a name="lets-go"></a><span data-ttu-id="c2258-115">Gidelim</span><span class="sxs-lookup"><span data-stu-id="c2258-115">Let's go</span></span>

<span data-ttu-id="c2258-116">Uzaktan düzenleme ve Azure'da çalışan bir Ubuntu VM my MacBook Pro, hata ayıklama aracılığıyla bu bölümde adım geçireceğiz.</span><span class="sxs-lookup"><span data-stu-id="c2258-116">In this section, I'll walk through remote editing and debugging from my MacBook Pro, to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="c2258-117">Ben Windows, kullanmıyor olabilir ancak **işlemi benzerdir**.</span><span class="sxs-lookup"><span data-stu-id="c2258-117">I might not be using Windows, but **the process is identical**.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="c2258-118">Yerel dosya açık EditorFile ile düzenleme</span><span class="sxs-lookup"><span data-stu-id="c2258-118">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="c2258-119">PowerShell uzantısıyla VSCode çalışmaya ve PowerShell tümleştirilmiş bir konsol açıldı, biz yazabilirsiniz `Open-EditorFile foo.ps1` veya `psedit foo.ps1` yerel foo.ps1 dosyanızı doğrudan düzenleyicide açın.</span><span class="sxs-lookup"><span data-stu-id="c2258-119">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Açık EditorFile foo.ps1 yerel olarak çalışır](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> <span data-ttu-id="c2258-121">foo.ps1 önceden var olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c2258-121">foo.ps1 must already exist.</span></span>

<span data-ttu-id="c2258-122">Burada, şunları yapabiliriz:</span><span class="sxs-lookup"><span data-stu-id="c2258-122">From there, we can:</span></span>

<span data-ttu-id="c2258-123">cilt payını için kesme noktaları ekleyebilirsiniz ![kanalını için kesme noktası ekleme](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span><span class="sxs-lookup"><span data-stu-id="c2258-123">add breakpoints to the gutter ![adding breakpoint to gutter](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span></span>

<span data-ttu-id="c2258-124">ve PowerShell komut dosyası hata ayıklamak için F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="c2258-124">and hit F5 to debug the PowerShell script.</span></span>
<span data-ttu-id="c2258-125">![Yerel PowerShell betik hata ayıklama](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span><span class="sxs-lookup"><span data-stu-id="c2258-125">![debugging the PowerShell local script](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span></span>

<span data-ttu-id="c2258-126">Hata ayıklarken hata ayıklama konsol ile etkileşemeyebilirsiniz, sol tarafta, hata ayıklama araçları diğer standart kapsam içinde değişkenlere göz atın.</span><span class="sxs-lookup"><span data-stu-id="c2258-126">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="c2258-127">Uzak dosya açık EditorFile ile düzenleme</span><span class="sxs-lookup"><span data-stu-id="c2258-127">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="c2258-128">Şimdi düzenleme ve hata ayıklama uzak dosya geçelim.</span><span class="sxs-lookup"><span data-stu-id="c2258-128">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="c2258-129">Adımlar neredeyse aynıdır, tek şey ihtiyacımız öncelikle-uzak sunucuya bizim PowerShell oturumu girin.</span><span class="sxs-lookup"><span data-stu-id="c2258-129">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="c2258-130">Bunu yapmak için bir cmdlet için yoktur.</span><span class="sxs-lookup"><span data-stu-id="c2258-130">There's a cmdlet for to do so.</span></span> <span data-ttu-id="c2258-131">Çağrıldığı `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="c2258-131">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="c2258-132">Cmdlet'ini aşağı watered açıklaması verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c2258-132">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="c2258-133">`Enter-PSSession -ComputerName foo` WinRM aracılığıyla bir oturumu başlatır</span><span class="sxs-lookup"><span data-stu-id="c2258-133">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="c2258-134">`Enter-PSSession -ContainerId foo` ve `Enter-PSSession -VmId foo` PowerShell Direct aracılığıyla bir oturumu başlatın</span><span class="sxs-lookup"><span data-stu-id="c2258-134">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="c2258-135">`Enter-PSSession -HostName foo` SSH aracılığıyla bir oturumu başlatır</span><span class="sxs-lookup"><span data-stu-id="c2258-135">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="c2258-136">Daha fazla bilgi için `Enter-PSSession`, belgelere göz atın [burada](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="c2258-136">For more info on `Enter-PSSession`, check out the docs [here](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span></span>

<span data-ttu-id="c2258-137">Azure'da bir Ubuntu sanal makinesi için macOS göstereceğim bu yana miyim uzaktan iletişim için SSH kullanacaklardır.</span><span class="sxs-lookup"><span data-stu-id="c2258-137">I'll be using SSH for remoting since I'm going from macOS to an Ubuntu VM in Azure.</span></span>

<span data-ttu-id="c2258-138">İlk olarak, tümleşik konsolunda bizim Enter-PSSession çalıştıralım.</span><span class="sxs-lookup"><span data-stu-id="c2258-138">First, in the Integrated Console, let's run our Enter-PSSession.</span></span> <span data-ttu-id="c2258-139">Oturumda çünkü olduğunuz anlarsınız `[something]` isteminiz solunda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="c2258-139">You'll know that you're in the session because `[something]` will show up to the left of your prompt.</span></span>

![Enter-PSSession çağrısı](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

<span data-ttu-id="c2258-141">Biz bir yerel komut dosyası düzenleme yaptığınız gibi Burada, uygulanacak adımlar yapabiliriz.</span><span class="sxs-lookup"><span data-stu-id="c2258-141">From there, we can do the exact steps as if we were editing a local script.</span></span>

1. <span data-ttu-id="c2258-142">Çalıştırma `Open-EditorFile test.ps1` veya `psedit test.ps1` uzak açmak için `test.ps1` dosya ![açık-EditorFile test.ps1 dosyası](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span><span class="sxs-lookup"><span data-stu-id="c2258-142">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file ![Open-EditorFile the test.ps1 file](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span></span>
2. <span data-ttu-id="c2258-143">Dosya/set kesme noktaları Düzenle</span><span class="sxs-lookup"><span data-stu-id="c2258-143">Edit the file/set breakpoints</span></span> ![düzenleme, kesme noktaları ayarlama](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. <span data-ttu-id="c2258-145">Uzak dosyanın (F5) hata ayıklamayı Başlat</span><span class="sxs-lookup"><span data-stu-id="c2258-145">Start debugging (F5) the remote file</span></span>

![Uzak dosyanın hata ayıklama](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

<span data-ttu-id="c2258-147">Tüm İşte bu kadar kolay!</span><span class="sxs-lookup"><span data-stu-id="c2258-147">That's all there's to it!</span></span> <span data-ttu-id="c2258-148">Bu kılavuz uzak hata ayıklama ve düzenleme VSCode içinde PowerShell hakkında sorular Temizle'kurmak Yardım umuyoruz.</span><span class="sxs-lookup"><span data-stu-id="c2258-148">We hope that this guide helped clear up any questions about remote debugging and editing PowerShell in VSCode.</span></span>

<span data-ttu-id="c2258-149">Herhangi bir sorun varsa, sorunları açmak buraya dönebilirsiniz [GitHub deposunda](http://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="c2258-149">If you have any problems, feel free to open issues [on the GitHub repo](http://github.com/powershell/vscode-powershell).</span></span>
