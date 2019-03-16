---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: Galeri, powershell, cmdlet, psgallery
title: Paketler uyumlu PowerShell sürümleri veya işletim sistemi
ms.openlocfilehash: 14038aa9b0453e1d06e6587e97da391b56297c75
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057187"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a><span data-ttu-id="b852d-103">PowerShell sürümleri veya işletim sistemleriyle uyumlu paketleri</span><span class="sxs-lookup"><span data-stu-id="b852d-103">Packages with compatible PowerShell Editions or Operating Systems</span></span>

<span data-ttu-id="b852d-104">5.1 sürümünden itibaren PowerShell çeşitli özellik kümelerini ve platform uyumluluğunu belirten farklı sürümler halinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b852d-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibilities.</span></span>

## <a name="searching-by-powershell-edition"></a><span data-ttu-id="b852d-105">PowerShell sürümüne göre arama</span><span class="sxs-lookup"><span data-stu-id="b852d-105">Searching by PowerShell Edition</span></span>

<span data-ttu-id="b852d-106">PowerShell'ın iki sürümü vardır:</span><span class="sxs-lookup"><span data-stu-id="b852d-106">The two editions of PowerShell are:</span></span>
- <span data-ttu-id="b852d-107">**Masaüstü sürümü:** .NET Framework üzerine inşa edilmiş ve Windows Masaüstü ve Windows Server Core gibi tam boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="b852d-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="b852d-108">**Çekirdek sürümü:** .NET Core üzerine yapılandırılan ve Nano Server gibi Windows ve Windows IOT azaltılmış boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="b852d-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="b852d-109">PowerShell Galerisi özel PowerShell sürümleri için paketler uyumlu filtrelemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b852d-109">PowerShell Gallery allows you to filter packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="b852d-110">Bir paket uyumlu varsa pseditions'ı, belirtilen 'PowerShell sürümleri' bir parçası olarak listelenen paketi görüntüleme sayfasında hem de paketleri sonuçları.</span><span class="sxs-lookup"><span data-stu-id="b852d-110">If a package has compatible PSEditions specified, they are listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>
<span data-ttu-id="b852d-111">PowerShell kullanarak uyumlu paketleri için arama da yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b852d-111">You can also search for compatible packages using PowerShell.</span></span>

![Pseditions'ı olan sayfa öğesi görüntüle](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a><span data-ttu-id="b852d-113">PowerShell Core üzerinde çalışan paketleri UI Galerisi'nde Ara</span><span class="sxs-lookup"><span data-stu-id="b852d-113">Search for packages in the gallery UI that work on PowerShell Core</span></span>

<span data-ttu-id="b852d-114">Etiketleri kullanma: "PSEdition_Desktop" ve etiketler: "PSEdition_Core" filtreleri PowerShell Galerisi paketleri.</span><span class="sxs-lookup"><span data-stu-id="b852d-114">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="b852d-115">Etiketleri kullanma: "PowerShell Core Edition ile uyumlu olan öğeleri aramasına izin PSEdition_Core".</span><span class="sxs-lookup"><span data-stu-id="b852d-115">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Çekirdek PSEdition ile uyumlu olan öğeleri için arama sonuçları](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="b852d-117">Etiketleri kullanma: "PowerShell Masaüstü sürümü ile uyumlu olan öğeleri aramasına izin PSEdition_Desktop".</span><span class="sxs-lookup"><span data-stu-id="b852d-117">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Masaüstü PSEdition ile uyumlu olan öğeleri için arama sonuçları](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a><span data-ttu-id="b852d-119">PowerShell kullanarak uyumlu sürümlerini bulmak paketleri Ara</span><span class="sxs-lookup"><span data-stu-id="b852d-119">Search for packages to find compatible editions using PowerShell</span></span>
<span data-ttu-id="b852d-120">PowerShell sürümü ve işletim sistemi için filtrelemek için etiketler belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b852d-120">You can specify tags to filter for the PowerShell edition and OS.</span></span>
<span data-ttu-id="b852d-121">Kullandığınız `Find-Package` cmdlet'i belirtme `-Tag` sürümü (ve işletim sistemi) belirtmek için parametre hedeflediğiniz.</span><span class="sxs-lookup"><span data-stu-id="b852d-121">You use the `Find-Package` cmdlet specifying the `-Tag` parameter to specify the edition (and OS) you are targeting.</span></span>
<span data-ttu-id="b852d-122">Böyle:</span><span class="sxs-lookup"><span data-stu-id="b852d-122">Like this:</span></span>

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a><span data-ttu-id="b852d-123">İşletim sistemi tarafından arama</span><span class="sxs-lookup"><span data-stu-id="b852d-123">Searching by Operating System</span></span>

<span data-ttu-id="b852d-124">PowerShell Core Windows, Linux ve MacOS için kullanılabilir olduğundan, paketleri galerisinde bu işletim sistemlerinden herhangi bir birleşimini için tasarlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="b852d-124">Since PowerShell Core is available for Windows, Linux, and MacOS, packages in the Gallery may be designed for any combination of these operating systems.</span></span> <span data-ttu-id="b852d-125">UI galeride, işletim sistemi tarafından etiketlenmiş paketler bulmak için aşağıdaki depolamaya etiketleri kullanın:</span><span class="sxs-lookup"><span data-stu-id="b852d-125">In the gallery UI use the following searchs tags to find packages tagged by operating system:</span></span>

- <span data-ttu-id="b852d-126">Etiketler: "Windows"</span><span class="sxs-lookup"><span data-stu-id="b852d-126">Tags: "Windows"</span></span>
- <span data-ttu-id="b852d-127">Etiketler: "Linux"</span><span class="sxs-lookup"><span data-stu-id="b852d-127">Tags: "Linux"</span></span>
- <span data-ttu-id="b852d-128">Etiketler: "MacOS"</span><span class="sxs-lookup"><span data-stu-id="b852d-128">Tags: "MacOS"</span></span>

<span data-ttu-id="b852d-129">Bu etiketler belirtebileceğiniz `Find-Module` (ve diğer cmdlet'ler PowerShellGet Modülü) şöyle:</span><span class="sxs-lookup"><span data-stu-id="b852d-129">You can specify these tags on `Find-Module` (and other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a><span data-ttu-id="b852d-130">Birden çok uyumluluğunu için arama</span><span class="sxs-lookup"><span data-stu-id="b852d-130">Searching for Multiple Compatibilities</span></span>

<span data-ttu-id="b852d-131">Söz dizimi kullanılarak birden çok uyumluluğunu olan bir paketi arayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b852d-131">You can look for a package that has multiple compatibilities by using the syntax:</span></span>

<span data-ttu-id="b852d-132">Etiketler: "Compatibility1" "Compatibility2"</span><span class="sxs-lookup"><span data-stu-id="b852d-132">Tags: "Compatibility1" "Compatibility2"</span></span>

<span data-ttu-id="b852d-133">Örneğin, bir paket my Windows ve Linux makinelerinde çalışır, PowerShell Core uyumluluğu için arıyorsanız, arama etiketleri kullanın:</span><span class="sxs-lookup"><span data-stu-id="b852d-133">For example, if you are looking for a package with PowerShell Core Compatibility that runs on both my Windows and Linux machines, use the search tags:</span></span>

<span data-ttu-id="b852d-134">Etiketler: "PSEdition_Core", "Windows" "Linux"</span><span class="sxs-lookup"><span data-stu-id="b852d-134">Tags: "PSEdition_Core" "Windows" "Linux"</span></span>

<span data-ttu-id="b852d-135">PowerShell kullanarak arama yapmak için kullanabileceğiniz `Find-Module` (ve diğer PowerShellGet modülündeki cmdlet'ler) şöyle:</span><span class="sxs-lookup"><span data-stu-id="b852d-135">To search using PowerShell, you can use the `Find-Module` (and the other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="b852d-136">Geliştirme ve paketler uyumlu PowerShell sürümleriyle bulma hakkında daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="b852d-136">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="b852d-137">PSEditions’ı olan Modüller</span><span class="sxs-lookup"><span data-stu-id="b852d-137">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="b852d-138">PSEditions’ı olan Betikler</span><span class="sxs-lookup"><span data-stu-id="b852d-138">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
