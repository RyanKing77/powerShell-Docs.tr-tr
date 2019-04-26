---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Dosya, Klasör ve Kayıt Defteri Anahtarları ile Çalışma
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: cd20cc50b573435ba80b52b51e164e60625dc1b6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086023"
---
# <a name="working-with-files-folders-and-registry-keys"></a><span data-ttu-id="4bda2-103">Dosya, klasör ve kayıt defteri anahtarları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="4bda2-103">Working With Files, Folders and Registry Keys</span></span>

<span data-ttu-id="4bda2-104">Windows PowerShell kullanan isim **öğesi** bir Windows PowerShell sürücüsünde bulunan öğeleri başvurmak için.</span><span class="sxs-lookup"><span data-stu-id="4bda2-104">Windows PowerShell uses the noun **Item** to refer to items found on a Windows PowerShell drive.</span></span> <span data-ttu-id="4bda2-105">Windows PowerShell dosya sistemi sağlayıcısı ile ilgilenirken bir **öğesi** bir dosya, klasör ya da Windows PowerShell sürücüsünü olabilir.</span><span class="sxs-lookup"><span data-stu-id="4bda2-105">When dealing with the Windows PowerShell FileSystem provider, an **Item** might be a file, a folder, or the Windows PowerShell drive.</span></span> <span data-ttu-id="4bda2-106">Bu görevleri ayrıntılı tartışmak istediğimiz şekilde listeleme ve bu öğeleri ile çalışma bir kritik temel çoğu yönetim ayarları'nda görevdir.</span><span class="sxs-lookup"><span data-stu-id="4bda2-106">Listing and working with these items is a critical basic task in most administrative settings, so we want to discuss these tasks in detail.</span></span>

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a><span data-ttu-id="4bda2-107">Dosyaları, klasörleri ve kayıt defteri anahtarlarını (Get-Childıtem) numaralandırma</span><span class="sxs-lookup"><span data-stu-id="4bda2-107">Enumerating Files, Folders, and Registry Keys (Get-ChildItem)</span></span>

<span data-ttu-id="4bda2-108">Belirli bir konumdan bir öğe koleksiyonu alma gibi genel bir görev, olduğundan **Get-Childıtem** cmdlet'i, özellikle bir klasörü gibi bir kapsayıcı içinde bulunan tüm öğeleri döndürmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4bda2-108">Since getting a collection of items from a particular location is such a common task, the **Get-ChildItem** cmdlet is designed specifically to return all items found within a container such as a folder.</span></span>

<span data-ttu-id="4bda2-109">Tüm dosyaları ve klasörleri doğrudan klasördeki C: bulunan dönmek istiyorsanız\\Windows, türü:</span><span class="sxs-lookup"><span data-stu-id="4bda2-109">If you want to return all files and folders that are contained directly within the folder C:\\Windows, type:</span></span>

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

<span data-ttu-id="4bda2-110">Listenin, girdiğinizde gördüğünüz için benzer **dir** komutunu **Cmd.exe**, veya **ls** UNIX komut kabuğu'nda komutu.</span><span class="sxs-lookup"><span data-stu-id="4bda2-110">The listing looks similar to what you would see when you enter the **dir** command in **Cmd.exe**, or the **ls** command in a UNIX command shell.</span></span>

<span data-ttu-id="4bda2-111">Çok karmaşık listelerini parametrelerini kullanarak gerçekleştirebileceğiniz **Get-Childıtem** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="4bda2-111">You can perform very complex listings by using parameters of the **Get-ChildItem** cmdlet.</span></span> <span data-ttu-id="4bda2-112">Biz birkaç senaryolarında sonraki görünecektir.</span><span class="sxs-lookup"><span data-stu-id="4bda2-112">We will look at a few scenarios next.</span></span> <span data-ttu-id="4bda2-113">Söz dizimi gördüğünüz **Get-Childıtem** yazarak cmdlet:</span><span class="sxs-lookup"><span data-stu-id="4bda2-113">You can see the syntax the **Get-ChildItem** cmdlet by typing:</span></span>

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

<span data-ttu-id="4bda2-114">Bu parametre, karma ve üst düzeyde özelleştirilmiş çıktısını almak için eşleşen.</span><span class="sxs-lookup"><span data-stu-id="4bda2-114">These parameters can be mixed and matched to get highly customized output.</span></span>

### <a name="listing-all-contained-items--recurse"></a><span data-ttu-id="4bda2-115">Tüm bulunan öğeleri listeleme (-Recurse)</span><span class="sxs-lookup"><span data-stu-id="4bda2-115">Listing all Contained Items (-Recurse)</span></span>

<span data-ttu-id="4bda2-116">Windows klasörünün içindeki öğeleri hem de alt klasörleri içinde yer alan tüm öğeleri görmek için **Recurse** parametresinin **Get-Childıtem**.</span><span class="sxs-lookup"><span data-stu-id="4bda2-116">To see both the items inside a Windows folder and any items that are contained within the subfolders, use the **Recurse** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="4bda2-117">Listenin her şeyi Windows klasörü ve alt öğelerinde içinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4bda2-117">The listing displays everything within the Windows folder and the items in its subfolders.</span></span> <span data-ttu-id="4bda2-118">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="4bda2-118">For example:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

### <a name="filtering-items-by-name--name"></a><span data-ttu-id="4bda2-119">Öğeleri ada göre filtreleme (-adı)</span><span class="sxs-lookup"><span data-stu-id="4bda2-119">Filtering Items by Name (-Name)</span></span>

<span data-ttu-id="4bda2-120">Yalnızca öğelerin adlarını görüntülemek için kullanın **adı** parametresinin **Get-Childıtem**:</span><span class="sxs-lookup"><span data-stu-id="4bda2-120">To display only the names of items, use the **Name** parameter of **Get-Childitem**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a><span data-ttu-id="4bda2-121">Gizli öğeleri zorla listeleme (-Force)</span><span class="sxs-lookup"><span data-stu-id="4bda2-121">Forcibly Listing Hidden Items (-Force)</span></span>

<span data-ttu-id="4bda2-122">Dosya Gezgini veya Cmd.exe normalde görünmeyen öğeleri çıktısında görüntülenmez bir **Get-Childıtem** komutu.</span><span class="sxs-lookup"><span data-stu-id="4bda2-122">Items that are normally invisible in File Explorer or Cmd.exe are not displayed in the output of a **Get-ChildItem** command.</span></span> <span data-ttu-id="4bda2-123">Gizli öğeleri görüntülemek için kullanın **zorla** parametresinin **Get-Childıtem**.</span><span class="sxs-lookup"><span data-stu-id="4bda2-123">To display hidden items, use the **Force** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="4bda2-124">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="4bda2-124">For example:</span></span>

```powershell
Get-ChildItem -Path C:\Windows -Force
```

<span data-ttu-id="4bda2-125">Zorla normal davranışı geçersiz kılabilirsiniz olduğundan bu parametreyi zorla adlı **Get-Childıtem** komutu.</span><span class="sxs-lookup"><span data-stu-id="4bda2-125">This parameter is named Force because you can forcibly override the normal behavior of the **Get-ChildItem** command.</span></span> <span data-ttu-id="4bda2-126">Zorla sistemin güvenliği tehlikeye atar herhangi bir eylem gerçekleştiremeyecek olsa da, bir cmdlet normalde gerçekleştirecek değil, bir eylem zorlar yaygın olarak kullanılan bir parametredir.</span><span class="sxs-lookup"><span data-stu-id="4bda2-126">Force is a widely used parameter that forces an action that a cmdlet would not normally perform, although it will not perform any action that compromises the security of the system.</span></span>

### <a name="matching-item-names-with-wildcards"></a><span data-ttu-id="4bda2-127">Joker karakterlerle eşleşen öğe adları</span><span class="sxs-lookup"><span data-stu-id="4bda2-127">Matching Item Names with Wildcards</span></span>

<span data-ttu-id="4bda2-128">**Get-Childıtem** komut listeye öğe yolunda joker karakterler kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4bda2-128">**The Get-ChildItem** command accepts wildcards in the path of the items to list.</span></span>

<span data-ttu-id="4bda2-129">Joker karakter eşlemesi Windows PowerShell altyapısı tarafından işlendiğinden, joker karakterleri kabul eden tüm cmdlet'ler aynı gösterimini kullanın ve eşleşen aynı davranışa sahip.</span><span class="sxs-lookup"><span data-stu-id="4bda2-129">Because wildcard matching is handled by the Windows PowerShell engine, all cmdlets that accepts wildcards use the same notation and have the same matching behavior.</span></span> <span data-ttu-id="4bda2-130">Windows PowerShell joker karakter gösterimi içerir:</span><span class="sxs-lookup"><span data-stu-id="4bda2-130">The Windows PowerShell wildcard notation includes:</span></span>

- <span data-ttu-id="4bda2-131">Yıldız işareti (\*) sıfır veya daha çok tekrarı herhangi bir karakterle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="4bda2-131">Asterisk (\*)matches zero or more occurrences of any character.</span></span>

- <span data-ttu-id="4bda2-132">Soru işareti (?) tam olarak bir karakterle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="4bda2-132">Question mark (?) matches exactly one character.</span></span>

- <span data-ttu-id="4bda2-133">Sol köşeli ayraç (\[) karakteri ve sağ köşeli ayraç (]) karakteri kapsamak eşleşmesi gereken karakter kümesi.</span><span class="sxs-lookup"><span data-stu-id="4bda2-133">Left bracket (\[) character and right bracket (]) character surround a set of characters to be matched.</span></span>

<span data-ttu-id="4bda2-134">Joker karakter belirtimi nasıl çalıştığına ilişkin bazı örnekleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4bda2-134">Here are some examples of how wildcard specification works.</span></span>

<span data-ttu-id="4bda2-135">Sonekine sahip Windows dizinindeki tüm dosyaları bulmak için **.log** ve tam olarak beş temel adı karakter aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="4bda2-135">To find all files in the Windows directory with the suffix **.log** and exactly five characters in the base name, enter the following command:</span></span>

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

<span data-ttu-id="4bda2-136">Harfi ile başlayan tüm dosyaları bulmak için **x** Windows dizini yazın:</span><span class="sxs-lookup"><span data-stu-id="4bda2-136">To find all files that begin with the letter **x** in the Windows directory, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\x*
```

<span data-ttu-id="4bda2-137">Adları ile başlayan tüm dosyaları bulmak için **x** veya **z**, türü:</span><span class="sxs-lookup"><span data-stu-id="4bda2-137">To find all files whose names begin with **x** or **z**, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

### <a name="excluding-items--exclude"></a><span data-ttu-id="4bda2-138">Öğeleri hariç (-hariç)</span><span class="sxs-lookup"><span data-stu-id="4bda2-138">Excluding Items (-Exclude)</span></span>

<span data-ttu-id="4bda2-139">Kullanarak belirli öğeleri hariç tutabilirsiniz **hariç** Get-childıtem komutunun parametre.</span><span class="sxs-lookup"><span data-stu-id="4bda2-139">You can exclude specific items by using the **Exclude** parameter of Get-ChildItem.</span></span> <span data-ttu-id="4bda2-140">Bu, tek bir deyimde filtreleme karmaşık gerçekleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4bda2-140">This lets you perform complex filtering in a single statement.</span></span>

<span data-ttu-id="4bda2-141">Örneğin, Windows Saat hizmeti DLL System32 klasöründe bulmaya çalıştığınız ve tüm DLL adı hatırlayabileceğiniz "W" ile başlayan ve "32" içerdiğinden varsayalım.</span><span class="sxs-lookup"><span data-stu-id="4bda2-141">For example, suppose you are trying to find the Windows Time Service DLL in the System32 folder, and all you can remember about the DLL name is that it begins with "W" and has "32" in it.</span></span>

<span data-ttu-id="4bda2-142">Bir ifade ister **w\&#42; 32\&#42;. dll** koşulları karşılayan tüm DLL'leri bulur ancak onu Windows 95 ve 16-bit Windows Uyumluluk "95" içeren bir dll veya "16" adlarında döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="4bda2-142">An expression like **w\&#42;32\&#42;.dll** will find all DLLs that satisfy the conditions, but it may also return the Windows 95 and 16-bit Windows compatibility DLLs that include "95" or "16" in their names.</span></span> <span data-ttu-id="4bda2-143">Adlarını kullanarak bu sayılardan birine sahip dosyaları atlayabilirsiniz **hariç** deseni parametresi  **\&#42;\[ 9516]\&#42;**:</span><span class="sxs-lookup"><span data-stu-id="4bda2-143">You can omit files that have any of these numbers in their names by using the **Exclude** parameter with the pattern **\&#42;\[9516]\&#42;**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*

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
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll
```

### <a name="mixing-get-childitem-parameters"></a><span data-ttu-id="4bda2-144">Get-Childıtem parametreleri karıştırma</span><span class="sxs-lookup"><span data-stu-id="4bda2-144">Mixing Get-ChildItem Parameters</span></span>

<span data-ttu-id="4bda2-145">Birkaç parametrelerinden biri kullanabileceğiniz **Get-Childıtem** aynı komutta cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="4bda2-145">You can use several of the parameters of the **Get-ChildItem** cmdlet in the same command.</span></span> <span data-ttu-id="4bda2-146">Parametreleri karıştırmak önce joker karakterlerle eşleşen anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4bda2-146">Before you mix parameters, be sure that you understand wildcard matching.</span></span> <span data-ttu-id="4bda2-147">Örneğin, aşağıdaki komut, sonuç döndürür:</span><span class="sxs-lookup"><span data-stu-id="4bda2-147">For example, the following command returns no results:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

<span data-ttu-id="4bda2-148">Windows klasöründeki "z" harfiyle başlayan iki DLL bulunsa bile hiçbir sonuç yok.</span><span class="sxs-lookup"><span data-stu-id="4bda2-148">There are no results, even though there are two DLLs that begin with the letter "z" in the Windows folder.</span></span>

<span data-ttu-id="4bda2-149">Biz joker karakter yolun bir parçası olarak belirtilen çünkü hiçbir sonuç döndürülmedi.</span><span class="sxs-lookup"><span data-stu-id="4bda2-149">No results were returned because we specified the wildcard as part of the path.</span></span> <span data-ttu-id="4bda2-150">Komut özyinelemeli olmasına rağmen **Get-Childıtem** cmdlet öğeleri Windows klasöründe ".dll" ile sonlanan adlara sahip olanlar için kısıtlanmış.</span><span class="sxs-lookup"><span data-stu-id="4bda2-150">Even though the command was recursive, the **Get-ChildItem** cmdlet restricted the items to those that are in the Windows folder with names ending with ".dll".</span></span>

<span data-ttu-id="4bda2-151">Adları, özel bir desenle eşleşen dosyaları için yinelemeli arama belirtmek için kullanın **-dahil** parametresi.</span><span class="sxs-lookup"><span data-stu-id="4bda2-151">To specify a recursive search for files whose names match a special pattern, use the **-Include** parameter.</span></span>

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