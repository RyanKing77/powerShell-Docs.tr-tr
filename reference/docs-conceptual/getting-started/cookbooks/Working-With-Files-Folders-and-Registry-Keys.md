---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Dosyalar klasörler ve kayıt defteri anahtarları ile çalışma"
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: 22a2390686659033bfd8b02a151b3397cfd46a22
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="working-with-files-folders-and-registry-keys"></a><span data-ttu-id="4f27b-103">Dosyalar, klasörler ve kayıt defteri anahtarları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="4f27b-103">Working With Files, Folders and Registry Keys</span></span>
<span data-ttu-id="4f27b-104">Windows PowerShell kullanan isim **öğesi** bir Windows PowerShell sürücüsünde bulunan öğeler başvurmak için.</span><span class="sxs-lookup"><span data-stu-id="4f27b-104">Windows PowerShell uses the noun **Item** to refer to items found on a Windows PowerShell drive.</span></span> <span data-ttu-id="4f27b-105">Windows PowerShell dosya sistemi sağlayıcısı ile ilgilenirken bir **öğesi** bir dosya, klasör veya Windows PowerShell sürücüsünü olabilir.</span><span class="sxs-lookup"><span data-stu-id="4f27b-105">When dealing with the Windows PowerShell FileSystem provider, an **Item** might be a file, a folder, or the Windows PowerShell drive.</span></span> <span data-ttu-id="4f27b-106">Bu görevler ayrıntılı tartışmak istiyoruz şekilde listesi ve bu öğeleri ile çalışma bir kritik temel çoğu yönetim ayarları'nda görevdir.</span><span class="sxs-lookup"><span data-stu-id="4f27b-106">Listing and working with these items is a critical basic task in most administrative settings, so we want to discuss these tasks in detail.</span></span>

### <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a><span data-ttu-id="4f27b-107">Dosyalar, klasörler ve kayıt defteri anahtarları (Get-Childıtem) numaralandırma</span><span class="sxs-lookup"><span data-stu-id="4f27b-107">Enumerating Files, Folders, and Registry Keys (Get-ChildItem)</span></span>
<span data-ttu-id="4f27b-108">Belirli bir konumdan öğeleri koleksiyonu alma gibi bir ortak görevi olduğundan **Get-Childıtem** cmdlet, özellikle bir klasörü gibi bir kapsayıcı içinde bulunan tüm öğeleri döndürmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4f27b-108">Since getting a collection of items from a particular location is such a common task, the **Get-ChildItem** cmdlet is designed specifically to return all items found within a container such as a folder.</span></span>

<span data-ttu-id="4f27b-109">Tüm dosya ve klasörlerin doğrudan klasördeki C: içerdiği dönmek isterseniz\\Windows, türü:</span><span class="sxs-lookup"><span data-stu-id="4f27b-109">If you want to return all files and folders that are contained directly within the folder C:\\Windows, type:</span></span>

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

<span data-ttu-id="4f27b-110">Liste, girdiğiniz zaman gördüğünüz için benzer **dir** komutunu **Cmd.exe**, veya **ls** UNIX komut kabuğunda komutu.</span><span class="sxs-lookup"><span data-stu-id="4f27b-110">The listing looks similar to what you would see when you enter the **dir** command in **Cmd.exe**, or the **ls** command in a UNIX command shell.</span></span>

<span data-ttu-id="4f27b-111">Parametreleri kullanarak çok karmaşık listelerini gerçekleştirebileceğiniz **Get-Childıtem** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="4f27b-111">You can perform very complex listings by using parameters of the **Get-ChildItem** cmdlet.</span></span> <span data-ttu-id="4f27b-112">Biz birkaç senaryolarında sonraki arar.</span><span class="sxs-lookup"><span data-stu-id="4f27b-112">We will look at a few scenarios next.</span></span> <span data-ttu-id="4f27b-113">Sözdizimi görebilirsiniz **Get-Childıtem** yazarak cmdlet:</span><span class="sxs-lookup"><span data-stu-id="4f27b-113">You can see the syntax the **Get-ChildItem** cmdlet by typing:</span></span>

```
PS> Get-Command -Name Get-ChildItem -Syntax
```

<span data-ttu-id="4f27b-114">Bu parametreler, karma ve yüksek oranda özelleştirilmiş çıkış almak için eşleşmedi.</span><span class="sxs-lookup"><span data-stu-id="4f27b-114">These parameters can be mixed and matched to get highly customized output.</span></span>

#### <a name="listing-all-contained-items--recurse"></a><span data-ttu-id="4f27b-115">Tüm bulunan öğeleri listeleme (-Recurse)</span><span class="sxs-lookup"><span data-stu-id="4f27b-115">Listing all Contained Items (-Recurse)</span></span>
<span data-ttu-id="4f27b-116">Öğeleri bir Windows klasörü içinde ve alt klasörlerin içinde bulunan tüm öğeleri görmek için **Recurse** parametresinin **Get-Childıtem**.</span><span class="sxs-lookup"><span data-stu-id="4f27b-116">To see both the items inside a Windows folder and any items that are contained within the subfolders, use the **Recurse** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="4f27b-117">Listenin her şeyi Windows klasöründeki ve onun alt klasörlerindeki öğelerde içinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4f27b-117">The listing displays everything within the Windows folder and the items in its subfolders.</span></span> <span data-ttu-id="4f27b-118">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="4f27b-118">For example:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

#### <a name="filtering-items-by-name--name"></a><span data-ttu-id="4f27b-119">Öğeleri ada göre filtreleme (-Name)</span><span class="sxs-lookup"><span data-stu-id="4f27b-119">Filtering Items by Name (-Name)</span></span>
<span data-ttu-id="4f27b-120">Yalnızca öğelerin adlarını görüntülemek için kullanın **adı** parametresinin **Get-Childıtem**:</span><span class="sxs-lookup"><span data-stu-id="4f27b-120">To display only the names of items, use the **Name** parameter of **Get-Childitem**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

#### <a name="forcibly-listing-hidden-items--force"></a><span data-ttu-id="4f27b-121">Zorla gizli öğeleri listeleme (-Force)</span><span class="sxs-lookup"><span data-stu-id="4f27b-121">Forcibly Listing Hidden Items (-Force)</span></span>
<span data-ttu-id="4f27b-122">Dosya Gezgini'ni veya Cmd.exe normalde görünmeyen öğeleri çıktısında görüntülenmez bir **Get-Childıtem** komutu.</span><span class="sxs-lookup"><span data-stu-id="4f27b-122">Items that are normally invisible in File Explorer or Cmd.exe are not displayed in the output of a **Get-ChildItem** command.</span></span> <span data-ttu-id="4f27b-123">Gizli öğeleri görüntülemek için kullanın **zorla** parametresinin **Get-Childıtem**.</span><span class="sxs-lookup"><span data-stu-id="4f27b-123">To display hidden items, use the **Force** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="4f27b-124">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="4f27b-124">For example:</span></span>

```
Get-ChildItem -Path C:\Windows -Force
```

<span data-ttu-id="4f27b-125">Zorla normal davranışını geçersiz kılabilirsiniz çünkü bu parametre zorla adlı **Get-Childıtem** komutu.</span><span class="sxs-lookup"><span data-stu-id="4f27b-125">This parameter is named Force because you can forcibly override the normal behavior of the **Get-ChildItem** command.</span></span> <span data-ttu-id="4f27b-126">Zorla sistem güvenliği tehlikeye atar herhangi bir işlem gerçekleştirmez olsa da, bir cmdlet normalde gerçekleştireceği değil, bir eylem zorlar yaygın olarak kullanılan bir parametredir.</span><span class="sxs-lookup"><span data-stu-id="4f27b-126">Force is a widely used parameter that forces an action that a cmdlet would not normally perform, although it will not perform any action that compromises the security of the system.</span></span>

#### <a name="matching-item-names-with-wildcards"></a><span data-ttu-id="4f27b-127">Joker karakterlerle eşleşen öğe adları</span><span class="sxs-lookup"><span data-stu-id="4f27b-127">Matching Item Names with Wildcards</span></span>
<span data-ttu-id="4f27b-128">**Get-Childıtem** komutu liste öğelerine yolda joker karakterleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4f27b-128">**The Get-ChildItem** command accepts wildcards in the path of the items to list.</span></span>

<span data-ttu-id="4f27b-129">Joker karakter eşleştirme Windows PowerShell altyapısı tarafından işlendiğinden, joker karakterler kabul tüm cmdlet'leri aynı gösterimi kullanabilir ve aynı eşleşen davranışı sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4f27b-129">Because wildcard matching is handled by the Windows PowerShell engine, all cmdlets that accepts wildcards use the same notation and have the same matching behavior.</span></span> <span data-ttu-id="4f27b-130">Windows PowerShell joker gösterimi içerir:</span><span class="sxs-lookup"><span data-stu-id="4f27b-130">The Windows PowerShell wildcard notation includes:</span></span>

- <span data-ttu-id="4f27b-131">Yıldız işareti (\*) herhangi bir karakter sıfır veya daha çok tekrarı ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="4f27b-131">Asterisk (\*)matches zero or more occurrences of any character.</span></span>

- <span data-ttu-id="4f27b-132">Soru işareti (?) tam olarak bir karakterle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="4f27b-132">Question mark (?) matches exactly one character.</span></span>

- <span data-ttu-id="4f27b-133">Sol köşeli ayraç (\[) karakteri ve sağ parantez (]) karakteri çevreleyen eşleştirilmesini karakter kümesi.</span><span class="sxs-lookup"><span data-stu-id="4f27b-133">Left bracket (\[) character and right bracket (]) character surround a set of characters to be matched.</span></span>

<span data-ttu-id="4f27b-134">Burada, joker karakter belirtimi nasıl çalıştığı bazı örnekler verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4f27b-134">Here are some examples of how wildcard specification works.</span></span>

<span data-ttu-id="4f27b-135">Son ekini içeren Windows dizinindeki tüm dosyaları bulmak için **.log** ve temel adı tam olarak beş karakter aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="4f27b-135">To find all files in the Windows directory with the suffix **.log** and exactly five characters in the base name, enter the following command:</span></span>

```
PS> Get-ChildItem -Path C:\Windows\?????.log
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

<span data-ttu-id="4f27b-136">Harfiyle başlayan tüm dosyaları bulmak için **x** Windows dizinde yazın:</span><span class="sxs-lookup"><span data-stu-id="4f27b-136">To find all files that begin with the letter **x** in the Windows directory, type:</span></span>

```
Get-ChildItem -Path C:\Windows\x*
```

<span data-ttu-id="4f27b-137">Adları ile başlayan tüm dosyaları bulmak için **x** veya **z**, türü:</span><span class="sxs-lookup"><span data-stu-id="4f27b-137">To find all files whose names begin with **x** or **z**, type:</span></span>

```
Get-ChildItem -Path C:\Windows\[xz]*
```

#### <a name="excluding-items--exclude"></a><span data-ttu-id="4f27b-138">Öğeleri hariç (-hariç)</span><span class="sxs-lookup"><span data-stu-id="4f27b-138">Excluding Items (-Exclude)</span></span>
<span data-ttu-id="4f27b-139">Belirli öğeleri kullanarak dışlayabilirsiniz **hariç** Get-Childıtem parametresi.</span><span class="sxs-lookup"><span data-stu-id="4f27b-139">You can exclude specific items by using the **Exclude** parameter of Get-ChildItem.</span></span> <span data-ttu-id="4f27b-140">Bu, tek bir deyimde filtreleme karmaşık gerçekleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4f27b-140">This lets you perform complex filtering in a single statement.</span></span>

<span data-ttu-id="4f27b-141">Örneğin, Windows Saat hizmeti DLL System32 klasöründe bulmayı denediğiniz ve tüm DLL adı unutmayın "W" ile başlar ve "32" içerdiği varsayalım.</span><span class="sxs-lookup"><span data-stu-id="4f27b-141">For example, suppose you are trying to find the Windows Time Service DLL in the System32 folder, and all you can remember about the DLL name is that it begins with "W" and has "32" in it.</span></span>

<span data-ttu-id="4f27b-142">Bir ifade ister **w\&#42; 32\&#42;. dll** koşullarını tüm DLL'ler bulur ancak, aynı zamanda Windows 95 ve 16 bit Windows Uyumluluğu "95" dahil DLL'leri ya da "16" adlarında döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="4f27b-142">An expression like **w\&#42;32\&#42;.dll** will find all DLLs that satisfy the conditions, but it may also return the Windows 95 and 16-bit Windows compatibility DLLs that include "95" or "16" in their names.</span></span> <span data-ttu-id="4f27b-143">Bu sayı adlarını kullanarak olan dosyaları atlayabilirsiniz **hariç** düzeni parametresiyle  **\&#42;\[ 9516]\&#42;**:</span><span class="sxs-lookup"><span data-stu-id="4f27b-143">You can omit files that have any of these numbers in their names by using the **Exclude** parameter with the pattern **\&#42;\[9516]\&#42;**:</span></span>

<pre>PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*
Directory: Microsoft.PowerShell.Core\FileSystem::C:\WINDOWS\System32
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     174592 w32time.dll
-a---        2004-08-04   8:00 AM      22016 w32topl.dll
-a---        2004-08-04   8:00 AM     101888 win32spl.dll
-a---        2004-08-04   8:00 AM     172032 wldap32.dll
-a---        2004-08-04   8:00 AM     264192 wow32.dll
-a---        2004-08-04   8:00 AM      82944 ws2_32.dll
-a---        2004-08-04   8:00 AM      42496 wsnmp32.dll
-a---        2004-08-04   8:00 AM      22528 wsock32.dll
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll</pre>

#### <a name="mixing-get-childitem-parameters"></a><span data-ttu-id="4f27b-144">Get-Childıtem parametreleri karıştırma</span><span class="sxs-lookup"><span data-stu-id="4f27b-144">Mixing Get-ChildItem Parameters</span></span>
<span data-ttu-id="4f27b-145">Birkaç parametrelerinden biri kullanabilirsiniz **Get-Childıtem** cmdlet aynı komutta.</span><span class="sxs-lookup"><span data-stu-id="4f27b-145">You can use several of the parameters of the **Get-ChildItem** cmdlet in the same command.</span></span> <span data-ttu-id="4f27b-146">Parametreleri karışık önce joker karakter eşleştirme anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4f27b-146">Before you mix parameters, be sure that you understand wildcard matching.</span></span> <span data-ttu-id="4f27b-147">Örneğin, aşağıdaki komut, hiçbir sonuç döndürür:</span><span class="sxs-lookup"><span data-stu-id="4f27b-147">For example, the following command returns no results:</span></span>

```
PS> Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

<span data-ttu-id="4f27b-148">Windows klasöründeki "z" harfiyle başlayan iki DLL olsa bile, sonuç yok.</span><span class="sxs-lookup"><span data-stu-id="4f27b-148">There are no results, even though there are two DLLs that begin with the letter "z" in the Windows folder.</span></span>

<span data-ttu-id="4f27b-149">Biz joker yolun bir parçası olarak belirtilen çünkü sonuç döndürülmedi.</span><span class="sxs-lookup"><span data-stu-id="4f27b-149">No results were returned because we specified the wildcard as part of the path.</span></span> <span data-ttu-id="4f27b-150">Komut özyinelemeli olmasına rağmen **Get-Childıtem** cmdlet öğeleri Windows klasöründe ".dll" ile biten adlara sahip olanlar için kısıtlanmış.</span><span class="sxs-lookup"><span data-stu-id="4f27b-150">Even though the command was recursive, the **Get-ChildItem** cmdlet restricted the items to those that are in the Windows folder with names ending with ".dll".</span></span>

<span data-ttu-id="4f27b-151">Dosya adları özel bir desenle eşleşen bir özyinelemeli arama belirtmek için kullanın **-dahil** parametresi.</span><span class="sxs-lookup"><span data-stu-id="4f27b-151">To specify a recursive search for files whose names match a special pattern, use the **-Include** parameter.</span></span>

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```

