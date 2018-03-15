---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery, psget
title: PowerShell Galerisi
ms.openlocfilehash: 7389ce8286c515b0bfc25f32634a482b060cb74c
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="f65ca-103">PowerShell Galerisi</span><span class="sxs-lookup"><span data-stu-id="f65ca-103">The PowerShell Gallery</span></span>

<span data-ttu-id="f65ca-104">PowerShell Galerisi PowerShell içerik için merkezi depodur.</span><span class="sxs-lookup"><span data-stu-id="f65ca-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="f65ca-105">Galeriden yeni PowerShell komutlarını ya da istenen durum Yapılandırması'nı (DSC) kaynakları bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f65ca-105">You can find new PowerShell commands or Desired State Configuration (DSC) resources in the Gallery.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="f65ca-106">PowerShellGet genel bakış</span><span class="sxs-lookup"><span data-stu-id="f65ca-106">PowerShellGet Overview</span></span>

<span data-ttu-id="f65ca-107">PowerShellGet modülü bulmak, yükleme, güncelleştirme ve modülleri, DSC kaynakları, rol özellikleri ve komut dosyalarından gibi PowerShell yapılarını yayımlama yönelik cmdlet'ler içeren [PowerShell Galerisi](https://www.PowerShellGallery.com) ve diğer özel depoları.</span><span class="sxs-lookup"><span data-stu-id="f65ca-107">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="f65ca-108">Galerisi'ni kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="f65ca-108">Getting Started with the Gallery</span></span>

<span data-ttu-id="f65ca-109">Galeriden öğelerini yüklemesi, Windows 10, Windows Management Framework (WMF) 5.0 içinde veya MSI tabanlı Yükleyicisi (PowerShell 3. ve 4) kullanılabilir PowerShellGet modülünün en son sürümünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f65ca-109">Installing items from the Gallery requires the latest version of the PowerShellGet module, which is available in Windows 10, in Windows Management Framework (WMF) 5.0, or in the MSI-based installer (for PowerShell 3 and 4).</span></span>

- <span data-ttu-id="f65ca-110">[**Windows 10 alma**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span><span class="sxs-lookup"><span data-stu-id="f65ca-110">[**Get Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span></span>
- <span data-ttu-id="f65ca-111">[**WMF 5.0 alma**](http://go.microsoft.com/fwlink/?LinkId=398175), veya</span><span class="sxs-lookup"><span data-stu-id="f65ca-111">[**Get WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), or</span></span>
- [<span data-ttu-id="f65ca-112">**MSI yükleyicisi Al**</span><span class="sxs-lookup"><span data-stu-id="f65ca-112">**Get MSI Installer**</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

<span data-ttu-id="f65ca-113">En son [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) modülü, şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f65ca-113">With the latest [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) module, you can:</span></span>

-   <span data-ttu-id="f65ca-114">Arama ile galeri öğeleri aracılığıyla [bulma Modülü](https://go.microsoft.com/fwlink/?LinkId=821658) ve [bulma komut dosyası](https://go.microsoft.com/fwlink/?LinkId=822322)</span><span class="sxs-lookup"><span data-stu-id="f65ca-114">Search through items in the Gallery with [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) and [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)</span></span>
-   <span data-ttu-id="f65ca-115">Öğeleri ile galerisinden sisteminize kaydetmek [Kaydet-Module](https://go.microsoft.com/fwlink/?LinkId=821669) ve [Kaydet-komut dosyası](https://go.microsoft.com/fwlink/?LinkId=822334)</span><span class="sxs-lookup"><span data-stu-id="f65ca-115">Save items to your system from the Gallery with [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) and [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)</span></span>
-   <span data-ttu-id="f65ca-116">Öğeleri ile galerisinden yüklemeyi [yükleme-Module](https://go.microsoft.com/fwlink/?LinkId=821663) ve [yükleme betiği](https://go.microsoft.com/fwlink/?LinkId=822327)</span><span class="sxs-lookup"><span data-stu-id="f65ca-116">Install items from the Gallery with [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) and [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)</span></span>
-   <span data-ttu-id="f65ca-117">İle galeri öğeleri karşıya [Yayımla-Module](https://go.microsoft.com/fwlink/?LinkId=821666) ve [Yayımla-komut dosyası](https://go.microsoft.com/fwlink/?LinkId=822331)</span><span class="sxs-lookup"><span data-stu-id="f65ca-117">Upload items to the Gallery with [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) and [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)</span></span>
-   <span data-ttu-id="f65ca-118">Kendi özel deposuyla eklemek [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)</span><span class="sxs-lookup"><span data-stu-id="f65ca-118">Add your own custom repository with [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)</span></span>

<span data-ttu-id="f65ca-119">Kullanıma [Başlarken](psgallery/psgallery_gettingstarted.md) PowerShellGet komutları Galerisi ile kullanma hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="f65ca-119">Check out the [Getting Started](psgallery/psgallery_gettingstarted.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="f65ca-120">De çalıştırabilirsiniz *Update-Help-modülü PowerShellGet* bu komutları için yerel Yardım yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="f65ca-120">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="f65ca-121">Desteklenen işletim sistemleri</span><span class="sxs-lookup"><span data-stu-id="f65ca-121">Supported Operating Systems</span></span>

<span data-ttu-id="f65ca-122">**PowerShellGet** modülü gerektirir **PowerShell 3.0 veya daha yeni**.</span><span class="sxs-lookup"><span data-stu-id="f65ca-122">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="f65ca-123">Bu nedenle, **PowerShellGet** aşağıdaki işletim sistemlerinden birini gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f65ca-123">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="f65ca-124">Windows 10</span><span class="sxs-lookup"><span data-stu-id="f65ca-124">Windows 10</span></span>
- <span data-ttu-id="f65ca-125">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="f65ca-125">Windows 8.1 Pro</span></span>
- <span data-ttu-id="f65ca-126">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="f65ca-126">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="f65ca-127">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="f65ca-127">Windows 7 SP1</span></span>
- <span data-ttu-id="f65ca-128">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="f65ca-128">Windows Server 2016</span></span>
- <span data-ttu-id="f65ca-129">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="f65ca-129">Windows Server 2012 R2</span></span>
- <span data-ttu-id="f65ca-130">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="f65ca-130">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="f65ca-131">**PowerShellGet** de .NET Framework 4.5 gerektirir veya üstü.</span><span class="sxs-lookup"><span data-stu-id="f65ca-131">**PowerShellGet** also  requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="f65ca-132">.NET Framework 4.5 yükleyebilirsiniz ya da yukarıdaki gelen [burada](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="f65ca-132">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>


## <a name="got-a-question-have-feedback"></a><span data-ttu-id="f65ca-133">Bir soru var mı?</span><span class="sxs-lookup"><span data-stu-id="f65ca-133">Got a question?</span></span> <span data-ttu-id="f65ca-134">Geri bildirim var mı?</span><span class="sxs-lookup"><span data-stu-id="f65ca-134">Have feedback?</span></span>

<span data-ttu-id="f65ca-135">PowerShell Galerisi ve PowerShellGet hakkında daha fazla bilgi bulunabilir [Başlarken](psgallery/psgallery_gettingstarted.md) sayfası.</span><span class="sxs-lookup"><span data-stu-id="f65ca-135">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](psgallery/psgallery_gettingstarted.md) page.</span></span> <span data-ttu-id="f65ca-136">Kullanarak geri bildirim ve rapor sorunlarını lütfen [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="f65ca-136">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>

