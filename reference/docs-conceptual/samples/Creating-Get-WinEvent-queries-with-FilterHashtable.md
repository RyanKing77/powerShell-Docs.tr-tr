---
ms.date: 3/18/2019
title: FilterHashtable ile Get-WinEvent sorguları oluşturma
ms.openlocfilehash: 28ba3c99a297944003a28eaba7de34b77d9df536
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984230"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a><span data-ttu-id="97a27-102">FilterHashtable ile Get-WinEvent sorguları oluşturma</span><span class="sxs-lookup"><span data-stu-id="97a27-102">Creating Get-WinEvent queries with FilterHashtable</span></span>

<span data-ttu-id="97a27-103">Özgün Haziran 3 2014 okunacak **Scripting Guy** post, blog gönderimize [kullanım FilterHashTable PowerShell ile filtre olay günlüğü için](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span><span class="sxs-lookup"><span data-stu-id="97a27-103">To read the original June 3, 2014 **Scripting Guy** blog post, see [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span></span>

<span data-ttu-id="97a27-104">Bu makalede bir alıntı özgün blog gönderisinin olduğu ve nasıl kullanılacağını açıklar `Get-WinEvent` cmdlet'in **FilterHashtable** olay günlüklerini filtrelemek için parametre.</span><span class="sxs-lookup"><span data-stu-id="97a27-104">This article is an excerpt of the original blog post and explains how to use the `Get-WinEvent` cmdlet's **FilterHashtable** parameter to filter event logs.</span></span> <span data-ttu-id="97a27-105">PowerShell'in `Get-WinEvent` cmdlet'tir Windows olay ve tanılama günlüklerini filtrelemek için güçlü bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="97a27-105">PowerShell's `Get-WinEvent` cmdlet is a powerful method to filter Windows event and diagnostic logs.</span></span> <span data-ttu-id="97a27-106">Performansı artıran bir `Get-WinEvent` sorgu kullandığı **FilterHashtable** parametresi.</span><span class="sxs-lookup"><span data-stu-id="97a27-106">Performance improves when a `Get-WinEvent` query uses the **FilterHashtable** parameter.</span></span>

<span data-ttu-id="97a27-107">Büyük olay günlükleri ile çalışırken, bu işlem hattına aşağı nesneleri göndermek için etkin değil bir `Where-Object` komutu.</span><span class="sxs-lookup"><span data-stu-id="97a27-107">When you work with large event logs, it's not efficient to send objects down the pipeline to a `Where-Object` command.</span></span> <span data-ttu-id="97a27-108">PowerShell 6'da önce `Get-EventLog` cmdlet'i olan günlük verilerini almak için başka bir seçenek.</span><span class="sxs-lookup"><span data-stu-id="97a27-108">Prior to PowerShell 6, the `Get-EventLog` cmdlet was another option to get log data.</span></span> <span data-ttu-id="97a27-109">Örneğin, aşağıdaki komutları için filtre verimsiz **Microsoft-Windows-birleştirme** günlükleri:</span><span class="sxs-lookup"><span data-stu-id="97a27-109">For example, the following commands are inefficient to filter the **Microsoft-Windows-Defrag** logs:</span></span>

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

<span data-ttu-id="97a27-110">Aşağıdaki komut, performansı geliştiren bir karma tablo kullanır:</span><span class="sxs-lookup"><span data-stu-id="97a27-110">The following command uses a hash table that improves the performance:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a><span data-ttu-id="97a27-111">Blog gönderileri numaralandırması</span><span class="sxs-lookup"><span data-stu-id="97a27-111">Blog posts about enumeration</span></span>

<span data-ttu-id="97a27-112">Bu makalede, numaralandırılmış değerlerin bir karma tablosunda kullanma hakkında bilgi gösterir.</span><span class="sxs-lookup"><span data-stu-id="97a27-112">This article presents information about how to use enumerated values in a hash table.</span></span> <span data-ttu-id="97a27-113">Bu sabit listesi hakkında daha fazla bilgi için okuma **Scripting Guy** blog gönderilerimize göz atın.</span><span class="sxs-lookup"><span data-stu-id="97a27-113">For more information about enumeration, read these **Scripting Guy** blog posts.</span></span> <span data-ttu-id="97a27-114">Numaralandırılmış değerler döndüren bir işlev oluşturmak için bkz [sabit listeleri ve değerleri](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span><span class="sxs-lookup"><span data-stu-id="97a27-114">To create a function that returns the enumerated values, see [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span></span>
<span data-ttu-id="97a27-115">Daha fazla bilgi için [Scripting Guy dizi blog yazılarını numaralandırma hakkında](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span><span class="sxs-lookup"><span data-stu-id="97a27-115">For more information, see the [Scripting Guy series of blog posts about enumeration](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span></span>

## <a name="hash-table-keyvalue-pairs"></a><span data-ttu-id="97a27-116">Karma tablo anahtar/değer çiftleri</span><span class="sxs-lookup"><span data-stu-id="97a27-116">Hash table key/value pairs</span></span>

<span data-ttu-id="97a27-117">Verimli sorgular derlemek için kullanma `Get-WinEvent` cmdlet'iyle **FilterHashtable** parametresi.</span><span class="sxs-lookup"><span data-stu-id="97a27-117">To build efficient queries, use the `Get-WinEvent` cmdlet with the **FilterHashtable** parameter.</span></span>
<span data-ttu-id="97a27-118">**FilterHashtable** karma tablo belirli bilgileri Windows olay günlüklerini almak için bir filtre olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="97a27-118">**FilterHashtable** accepts a hash table as a filter to get specific information from Windows event logs.</span></span> <span data-ttu-id="97a27-119">Bir karma tablo kullandığı **anahtar/değer** çiftleri.</span><span class="sxs-lookup"><span data-stu-id="97a27-119">A hash table uses **key/value** pairs.</span></span> <span data-ttu-id="97a27-120">Karma tabloları hakkında daha fazla bilgi için bkz. [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="97a27-120">For more information about hash tables, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="97a27-121">Varsa **anahtar/değer** çiftleridir aynı satırda, noktalı virgülle ayrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="97a27-121">If the **key/value** pairs are on the same line, they must be separated by a semicolon.</span></span> <span data-ttu-id="97a27-122">Her varsa **anahtar/değer** çifti ayrı bir satırda, noktalı virgül gerekmez.</span><span class="sxs-lookup"><span data-stu-id="97a27-122">If each **key/value** pair is on a separate line, the semicolon isn't needed.</span></span> <span data-ttu-id="97a27-123">Örneğin, bu makalede yerleştirir **anahtar/değer** çiftlerini ayrı satırlarda ve noktalı kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="97a27-123">For example, this article places **key/value** pairs on separate lines and doesn't use semicolons.</span></span>

<span data-ttu-id="97a27-124">Bu örnek, birkaç kullanmaktadır **FilterHashtable** parametrenin **anahtar/değer** çiftleri.</span><span class="sxs-lookup"><span data-stu-id="97a27-124">This sample uses several of the **FilterHashtable** parameter's **key/value** pairs.</span></span> <span data-ttu-id="97a27-125">Tamamlanan sorgu içeren **günlükadı**, **ProviderName**, **anahtar sözcükleri**, **kimliği**, ve **düzeyi**.</span><span class="sxs-lookup"><span data-stu-id="97a27-125">The completed query includes **LogName**, **ProviderName**, **Keywords**, **ID**, and **Level**.</span></span>

<span data-ttu-id="97a27-126">Kabul edilen **anahtar/değer** çiftleri aşağıdaki tabloda gösterilen ve belgeler için dahil edilen [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parametre.</span><span class="sxs-lookup"><span data-stu-id="97a27-126">The accepted **key/value** pairs are shown in the following table and are included in the documentation for the [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parameter.</span></span>

<span data-ttu-id="97a27-127">Aşağıdaki tabloda, anahtar adları, veri türleri görüntüler ve joker karakterler için veri değeri olup olmadığı kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="97a27-127">The following table displays the key names, data types, and whether wildcard characters are accepted for a data value.</span></span>

| <span data-ttu-id="97a27-128">Anahtar adı</span><span class="sxs-lookup"><span data-stu-id="97a27-128">Key name</span></span>     | <span data-ttu-id="97a27-129">Değer veri türü</span><span class="sxs-lookup"><span data-stu-id="97a27-129">Value data type</span></span>    | <span data-ttu-id="97a27-130">Joker karakterler kabul ediyor mu?</span><span class="sxs-lookup"><span data-stu-id="97a27-130">Accepts wildcard characters?</span></span> |
|------------- | ------------------ | ---------------------------- |
| <span data-ttu-id="97a27-131">Günlükadı</span><span class="sxs-lookup"><span data-stu-id="97a27-131">LogName</span></span>      | `<String[]>`       | <span data-ttu-id="97a27-132">Evet</span><span class="sxs-lookup"><span data-stu-id="97a27-132">Yes</span></span> |
| <span data-ttu-id="97a27-133">ProviderName</span><span class="sxs-lookup"><span data-stu-id="97a27-133">ProviderName</span></span> | `<String[]>`       | <span data-ttu-id="97a27-134">Evet</span><span class="sxs-lookup"><span data-stu-id="97a27-134">Yes</span></span> |
| <span data-ttu-id="97a27-135">Yol</span><span class="sxs-lookup"><span data-stu-id="97a27-135">Path</span></span>         | `<String[]>`       | <span data-ttu-id="97a27-136">Hayır</span><span class="sxs-lookup"><span data-stu-id="97a27-136">No</span></span>  |
| <span data-ttu-id="97a27-137">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="97a27-137">Keywords</span></span>     | `<Long[]>`         | <span data-ttu-id="97a27-138">Hayır</span><span class="sxs-lookup"><span data-stu-id="97a27-138">No</span></span>  |
| <span data-ttu-id="97a27-139">ID</span><span class="sxs-lookup"><span data-stu-id="97a27-139">ID</span></span>           | `<Int32[]>`        | <span data-ttu-id="97a27-140">Hayır</span><span class="sxs-lookup"><span data-stu-id="97a27-140">No</span></span>  |
| <span data-ttu-id="97a27-141">Düzey</span><span class="sxs-lookup"><span data-stu-id="97a27-141">Level</span></span>        | `<Int32[]>`        | <span data-ttu-id="97a27-142">Hayır</span><span class="sxs-lookup"><span data-stu-id="97a27-142">No</span></span>  |
| <span data-ttu-id="97a27-143">startTime</span><span class="sxs-lookup"><span data-stu-id="97a27-143">StartTime</span></span>    | `<DateTime>`       | <span data-ttu-id="97a27-144">Hayır</span><span class="sxs-lookup"><span data-stu-id="97a27-144">No</span></span>  |
| <span data-ttu-id="97a27-145">EndTime</span><span class="sxs-lookup"><span data-stu-id="97a27-145">EndTime</span></span>      | `<DateTime>`       | <span data-ttu-id="97a27-146">Hayır</span><span class="sxs-lookup"><span data-stu-id="97a27-146">No</span></span>  |
| <span data-ttu-id="97a27-147">Kullanıcı Kimliği</span><span class="sxs-lookup"><span data-stu-id="97a27-147">UserID</span></span>       | `<SID>`            | <span data-ttu-id="97a27-148">Hayır</span><span class="sxs-lookup"><span data-stu-id="97a27-148">No</span></span>  |
| <span data-ttu-id="97a27-149">Veriler</span><span class="sxs-lookup"><span data-stu-id="97a27-149">Data</span></span>         | `<String[]>`       | <span data-ttu-id="97a27-150">Hayır</span><span class="sxs-lookup"><span data-stu-id="97a27-150">No</span></span>  |
| *            | `<String[]>`       | <span data-ttu-id="97a27-151">Hayır</span><span class="sxs-lookup"><span data-stu-id="97a27-151">No</span></span>  |

## <a name="building-a-query-with-a-hash-table"></a><span data-ttu-id="97a27-152">Bir karma tablo içeren bir sorgu oluşturma</span><span class="sxs-lookup"><span data-stu-id="97a27-152">Building a query with a hash table</span></span>

<span data-ttu-id="97a27-153">Sonuçları doğrulamak ve sorunları gidermek için karma tablosu oluşturmak için Yardım ettiği **anahtar/değer** birer birer çifti.</span><span class="sxs-lookup"><span data-stu-id="97a27-153">To verify results and troubleshoot problems, it helps to build the hash table one **key/value** pair at a time.</span></span> <span data-ttu-id="97a27-154">Verilerden sorguyu alır **uygulama** günlük.</span><span class="sxs-lookup"><span data-stu-id="97a27-154">The query gets data from the **Application** log.</span></span> <span data-ttu-id="97a27-155">Karma tablo eşdeğerdir `Get-WinEvent –LogName Application`.</span><span class="sxs-lookup"><span data-stu-id="97a27-155">The hash table is equivalent to `Get-WinEvent –LogName Application`.</span></span>

<span data-ttu-id="97a27-156">Başlamak için oluşturmanız `Get-WinEvent` sorgu.</span><span class="sxs-lookup"><span data-stu-id="97a27-156">To begin, create the `Get-WinEvent` query.</span></span> <span data-ttu-id="97a27-157">Kullanım **FilterHashtable** parametrenin **anahtar/değer** pair anahtarla **günlükadı**, değeri **uygulama**.</span><span class="sxs-lookup"><span data-stu-id="97a27-157">Use the **FilterHashtable** parameter's **key/value** pair with the key, **LogName**, and the value, **Application**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

<span data-ttu-id="97a27-158">İle karma tablo oluşturmaya devam **ProviderName** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="97a27-158">Continue to build the hash table with the **ProviderName** key.</span></span> <span data-ttu-id="97a27-159">**ProviderName** görünen adı **kaynak** alanındaki **Windows Olay Görüntüleyicisi'ni**.</span><span class="sxs-lookup"><span data-stu-id="97a27-159">The **ProviderName** is the name that appears in the **Source** field in the **Windows Event Viewer**.</span></span> <span data-ttu-id="97a27-160">Örneğin, **.NET çalışma zamanı** aşağıdaki ekran görüntüsünde:</span><span class="sxs-lookup"><span data-stu-id="97a27-160">For example, **.NET Runtime** in the following screenshot:</span></span>

![Windows Olay Görüntüleyicisi'ni kaynakları görüntüsü.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

<span data-ttu-id="97a27-162">Karma tablo güncelleştirin ve dahil **anahtar/değer** pair anahtarla \*\* ProviderName, değeri **.NET çalışma zamanı**.</span><span class="sxs-lookup"><span data-stu-id="97a27-162">Update the hash table and include the **key/value** pair with the key, \*\*ProviderName, and the value, **.NET Runtime**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

<span data-ttu-id="97a27-163">Sorgunuzu arşivlenen olay günlüklerinden veri almak gerekiyorsa kullanın **yolu** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="97a27-163">If your query needs to get data from archived event logs, use the **Path** key.</span></span> <span data-ttu-id="97a27-164">**Yolu** değeri günlük dosyasının tam yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="97a27-164">The **Path** value specifies the full path to the log file.</span></span> <span data-ttu-id="97a27-165">Daha fazla bilgi için **Scripting Guy** blog gönderisi [PowerShell kullanarak için ayrıştırma kaydedilen hataları için olay günlüklerini](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span><span class="sxs-lookup"><span data-stu-id="97a27-165">For more information, see the **Scripting Guy** blog post, [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span></span>

## <a name="using-enumerated-values-in-a-hash-table"></a><span data-ttu-id="97a27-166">Bir karma tabloda listelenmiş değerler kullanarak</span><span class="sxs-lookup"><span data-stu-id="97a27-166">Using enumerated values in a hash table</span></span>

<span data-ttu-id="97a27-167">**Anahtar sözcükler** karma tablosundaki sonraki anahtardır.</span><span class="sxs-lookup"><span data-stu-id="97a27-167">**Keywords** is the next key in the hash table.</span></span> <span data-ttu-id="97a27-168">**Anahtar sözcükleri** veri türü olan bir dizi `[long]` değeri tutan çok sayıda türüdür.</span><span class="sxs-lookup"><span data-stu-id="97a27-168">The **Keywords** data type is an array of the `[long]` value type that holds a large number.</span></span> <span data-ttu-id="97a27-169">En büyük değerini bulmak için aşağıdaki komutu kullanın `[long]`:</span><span class="sxs-lookup"><span data-stu-id="97a27-169">Use the following command to find the maximum value of `[long]`:</span></span>

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

<span data-ttu-id="97a27-170">İçin **anahtar sözcükleri** anahtar, PowerShell, bir dize olmak üzere bir sayı gibi kullanan **güvenlik**.</span><span class="sxs-lookup"><span data-stu-id="97a27-170">For the **Keywords** key, PowerShell uses a number, not a string such as **Security**.</span></span> <span data-ttu-id="97a27-171">**Windows Olay Görüntüleyicisi'ni** görüntüler **anahtar sözcükleri** olarak dizeler, ancak bunlar numaralandırılmış değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="97a27-171">**Windows Event Viewer** displays the **Keywords** as strings, but they are enumerated values.</span></span> <span data-ttu-id="97a27-172">Kullanırsanız karma tablosundaki **anahtar sözcükleri** anahtar bir dize değeri ile bir hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="97a27-172">In the hash table, if you use the **Keywords** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="97a27-173">Açık **Windows Olay Görüntüleyicisi'ni** ve **eylemleri** bölmesinde, tıklayarak **geçerli günlüğü Filtrele**.</span><span class="sxs-lookup"><span data-stu-id="97a27-173">Open the **Windows Event Viewer** and from the **Actions** pane, click on **Filter current log**.</span></span>
<span data-ttu-id="97a27-174">**Anahtar sözcükleri** aşağıdaki ekran görüntüsünde gösterildiği gibi açılan menü görüntüler kullanılabilir anahtar sözcükler:</span><span class="sxs-lookup"><span data-stu-id="97a27-174">The **Keywords** drop-down menu displays the available keywords, as shown in the following screenshot:</span></span>

![Windows Olay Görüntüleyicisi'ni anahtar sözcükleri görüntüsü.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

<span data-ttu-id="97a27-176">Görüntülemek için aşağıdaki komutu kullanın `StandardEventKeywords` özellik adları.</span><span class="sxs-lookup"><span data-stu-id="97a27-176">Use the following command to display the `StandardEventKeywords` property names.</span></span>

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

<span data-ttu-id="97a27-177">Numaralandırılmış değerler bölümünde belgelendirilen **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="97a27-177">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="97a27-178">Daha fazla bilgi için [StandardEventKeywords numaralandırma](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="97a27-178">For more information, see [StandardEventKeywords Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="97a27-179">**Anahtar sözcükleri** adları ve listelenmiş değerler aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="97a27-179">The **Keywords** names and enumerated values are as follows:</span></span>

| <span data-ttu-id="97a27-180">Adı</span><span class="sxs-lookup"><span data-stu-id="97a27-180">Name</span></span>             |  <span data-ttu-id="97a27-181">Değer</span><span class="sxs-lookup"><span data-stu-id="97a27-181">Value</span></span>            |
| ---------------- | ------------------|
| <span data-ttu-id="97a27-182">AuditFailure</span><span class="sxs-lookup"><span data-stu-id="97a27-182">AuditFailure</span></span>     | <span data-ttu-id="97a27-183">4503599627370496</span><span class="sxs-lookup"><span data-stu-id="97a27-183">4503599627370496</span></span>  |
| <span data-ttu-id="97a27-184">AuditSuccess</span><span class="sxs-lookup"><span data-stu-id="97a27-184">AuditSuccess</span></span>     | <span data-ttu-id="97a27-185">9007199254740992</span><span class="sxs-lookup"><span data-stu-id="97a27-185">9007199254740992</span></span>  |
| <span data-ttu-id="97a27-186">CorrelationHint2</span><span class="sxs-lookup"><span data-stu-id="97a27-186">CorrelationHint2</span></span> | <span data-ttu-id="97a27-187">18014398509481984</span><span class="sxs-lookup"><span data-stu-id="97a27-187">18014398509481984</span></span> |
| <span data-ttu-id="97a27-188">EventLogClassic</span><span class="sxs-lookup"><span data-stu-id="97a27-188">EventLogClassic</span></span>  | <span data-ttu-id="97a27-189">36028797018963968</span><span class="sxs-lookup"><span data-stu-id="97a27-189">36028797018963968</span></span> |
| <span data-ttu-id="97a27-190">SQM</span><span class="sxs-lookup"><span data-stu-id="97a27-190">Sqm</span></span>              | <span data-ttu-id="97a27-191">2251799813685248</span><span class="sxs-lookup"><span data-stu-id="97a27-191">2251799813685248</span></span>  |
| <span data-ttu-id="97a27-192">WdiDiagnostic</span><span class="sxs-lookup"><span data-stu-id="97a27-192">WdiDiagnostic</span></span>    | <span data-ttu-id="97a27-193">1125899906842624</span><span class="sxs-lookup"><span data-stu-id="97a27-193">1125899906842624</span></span>  |
| <span data-ttu-id="97a27-194">WdiContext</span><span class="sxs-lookup"><span data-stu-id="97a27-194">WdiContext</span></span>       | <span data-ttu-id="97a27-195">562949953421312</span><span class="sxs-lookup"><span data-stu-id="97a27-195">562949953421312</span></span>   |
| <span data-ttu-id="97a27-196">Yanıt süresi</span><span class="sxs-lookup"><span data-stu-id="97a27-196">ResponseTime</span></span>     | <span data-ttu-id="97a27-197">281474976710656</span><span class="sxs-lookup"><span data-stu-id="97a27-197">281474976710656</span></span>   |
| <span data-ttu-id="97a27-198">Yok</span><span class="sxs-lookup"><span data-stu-id="97a27-198">None</span></span>             | <span data-ttu-id="97a27-199">0</span><span class="sxs-lookup"><span data-stu-id="97a27-199">0</span></span>                 |

<span data-ttu-id="97a27-200">Karma tablo güncelleştirin ve dahil **anahtar/değer** pair anahtarla **anahtar sözcükleri**ve **EventLogClassic** numaralandırma değeri **36028797018963968** .</span><span class="sxs-lookup"><span data-stu-id="97a27-200">Update the hash table and include the **key/value** pair with the key, **Keywords**, and the **EventLogClassic** enumeration value, **36028797018963968**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a><span data-ttu-id="97a27-201">Anahtar sözcükler statik özellik değeri (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="97a27-201">Keywords static property value (optional)</span></span>

<span data-ttu-id="97a27-202">**Anahtar sözcükleri** anahtar listelenmiş, ancak statik özellik adı karma tablo sorgusu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97a27-202">The **Keywords** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="97a27-203">Döndürülen dize kullanmak yerine, özellik adı ile bir değere dönüştürülmelidir **Value__** özelliği.</span><span class="sxs-lookup"><span data-stu-id="97a27-203">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="97a27-204">Örneğin, aşağıdaki kullanan betik **Value__** özelliği.</span><span class="sxs-lookup"><span data-stu-id="97a27-204">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a><span data-ttu-id="97a27-205">Olay kimliğine göre filtreleme</span><span class="sxs-lookup"><span data-stu-id="97a27-205">Filtering by Event Id</span></span>

<span data-ttu-id="97a27-206">Daha belirli verileri almak için sorgu sonuçlarına göre filtrelenir **öğesini belirten Olay No.**. **Öğesini belirten Olay No.** karma tablo anahtarı olarak anılan **kimliği** ve belirli bir değerdir **öğesini belirten Olay No.**. **Windows Olay Görüntüleyicisi'ni** görüntüler **öğesini belirten Olay No.**. Bu örnekte **olay kimliği 1023**.</span><span class="sxs-lookup"><span data-stu-id="97a27-206">To get more specific data, the query's results are filtered by **Event Id**. The **Event Id** is referenced in the hash table as the key **ID** and the value is a specific **Event Id**. The **Windows Event Viewer** displays the **Event Id**. This example uses **Event Id 1023**.</span></span>

<span data-ttu-id="97a27-207">Karma tablo güncelleştirin ve dahil **anahtar/değer** pair anahtarla **kimliği** değeri **1023**.</span><span class="sxs-lookup"><span data-stu-id="97a27-207">Update the hash table and include the **key/value** pair with the key, **ID** and the value, **1023**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a><span data-ttu-id="97a27-208">Düzeye göre filtreleme</span><span class="sxs-lookup"><span data-stu-id="97a27-208">Filtering by Level</span></span>

<span data-ttu-id="97a27-209">Daha ayrıntılı sonuçları daraltmak ve hataları olan olayları dahil için kullandığınız **düzeyi** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="97a27-209">To further refine the results and include only events that are errors, use the **Level** key.</span></span>
<span data-ttu-id="97a27-210">**Windows Olay Görüntüleyicisi'ni** görüntüler **düzeyi** gibi dize değerleri, ancak bunlar numaralandırılmış değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="97a27-210">**Windows Event Viewer** displays the **Level** as string values, but they are enumerated values.</span></span> <span data-ttu-id="97a27-211">Kullanırsanız karma tablosundaki **düzeyi** anahtar bir dize değeri ile bir hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="97a27-211">In the hash table, if you use the **Level** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="97a27-212">**Düzey** değerleri gibi sahip **hata**, **uyarı**, veya **bilgilendirici**.</span><span class="sxs-lookup"><span data-stu-id="97a27-212">**Level** has values such as **Error**, **Warning**, or **Informational**.</span></span> <span data-ttu-id="97a27-213">Görüntülemek için aşağıdaki komutu kullanın `StandardEventLevel` özellik adları.</span><span class="sxs-lookup"><span data-stu-id="97a27-213">Use the following command to display the `StandardEventLevel` property names.</span></span>

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

<span data-ttu-id="97a27-214">Numaralandırılmış değerler bölümünde belgelendirilen **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="97a27-214">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="97a27-215">Daha fazla bilgi için [StandardEventLevel numaralandırma](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="97a27-215">For more information, see [StandardEventLevel Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="97a27-216">**Düzeyi** anahtarının adları ve listelenmiş değerler aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="97a27-216">The **Level** key's names and enumerated values are as follows:</span></span>

| <span data-ttu-id="97a27-217">Adı</span><span class="sxs-lookup"><span data-stu-id="97a27-217">Name</span></span>           | <span data-ttu-id="97a27-218">Değer</span><span class="sxs-lookup"><span data-stu-id="97a27-218">Value</span></span> |
| -------------- | ----- |
| <span data-ttu-id="97a27-219">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="97a27-219">Verbose</span></span>        |   <span data-ttu-id="97a27-220">5</span><span class="sxs-lookup"><span data-stu-id="97a27-220">5</span></span>   |
| <span data-ttu-id="97a27-221">Bilgi</span><span class="sxs-lookup"><span data-stu-id="97a27-221">Informational</span></span>  |   <span data-ttu-id="97a27-222">4</span><span class="sxs-lookup"><span data-stu-id="97a27-222">4</span></span>   |
| <span data-ttu-id="97a27-223">Uyarı</span><span class="sxs-lookup"><span data-stu-id="97a27-223">Warning</span></span>        |   <span data-ttu-id="97a27-224">3</span><span class="sxs-lookup"><span data-stu-id="97a27-224">3</span></span>   |
| <span data-ttu-id="97a27-225">Hata</span><span class="sxs-lookup"><span data-stu-id="97a27-225">Error</span></span>          |   <span data-ttu-id="97a27-226">2</span><span class="sxs-lookup"><span data-stu-id="97a27-226">2</span></span>   |
| <span data-ttu-id="97a27-227">Kritik</span><span class="sxs-lookup"><span data-stu-id="97a27-227">Critical</span></span>       |   <span data-ttu-id="97a27-228">1</span><span class="sxs-lookup"><span data-stu-id="97a27-228">1</span></span>   |
| <span data-ttu-id="97a27-229">LogAlways</span><span class="sxs-lookup"><span data-stu-id="97a27-229">LogAlways</span></span>      |   <span data-ttu-id="97a27-230">0</span><span class="sxs-lookup"><span data-stu-id="97a27-230">0</span></span>   |

<span data-ttu-id="97a27-231">Tamamlanan sorgu için karma tablo anahtarı içeren **düzeyi**, değeri **2**.</span><span class="sxs-lookup"><span data-stu-id="97a27-231">The hash table for the completed query includes the key, **Level**, and the value, **2**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a><span data-ttu-id="97a27-232">Sabit listesi (isteğe bağlı) statik özellik düzeyi</span><span class="sxs-lookup"><span data-stu-id="97a27-232">Level static property in enumeration (optional)</span></span>

<span data-ttu-id="97a27-233">**Düzeyi** anahtar listelenmiş, ancak statik özellik adı karma tablo sorgusu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97a27-233">The **Level** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="97a27-234">Döndürülen dize kullanmak yerine, özellik adı ile bir değere dönüştürülmelidir **Value__** özelliği.</span><span class="sxs-lookup"><span data-stu-id="97a27-234">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="97a27-235">Örneğin, aşağıdaki kullanan betik **Value__** özelliği.</span><span class="sxs-lookup"><span data-stu-id="97a27-235">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```