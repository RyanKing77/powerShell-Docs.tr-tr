---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Çıkış Görünümünü Değiştirmek İçin Biçimlendirme Komutları Kullanma
ms.openlocfilehash: a1712dade1e7508c0c4a004685bd1bb04a126f74
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030066"
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="1c058-103">Çıkış Görünümünü Değiştirmek İçin Biçimlendirme Komutları Kullanma</span><span class="sxs-lookup"><span data-stu-id="1c058-103">Using Format Commands to Change Output View</span></span>

<span data-ttu-id="1c058-104">Windows PowerShell, hangi özellikler belirli nesneler için görüntülenen denetlemenize olanak sağlayan cmdlet'ler kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="1c058-104">Windows PowerShell has a set of cmdlets that allow you to control which properties are displayed for particular objects.</span></span> <span data-ttu-id="1c058-105">Tüm cmdlet'lerin adlarını fiili ile başlayan **biçimi**.</span><span class="sxs-lookup"><span data-stu-id="1c058-105">The names of all the cmdlets begin with the verb **Format**.</span></span> <span data-ttu-id="1c058-106">Gösterilecek bir veya daha fazla özellikler seçmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c058-106">They let you select one or more properties to show.</span></span>

<span data-ttu-id="1c058-107">**Biçimi** cmdlet'leri **biçimi genelinde**, **Format-List**, **Format-Table**, ve **biçim özel**.</span><span class="sxs-lookup"><span data-stu-id="1c058-107">The **Format** cmdlets are **Format-Wide**, **Format-List**, **Format-Table**, and **Format-Custom**.</span></span> <span data-ttu-id="1c058-108">Biz yalnızca anlatmaktadır **biçimi genelinde**, **Format-List**, ve **Format-Table** cmdlet'leri Bu Kullanıcı Kılavuzu'nda.</span><span class="sxs-lookup"><span data-stu-id="1c058-108">We will only describe the **Format-Wide**, **Format-List**, and **Format-Table** cmdlets in this user's guide.</span></span>

<span data-ttu-id="1c058-109">Her biçim cmdlet'inin görüntülemek için belirli özellikler belirtmezseniz, kullanılacak varsayılan özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="1c058-109">Each format cmdlet has default properties that will be used if you do not specify specific properties to display.</span></span> <span data-ttu-id="1c058-110">Her cmdlet de aynı parametre adı kullanır **özelliği**görüntülemek istediğiniz özellikler belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="1c058-110">Each cmdlet also uses the same parameter name, **Property**, to specify which properties you want to display.</span></span> <span data-ttu-id="1c058-111">Çünkü **biçimi genelinde** yalnızca tek bir özelliğe gösterir, **özelliği** parametresi yalnızca özellik parametrelerini ancak tek bir değer alır **Format-List** ve **Format-Table** özellik adlarının bir listesini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="1c058-111">Because **Format-Wide** only shows a single property, its **Property** parameter only takes a single value, but the property parameters of **Format-List** and **Format-Table** will accept a list of property names.</span></span>

<span data-ttu-id="1c058-112">Komutu kullanırsanız **Get-Process - ad powershell** ile iki örnek Windows PowerShell çalıştırma, şuna benzer bir çıktı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="1c058-112">If you use the command **Get-Process -Name powershell** with two instances of Windows PowerShell running, you get output that looks like this:</span></span>

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

<span data-ttu-id="1c058-113">Bu bölümün kalanında, biz nasıl kullanılacağı inceleyeceksiniz **biçimi** bu komutun çıktısı görüntülenir şeklini değiştirmek için cmdlet'ler.</span><span class="sxs-lookup"><span data-stu-id="1c058-113">In the rest of this section, we will explore how to use **Format** cmdlets to change the way the output of this command is displayed.</span></span>

## <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="1c058-114">Biçim genelinde tek öğeli çıkış için kullanma</span><span class="sxs-lookup"><span data-stu-id="1c058-114">Using Format-Wide for Single-Item Output</span></span>

<span data-ttu-id="1c058-115">`Format-Wide` Cmdlet'i, varsayılan olarak, yalnızca bir nesne için varsayılan özelliği görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1c058-115">The `Format-Wide` cmdlet, by default, displays only the default property of an object.</span></span>
<span data-ttu-id="1c058-116">Her nesneyle ilişkili bilgileri tek bir sütunda görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="1c058-116">The information associated with each object is displayed in a single column:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide
```

```output
Format-Custom                          Format-Hex
Format-List                            Format-Table
Format-Wide
```

<span data-ttu-id="1c058-117">Varsayılan olmayan bir özellik de belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1c058-117">You can also specify a non-default property:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```output
Custom                                 Hex
List                                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="1c058-118">Biçim genelinde görüntü sütunu denetleme</span><span class="sxs-lookup"><span data-stu-id="1c058-118">Controlling Format-Wide Display with Column</span></span>

<span data-ttu-id="1c058-119">İle `Format-Wide` cmdlet'i, aynı anda yalnızca tek bir özellik görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c058-119">With the `Format-Wide` cmdlet, you can only display a single property at a time.</span></span>
<span data-ttu-id="1c058-120">Bu, her satırda yalnızca bir öğeyi gösteren basit listelerini görüntülemek için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="1c058-120">This makes it useful for displaying simple lists that show only one element per line.</span></span>
<span data-ttu-id="1c058-121">Basit bir listesini almak için değerini ayarlamak **sütun** yazarak 1 parametresi:</span><span class="sxs-lookup"><span data-stu-id="1c058-121">To get a simple listing, set the value of the **Column** parameter to 1 by typing:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 1
```

```output
Custom
Hex
List
Table
Wide
```

## <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="1c058-122">Bir liste görünümü için biçim listesi kullanma</span><span class="sxs-lookup"><span data-stu-id="1c058-122">Using Format-List for a List View</span></span>

<span data-ttu-id="1c058-123">**Format-List** cmdlet etiketlenmiş ve ayrı bir satıra görüntülenen her bir özellik içeren bir liste biçiminde bir nesne görüntüler:</span><span class="sxs-lookup"><span data-stu-id="1c058-123">The **Format-List** cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

<span data-ttu-id="1c058-124">İstediğiniz sayıda özelliklerini belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1c058-124">You can specify as many properties as you want:</span></span>

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="1c058-125">Biçim listesinde joker karakterlerini kullanarak ayrıntılı bilgilerini alma</span><span class="sxs-lookup"><span data-stu-id="1c058-125">Getting Detailed Information by Using Format-List with Wildcards</span></span>

<span data-ttu-id="1c058-126">**Format-List** cmdlet'i değeri olarak bir joker karakter kullanmanıza imkan tanır, **özelliği** parametresi.</span><span class="sxs-lookup"><span data-stu-id="1c058-126">The **Format-List** cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="1c058-127">Bu, ayrıntılı bilgileri görüntülemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c058-127">This lets you display detailed information.</span></span> <span data-ttu-id="1c058-128">Genellikle, nesneleri, Windows PowerShell, varsayılan olarak tüm özellik değerlerini göstermiyor neden olan ihtiyacınız olandan daha fazla bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="1c058-128">Often, objects include more information than you need, which is why Windows PowerShell does not show all property values by default.</span></span> <span data-ttu-id="1c058-129">Tüm bir nesnenin özelliklerini göstermek için kullanma **Format-List-özellik \&#42;** komutu.</span><span class="sxs-lookup"><span data-stu-id="1c058-129">To show all of properties of an object, use the **Format-List -Property \&#42;** command.</span></span> <span data-ttu-id="1c058-130">Aşağıdaki komut, çıktı tek bir işlem için 60'tan fazla satırları oluşturur:</span><span class="sxs-lookup"><span data-stu-id="1c058-130">The following command generates over 60 lines of output for a single process:</span></span>

```powershell
Get-Process -Name powershell | Format-List -Property *
```

<span data-ttu-id="1c058-131">Ancak **Format-List** komutu, birçok öğeyi içeren çıkış genel bir bakış istediğiniz, daha basit bir tablo görünümüne ise genellikle daha fazla ayrıntı göstermek için kullanışlıdır yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1c058-131">Although the **Format-List** command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

## <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="1c058-132">Biçim tablosu için tablo çıktısı kullanma</span><span class="sxs-lookup"><span data-stu-id="1c058-132">Using Format-Table for Tabular Output</span></span>

<span data-ttu-id="1c058-133">Kullanırsanız **Format-Table** cmdlet hiçbir özellik adı ile belirtilen çıkışını biçimlendirmek için **Get-Process** komutunu tam olarak aynı biçimlendirmeleri yapmadan yaptığınız gibi çıktısını alın.</span><span class="sxs-lookup"><span data-stu-id="1c058-133">If you use the **Format-Table** cmdlet with no property names specified to format the output of the **Get-Process** command, you get exactly the same output as you do without performing any formatting.</span></span> <span data-ttu-id="1c058-134">Çoğu Windows PowerShell nesneleri gibi işlemler genellikle bir tablo biçiminde görüntülenir nedenidir.</span><span class="sxs-lookup"><span data-stu-id="1c058-134">The reason is that processes are usually displayed in a tabular format, as are most Windows PowerShell objects.</span></span>

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="1c058-135">Tablo biçiminde çıktı (AutoSize) geliştirme</span><span class="sxs-lookup"><span data-stu-id="1c058-135">Improving Format-Table Output (AutoSize)</span></span>

<span data-ttu-id="1c058-136">Tablolu bir görünümü birçok karşılaştırılabilir bilgi görüntülemek için kullanışlı olsa da, görüntü verilerini çok darsa yorumlamak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="1c058-136">Although a tabular view is useful for displaying a lot of comparable information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="1c058-137">İşlem yolu, kimlik, ad ve şirket görüntülenecek çalışırsanız, örneğin, kısaltılmış çıktı işlem yolu ve şirket sütun için olursunuz:</span><span class="sxs-lookup"><span data-stu-id="1c058-137">For example, if you try to display process path, ID, name, and company, you get truncated output for the process path and the company column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

<span data-ttu-id="1c058-138">Belirtirseniz **AutoSize** çalıştırdığınızda parametresi **Format-Table** komutu, Windows PowerShell, görüntülenecek seçeceğiz gerçek verilere dayalı sütun genişliklerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="1c058-138">If you specify the **AutoSize** parameter when you run the **Format-Table** command, Windows PowerShell will calculate column widths based on the actual data you are going to display.</span></span> <span data-ttu-id="1c058-139">Böylece **yolu** sütun okunabilir, ancak şirket sütun kesilmiş kalır:</span><span class="sxs-lookup"><span data-stu-id="1c058-139">This makes the **Path** column readable, but the company column remains truncated:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

<span data-ttu-id="1c058-140">**Format-Table** cmdlet veri yine de kesin, ancak bunu yalnızca ekran sonunda bunu yapar.</span><span class="sxs-lookup"><span data-stu-id="1c058-140">The **Format-Table** cmdlet might still truncate data, but it will only do so at the end of the screen.</span></span> <span data-ttu-id="1c058-141">Görüntülenen son farklı özellikler, bunların düzgün görüntülenmesi kendi uzun veri öğesi için gerektiği kadar boyutu verilir.</span><span class="sxs-lookup"><span data-stu-id="1c058-141">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span> <span data-ttu-id="1c058-142">Şirket adı görülebilir ancak yolu konumlarını değiştirme, kısaltılır gördüğünüz **yolu** ve **şirket** içinde **özelliği** değer listesi:</span><span class="sxs-lookup"><span data-stu-id="1c058-142">You can see that company name is visible but path is truncated if you swap the locations of **Path** and **Company** in the **Property** value list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

<span data-ttu-id="1c058-143">**Format-Table** komut varsayar, nearer daha önemli olan özellik listesi başlangıcına özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="1c058-143">The **Format-Table** command assumes that the nearer a property is to the beginning of the property list, the more important it is.</span></span> <span data-ttu-id="1c058-144">Başına en yakın özelliklerini görüntülemek çalışır böylece tamamen.</span><span class="sxs-lookup"><span data-stu-id="1c058-144">So it attempts to display the properties nearest the beginning completely.</span></span> <span data-ttu-id="1c058-145">Varsa **Format-Table** komutu tüm özelliklerini görüntüleme, uyarı ve görüntüden bazı sütunları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1c058-145">If the **Format-Table** command cannot display all the properties, it will remove some columns from the display and provide a warning.</span></span> <span data-ttu-id="1c058-146">Siz bu davranışı gördüğünüz **adı** listesindeki en son özellik:</span><span class="sxs-lookup"><span data-stu-id="1c058-146">You can see this behavior if you make **Name** the last property in the list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

<span data-ttu-id="1c058-147">Yukarıdaki çıktıda kimlik sütunu listenin içine sığması için kesilmiş ve sütun başlıklarından yığılır.</span><span class="sxs-lookup"><span data-stu-id="1c058-147">In the output above, the ID column is truncated to make it fit into the listing, and the column headings are stacked up.</span></span> <span data-ttu-id="1c058-148">Otomatik olarak sütunları yeniden boyutlandırma her zaman, istediğiniz yapmaz.</span><span class="sxs-lookup"><span data-stu-id="1c058-148">Automatically resizing the columns does not always do what you want.</span></span>

### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="1c058-149">Format-Table çıkış sütunları (kaydırma) sarmalama</span><span class="sxs-lookup"><span data-stu-id="1c058-149">Wrapping Format-Table Output in Columns (Wrap)</span></span>

<span data-ttu-id="1c058-150">Uzun zorlayabilirsiniz **Format-Table** kullanarak kendi görüntü sütunu içinde sarmalamak için veri **kaydırma** parametresi.</span><span class="sxs-lookup"><span data-stu-id="1c058-150">You can force lengthy **Format-Table** data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="1c058-151">Kullanarak **kaydırma** parametre tek başına değil gerekmeyen yeterlidir de belirtmezseniz varsayılan ayarları kullandığından, beklediğiniz **AutoSize**:</span><span class="sxs-lookup"><span data-stu-id="1c058-151">Using the **Wrap** parameter alone will not necessarily do what you expect, since it uses default settings if you do not also specify **AutoSize**:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

<span data-ttu-id="1c058-152">Kullanmanın bir avantajı **kaydırma** kendisi tarafından parametredir, çok fazla işleme yavaş değil.</span><span class="sxs-lookup"><span data-stu-id="1c058-152">An advantage of using the **Wrap** parameter by itself is that it does not slow down processing very much.</span></span> <span data-ttu-id="1c058-153">Büyük dizin sistemi özyinelemeli dosya listesini gerçekleştirirseniz, çok uzun sürüyor ve çok miktarda bellek kullanıyorsanız, ilk çıktı öğeleri görüntülemeden önce kullanın **AutoSize**.</span><span class="sxs-lookup"><span data-stu-id="1c058-153">If you perform a recursive file listing of a large directory system, it might take a very long time and use a lot of memory before displaying the first output items if you use **AutoSize**.</span></span>

<span data-ttu-id="1c058-154">Ardından sistem yükü bir kaygınız yoksa **AutoSize** şununla düzgün çalışır **kaydırma** parametresi.</span><span class="sxs-lookup"><span data-stu-id="1c058-154">If you are not concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span> <span data-ttu-id="1c058-155">Başlangıç sütunlarını her zaman tek bir satırda belirttiğinizde olarak, öğeleri görüntülemek gerektiği kadar genişliği ayrılan **AutoSize** olmadan **kaydırma** parametresi.</span><span class="sxs-lookup"><span data-stu-id="1c058-155">The initial columns are always allotted as much width as they need to display items on one line, just as when you specify **AutoSize** without the **Wrap** parameter.</span></span> <span data-ttu-id="1c058-156">Tek fark, gerekirse son sütunu sarmalanır.:</span><span class="sxs-lookup"><span data-stu-id="1c058-156">The only difference is that the final column will be wrapped if necessary:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

<span data-ttu-id="1c058-157">İlk olarak, geniş sütun belirtirseniz, öncelikle küçük veri öğelerini belirtmek güvenli, bu nedenle bazı sütunları görüntülenmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="1c058-157">Some columns might not be displayed if you specify the widest columns first, so it is safest to specify the smallest data elements first.</span></span> <span data-ttu-id="1c058-158">Aşağıdaki örnekte, biz çok geniş bir yol öğesi ilk belirtin ve hatta kaydırma ile biz yine de son kaybetmek **adı** sütun:</span><span class="sxs-lookup"><span data-stu-id="1c058-158">In the following example, we specify the extremely wide path element first, and even with wrapping, we still lose the final **Name** column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

### <a name="organizing-table-output--groupby"></a><span data-ttu-id="1c058-159">Tablo çıkışına düzenleme (-gruplandırma ölçütü)</span><span class="sxs-lookup"><span data-stu-id="1c058-159">Organizing Table Output (-GroupBy)</span></span>

<span data-ttu-id="1c058-160">Tablo çıktısı denetimi için başka bir kullanışlı parametresi **GroupBy**.</span><span class="sxs-lookup"><span data-stu-id="1c058-160">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="1c058-161">Tablo listeleri artık özellikle Karşılaştırılacak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="1c058-161">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="1c058-162">**GroupBy** parametresi çıkışı bir özellik değerine göre gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="1c058-162">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="1c058-163">Örneğin, şu işlemler için daha kolay denetleme özelliği listenin şirket değerini atlayarak şirket tarafından gruplandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1c058-163">For example, we can group processes by company for easier inspection, omitting the company value from the property listing:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```
