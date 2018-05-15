---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery, psget
title: PowerShell Galerisi
ms.openlocfilehash: cffb2f0182ffe9072f9fbbc7f4cdfcf28de276db
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="c3d87-103">PowerShell Galerisi</span><span class="sxs-lookup"><span data-stu-id="c3d87-103">The PowerShell Gallery</span></span>

<span data-ttu-id="c3d87-104">PowerShell Galerisi PowerShell içerik için merkezi depodur.</span><span class="sxs-lookup"><span data-stu-id="c3d87-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="c3d87-105">İçinde PowerShell komutlarını ve istenen durum Yapılandırması'nı (DSC) kaynakları içeren yararlı PowerShell modülleri bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3d87-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="c3d87-106">PowerShell komut dosyaları, bazıları PowerShell iş akışları ve hangi bir dizi görevi anahat içeren ve bu görevler için sıralama sağlamak da bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3d87-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="c3d87-107">Bu öğelerin bazıları, Microsoft tarafından yazılan ve diğerleri PowerShell topluluğu tarafından yazılan.</span><span class="sxs-lookup"><span data-stu-id="c3d87-107">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="c3d87-108">PowerShellGet genel bakış</span><span class="sxs-lookup"><span data-stu-id="c3d87-108">PowerShellGet Overview</span></span>

<span data-ttu-id="c3d87-109">PowerShellGet modülü bulmak, yükleme, güncelleştirme ve modülleri, DSC kaynakları, rol özellikleri ve komut dosyalarından gibi PowerShell yapılarını yayımlama yönelik cmdlet'ler içeren [PowerShell Galerisi](https://www.PowerShellGallery.com) ve diğer özel depoları.</span><span class="sxs-lookup"><span data-stu-id="c3d87-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="c3d87-110">Galerisi'ni kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="c3d87-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="c3d87-111">Galeriden öğeleri yükleme PowerShellGet modülü en son sürümünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c3d87-111">Installing items from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="c3d87-112">Bkz: [yükleme PowerShellGet](installing-psget.md) tam yönergeler için.</span><span class="sxs-lookup"><span data-stu-id="c3d87-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="c3d87-113">Kullanıma [Başlarken](getting-started.md) PowerShellGet komutları Galerisi ile kullanma hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="c3d87-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="c3d87-114">De çalıştırabilirsiniz *Update-Help-modülü PowerShellGet* bu komutları için yerel Yardım yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="c3d87-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="c3d87-115">Desteklenen işletim sistemleri</span><span class="sxs-lookup"><span data-stu-id="c3d87-115">Supported Operating Systems</span></span>

<span data-ttu-id="c3d87-116">**PowerShellGet** modülü gerektirir **PowerShell 3.0 veya daha yeni**.</span><span class="sxs-lookup"><span data-stu-id="c3d87-116">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="c3d87-117">Bu nedenle, **PowerShellGet** aşağıdaki işletim sistemlerinden birini gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c3d87-117">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="c3d87-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="c3d87-118">Windows 10</span></span>
- <span data-ttu-id="c3d87-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="c3d87-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="c3d87-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="c3d87-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="c3d87-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="c3d87-121">Windows 7 SP1</span></span>
- <span data-ttu-id="c3d87-122">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="c3d87-122">Windows Server 2016</span></span>
- <span data-ttu-id="c3d87-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="c3d87-123">Windows Server 2012 R2</span></span>
- <span data-ttu-id="c3d87-124">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="c3d87-124">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="c3d87-125">**PowerShellGet** de .NET Framework 4.5 gerektirir veya üstü.</span><span class="sxs-lookup"><span data-stu-id="c3d87-125">**PowerShellGet** also requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="c3d87-126">.NET Framework 4.5 yükleyebilirsiniz ya da yukarıdaki gelen [burada](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="c3d87-126">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="c3d87-127">Bir soru var mı?</span><span class="sxs-lookup"><span data-stu-id="c3d87-127">Got a question?</span></span> <span data-ttu-id="c3d87-128">Geri bildirim var mı?</span><span class="sxs-lookup"><span data-stu-id="c3d87-128">Have feedback?</span></span>

<span data-ttu-id="c3d87-129">PowerShell Galerisi ve PowerShellGet hakkında daha fazla bilgi bulunabilir [Başlarken](getting-started.md) sayfası.</span><span class="sxs-lookup"><span data-stu-id="c3d87-129">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="c3d87-130">Kullanarak geri bildirim ve rapor sorunlarını lütfen [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="c3d87-130">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>