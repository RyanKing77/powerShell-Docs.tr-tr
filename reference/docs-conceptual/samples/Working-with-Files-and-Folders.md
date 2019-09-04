---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Dosya ve Klasörlerle Çalışma
ms.openlocfilehash: 743e261d2f5e8bfa39f2731fca7fea6e5678c711
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215525"
---
# <a name="working-with-files-and-folders"></a><span data-ttu-id="74ee1-103">Dosya ve Klasörlerle Çalışma</span><span class="sxs-lookup"><span data-stu-id="74ee1-103">Working with Files and Folders</span></span>

<span data-ttu-id="74ee1-104">Windows PowerShell sürücülerinden gezinmek ve bunların üzerindeki öğelerin düzenlenmesi, Windows fiziksel disk sürücülerindeki dosya ve klasörleri düzenleme ile benzerdir.</span><span class="sxs-lookup"><span data-stu-id="74ee1-104">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="74ee1-105">Bu bölümde, PowerShell kullanarak belirli dosya ve klasör işleme görevleriyle nasıl başa çıkılabileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="74ee1-105">This section discusses how to deal with specific file and folder manipulation tasks using PowerShell.</span></span>

## <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="74ee1-106">Bir klasör Içindeki tüm dosya ve klasörleri listeleme</span><span class="sxs-lookup"><span data-stu-id="74ee1-106">Listing All the Files and Folders Within a Folder</span></span>

<span data-ttu-id="74ee1-107">**Get-ChildItem**kullanarak tüm öğeleri doğrudan bir klasör içinde alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74ee1-107">You can get all items directly within a folder by using **Get-ChildItem**.</span></span> <span data-ttu-id="74ee1-108">Gizli veya sistem öğelerini göstermek için isteğe bağlı **zorlama** parametresini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="74ee1-108">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="74ee1-109">Örneğin, bu komut Windows PowerShell sürücüsü C 'nin (Windows fiziksel sürücü C ile aynı) doğrudan içeriğini görüntüler:</span><span class="sxs-lookup"><span data-stu-id="74ee1-109">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```powershell
Get-ChildItem -Path C:\ -Force
```

<span data-ttu-id="74ee1-110">Komut, cmd. exe ' nin **dır** komutunu ya da bir UNIX kabuğundan **ls** gibi yalnızca doğrudan içerilen öğeleri listeler.</span><span class="sxs-lookup"><span data-stu-id="74ee1-110">The command lists only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="74ee1-111">İçerilen öğeleri göstermek için **-Recurse** parametresini de belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="74ee1-111">In order to show contained items, you need to specify the **-Recurse** parameter as well.</span></span> <span data-ttu-id="74ee1-112">(Bu işlem, tamamlanması çok uzun zaman alabilir.) C sürücüsündeki her şeyi listelemek için:</span><span class="sxs-lookup"><span data-stu-id="74ee1-112">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

<span data-ttu-id="74ee1-113">**Get-ChildItem** , öğeleri **yolu**, **filtresi**, **içerme**ve **dışlama** parametreleriyle filtreleyip, ancak bunlar genellikle yalnızca adı temel alır.</span><span class="sxs-lookup"><span data-stu-id="74ee1-113">**Get-ChildItem** can filter items with its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="74ee1-114">**WHERE-Object**kullanarak öğelerin diğer özelliklerine göre karmaşık filtreleme gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74ee1-114">You can perform complex filtering based on other properties of items by using **Where-Object**.</span></span>

<span data-ttu-id="74ee1-115">Aşağıdaki komut, 1 Ekim 2005 ' den sonra son değiştirilen ve 1 megabayttan küçük veya 10 megabayttan büyük olmayan program dosyaları klasöründeki tüm yürütülebilir dosyaları bulur:</span><span class="sxs-lookup"><span data-stu-id="74ee1-115">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a><span data-ttu-id="74ee1-116">Dosya ve klasörleri kopyalama</span><span class="sxs-lookup"><span data-stu-id="74ee1-116">Copying Files and Folders</span></span>

<span data-ttu-id="74ee1-117">Kopyalama, kopyalama **öğesi**ile yapılır.</span><span class="sxs-lookup"><span data-stu-id="74ee1-117">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="74ee1-118">Aşağıdaki komut c:\\Boot. ini dosyasını c:\\Boot. bak öğesine yedekler:</span><span class="sxs-lookup"><span data-stu-id="74ee1-118">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

<span data-ttu-id="74ee1-119">Hedef dosya zaten varsa kopyalama girişimi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="74ee1-119">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="74ee1-120">Önceden var olan bir hedefin üzerine yazmak için **zorla** parametresini kullanın:</span><span class="sxs-lookup"><span data-stu-id="74ee1-120">To overwrite a pre-existing destination, use the **Force** parameter:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

<span data-ttu-id="74ee1-121">Bu komut, hedef salt okunurdur olsa bile işe yarar.</span><span class="sxs-lookup"><span data-stu-id="74ee1-121">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="74ee1-122">Klasör kopyalama aynı şekilde çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="74ee1-122">Folder copying works the same way.</span></span> <span data-ttu-id="74ee1-123">Bu komut c\\: temp\\test1 klasörünü yeni c:\\temp\\klasörüne kopyalar.</span><span class="sxs-lookup"><span data-stu-id="74ee1-123">This command copies the folder C:\\temp\\test1 to the new folder C:\\temp\\DeleteMe recursively:</span></span>

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

<span data-ttu-id="74ee1-124">Ayrıca, öğelerin bir seçimini de kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74ee1-124">You can also copy a selection of items.</span></span> <span data-ttu-id="74ee1-125">Aşağıdaki komut, c:\\Data içinde herhangi bir yerde bulunan tüm. txt dosyalarını\\c: temp\\metnine kopyalar:</span><span class="sxs-lookup"><span data-stu-id="74ee1-125">The following command copies all .txt files contained anywhere in c:\\data to c:\\temp\\text:</span></span>

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

<span data-ttu-id="74ee1-126">Dosya sistemi kopyalarını gerçekleştirmek için diğer araçları kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74ee1-126">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="74ee1-127">XCOPY, ROBOCOPY ve **Scripting. Filesystemmobject** gibi com nesneleri Windows PowerShell 'de çalışır.</span><span class="sxs-lookup"><span data-stu-id="74ee1-127">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="74ee1-128">Örneğin, c:\\Boot. ini dosyasını c:\\Boot. bak ' a yedeklemek için Windows Script Host **Scripting. FileSystem com** sınıfını kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="74ee1-128">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a><span data-ttu-id="74ee1-129">Dosya ve klasör oluşturma</span><span class="sxs-lookup"><span data-stu-id="74ee1-129">Creating Files and Folders</span></span>

<span data-ttu-id="74ee1-130">Yeni öğelerin oluşturulması, tüm Windows PowerShell sağlayıcılarıyla aynı şekilde çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="74ee1-130">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="74ee1-131">Bir Windows PowerShell sağlayıcısında birden fazla öğe türü varsa — Örneğin, dosya sistemi Windows PowerShell sağlayıcısı dizinler ve dosyalar arasında ayrım yapar; öğe türünü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="74ee1-131">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="74ee1-132">Bu komut yeni bir klasör oluşturur C:\\temp\\yeni klasör:</span><span class="sxs-lookup"><span data-stu-id="74ee1-132">This command creates a new folder C:\\temp\\New Folder:</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

<span data-ttu-id="74ee1-133">Bu komut yeni bir boş dosya oluşturur C:\\temp\\yeni klasör\\File. txt</span><span class="sxs-lookup"><span data-stu-id="74ee1-133">This command creates a new empty file C:\\temp\\New Folder\\file.txt</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="74ee1-134">Bir klasör Içindeki tüm dosya ve klasörleri kaldırma</span><span class="sxs-lookup"><span data-stu-id="74ee1-134">Removing All Files and Folders Within a Folder</span></span>

<span data-ttu-id="74ee1-135">İçerilen öğeleri **Remove-Item**' ı kullanarak kaldırabilirsiniz, ancak öğe başka bir şey içeriyorsa kaldırma işlemini onaylamanız istenir.</span><span class="sxs-lookup"><span data-stu-id="74ee1-135">You can remove contained items using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="74ee1-136">Örneğin, diğer öğeleri içeren C:\\temp\\deleteme klasörünü silmeye çalışırsanız, Windows PowerShell, klasörü silmeden önce sizden onay ister:</span><span class="sxs-lookup"><span data-stu-id="74ee1-136">For example, if you attempt to delete the folder C:\\temp\\DeleteMe that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="74ee1-137">İçerilen her öğe için istenmesini istemiyorsanız, **Recurse** parametresini belirtin:</span><span class="sxs-lookup"><span data-stu-id="74ee1-137">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-drive"></a><span data-ttu-id="74ee1-138">Yerel bir klasörü sürücü olarak eşleme</span><span class="sxs-lookup"><span data-stu-id="74ee1-138">Mapping a Local Folder as a drive</span></span>

<span data-ttu-id="74ee1-139">Ayrıca, **New-PSDrive** komutunu kullanarak yerel bir klasörü eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74ee1-139">You can also map a local folder, using the **New-PSDrive** command.</span></span> <span data-ttu-id="74ee1-140">Aşağıdaki komut, yerel Program Files dizininde belirtilen yerel bir sürücü olan P: ' i yalnızca PowerShell oturumundan görünür olarak oluşturur:</span><span class="sxs-lookup"><span data-stu-id="74ee1-140">The following command creates a local drive P: rooted in the local Program Files directory, visible only from the PowerShell session:</span></span>

```powershell
New-PSDrive -Name P -Root $env:ProgramFiles -PSProvider FileSystem
```

<span data-ttu-id="74ee1-141">Ağ sürücülerinde olduğu gibi, Windows PowerShell içinde eşlenen sürücüler hemen Windows PowerShell kabuğu tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="74ee1-141">Just as with network drives, drives mapped within Windows PowerShell are immediately visible to the Windows PowerShell shell.</span></span>
<span data-ttu-id="74ee1-142">Dosya Gezgini 'nden görünebilir bir eşlenen sürücü oluşturmak için, **-Persist** parametresi gerekir.</span><span class="sxs-lookup"><span data-stu-id="74ee1-142">In order to create a mapped drive visible from File Explorer, the parameter **-Persist** is needed.</span></span> <span data-ttu-id="74ee1-143">Ancak, kalıcı olarak yalnızca uzak yollar kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="74ee1-143">However, only remote paths can be used with Persist.</span></span>


## <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="74ee1-144">Bir metin dosyasını bir diziye okuma</span><span class="sxs-lookup"><span data-stu-id="74ee1-144">Reading a Text File into an Array</span></span>

<span data-ttu-id="74ee1-145">Metin verileri için daha yaygın depolama biçimlerinden biri ayrı satırlar olarak değerlendirilen bir dosya içinde farklı veri öğeleri olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="74ee1-145">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="74ee1-146">**Get-Content** cmdlet 'i, burada gösterildiği gibi, bir adımda tüm bir dosyayı okumak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="74ee1-146">The **Get-Content** cmdlet can be used to read an entire file in one step, as shown here:</span></span>

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional
with Data Execution Prevention" /noexecute=optin /fastdetect
```

<span data-ttu-id="74ee1-147">**Get-Content** , dosya içeriğinin her satırı için bir öğe olarak dosyadaki okunan verileri bir dizi olarak zaten değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="74ee1-147">**Get-Content** already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="74ee1-148">Döndürülen içeriğin **uzunluğunu** denetleyerek bunu doğrulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="74ee1-148">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="74ee1-149">Bu komut, Windows PowerShell 'e doğrudan bilgi listesi almak için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="74ee1-149">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="74ee1-150">Örneğin, bir bilgisayar adı veya IP adresi listesini dosyanın her satırında tek bir ada sahip C:\\temp\\domainmembers. txt dosyasında saklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74ee1-150">For example, you might store a list of computer names or IP addresses in a file C:\\temp\\domainMembers.txt, with one name on each line of the file.</span></span> <span data-ttu-id="74ee1-151">Dosya içeriğini almak ve **$Computers**değişkenine koymak için **Get-Content** kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="74ee1-151">You can use **Get-Content** to retrieve the file contents and put them in the variable **$Computers**:</span></span>

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="74ee1-152">**$Computers** artık her öğe için bir bilgisayar adı içeren bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="74ee1-152">**$Computers** is now an array containing a computer name in each element.</span></span>
