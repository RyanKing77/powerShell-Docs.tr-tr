---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery, psget
title: PowerShell Galerisi
ms.openlocfilehash: dc7e8dd7e4d96d8424a62cb3256c3164b63a3684
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482939"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="8144f-103">PowerShell Galerisi</span><span class="sxs-lookup"><span data-stu-id="8144f-103">The PowerShell Gallery</span></span>

<span data-ttu-id="8144f-104">PowerShell Galerisi PowerShell içerik için merkezi depodur.</span><span class="sxs-lookup"><span data-stu-id="8144f-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="8144f-105">İçinde PowerShell komutlarını ve istenen durum Yapılandırması'nı (DSC) kaynakları içeren yararlı PowerShell modülleri bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8144f-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="8144f-106">PowerShell komut dosyaları, bazıları PowerShell iş akışları ve hangi bir dizi görevi anahat içeren ve bu görevler için sıralama sağlamak da bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8144f-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="8144f-107">Bu öğelerin bazıları, Microsoft tarafından yazılan ve diğerleri PowerShell topluluğu tarafından yazılan.</span><span class="sxs-lookup"><span data-stu-id="8144f-107">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="8144f-108">PowerShellGet genel bakış</span><span class="sxs-lookup"><span data-stu-id="8144f-108">PowerShellGet Overview</span></span>

<span data-ttu-id="8144f-109">PowerShellGet modülü bulmak, yükleme, güncelleştirme ve modülleri, DSC kaynakları, rol özellikleri ve komut dosyalarından gibi PowerShell yapılarını yayımlama yönelik cmdlet'ler içeren [PowerShell Galerisi](https://www.PowerShellGallery.com) ve diğer özel depoları.</span><span class="sxs-lookup"><span data-stu-id="8144f-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="8144f-110">Galerisi'ni kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="8144f-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="8144f-111">Galeriden öğeleri yükleme PowerShellGet modülü en son sürümünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8144f-111">Installing items from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="8144f-112">Bkz: [yükleme PowerShellGet](installing-psget.md) tam yönergeler için.</span><span class="sxs-lookup"><span data-stu-id="8144f-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="8144f-113">Kullanıma [Başlarken](getting-started.md) PowerShellGet komutları Galerisi ile kullanma hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="8144f-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="8144f-114">De çalıştırabilirsiniz *Update-Help-modülü PowerShellGet* bu komutları için yerel Yardım yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="8144f-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="8144f-115">Desteklenen işletim sistemleri</span><span class="sxs-lookup"><span data-stu-id="8144f-115">Supported Operating Systems</span></span>

<span data-ttu-id="8144f-116">**PowerShellGet** modülü gerektirir **Windows PowerShell 3.0 veya daha yeni**, veya **PowerShell çekirdek 6.0 veya daha yeni**.</span><span class="sxs-lookup"><span data-stu-id="8144f-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="8144f-117">Uygun bir sürümünü **Windows PowerShell** bu işletim sistemleri için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="8144f-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="8144f-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="8144f-118">Windows 10</span></span>
- <span data-ttu-id="8144f-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="8144f-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="8144f-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="8144f-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="8144f-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="8144f-121">Windows 7 SP1</span></span>
- <span data-ttu-id="8144f-122">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="8144f-122">Windows Server 2016</span></span>
- <span data-ttu-id="8144f-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="8144f-123">Windows Server 2012 R2</span></span>
- <span data-ttu-id="8144f-124">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="8144f-124">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="8144f-125">**PowerShellGet** de .NET Framework 4.5 gerektirir veya üstü.</span><span class="sxs-lookup"><span data-stu-id="8144f-125">**PowerShellGet** also requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="8144f-126">.NET Framework 4.5 yükleyebilirsiniz ya da yukarıdaki gelen [burada](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="8144f-126">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="8144f-127">**PowerShell çekirdek** birçok işletim sistemlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="8144f-127">**PowerShell Core** supports many operating systems.</span></span> <span data-ttu-id="8144f-128">Bkz: [bu makalede](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/) tam listesi için.</span><span class="sxs-lookup"><span data-stu-id="8144f-128">See [this article](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/) for a full list.</span></span>

<span data-ttu-id="8144f-129">Birçok modül galeride barındırılan, farklı işletim sistemleri destekler ve ek gereksinimleri vardır.</span><span class="sxs-lookup"><span data-stu-id="8144f-129">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="8144f-130">Lütfen daha fazla bilgi için modülleri için belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="8144f-130">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="8144f-131">Bir soru var mı?</span><span class="sxs-lookup"><span data-stu-id="8144f-131">Got a question?</span></span> <span data-ttu-id="8144f-132">Geri bildirim var mı?</span><span class="sxs-lookup"><span data-stu-id="8144f-132">Have feedback?</span></span>

<span data-ttu-id="8144f-133">PowerShell Galerisi ve PowerShellGet hakkında daha fazla bilgi bulunabilir [Başlarken](getting-started.md) sayfası.</span><span class="sxs-lookup"><span data-stu-id="8144f-133">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="8144f-134">Kullanarak geri bildirim ve rapor sorunlarını lütfen [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="8144f-134">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
