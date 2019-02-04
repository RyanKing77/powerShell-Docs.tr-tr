---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: fcf2adf67f36edb534df3e2a849459fb20e1c2de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685623"
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a><span data-ttu-id="76ed0-102">Yapılandırılmış Nesneleri Dizeden Çıkarma ve Ayıklama</span><span class="sxs-lookup"><span data-stu-id="76ed0-102">Extract and Parse Structured Objects out of String</span></span>

<span data-ttu-id="76ed0-103">Bu da bazı ilave işlevler için tanıtılmaktadır `ConvertFrom-String` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="76ed0-103">This also introduces some additional functionality for the `ConvertFrom-String` cmdlet:</span></span>

- <span data-ttu-id="76ed0-104">Uzantı metin özelliği varsayılan olarak kaldırır.</span><span class="sxs-lookup"><span data-stu-id="76ed0-104">Removes the extent text property by default.</span></span> <span data-ttu-id="76ed0-105">-IncludeExtent parametresiyle ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76ed0-105">You can include it with the -IncludeExtent parameter.</span></span>

- <span data-ttu-id="76ed0-106">Birçok algoritma hata düzeltmelerine MVP ve topluluk geri bildirimine ilişkin öğrenme.</span><span class="sxs-lookup"><span data-stu-id="76ed0-106">Many learning algorithm bug fixes from MVP and community feedback.</span></span>

- <span data-ttu-id="76ed0-107">Şablon dosyası bir açıklama içine öğrenme algoritmasını sonuçlarını kaydetmek için yeni bir - UpdateTemplate parametre.</span><span class="sxs-lookup"><span data-stu-id="76ed0-107">A new -UpdateTemplate parameter to save the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="76ed0-108">Bu tek seferlik bir ücret (yavaş aşaması) işlem öğrenme sağlar.</span><span class="sxs-lookup"><span data-stu-id="76ed0-108">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="76ed0-109">Dize dönüştürme kodlanmış öğrenme algoritmasını içeren bir şablon ile artık neredeyse anında çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="76ed0-109">Running Convert-String with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

## <a name="extract-and-parse-structured-objects-out-of-string-content"></a><span data-ttu-id="76ed0-110">Yapılandırılmış nesneleri dize içerik dışına çıkarma ve</span><span class="sxs-lookup"><span data-stu-id="76ed0-110">Extract and parse structured objects out of string content</span></span>

<span data-ttu-id="76ed0-111">İşbirliği ile [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), yeni bir `ConvertFrom-String` cmdlet'i eklendi.</span><span class="sxs-lookup"><span data-stu-id="76ed0-111">In collaboration with [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), a new `ConvertFrom-String` cmdlet has been added.</span></span>

<span data-ttu-id="76ed0-112">Bu cmdlet iki modu destekler: basic ayrıştırma ve otomatik örnek temelli ayrıştırma ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="76ed0-112">This cmdlet supports two modes: basic delimited parsing, and auto generated example-driven parsing.</span></span>

<span data-ttu-id="76ed0-113">Varsayılan olarak, sınırlandırılmış ayrıştırma boşluk konumundaki giriş böler ve elde edilen gruplara özellik adlarını atar.</span><span class="sxs-lookup"><span data-stu-id="76ed0-113">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span> <span data-ttu-id="76ed0-114">Sınırlayıcı özelleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="76ed0-114">You can customize the delimiter:</span></span>

```powershell
"Hello World" | ConvertFrom-String | Format-Table -Auto
```

```output
P1     P2
--     --
Hello  World
```

<span data-ttu-id="76ed0-115">Cmdlet, ayrıca otomatik olarak oluşturulan göre örnek temelli ayrıştırma destekler [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) araştırma çalışması [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).</span><span class="sxs-lookup"><span data-stu-id="76ed0-115">The cmdlet also supports auto-generated example-driven parsing based on the [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) research work in [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).</span></span>

<span data-ttu-id="76ed0-116">Başlamak için bir metin tabanlı adres defteri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="76ed0-116">To get started, consider a text-based address book:</span></span>

```
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
```

<span data-ttu-id="76ed0-117">Bazı örnekler, şablon olarak kullanacağınız bir dosyaya kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="76ed0-117">Copy a few examples into a file, which you will use as your template:</span></span>

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA
```

<span data-ttu-id="76ed0-118">Bunu gibi bir ad verip ayıklamak istediğiniz verileriyle küme ayracı yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="76ed0-118">Put curly braces around data that you want to extract, giving it a name as you do so.</span></span> <span data-ttu-id="76ed0-119">Çünkü **adı** özelliği (ve ilgili diğer özellikleri) birden çok kez görünür, bir yıldız işareti kullanın (\*) bu birden çok kayıt (yerine tek bir sürü özellikleri ayıklama sonuçları göstermek için kayıt için):</span><span class="sxs-lookup"><span data-stu-id="76ed0-119">Because the **Name** property (and its associated other properties) can appear multiple times, use an asterisk (\*) to indicate that this results in multiple records (rather than extracting a bunch of properties into one record):</span></span>

```
    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}
```

<span data-ttu-id="76ed0-120">Bu örnekler, kümesinden `ConvertFrom-String` artık otomatik olarak nesne tabanlı çıkış benzer yapıya sahip giriş dosyalarından ayıklayabilir.</span><span class="sxs-lookup"><span data-stu-id="76ed0-120">From this set of examples, `ConvertFrom-String` can now automatically extract object-based output from input files with similar structure.</span></span>

```powershell
Get-Content .\addresses.output.txt | ConvertFrom-String -TemplateFile .\addresses.template.txt | Format-Table -Auto
```

```output
ExtentText                     Name               City     State
----------                     ----               ----     -----
Ana Trujillo...                Ana Trujillo       Redmond  WA
Antonio Moreno...              Antonio Moreno     Renton   WA
Thomas Hardy...                Thomas Hardy       Seattle  WA
Christina Berglund...          Christina Berglund Redmond  WA
Hanna Moos...                  Hanna Moos         Puyallup WA
```

<span data-ttu-id="76ed0-121">Ayıklanan metin üzerinde ek veri işleme yapmak için **ExtentText** özelliği kendisinden kaydı çıkarılan ham metni yakalar.</span><span class="sxs-lookup"><span data-stu-id="76ed0-121">To do additional data manipulation on extracted text, the **ExtentText** property captures the raw text from which the record was extracted.</span></span> <span data-ttu-id="76ed0-122">Bu özellik hakkında geri bildirim sağlamak veya zorluk örnekler yazmak zorunda içeriği paylaşmak için lütfen e-posta <psdmfb@microsoft.com>.</span><span class="sxs-lookup"><span data-stu-id="76ed0-122">To provide feedback on this feature, or to share content for which you are having difficulty writing examples, please email <psdmfb@microsoft.com>.</span></span>