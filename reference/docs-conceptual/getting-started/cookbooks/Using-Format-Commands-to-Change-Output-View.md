---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Çıkış Görünümünü Değiştirmek İçin Biçimlendirme Komutları Kullanma
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: 97d3a9e04abb61bb80a0b8c67d9fb9e885a0b91b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="9d876-103">Çıkış Görünümünü Değiştirmek İçin Biçimlendirme Komutları Kullanma</span><span class="sxs-lookup"><span data-stu-id="9d876-103">Using Format Commands to Change Output View</span></span>

<span data-ttu-id="9d876-104">Windows PowerShell hangi özelliklerin belirli nesneler için görüntülenen denetlemenize izin cmdlet'ler kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="9d876-104">Windows PowerShell has a set of cmdlets that allow you to control which properties are displayed for particular objects.</span></span> <span data-ttu-id="9d876-105">Tüm cmdlet'ler adlarını fiil ile başlayan **biçimi**.</span><span class="sxs-lookup"><span data-stu-id="9d876-105">The names of all the cmdlets begin with the verb **Format**.</span></span> <span data-ttu-id="9d876-106">Bunlar göstermek için bir veya daha fazla özellikleri seçmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9d876-106">They let you select one or more properties to show.</span></span>

<span data-ttu-id="9d876-107">**Biçimi** cmdlet'leri **biçimi genelinde**, **Format-List**, **Format-Table**, ve **biçimi-özel**.</span><span class="sxs-lookup"><span data-stu-id="9d876-107">The **Format** cmdlets are **Format-Wide**, **Format-List**, **Format-Table**, and **Format-Custom**.</span></span> <span data-ttu-id="9d876-108">Biz yalnızca anlatmaktadır **biçimi genelinde**, **Format-List**, ve **Format-Table** cmdlet'leri Bu Kullanıcı Kılavuzu'nda.</span><span class="sxs-lookup"><span data-stu-id="9d876-108">We will only describe the **Format-Wide**, **Format-List**, and **Format-Table** cmdlets in this user's guide.</span></span>

<span data-ttu-id="9d876-109">Her biçim cmdlet'ine görüntülemek için belirli özellikler belirtmezseniz, kullanılacak varsayılan özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="9d876-109">Each format cmdlet has default properties that will be used if you do not specify specific properties to display.</span></span> <span data-ttu-id="9d876-110">Her cmdlet de aynı parametre adı kullanan **özelliği**, görüntülemek istediğiniz hangi özelliklerini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="9d876-110">Each cmdlet also uses the same parameter name, **Property**, to specify which properties you want to display.</span></span> <span data-ttu-id="9d876-111">Çünkü **biçimi genelinde** yalnızca tek bir özellik gösterir, **özelliği** parametresi yalnızca özellik parametrelerinin ancak tek bir değer alır **Format-List** ve **Format-Table** özellik adlarının bir listesini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="9d876-111">Because **Format-Wide** only shows a single property, its **Property** parameter only takes a single value, but the property parameters of **Format-List** and **Format-Table** will accept a list of property names.</span></span>

<span data-ttu-id="9d876-112">Komutunu kullanırsanız **Get-Process - ad powershell** Windows PowerShell çalışan iki örnekleriyle şuna benzer bir çıktı alın:</span><span class="sxs-lookup"><span data-stu-id="9d876-112">If you use the command **Get-Process -Name powershell** with two instances of Windows PowerShell running, you get output that looks like this:</span></span>

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

<span data-ttu-id="9d876-113">Bu bölümde kalan biz nasıl kullanılacağını inceleyeceksiniz **biçimi** bu komutun çıktısı görüntülenir şeklini değiştirmek için cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="9d876-113">In the rest of this section, we will explore how to use **Format** cmdlets to change the way the output of this command is displayed.</span></span>

### <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="9d876-114">Biçim genelinde tek öğe çıkışı için kullanma</span><span class="sxs-lookup"><span data-stu-id="9d876-114">Using Format-Wide for Single-Item Output</span></span>

<span data-ttu-id="9d876-115">**Biçimi genelinde** cmdlet'i, varsayılan olarak, yalnızca bir nesnenin varsayılan özelliğine görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9d876-115">The **Format-Wide** cmdlet, by default, displays only the default property of an object.</span></span> <span data-ttu-id="9d876-116">Her nesne ile ilişkili bilgileri tek bir sütunda görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="9d876-116">The information associated with each object is displayed in a single column:</span></span>

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

<span data-ttu-id="9d876-117">Ayrıca, varsayılan olmayan bir özellik belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9d876-117">You can also specify a non-default property:</span></span>

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="9d876-118">Sütun biçimi genelinde ekranıyla denetleme</span><span class="sxs-lookup"><span data-stu-id="9d876-118">Controlling Format-Wide Display with Column</span></span>

<span data-ttu-id="9d876-119">İle **biçimi genelinde** cmdlet, aynı anda yalnızca tek bir özellik görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d876-119">With the **Format-Wide** cmdlet, you can only display a single property at a time.</span></span> <span data-ttu-id="9d876-120">Bu, satır başına yalnızca tek bir öğe Göster basit listelerini görüntülemek için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="9d876-120">This makes it useful for displaying simple lists that show only one element per line.</span></span> <span data-ttu-id="9d876-121">Basit bir listesini almak için değerini ayarlamak **sütun** parametresi yazarak 1:</span><span class="sxs-lookup"><span data-stu-id="9d876-121">To get a simple listing, set the value of the **Column** parameter to 1 by typing:</span></span>

```powershell
Get-Command Format-Wide -Property Name -Column 1
```

### <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="9d876-122">Bir liste görünümü için Format-List kullanma</span><span class="sxs-lookup"><span data-stu-id="9d876-122">Using Format-List for a List View</span></span>

<span data-ttu-id="9d876-123">**Format-List** cmdlet etiketli ve ayrı bir satırda görüntülenen her bir özellik içeren bir liste biçiminde bir nesne görüntüler:</span><span class="sxs-lookup"><span data-stu-id="9d876-123">The **Format-List** cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

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

<span data-ttu-id="9d876-124">İstediğiniz sayıda özelliklerini belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9d876-124">You can specify as many properties as you want:</span></span>

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

#### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="9d876-125">Joker karakter olarak Format-List kullanarak alma ayrıntılı bilgi</span><span class="sxs-lookup"><span data-stu-id="9d876-125">Getting Detailed Information by Using Format-List with Wildcards</span></span>

<span data-ttu-id="9d876-126">**Format-List** cmdlet'i bir joker karakter değeri olarak kullanmanıza imkan tanır kendi **özelliği** parametresi.</span><span class="sxs-lookup"><span data-stu-id="9d876-126">The **Format-List** cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="9d876-127">Bu, ayrıntılı bilgileri görüntülemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d876-127">This lets you display detailed information.</span></span> <span data-ttu-id="9d876-128">Genellikle, Windows PowerShell, varsayılan olarak tüm özellik değerlerini göstermez neden olan gereksinim duyduğunuz daha fazla bilgi nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9d876-128">Often, objects include more information than you need, which is why Windows PowerShell does not show all property values by default.</span></span> <span data-ttu-id="9d876-129">Tüm nesne özelliklerini görüntülemek için kullanın **Format-List-özelliği \&#42;** komutu.</span><span class="sxs-lookup"><span data-stu-id="9d876-129">To show all of properties of an object, use the **Format-List -Property \&#42;** command.</span></span> <span data-ttu-id="9d876-130">Aşağıdaki komut 60 satırlık bir tek bir işlem için çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="9d876-130">The following command generates over 60 lines of output for a single process:</span></span>

```powershell
Get-Process -Name powershell | Format-List -Property *
```

<span data-ttu-id="9d876-131">Ancak **Format-List** komutu çok sayıda öğe içeren çıktı genel bir bakış istediğiniz, daha basit bir tablo görünümü ise genellikle daha fazla ayrıntı, göstermek için yararlıdır yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="9d876-131">Although the **Format-List** command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

### <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="9d876-132">Biçim tablosu için tablo çıktısı kullanarak</span><span class="sxs-lookup"><span data-stu-id="9d876-132">Using Format-Table for Tabular Output</span></span>

<span data-ttu-id="9d876-133">Kullanırsanız **Format-Table** hiçbir özellik adları cmdlet'iyle belirtilen çıktısını biçimlendirmek için **Get-Process** komutu tam olarak aynı herhangi bir biçimlendirme yapmadan yaptığınız gibi çıktısını alırsınız.</span><span class="sxs-lookup"><span data-stu-id="9d876-133">If you use the **Format-Table** cmdlet with no property names specified to format the output of the **Get-Process** command, you get exactly the same output as you do without performing any formatting.</span></span> <span data-ttu-id="9d876-134">Çoğu Windows PowerShell nesneler gibi işlemleri genellikle bir tablo biçiminde görüntülenen nedenidir.</span><span class="sxs-lookup"><span data-stu-id="9d876-134">The reason is that processes are usually displayed in a tabular format, as are most Windows PowerShell objects.</span></span>

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="9d876-135">Tablo Biçimlendir çıkış (AutoSize) artırma</span><span class="sxs-lookup"><span data-stu-id="9d876-135">Improving Format-Table Output (AutoSize)</span></span>

<span data-ttu-id="9d876-136">Bir tablo görünümü çok sayıda karşılaştırılabilir bilgi görüntülemek için yararlı olsa da, görüntü verilerini çok darsa yorumlamaya zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="9d876-136">Although a tabular view is useful for displaying a lot of comparable information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="9d876-137">İşlem yolu, kimliği, ad ve şirket görüntülemeye, örneğin, kesilmiş çıktı işlem yolu ve şirket sütun için alırsınız:</span><span class="sxs-lookup"><span data-stu-id="9d876-137">For example, if you try to display process path, ID, name, and company, you get truncated output for the process path and the company column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

<span data-ttu-id="9d876-138">Belirtirseniz **AutoSize** çalıştırdığınızda parametre **Format-Table** komutu, Windows PowerShell bulacağınızı görüntülemek için gerçek verileri temel alan sütun genişliklerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="9d876-138">If you specify the **AutoSize** parameter when you run the **Format-Table** command, Windows PowerShell will calculate column widths based on the actual data you are going to display.</span></span> <span data-ttu-id="9d876-139">Böylece **yolu** sütun okunabilir ancak şirket sütun kesilmiş kalır:</span><span class="sxs-lookup"><span data-stu-id="9d876-139">This makes the **Path** column readable, but the company column remains truncated:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

<span data-ttu-id="9d876-140">**Format-Table** cmdlet veri hala kesmek, ancak bunu yalnızca ekran sonunda görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="9d876-140">The **Format-Table** cmdlet might still truncate data, but it will only do so at the end of the screen.</span></span> <span data-ttu-id="9d876-141">Görüntülenen son farklı özellikleri düzgün görüntülemek kendi uzun veri öğesi için gerektiği kadar boyutu verilir.</span><span class="sxs-lookup"><span data-stu-id="9d876-141">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span> <span data-ttu-id="9d876-142">Şirket adı görülebilir ancak yolu konumlarını değiştirme, kısaltılır görebilirsiniz **yolu** ve **şirket** içinde **özelliği** değer listesi:</span><span class="sxs-lookup"><span data-stu-id="9d876-142">You can see that company name is visible but path is truncated if you swap the locations of **Path** and **Company** in the **Property** value list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

<span data-ttu-id="9d876-143">**Format-Table** komut varsayar, nearer bir özellik listesi başlangıcına daha önemli olduğunu özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="9d876-143">The **Format-Table** command assumes that the nearer a property is to the beginning of the property list, the more important it is.</span></span> <span data-ttu-id="9d876-144">Başına en yakın özelliklerini görüntülemek deneme şekilde tamamen.</span><span class="sxs-lookup"><span data-stu-id="9d876-144">So it attempts to display the properties nearest the beginning completely.</span></span> <span data-ttu-id="9d876-145">Varsa **Format-Table** komutu tüm özelliklerini görüntüleyemiyor, bu görüntüden bazı sütunları kaldırmak ve bir uyarı sağlayın.</span><span class="sxs-lookup"><span data-stu-id="9d876-145">If the **Format-Table** command cannot display all the properties, it will remove some columns from the display and provide a warning.</span></span> <span data-ttu-id="9d876-146">Bunu yaparsanız, bu davranış görebilirsiniz **adı** listedeki son özellik:</span><span class="sxs-lookup"><span data-stu-id="9d876-146">You can see this behavior if you make **Name** the last property in the list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

<span data-ttu-id="9d876-147">Yukarıdaki çıktıda ID sütunu listenin içine sığması için kesilir ve sütun başlıkları Yığılmış.</span><span class="sxs-lookup"><span data-stu-id="9d876-147">In the output above, the ID column is truncated to make it fit into the listing, and the column headings are stacked up.</span></span> <span data-ttu-id="9d876-148">Otomatik olarak sütunları yeniden boyutlandırma her zaman istediğinizi yapmaz.</span><span class="sxs-lookup"><span data-stu-id="9d876-148">Automatically resizing the columns does not always do what you want.</span></span>

#### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="9d876-149">Kaydırma Tablo Biçimlendir çıkış sütunlarında (kaydırma)</span><span class="sxs-lookup"><span data-stu-id="9d876-149">Wrapping Format-Table Output in Columns (Wrap)</span></span>

<span data-ttu-id="9d876-150">Uzun zorlayabilirsiniz **Format-Table** kullanarak, görüntü sütunu içinde kaydırmak için veri **sarmalamak** parametresi.</span><span class="sxs-lookup"><span data-stu-id="9d876-150">You can force lengthy **Format-Table** data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="9d876-151">Kullanarak **sarmalamak** parametresi tek başına mutlaka yapmaması de belirtmezseniz varsayılan ayarları kullandığından, beklediğiniz **AutoSize**:</span><span class="sxs-lookup"><span data-stu-id="9d876-151">Using the **Wrap** parameter alone will not necessarily do what you expect, since it uses default settings if you do not also specify **AutoSize**:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

<span data-ttu-id="9d876-152">Kullanmanın bir avantajı **sarmalamak** kendisi tarafından parametredir, çok fazla işleme yavaş değil.</span><span class="sxs-lookup"><span data-stu-id="9d876-152">An advantage of using the **Wrap** parameter by itself is that it does not slow down processing very much.</span></span> <span data-ttu-id="9d876-153">Özyinelemeli dosya listesini büyük dizin sistemi gerçekleştirirseniz, çok uzun sürebilir ve kullanıyorsanız ilk çıkış öğeleri görüntülenmeden önce bir miktarda bellek kullanmak **AutoSize**.</span><span class="sxs-lookup"><span data-stu-id="9d876-153">If you perform a recursive file listing of a large directory system, it might take a very long time and use a lot of memory before displaying the first output items if you use **AutoSize**.</span></span>

<span data-ttu-id="9d876-154">Ardından sistem yükü bir kaygınız yoksa **AutoSize** ile iyi çalışır **sarmalamak** parametresi.</span><span class="sxs-lookup"><span data-stu-id="9d876-154">If you are not concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span> <span data-ttu-id="9d876-155">İlk sütun her zaman belirttiğinizde gibi bir satıra öğeleri görüntülemek gerektiği kadar genişliği ayrılan **AutoSize** olmadan **sarmalamak** parametresi.</span><span class="sxs-lookup"><span data-stu-id="9d876-155">The initial columns are always allotted as much width as they need to display items on one line, just as when you specify **AutoSize** without the **Wrap** parameter.</span></span> <span data-ttu-id="9d876-156">Tek fark, gerekirse son sütun sarılır şöyledir:</span><span class="sxs-lookup"><span data-stu-id="9d876-156">The only difference is that the final column will be wrapped if necessary:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

<span data-ttu-id="9d876-157">İlk olarak, en geniş sütunları belirtirseniz, en küçük veri öğeleri ilk belirtmek güvenli olması için bazı sütunları görüntülenmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="9d876-157">Some columns might not be displayed if you specify the widest columns first, so it is safest to specify the smallest data elements first.</span></span> <span data-ttu-id="9d876-158">Aşağıdaki örnekte, biz çok geniş yol öğesi ilk belirtin ve hatta kaydırma ile biz yine son kaybedersiniz **adı** sütun:</span><span class="sxs-lookup"><span data-stu-id="9d876-158">In the following example, we specify the extremely wide path element first, and even with wrapping, we still lose the final **Name** column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### <a name="organizing-table-output--groupby"></a><span data-ttu-id="9d876-159">Tablo çıktısı düzenleme (-GroupBy)</span><span class="sxs-lookup"><span data-stu-id="9d876-159">Organizing Table Output (-GroupBy)</span></span>

<span data-ttu-id="9d876-160">Tablo çıkış denetimi için başka bir yararlı parametresi **GroupBy**.</span><span class="sxs-lookup"><span data-stu-id="9d876-160">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="9d876-161">Artık Tablo listelerini özellikle karşılaştırmak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="9d876-161">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="9d876-162">**GroupBy** parametresi bir özellik değerine dayalı çıktı grupları.</span><span class="sxs-lookup"><span data-stu-id="9d876-162">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="9d876-163">Örneğin, biz işlemler daha kolay denetleme özelliği listenin şirket değerinden atlama şirket tarafından gruplayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d876-163">For example, we can group processes by company for easier inspection, omitting the company value from the property listing:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```