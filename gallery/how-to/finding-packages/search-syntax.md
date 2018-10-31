---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Galeri arama söz dizimi
ms.openlocfilehash: 9aadb6771c85845cc3fa05cb56f0194b060d1c1b
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004146"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="934bb-103">Galeri arama söz dizimi</span><span class="sxs-lookup"><span data-stu-id="934bb-103">Gallery Search Syntax</span></span>

<span data-ttu-id="934bb-104">PowerShell Galerisi, burada sözcük ve tümcecikleri anahtar ifadeleri arama sonuçları daraltmak için kullanabileceğiniz bir metin searchbox sunar.</span><span class="sxs-lookup"><span data-stu-id="934bb-104">PowerShell Gallery offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="934bb-105">Anahtar sözcüklere göre ara</span><span class="sxs-lookup"><span data-stu-id="934bb-105">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="934bb-106">Arama tüm 3 anahtar sözcükleri içeren ilgili belgeleri bulmak için en iyi deneme yapın ve eşleşen belgeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="934bb-106">Search will do its best effort to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="934bb-107">İfadeler ve anahtar sözcükleri kullanarak arama</span><span class="sxs-lookup"><span data-stu-id="934bb-107">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="934bb-108">Tırnak işaretleri arasına tümcecik girerek ("") yerine ayrı bir anahtar sözcük belirli tümceciği aramak için arama değiştirin.</span><span class="sxs-lookup"><span data-stu-id="934bb-108">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="934bb-109">Eşleşen belgelerin genellikle "azure sql" büyük/küçük harf çeşidi örn dahil olmak üzere, tam tümcecik içermelidir "Azure SQL" ve de genellikle 'dağıtımı' sözcük içerir.</span><span class="sxs-lookup"><span data-stu-id="934bb-109">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="934bb-110">Alanlarda filtreleme</span><span class="sxs-lookup"><span data-stu-id="934bb-110">Filtering on fields</span></span>

<span data-ttu-id="934bb-111">Bir belirli bir paket kimliği (veya 'Id' veya 'id') arama yapabilirsiniz veya alan adı şartlarını önek tarafından diğer belirli alanları arama yapın.</span><span class="sxs-lookup"><span data-stu-id="934bb-111">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="934bb-112">Şu anda aranabilir alanları 'Id', 'Version', 'Etiketleri', 'Yazma', 'Owner', 'İşlevler', 'Cmdlet'leri', 'DscResources' ve 'PowerShellVersion' ' dir.</span><span class="sxs-lookup"><span data-stu-id="934bb-112">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="934bb-113">[ID ve başlık arasındaki fark nedir?</span><span class="sxs-lookup"><span data-stu-id="934bb-113">[What's the difference between ID and Title?</span></span> <span data-ttu-id="934bb-114">Kimliği konsolda kullandığınız addır.</span><span class="sxs-lookup"><span data-stu-id="934bb-114">ID is the name you use in the console.</span></span> <span data-ttu-id="934bb-115">Arama sonuçlarında paket sayfanın üstünde gösterilen başlıktır.]</span><span class="sxs-lookup"><span data-stu-id="934bb-115">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="934bb-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="934bb-116">Examples</span></span>

    ID:"PSReadline"
    id:"AzureRM.Profile"

<span data-ttu-id="934bb-117">"PSReadline" veya "AzureRM.Profile" olan paketleri kendi Kimliği alanında sırasıyla bulur.</span><span class="sxs-lookup"><span data-stu-id="934bb-117">finds packages with "PSReadline" or "AzureRM.Profile" in their ID field respectively.</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="934bb-118">"AzureRM.Profile" paketlerle kendi Kimliği alanı bulmak için başka bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="934bb-118">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="934bb-119">'Id' filtresi, bir alt dizesi eşleşiyorsa, bu nedenle aşağıdakiler için arama şöyledir:</span><span class="sxs-lookup"><span data-stu-id="934bb-119">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="934bb-120">'AzureRM.Profile' ve 'Azure.Storage' benzer bir sonuç elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="934bb-120">You'll get results like 'AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="934bb-121">Tek bir alanda birden çok anahtar sözcük için arama da yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="934bb-121">You can also search for multiple keywords in a single field.</span></span> <span data-ttu-id="934bb-122">Veya karıştırıp eşleştirebilirsiniz alanları.</span><span class="sxs-lookup"><span data-stu-id="934bb-122">Or mix and match fields.</span></span>

    id:azure tags:intellisense
    id:azure id:storage

<span data-ttu-id="934bb-123">Ve tümcecik aramaları gerçekleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="934bb-123">And you can perform phrase searches:</span></span>

    id:"azure.storage"


<span data-ttu-id="934bb-124">DSC etikete sahip tüm paketleri aramak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="934bb-124">To search all packages with DSC tag.</span></span>

    Tags:"DSC"

<span data-ttu-id="934bb-125">Belirtilen işlev olan tüm paketleri aramak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="934bb-125">To search all packages with the specified function.</span></span>

    Functions:"Update-AzureRM"

<span data-ttu-id="934bb-126">Belirtilen cmdlet'i ile tüm paketleri aramak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="934bb-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:"Get-AzureRmEnvironment"

<span data-ttu-id="934bb-127">Belirtilen DSC kaynak adına sahip tüm paketleri aramak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="934bb-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:"xArchive"

<span data-ttu-id="934bb-128">Belirtilen PowerShellVersion olan tüm paketleri aramak için</span><span class="sxs-lookup"><span data-stu-id="934bb-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


<span data-ttu-id="934bb-129">Son olarak, bir alan, 'komutları gibi' desteklemiyoruz kullanırsanız, biz yalnızca yoksayabilir ve tüm alanları arayın.</span><span class="sxs-lookup"><span data-stu-id="934bb-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="934bb-130">Bu nedenle sorguyu aşağıdaki</span><span class="sxs-lookup"><span data-stu-id="934bb-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="934bb-131">Olduğu aynı şekilde bu sorgu yorumlanır:</span><span class="sxs-lookup"><span data-stu-id="934bb-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage
