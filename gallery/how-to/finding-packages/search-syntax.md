---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Galeri arama söz dizimi
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: e24525046dd37166b9d83eeecdc534726316f429
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2018
ms.locfileid: "52742865"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="63ff2-103">Galeri arama söz dizimi</span><span class="sxs-lookup"><span data-stu-id="63ff2-103">Gallery Search Syntax</span></span>

<span data-ttu-id="63ff2-104">PowerShell Galerisi kullanılarak arama [PowerShell galerinin web sitesi](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="63ff2-104">You can search the PowerShell Gallery using the [PowerShell Gallery's web site](https://www.powershellgallery.com/).</span></span>
<span data-ttu-id="63ff2-105">Burada sözcük ve tümcecikleri anahtar ifadeleri arama sonuçları daraltmak için kullanabileceğiniz bir metin searchbox PowerShell Galerisi web sitesi sunar.</span><span class="sxs-lookup"><span data-stu-id="63ff2-105">PowerShell Gallery web site offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="63ff2-106">Anahtar sözcüklere göre ara</span><span class="sxs-lookup"><span data-stu-id="63ff2-106">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="63ff2-107">Arama, tüm 3 anahtar sözcükleri içeren ilgili belgeleri bulun ve eşleşen belgelerin dönüş dener.</span><span class="sxs-lookup"><span data-stu-id="63ff2-107">Search attempts to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="63ff2-108">İfadeler ve anahtar sözcükleri kullanarak arama</span><span class="sxs-lookup"><span data-stu-id="63ff2-108">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="63ff2-109">Tırnak işaretleri arasına tümcecik girerek ("") yerine ayrı bir anahtar sözcük belirli tümceciği aramak için arama değiştirin.</span><span class="sxs-lookup"><span data-stu-id="63ff2-109">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="63ff2-110">Eşleşen belgelerin genellikle "azure sql" büyük/küçük harf çeşidi örn dahil olmak üzere, tam tümcecik içermelidir "Azure SQL" ve de genellikle 'dağıtımı' sözcük içerir.</span><span class="sxs-lookup"><span data-stu-id="63ff2-110">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="63ff2-111">Alanlarda filtreleme</span><span class="sxs-lookup"><span data-stu-id="63ff2-111">Filtering on fields</span></span>

<span data-ttu-id="63ff2-112">Bir belirli bir paket kimliği (veya 'Id' veya 'id') arama yapabilirsiniz veya alan adı şartlarını önek tarafından diğer belirli alanları arama yapın.</span><span class="sxs-lookup"><span data-stu-id="63ff2-112">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="63ff2-113">Şu anda aranabilir alanları 'Id', 'Version', 'Etiketleri', 'Yazma', 'Owner', 'İşlevler', 'Cmdlet'leri', 'DscResources' ve 'PowerShellVersion' ' dir.</span><span class="sxs-lookup"><span data-stu-id="63ff2-113">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="63ff2-114">[ID ve başlık arasındaki fark nedir?</span><span class="sxs-lookup"><span data-stu-id="63ff2-114">[What's the difference between ID and Title?</span></span> <span data-ttu-id="63ff2-115">Kimliği konsolda kullandığınız addır.</span><span class="sxs-lookup"><span data-stu-id="63ff2-115">ID is the name you use in the console.</span></span> <span data-ttu-id="63ff2-116">Arama sonuçlarında paket sayfanın üstünde gösterilen başlıktır.]</span><span class="sxs-lookup"><span data-stu-id="63ff2-116">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="63ff2-117">Örnekler</span><span class="sxs-lookup"><span data-stu-id="63ff2-117">Examples</span></span>

    ID:PSReadline
    
<span data-ttu-id="63ff2-118">"PSReadline" içeren bir kimliği paketleri bulur.</span><span class="sxs-lookup"><span data-stu-id="63ff2-118">finds packages with an ID containing "PSReadline".</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="63ff2-119">"AzureRM.Profile" paketlerle kendi Kimliği alanı bulmak için başka bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="63ff2-119">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="63ff2-120">'Id' filtresi, bir alt dizesi eşleşiyorsa, bu nedenle aşağıdakiler için arama şöyledir:</span><span class="sxs-lookup"><span data-stu-id="63ff2-120">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="63ff2-121">Bu AzureRM.Profile içeren sonuçları sağlar ' ve 'Azure.Storage'.</span><span class="sxs-lookup"><span data-stu-id="63ff2-121">This provides results that include AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="63ff2-122">Tek bir alanda birden çok anahtar sözcük için arama da yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63ff2-122">You can also search for multiple keywords in a single field.</span></span> 

    id:azure tags:intellisense

<span data-ttu-id="63ff2-123">Ve tümcecik aramaları çift tırnak işareti kullanarak gerçekleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="63ff2-123">And you can perform phrase searches using double quotes:</span></span>

    id:"azure.storage"

<span data-ttu-id="63ff2-124">DSC etikete sahip tüm paketleri aramak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63ff2-124">To search all packages with DSC tag.</span></span>

    Tags:DSC

<span data-ttu-id="63ff2-125">Belirtilen işlev olan tüm paketleri aramak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63ff2-125">To search all packages with the specified function.</span></span>

    Functions:Get-TreeSize

<span data-ttu-id="63ff2-126">Belirtilen cmdlet'i ile tüm paketleri aramak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63ff2-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:Get-AzureRmEnvironment

<span data-ttu-id="63ff2-127">Belirtilen DSC kaynak adına sahip tüm paketleri aramak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63ff2-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:xArchive

<span data-ttu-id="63ff2-128">Belirtilen PowerShellVersion olan tüm paketleri aramak için</span><span class="sxs-lookup"><span data-stu-id="63ff2-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:2.0

<span data-ttu-id="63ff2-129">Son olarak, bir alan, 'komutları gibi' desteklemiyoruz kullanırsanız, biz yalnızca yoksayabilir ve tüm alanları arayın.</span><span class="sxs-lookup"><span data-stu-id="63ff2-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="63ff2-130">Bu nedenle sorguyu aşağıdaki</span><span class="sxs-lookup"><span data-stu-id="63ff2-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="63ff2-131">Olduğu aynı şekilde bu sorgu yorumlanır:</span><span class="sxs-lookup"><span data-stu-id="63ff2-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage
