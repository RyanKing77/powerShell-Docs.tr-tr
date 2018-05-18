---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Galeri arama söz dizimi
ms.openlocfilehash: 52fca21a00bcc6e3789bceb331acf5bc771bb0f2
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="bcb23-103">Galeri arama söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bcb23-103">Gallery Search Syntax</span></span>

<span data-ttu-id="bcb23-104">Arama sonuçları daraltmak için sözcükler, ifadeler ve anahtar sözcüğü ifadeler burada kullanabilirsiniz metin searchbox PowerShell Galerisi sunar.</span><span class="sxs-lookup"><span data-stu-id="bcb23-104">PowerShell Gallery offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="bcb23-105">Anahtar sözcükler göre ara</span><span class="sxs-lookup"><span data-stu-id="bcb23-105">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="bcb23-106">Arama tüm 3 anahtar sözcükler içeren ilgili belgeleri bulmak için en iyi çaba yapın ve eşleşen belgeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="bcb23-106">Search will do its best effort to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="bcb23-107">Tümcecikleri ve anahtar sözcükler kullanarak arama</span><span class="sxs-lookup"><span data-stu-id="bcb23-107">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="bcb23-108">Tırnak işaretleri arasında tümcecik girerek ("") ayrı anahtar sözcükler yerine belirli tümceciği aramak için arama değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bcb23-108">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="bcb23-109">Eşleşen belgelerin genellikle "azure sql" büyük/küçük harf çeşidi örneğin de dahil olmak üzere, tam deyim içermelidir "Azure SQL" ve de genellikle word 'dağıtım' içermelidir.</span><span class="sxs-lookup"><span data-stu-id="bcb23-109">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="bcb23-110">Alanları filtreleme</span><span class="sxs-lookup"><span data-stu-id="bcb23-110">Filtering on fields</span></span>

<span data-ttu-id="bcb23-111">Bir özel öğesi kimliği (veya 'Id' veya 'ID') arayabilirsiniz veya alan adı şartlarını bazı diğer alanlar önek olarak arama yapın.</span><span class="sxs-lookup"><span data-stu-id="bcb23-111">You can search for a specific item ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="bcb23-112">Şu anda aranabilir 'Id', 'Version', 'Etiketleri', 'Yazar', 'Sahibi', 'İşlevleri', 'Cmdlet'leri', 'DscResources' ve 'PowerShellVersion' alanlardır.</span><span class="sxs-lookup"><span data-stu-id="bcb23-112">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="bcb23-113">[Başlık kimliği arasındaki fark nedir?</span><span class="sxs-lookup"><span data-stu-id="bcb23-113">[What's the difference between ID and Title?</span></span> <span data-ttu-id="bcb23-114">Kimliği konsolda kullandığınız addır.</span><span class="sxs-lookup"><span data-stu-id="bcb23-114">ID is the name you use in the console.</span></span> <span data-ttu-id="bcb23-115">Başlık sayfanın üst kısmındaki öğe arama sonuçlarında gösterilen yer alır.]</span><span class="sxs-lookup"><span data-stu-id="bcb23-115">Title is what is shown at the top of the item page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="bcb23-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="bcb23-116">Examples</span></span>

    ID:"PSReadline"
    id:"AzureRM.Profile"

<span data-ttu-id="bcb23-117">"PSReadline" veya "AzureRM.Profile" öğeleriyle kendi Kimliği alanında sırasıyla bulur.</span><span class="sxs-lookup"><span data-stu-id="bcb23-117">finds items with "PSReadline" or "AzureRM.Profile" in their ID field respectively.</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="bcb23-118">kendi Kimliği alanında "AzureRM.Profile" ile öğelerini bulmak için başka bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="bcb23-118">is another way to find items with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="bcb23-119">'Id' filtre, bir alt dizesi eşleşiyorsa, bunu aşağıdakiler için arama şöyledir:</span><span class="sxs-lookup"><span data-stu-id="bcb23-119">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="bcb23-120">'AzureRM.Profile' ve 'Azure.Storage' gibi sonuçları elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="bcb23-120">You'll get results like 'AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="bcb23-121">Tek bir alanda birden çok anahtar kelimeleri arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bcb23-121">You can also search for multiple keywords in a single field.</span></span> <span data-ttu-id="bcb23-122">Karışık ve alanların eşleştiği.</span><span class="sxs-lookup"><span data-stu-id="bcb23-122">Or mix and match fields.</span></span>

    id:azure tags:intellisense
    id:azure id:storage

<span data-ttu-id="bcb23-123">Ayrıca, deyim aramalarını gerçekleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bcb23-123">And you can perform phrase searches:</span></span>

    id:"azure.storage"


<span data-ttu-id="bcb23-124">DSC etikete sahip tüm öğeleri aramak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bcb23-124">To search all items with DSC tag.</span></span>

    Tags:"DSC"

<span data-ttu-id="bcb23-125">Belirtilen işlevi olan tüm öğeleri aramak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bcb23-125">To search all items with the specified function.</span></span>

    Functions:"Update-AzureRM"

<span data-ttu-id="bcb23-126">Belirtilen cmdlet'ini tüm öğeleri aramak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bcb23-126">To search all items with the specified cmdlet.</span></span>

    Cmdlets:"Get-AzureRmEnvironment"

<span data-ttu-id="bcb23-127">Belirtilen DSC kaynağı ada sahip tüm öğeleri aramak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bcb23-127">To search all items with the specified DSC Resource name.</span></span>

    DscResources:"xArchive"

<span data-ttu-id="bcb23-128">Belirtilen PowerShellVersion tüm öğeleri aramak için</span><span class="sxs-lookup"><span data-stu-id="bcb23-128">To search all items with the specified PowerShellVersion</span></span>

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


<span data-ttu-id="bcb23-129">Son olarak, 'gibi komutları' desteklemiyoruz alan kullanırsanız, biz yalnızca yok sayın ve tüm alanları arayın.</span><span class="sxs-lookup"><span data-stu-id="bcb23-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="bcb23-130">Bu nedenle sorgu aşağıdaki</span><span class="sxs-lookup"><span data-stu-id="bcb23-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="bcb23-131">Olan tam olarak aynı bu sorguyu yorumlanır:</span><span class="sxs-lookup"><span data-stu-id="bcb23-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage