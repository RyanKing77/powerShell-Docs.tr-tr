---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Arama sonuçlarını filtreleme
ms.openlocfilehash: eafbc993a37eaee7413102ef9d669a6b07d6ff6e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188817"
---
# <a name="filtering-search-results"></a><span data-ttu-id="a799e-103">Arama sonuçlarını filtreleme</span><span class="sxs-lookup"><span data-stu-id="a799e-103">Filtering search results</span></span>

<span data-ttu-id="a799e-104">[Öğeleri sekmesini](https://www.powershellgallery.com/items) PowerShell galerisinde tüm kullanılabilir öğeleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a799e-104">The [Items tab](https://www.powershellgallery.com/items) displays all available items in the PowerShell Gallery.</span></span>

<span data-ttu-id="a799e-105">Filtre, sıralama ve öğeleri aramak için birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="a799e-105">There are several ways to filter, sort, and search the items.</span></span>
<span data-ttu-id="a799e-106">Belirli bir öğe hakkında daha fazla ayrıntı görmek için öğeyi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a799e-106">To see more details about a particular item, click the item.</span></span>

## <a name="filter-by"></a><span data-ttu-id="a799e-107">Filtre ölçütü</span><span class="sxs-lookup"><span data-stu-id="a799e-107">Filter By</span></span>

<span data-ttu-id="a799e-108">Aşağı açılan "Filtre tarafından" altında sonuçlarına göre filtre uygulamak kullanıcıların sağlar:</span><span class="sxs-lookup"><span data-stu-id="a799e-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
- <span data-ttu-id="a799e-109">Yayın öncesi içerir</span><span class="sxs-lookup"><span data-stu-id="a799e-109">Include Prerelease</span></span>
- <span data-ttu-id="a799e-110">Yalnızca kararlı</span><span class="sxs-lookup"><span data-stu-id="a799e-110">Stable Only</span></span>

<span data-ttu-id="a799e-111">"Yayın öncesi" ve "Kararlı" hakkında daha fazla bilgi için bkz: [yayın öncesi sürüm eklenen PowerShellGet ve PowerShell Galerisi](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) PowerShell ekip blogu içinde.</span><span class="sxs-lookup"><span data-stu-id="a799e-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="a799e-112">Aşağı açılan altında onay kutularını sonuçlarına göre filtre uygulamak kullanıcılara izin ver:</span><span class="sxs-lookup"><span data-stu-id="a799e-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
- <span data-ttu-id="a799e-113">Öğesi türleri</span><span class="sxs-lookup"><span data-stu-id="a799e-113">Item Types</span></span>
  - <span data-ttu-id="a799e-114">Modül</span><span class="sxs-lookup"><span data-stu-id="a799e-114">Module</span></span>
  - <span data-ttu-id="a799e-115">Betik</span><span class="sxs-lookup"><span data-stu-id="a799e-115">Script</span></span>
- <span data-ttu-id="a799e-116">kategorileri</span><span class="sxs-lookup"><span data-stu-id="a799e-116">Categories</span></span>
  - <span data-ttu-id="a799e-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a799e-117">Cmdlet</span></span>
  - <span data-ttu-id="a799e-118">DSC kaynağı</span><span class="sxs-lookup"><span data-stu-id="a799e-118">DSC Resource</span></span>
  - <span data-ttu-id="a799e-119">İşlev</span><span class="sxs-lookup"><span data-stu-id="a799e-119">Function</span></span>
  - <span data-ttu-id="a799e-120">Rol özelliği</span><span class="sxs-lookup"><span data-stu-id="a799e-120">Role Capability</span></span>
  - <span data-ttu-id="a799e-121">İş akışı</span><span class="sxs-lookup"><span data-stu-id="a799e-121">Workflow</span></span>

<span data-ttu-id="a799e-122">Yalnızca PowerShell Galerisi modülleri, modül öğesi türleri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a799e-122">To see only modules in the PowerShell Gallery, check Module in the Item Types.</span></span>
<span data-ttu-id="a799e-123">Benzer şekilde, yalnızca PowerShell galerisinde komut dosyaları, komut dosyasında öğesi türlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a799e-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Item Types.</span></span>

> [!NOTE]
> <span data-ttu-id="a799e-124">Filtreler dahildir.</span><span class="sxs-lookup"><span data-stu-id="a799e-124">Filters are inclusive.</span></span>
> <span data-ttu-id="a799e-125">Örnek: Cmdlet'ler ve işlevler içeren bir öğeyi cmdlet'ini veya işlevi (veya her ikisi de) işaretlediyseniz görünür.</span><span class="sxs-lookup"><span data-stu-id="a799e-125">Example: An item containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="a799e-126">Hiçbiri seçili ise, öğenin görünmez.</span><span class="sxs-lookup"><span data-stu-id="a799e-126">If neither are selected, the item will not appear.</span></span>
> <span data-ttu-id="a799e-127">Benzer şekilde, tüm kategorileri seçtiyseniz, yalnızca bu kategorilerden birini içeren öğeleri görünür.</span><span class="sxs-lookup"><span data-stu-id="a799e-127">Similarly, if all categories are selected, only items containing one of those categories will appear.</span></span>
> <span data-ttu-id="a799e-128">**Bu kategorilerin hiçbirine ait olmadığından öğeleri görünmez.**</span><span class="sxs-lookup"><span data-stu-id="a799e-128">**Items that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="a799e-129">Sıralama ölçütü</span><span class="sxs-lookup"><span data-stu-id="a799e-129">Sort By</span></span>

<span data-ttu-id="a799e-130">Sıralama ölçütü açılan sonuçlarına göre sıralamak kullanıcıların sağlar:</span><span class="sxs-lookup"><span data-stu-id="a799e-130">The Sort By drop-down allows users to sort the results by:</span></span>
- <span data-ttu-id="a799e-131">Popülerliği - popülerliği karşıdan sayısı tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="a799e-131">Popularity - Popularity is determined by Download Count</span></span>
- <span data-ttu-id="a799e-132">A-Z - ada göre öğesi</span><span class="sxs-lookup"><span data-stu-id="a799e-132">A-Z - Alphabetically by item name</span></span>
- <span data-ttu-id="a799e-133">Son - öğeleri Yayımla tarih sırasına göre görünür</span><span class="sxs-lookup"><span data-stu-id="a799e-133">Recent - Items appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="a799e-134">Arama kutusu</span><span class="sxs-lookup"><span data-stu-id="a799e-134">Search Box</span></span>

<span data-ttu-id="a799e-135">Arama kutusuna anahtar sözcükleri öğeleri aramak kullanıcıların sağlar.</span><span class="sxs-lookup"><span data-stu-id="a799e-135">The Search Box allows users to search the items on keywords.</span></span>
<span data-ttu-id="a799e-136">Daha fazla bilgi için bkz: [galeri arama söz dizimi](search-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="a799e-136">For more information, see [Gallery Search Syntax](search-syntax.md).</span></span>