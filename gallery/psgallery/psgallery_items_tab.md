---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: psgallery_items_tab
ms.openlocfilehash: 8704091542de5c19817ab0b4f77fd98987084b5d
ms.sourcegitcommit: 1a0a0928c1e3cae4e8df8d79b0737bd7ed6b4e47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="items-tab"></a><span data-ttu-id="4a94d-103">Öğeler sekmesi</span><span class="sxs-lookup"><span data-stu-id="4a94d-103">Items Tab</span></span>

<span data-ttu-id="4a94d-104">[Öğeleri sekmesini](https://www.powershellgallery.com/items) PowerShell galerisinde tüm kullanılabilir öğeleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4a94d-104">The [Items tab](https://www.powershellgallery.com/items) displays all available items in the PowerShell Gallery.</span></span>

<span data-ttu-id="4a94d-105">Filtre, sıralama ve öğeleri aramak için birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="4a94d-105">There are several ways to filter, sort, and search the items.</span></span>
<span data-ttu-id="4a94d-106">Belirli bir öğe hakkında daha fazla ayrıntı görmek için öğeyi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4a94d-106">To see more details about a particular item, click the item.</span></span>

## <a name="filter-by"></a><span data-ttu-id="4a94d-107">Filtre ölçütü</span><span class="sxs-lookup"><span data-stu-id="4a94d-107">Filter By</span></span>

<span data-ttu-id="4a94d-108">Aşağı açılan "Filtre tarafından" altında sonuçlarına göre filtre uygulamak kullanıcıların sağlar:</span><span class="sxs-lookup"><span data-stu-id="4a94d-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
* <span data-ttu-id="4a94d-109">Yayın öncesi içerir</span><span class="sxs-lookup"><span data-stu-id="4a94d-109">Include Prerelease</span></span>
* <span data-ttu-id="4a94d-110">Yalnızca kararlı</span><span class="sxs-lookup"><span data-stu-id="4a94d-110">Stable Only</span></span>

<span data-ttu-id="4a94d-111">"Yayın öncesi" ve "Kararlı" hakkında daha fazla bilgi için bkz: [yayın öncesi sürüm eklenen PowerShellGet ve PowerShell Galerisi](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) PowerShell ekip blogu içinde.</span><span class="sxs-lookup"><span data-stu-id="4a94d-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="4a94d-112">Aşağı açılan altında onay kutularını sonuçlarına göre filtre uygulamak kullanıcılara izin ver:</span><span class="sxs-lookup"><span data-stu-id="4a94d-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
* <span data-ttu-id="4a94d-113">Öğesi türleri</span><span class="sxs-lookup"><span data-stu-id="4a94d-113">Item Types</span></span>
  - <span data-ttu-id="4a94d-114">Modül</span><span class="sxs-lookup"><span data-stu-id="4a94d-114">Module</span></span>
  - <span data-ttu-id="4a94d-115">Betik</span><span class="sxs-lookup"><span data-stu-id="4a94d-115">Script</span></span>
* <span data-ttu-id="4a94d-116">kategorileri</span><span class="sxs-lookup"><span data-stu-id="4a94d-116">Categories</span></span>
  - <span data-ttu-id="4a94d-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4a94d-117">Cmdlet</span></span>
  - <span data-ttu-id="4a94d-118">DSC kaynağı</span><span class="sxs-lookup"><span data-stu-id="4a94d-118">DSC Resource</span></span>
  - <span data-ttu-id="4a94d-119">İşlev</span><span class="sxs-lookup"><span data-stu-id="4a94d-119">Function</span></span>
  - <span data-ttu-id="4a94d-120">Rol özelliği</span><span class="sxs-lookup"><span data-stu-id="4a94d-120">Role Capability</span></span>
  - <span data-ttu-id="4a94d-121">İş akışı</span><span class="sxs-lookup"><span data-stu-id="4a94d-121">Workflow</span></span>

<span data-ttu-id="4a94d-122">Yalnızca PowerShell Galerisi modülleri, modül öğesi türleri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4a94d-122">To see only modules in the PowerShell Gallery, check Module in the Item Types.</span></span>
<span data-ttu-id="4a94d-123">Benzer şekilde, yalnızca PowerShell galerisinde komut dosyaları, komut dosyasında öğesi türlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4a94d-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Item Types.</span></span>

> [!NOTE]
> <span data-ttu-id="4a94d-124">Filtreler dahildir.</span><span class="sxs-lookup"><span data-stu-id="4a94d-124">Filters are inclusive.</span></span>
> <span data-ttu-id="4a94d-125">Örnek: Cmdlet'ler ve işlevler içeren bir öğeyi cmdlet'ini veya işlevi (veya her ikisi de) işaretlediyseniz görünür.</span><span class="sxs-lookup"><span data-stu-id="4a94d-125">Example: An item containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="4a94d-126">Hiçbiri seçili ise, öğenin görünmez.</span><span class="sxs-lookup"><span data-stu-id="4a94d-126">If neither are selected, the item will not appear.</span></span>
> <span data-ttu-id="4a94d-127">Benzer şekilde, tüm kategorileri seçtiyseniz, yalnızca bu kategorilerden birini içeren öğeleri görünür.</span><span class="sxs-lookup"><span data-stu-id="4a94d-127">Similarly, if all categories are selected, only items containing one of those categories will appear.</span></span>
> <span data-ttu-id="4a94d-128">**Bu kategorilerin hiçbirine ait olmadığından öğeleri görünmez.**</span><span class="sxs-lookup"><span data-stu-id="4a94d-128">**Items that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="4a94d-129">Sıralama ölçütü</span><span class="sxs-lookup"><span data-stu-id="4a94d-129">Sort By</span></span>

<span data-ttu-id="4a94d-130">Sıralama ölçütü açılan sonuçlarına göre sıralamak kullanıcıların sağlar:</span><span class="sxs-lookup"><span data-stu-id="4a94d-130">The Sort By drop-down allows users to sort the results by:</span></span>
* <span data-ttu-id="4a94d-131">Popülerliği - popülerliği karşıdan sayısı tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="4a94d-131">Popularity - Popularity is determined by Download Count</span></span>
* <span data-ttu-id="4a94d-132">A-Z - ada göre öğesi</span><span class="sxs-lookup"><span data-stu-id="4a94d-132">A-Z - Alphabetically by item name</span></span>
* <span data-ttu-id="4a94d-133">Son - öğeleri Yayımla tarih sırasına göre görünür</span><span class="sxs-lookup"><span data-stu-id="4a94d-133">Recent - Items appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="4a94d-134">Arama kutusu</span><span class="sxs-lookup"><span data-stu-id="4a94d-134">Search Box</span></span>

<span data-ttu-id="4a94d-135">Arama kutusuna anahtar sözcükleri öğeleri aramak kullanıcıların sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a94d-135">The Search Box allows users to search the items on keywords.</span></span>
<span data-ttu-id="4a94d-136">Daha fazla bilgi için bkz: [galeri arama söz dizimi](psgallery_search_syntax.md).</span><span class="sxs-lookup"><span data-stu-id="4a94d-136">For more information, see [Gallery Search Syntax](psgallery_search_syntax.md).</span></span>
