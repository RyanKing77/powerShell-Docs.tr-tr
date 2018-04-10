---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: cedda61241df4965fe5db723f03e3497f046fa44
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a><span data-ttu-id="eac29-102">Yapılandırılmış Nesneleri Dizeden Çıkarma ve Ayıklama</span><span class="sxs-lookup"><span data-stu-id="eac29-102">Extract and Parse Structured Objects out of String</span></span>
<span data-ttu-id="eac29-103">Bu aynı zamanda ConvertFrom dize cmdlet'i için bazı ek işlevler sunar:</span><span class="sxs-lookup"><span data-stu-id="eac29-103">This also introduces some additional functionality for the ConvertFrom-String cmdlet:</span></span>

-   <span data-ttu-id="eac29-104">Uzantı metin özelliği varsayılan olarak kaldırır.</span><span class="sxs-lookup"><span data-stu-id="eac29-104">Removes the extent text property by default.</span></span> <span data-ttu-id="eac29-105">-IncludeExtent parametresiyle ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eac29-105">You can include it with the -IncludeExtent parameter.</span></span>

-   <span data-ttu-id="eac29-106">Çok sayıda algoritma hata düzeltmeleri MVP ve topluluk geri bildirim alanından öğrenme.</span><span class="sxs-lookup"><span data-stu-id="eac29-106">Many learning algorithm bug fixes from MVP and community feedback.</span></span>

-   <span data-ttu-id="eac29-107">Şablon dosyası bir açıklama içine öğrenme algoritmasını sonuçlarını kaydetmek için yeni bir - UpdateTemplate parametresi.</span><span class="sxs-lookup"><span data-stu-id="eac29-107">A new -UpdateTemplate parameter to save the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="eac29-108">Bu bir kerelik maliyeti (yavaş aşama) işlem öğrenme hale getirir.</span><span class="sxs-lookup"><span data-stu-id="eac29-108">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="eac29-109">Dönüştürme dizesi kodlanmış öğrenme algoritmasını içeren bir şablonla şimdi neredeyse anlık çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="eac29-109">Running Convert-String with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>


<a name="extract-and-parse-structured-objects-out-of-string-content"></a><span data-ttu-id="eac29-110">Ayıklamak ve dize içeriği dışında yapılandırılmış nesneleri ayrıştırılamadı</span><span class="sxs-lookup"><span data-stu-id="eac29-110">Extract and parse structured objects out of string content</span></span>
----------------------------------------------------------

<span data-ttu-id="eac29-111">İşbirliğiyle [Microsoft Research](http://research.microsoft.com/), yeni bir **ConvertFrom dize** cmdlet eklendi.</span><span class="sxs-lookup"><span data-stu-id="eac29-111">In collaboration with [Microsoft Research](http://research.microsoft.com/), a new **ConvertFrom-String** cmdlet has been added.</span></span>

<span data-ttu-id="eac29-112">Bu cmdlet iki modlarını destekler: basic, ayrıştırma ve örnek temelli otomatik ayrıştırma ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="eac29-112">This cmdlet supports two modes: basic delimited parsing, and auto generated example-driven parsing.</span></span>

<span data-ttu-id="eac29-113">Varsayılan olarak, ayrılmış ayrıştırma boşluk konumundaki giriş böler ve sonuçta elde edilen gruplarına özellik adları atar.</span><span class="sxs-lookup"><span data-stu-id="eac29-113">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span> <span data-ttu-id="eac29-114">Sınırlayıcı özelleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="eac29-114">You can customize the delimiter:</span></span>

> <span data-ttu-id="eac29-115">1 \[C:\\temp\] &gt; &gt; "Hello World" | ConvertFrom dize | Format-Table-otomatik</span><span class="sxs-lookup"><span data-stu-id="eac29-115">1 \[C:\\temp\] &gt;&gt; "Hello World" | ConvertFrom-String | Format-Table -Auto</span></span>

<span data-ttu-id="eac29-116">P1    P2</span><span class="sxs-lookup"><span data-stu-id="eac29-116">P1    P2</span></span>
--    --

<span data-ttu-id="eac29-117">Cmdlet ayrıca otomatik olarak oluşturulan göre örnek temelli ayrıştırma destekler [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) araştırma iş [Microsoft Research](http://research.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="eac29-117">The cmdlet also supports auto-generated example-driven parsing based on the [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) research work in [Microsoft Research](http://research.microsoft.com).</span></span>

<span data-ttu-id="eac29-118">Başlamak için bir metin tabanlı adres defteri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="eac29-118">To get started, consider a text-based address book:</span></span>

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

    Thomas Hardy

    Seattle, WA

    Christina Berglund

    Redmond, WA

    Hanna Moos

    Puyallup, WA

<span data-ttu-id="eac29-119">Birkaç örnek, şablon olarak kullanacağınız bir dosyaya kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="eac29-119">Copy a few examples into a file, which you will use as your template:</span></span>

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA



<span data-ttu-id="eac29-120">Ayıklamak istediğiniz verilerin etrafına süslü ayraçlar bunu gibi bir ad verip yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="eac29-120">Put curly braces around data that you want to extract, giving it a name as you do so.</span></span> <span data-ttu-id="eac29-121">Çünkü **adı** özelliği (ve diğer özellikleri ilişkili) birden çok kez görüntülenir, bir yıldız işareti kullanın (\*) bu birden çok kayıt (yerine tek bir demet özelliklerinin ayıklanıyor sonuçları göstermek için kayıt):</span><span class="sxs-lookup"><span data-stu-id="eac29-121">Because the **Name** property (and its associated other properties) can appear multiple times, use an asterisk (\*) to indicate that this results in multiple records (rather than extracting a bunch of properties into one record):</span></span>

    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}

<span data-ttu-id="eac29-122">Bu örnekler, kümesinden **ConvertFrom dize** artık otomatik olarak nesne tabanlı çıkış benzer yapıya sahip girdi dosyalarındaki ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eac29-122">From this set of examples, **ConvertFrom-String** can now automatically extract object-based output from input files with similar structure.</span></span>

> <span data-ttu-id="eac29-123">2 \[C:\\temp\]</span><span class="sxs-lookup"><span data-stu-id="eac29-123">2 \[C:\\temp\]</span></span>
>
> <span data-ttu-id="eac29-124">&gt;&gt; Get-içerik. \\addresses.output.txt | ConvertFrom dize - TemplateFile. \\addresses.template.txt | &gt; &gt; &gt; Format-Table-otomatik</span><span class="sxs-lookup"><span data-stu-id="eac29-124">&gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto</span></span>
>
> <span data-ttu-id="eac29-125">ExtentText adı Şehir durumu</span><span class="sxs-lookup"><span data-stu-id="eac29-125">ExtentText                     Name               City     State</span></span>
> ----------                     ----               ----     -----
> <span data-ttu-id="eac29-126">Ana Trujillo...                Ana Trujillo       Redmond  WA Antonio Moreno...              Antonio Moreno Renton WA Thomas Hardy...                Thomas Hardy Seattle WA Çiğdem Berglund...          Christina Berglund Redmond  WA Hanna Moos...                  Hanna Moos         Puyallup WA</span><span class="sxs-lookup"><span data-stu-id="eac29-126">Ana Trujillo...                Ana Trujillo       Redmond  WA Antonio Moreno...              Antonio Moreno     Renton   WA Thomas Hardy...                Thomas Hardy       Seattle  WA Christina Berglund...          Christina Berglund Redmond  WA Hanna Moos...                  Hanna Moos         Puyallup WA</span></span>

<span data-ttu-id="eac29-127">Ek veri işleme ayıklanan metni yapmak için **ExtentText** özelliği kendisinden kaydı çıkarılan ham metni yakalar.</span><span class="sxs-lookup"><span data-stu-id="eac29-127">To do additional data manipulation on extracted text, the **ExtentText** property captures the raw text from which the record was extracted.</span></span> <span data-ttu-id="eac29-128">Bu özellik üzerinde geribildirim sağlamak veya örnekler yazma zorluk sahip içeriği paylaşmak için lütfen e-posta <psdmfb@microsoft.com>.</span><span class="sxs-lookup"><span data-stu-id="eac29-128">To provide feedback on this feature, or to share content for which you are having difficulty writing examples, please email <psdmfb@microsoft.com>.</span></span>