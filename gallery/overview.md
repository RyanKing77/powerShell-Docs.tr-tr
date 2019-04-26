---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery, psget
title: PowerShell Galerisi
ms.openlocfilehash: d3e3b9d8bb3d6cefd3a3bfe79b012bb1dc1d8a2d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076030"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="05536-103">PowerShell Galerisi</span><span class="sxs-lookup"><span data-stu-id="05536-103">The PowerShell Gallery</span></span>

<span data-ttu-id="05536-104">PowerShell Galerisi, PowerShell içeriği için merkezi depodur.</span><span class="sxs-lookup"><span data-stu-id="05536-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="05536-105">İçinde yararlı PowerShell modülleri PowerShell komutlarını ve Desired State Configuration ' nı (DSC) kaynakları içeren bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05536-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="05536-106">PowerShell betikleri, bazıları PowerShell iş akışları ve bir dizi görevi, anahat içeren ve bu görevler için sıralama sağlamak da bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05536-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="05536-107">Bu paketler bazıları Microsoft tarafından yazılmış ve başkaları PowerShell topluluğu tarafından yazılan.</span><span class="sxs-lookup"><span data-stu-id="05536-107">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="05536-108">PowerShellGet genel bakış</span><span class="sxs-lookup"><span data-stu-id="05536-108">PowerShellGet Overview</span></span>

<span data-ttu-id="05536-109">PowerShellGet modülü bulma, yükleme, güncelleştirme, modüller, DSC kaynakları, rol işlevleri ve komut dosyasından gibi yapıları içeren PowerShell paketleri yayımlama için cmdlet'leri içerir [PowerShell Galerisi](https://www.PowerShellGallery.com)ve diğer özel depolar.</span><span class="sxs-lookup"><span data-stu-id="05536-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell packages which contain artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="05536-110">Galeri ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="05536-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="05536-111">Galeriden paketlerini yükleme PowerShellGet modülünün en son sürümünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="05536-111">Installing packages from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="05536-112">Bkz: [PowerShellGet yükleme](installing-psget.md) eksiksiz yönergeler için.</span><span class="sxs-lookup"><span data-stu-id="05536-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="05536-113">Kullanıma [Başlarken](getting-started.md) galeri ile PowerShellGet komutlarını kullanma hakkında daha fazla bilgi için sayfa.</span><span class="sxs-lookup"><span data-stu-id="05536-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="05536-114">Ayrıca çalıştırabileceğiniz *Update-Help-PowerShellGet Modülü* bu komutları için yerel Yardım'ı yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="05536-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="05536-115">Desteklenen işletim sistemleri</span><span class="sxs-lookup"><span data-stu-id="05536-115">Supported Operating Systems</span></span>

<span data-ttu-id="05536-116">**PowerShellGet** modülü gerektirir **Windows PowerShell 3.0 veya daha yeni**, veya **PowerShell Core 6.0 veya daha yeni**.</span><span class="sxs-lookup"><span data-stu-id="05536-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="05536-117">Uygun bir sürümünü **Windows PowerShell** bu işletim sistemlerinde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="05536-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="05536-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="05536-118">Windows 10</span></span>
- <span data-ttu-id="05536-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="05536-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="05536-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="05536-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="05536-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="05536-121">Windows 7 SP1</span></span>
- <span data-ttu-id="05536-122">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="05536-122">Windows Server 2019</span></span>
- <span data-ttu-id="05536-123">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="05536-123">Windows Server 2016</span></span>
- <span data-ttu-id="05536-124">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="05536-124">Windows Server 2012 R2</span></span>
- <span data-ttu-id="05536-125">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="05536-125">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="05536-126">**PowerShellGet** gerektiren .NET Framework 4.5 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="05536-126">**PowerShellGet** requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="05536-127">.NET Framework 4.5 yüklemek ya da yukarıdaki gelen [burada](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="05536-127">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="05536-128">Bu yana **PowerShell Core** platformlar arası ve Windows, Linux ve Macos'ta çalıştığı anlamına gelir, ayrıca yapıyorsa **PowerShellGet** bu sistemlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="05536-128">Since **PowerShell Core** is cross-platform and that means it works on Windows, Linux and MacOS, that also makes **PowerShellGet** available on those systems.</span></span> <span data-ttu-id="05536-129">Tarafından desteklenen sistemlerinin tam listesi için **PowerShell Core** bkz [PowerShell'i yükleme](/powershell/scripting/setup/installing-powershell).</span><span class="sxs-lookup"><span data-stu-id="05536-129">For a full list of systems supported by **PowerShell Core** see [Installing PowerShell](/powershell/scripting/setup/installing-powershell).</span></span>

<span data-ttu-id="05536-130">Galeride bulunan birçok modülleri, farklı işletim sistemleri destekler ve ek gereksinimleri vardır.</span><span class="sxs-lookup"><span data-stu-id="05536-130">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="05536-131">Modüller için daha fazla bilgi için belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="05536-131">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="05536-132">Bir sorunuz var mı?</span><span class="sxs-lookup"><span data-stu-id="05536-132">Got a question?</span></span> <span data-ttu-id="05536-133">Geri bildirim var mı?</span><span class="sxs-lookup"><span data-stu-id="05536-133">Have feedback?</span></span>

<span data-ttu-id="05536-134">PowerShellGet ve PowerShell Galerisi hakkında daha fazla bilgi bulunabilir [Başlarken](getting-started.md) sayfası.</span><span class="sxs-lookup"><span data-stu-id="05536-134">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="05536-135">Lütfen kullanarak geri bildirim ve rapor sorunlarını sağlayın [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="05536-135">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
