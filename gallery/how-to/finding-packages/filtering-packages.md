---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Arama sonuçlarını filtreleme
ms.openlocfilehash: 13270a310613a974e1588a9f56d443a936cfebb8
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004212"
---
# <a name="filtering-search-results"></a><span data-ttu-id="14dcb-103">Arama sonuçlarını filtreleme</span><span class="sxs-lookup"><span data-stu-id="14dcb-103">Filtering search results</span></span>

<span data-ttu-id="14dcb-104">[Paketleri sekmesinde](https://www.powershellgallery.com/packages) PowerShell galerisinde kullanılabilir tüm paketleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="14dcb-104">The [Packages tab](https://www.powershellgallery.com/packages) displays all available packages in the PowerShell Gallery.</span></span>

<span data-ttu-id="14dcb-105">Filtrelemek, sıralamak ve paketleri aramak için birkaç yol vardır.</span><span class="sxs-lookup"><span data-stu-id="14dcb-105">There are several ways to filter, sort, and search the packages.</span></span>
<span data-ttu-id="14dcb-106">Belirli bir paket hakkında daha fazla ayrıntı görmek için paket'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="14dcb-106">To see more details about a particular package, click the package.</span></span>

## <a name="filter-by"></a><span data-ttu-id="14dcb-107">Filtreleme Ölçütü</span><span class="sxs-lookup"><span data-stu-id="14dcb-107">Filter By</span></span>

<span data-ttu-id="14dcb-108">"Filtresi tarafından" altındaki açılan sonuçlarına göre filtre uygulamak kullanıcıların sağlar:</span><span class="sxs-lookup"><span data-stu-id="14dcb-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
- <span data-ttu-id="14dcb-109">Ön sürümü dahil et</span><span class="sxs-lookup"><span data-stu-id="14dcb-109">Include Prerelease</span></span>
- <span data-ttu-id="14dcb-110">Yalnızca kararlı</span><span class="sxs-lookup"><span data-stu-id="14dcb-110">Stable Only</span></span>

<span data-ttu-id="14dcb-111">"Ön" ve "Kararlı" hakkında daha fazla bilgi için bkz: [yayın öncesi sürüm eklenen PowerShellGet ve PowerShell Galerisi](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) PowerShell Ekibi blogunda.</span><span class="sxs-lookup"><span data-stu-id="14dcb-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="14dcb-112">Aşağı açılan altındaki onay kutularını sonuçlarına göre filtre uygulamak kullanıcılara izin ver:</span><span class="sxs-lookup"><span data-stu-id="14dcb-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
- <span data-ttu-id="14dcb-113">Paket türleri</span><span class="sxs-lookup"><span data-stu-id="14dcb-113">Package Types</span></span>
  - <span data-ttu-id="14dcb-114">Modül</span><span class="sxs-lookup"><span data-stu-id="14dcb-114">Module</span></span>
  - <span data-ttu-id="14dcb-115">Betik</span><span class="sxs-lookup"><span data-stu-id="14dcb-115">Script</span></span>
- <span data-ttu-id="14dcb-116">Kategorileri</span><span class="sxs-lookup"><span data-stu-id="14dcb-116">Categories</span></span>
  - <span data-ttu-id="14dcb-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="14dcb-117">Cmdlet</span></span>
  - <span data-ttu-id="14dcb-118">DSC kaynak</span><span class="sxs-lookup"><span data-stu-id="14dcb-118">DSC Resource</span></span>
  - <span data-ttu-id="14dcb-119">İşlev</span><span class="sxs-lookup"><span data-stu-id="14dcb-119">Function</span></span>
  - <span data-ttu-id="14dcb-120">Rol özelliği</span><span class="sxs-lookup"><span data-stu-id="14dcb-120">Role Capability</span></span>
  - <span data-ttu-id="14dcb-121">İş akışı</span><span class="sxs-lookup"><span data-stu-id="14dcb-121">Workflow</span></span>

<span data-ttu-id="14dcb-122">Yalnızca PowerShell Galerisi modülleri görmek için paket türleri bir modülde denetleyin.</span><span class="sxs-lookup"><span data-stu-id="14dcb-122">To see only modules in the PowerShell Gallery, check Module in the Package Types.</span></span>
<span data-ttu-id="14dcb-123">Benzer şekilde, yalnızca betikler PowerShell galerisinde görmek için paket türleri betikte denetleyin.</span><span class="sxs-lookup"><span data-stu-id="14dcb-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Package Types.</span></span>

> [!NOTE]
> <span data-ttu-id="14dcb-124">Filtreler dahildir.</span><span class="sxs-lookup"><span data-stu-id="14dcb-124">Filters are inclusive.</span></span>
> <span data-ttu-id="14dcb-125">Örnek: hem cmdlet'ler ve işlevler içeren bir paket cmdlet'ini veya işlevinde (veya her ikisi de) işaretlediyseniz görünür.</span><span class="sxs-lookup"><span data-stu-id="14dcb-125">Example: A package containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="14dcb-126">Ne seçili değilse, paket görünmez.</span><span class="sxs-lookup"><span data-stu-id="14dcb-126">If neither are selected, the package will not appear.</span></span>
> <span data-ttu-id="14dcb-127">Benzer şekilde, tüm kategorileri seçilirse yalnızca bu kategorilerden birindeyse içeren paketler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="14dcb-127">Similarly, if all categories are selected, only packages containing one of those categories will appear.</span></span>
> <span data-ttu-id="14dcb-128">**Bu kategorilerin hiçbirine ait olmayan paketleri görünmez.**</span><span class="sxs-lookup"><span data-stu-id="14dcb-128">**Packages that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="14dcb-129">Sıralama ölçütü</span><span class="sxs-lookup"><span data-stu-id="14dcb-129">Sort By</span></span>

<span data-ttu-id="14dcb-130">Sıralama açılan sonuçlarına göre sıralama olanağı sağlar:</span><span class="sxs-lookup"><span data-stu-id="14dcb-130">The Sort By drop-down allows users to sort the results by:</span></span>
- <span data-ttu-id="14dcb-131">Popülerlik - popülerliği indirme sayısına göre belirlenir</span><span class="sxs-lookup"><span data-stu-id="14dcb-131">Popularity - Popularity is determined by Download Count</span></span>
- <span data-ttu-id="14dcb-132">A-Z - paket adına göre alfabetik</span><span class="sxs-lookup"><span data-stu-id="14dcb-132">A-Z - Alphabetically by package name</span></span>
- <span data-ttu-id="14dcb-133">Son - paketleri yayımlama tarih sırasına göre görünür</span><span class="sxs-lookup"><span data-stu-id="14dcb-133">Recent - Packages appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="14dcb-134">Arama kutusu</span><span class="sxs-lookup"><span data-stu-id="14dcb-134">Search Box</span></span>

<span data-ttu-id="14dcb-135">Arama kutusuna anahtar sözcükleri paketleri aramak kullanıcıların sağlar.</span><span class="sxs-lookup"><span data-stu-id="14dcb-135">The Search Box allows users to search the packages on keywords.</span></span>
<span data-ttu-id="14dcb-136">Daha fazla bilgi için [galeri arama söz dizimi](search-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="14dcb-136">For more information, see [Gallery Search Syntax](search-syntax.md).</span></span>
