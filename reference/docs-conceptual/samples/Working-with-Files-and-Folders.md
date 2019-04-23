---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Dosya ve Klasörlerle Çalışma
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: 393e886a4945222198d9b81019250c5d5b905ad3
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984400"
---
# <a name="working-with-files-and-folders"></a><span data-ttu-id="96985-103">Dosya ve Klasörlerle Çalışma</span><span class="sxs-lookup"><span data-stu-id="96985-103">Working with Files and Folders</span></span>

<span data-ttu-id="96985-104">Windows PowerShell sürücülerini gezinme ve bunları öğelerde düzenleme Windows fiziksel disk sürücüsü üzerindeki dosya ve klasörleri yönetmek için benzerdir.</span><span class="sxs-lookup"><span data-stu-id="96985-104">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="96985-105">Bu bölümde, PowerShell kullanarak belirli dosya ve klasör düzenleme görevlerle başa çıkma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="96985-105">This section discusses how to deal with specific file and folder manipulation tasks using PowerShell.</span></span>

## <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="96985-106">Tüm dosya ve klasörlerin bir klasördeki listeleme</span><span class="sxs-lookup"><span data-stu-id="96985-106">Listing All the Files and Folders Within a Folder</span></span>

<span data-ttu-id="96985-107">Kullanarak, doğrudan bir klasördeki tüm öğeleri alabilirsiniz **Get-Childıtem**.</span><span class="sxs-lookup"><span data-stu-id="96985-107">You can get all items directly within a folder by using **Get-ChildItem**.</span></span> <span data-ttu-id="96985-108">İsteğe bağlı ekleme **zorla** gizli görüntülemek ya da sistem öğeleri için parametre.</span><span class="sxs-lookup"><span data-stu-id="96985-108">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="96985-109">Örneğin, bu komut (olan Windows fiziksel sürücü C ile aynı) Windows PowerShell sürücüsü C doğrudan içeriğini görüntüler:</span><span class="sxs-lookup"><span data-stu-id="96985-109">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```powershell
Get-ChildItem -Path C:\ -Force
```

<span data-ttu-id="96985-110">Komut Cmd.exe's kullanma gibi doğrudan içerilen öğelerin yalnızca listeler **DIR** komutu veya **ls** UNIX Kabuğu'nda.</span><span class="sxs-lookup"><span data-stu-id="96985-110">The command lists only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="96985-111">İçerilen öğelerin göstermek için belirtmeniz gerekir **-Recurse** parametresini de.</span><span class="sxs-lookup"><span data-stu-id="96985-111">In order to show contained items, you need to specify the **-Recurse** parameter as well.</span></span> <span data-ttu-id="96985-112">(Bu, tamamlanması çok uzun zaman alabilir.) Her şeyi C sürücüsünde listelemek için:</span><span class="sxs-lookup"><span data-stu-id="96985-112">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

<span data-ttu-id="96985-113">**Get-Childıtem** öğeleriyle filtreleyebilirsiniz kendi **yolu**, **filtre**, **INCLUDE**, ve **hariç** parametreleri, ancak bu genellikle yalnızca adına göre.</span><span class="sxs-lookup"><span data-stu-id="96985-113">**Get-ChildItem** can filter items with its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="96985-114">Karmaşık filtreleme öğelerin diğer özelliklerini kullanarak gerçekleştirebileceğiniz **Where-Object**.</span><span class="sxs-lookup"><span data-stu-id="96985-114">You can perform complex filtering based on other properties of items by using **Where-Object**.</span></span>

<span data-ttu-id="96985-115">Aşağıdaki komutu, son 1 Ekim 2005'ten sonra değiştirilmiş olan ve 1 megabayt değerinden küçük veya büyük 10 megabayt olan Program dosyaları klasöründeki tüm yürütülebilir dosyaları bulur:</span><span class="sxs-lookup"><span data-stu-id="96985-115">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a><span data-ttu-id="96985-116">Dosya ve klasörleri kopyalama</span><span class="sxs-lookup"><span data-stu-id="96985-116">Copying Files and Folders</span></span>

<span data-ttu-id="96985-117">Kopyalama ile yapılır **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="96985-117">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="96985-118">C: aşağıdaki komutu yedekler\\c: boot.ini\\boot.bak:</span><span class="sxs-lookup"><span data-stu-id="96985-118">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

<span data-ttu-id="96985-119">Hedef dosya zaten var. kopyalama girişimi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="96985-119">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="96985-120">Önceden var olan bir hedef üzerine yazmak için kullanın **zorla** parametresi:</span><span class="sxs-lookup"><span data-stu-id="96985-120">To overwrite a pre-existing destination, use the **Force** parameter:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

<span data-ttu-id="96985-121">Bu komut, hedef salt okunur olsa bile çalışır.</span><span class="sxs-lookup"><span data-stu-id="96985-121">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="96985-122">Klasörü kopyalama aynı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="96985-122">Folder copying works the same way.</span></span> <span data-ttu-id="96985-123">Bu komut ' % s'klasörü C: kopyalar\\temp\\yeni klasöre C: test1\\temp\\DeleteMe yinelemeli olarak:</span><span class="sxs-lookup"><span data-stu-id="96985-123">This command copies the folder C:\\temp\\test1 to the new folder C:\\temp\\DeleteMe recursively:</span></span>

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

<span data-ttu-id="96985-124">Öğelerin seçimini de kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96985-124">You can also copy a selection of items.</span></span> <span data-ttu-id="96985-125">Aşağıdaki komut c: herhangi bir yerde bulunan tüm .txt dosyaları kopyalar\\c: veri\\temp\\metin:</span><span class="sxs-lookup"><span data-stu-id="96985-125">The following command copies all .txt files contained anywhere in c:\\data to c:\\temp\\text:</span></span>

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

<span data-ttu-id="96985-126">Dosya sistemi kopyalarını gerçekleştirmek için diğer araçları kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96985-126">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="96985-127">XCOPY, ROBOCOPY ve COM nesneleri gibi **Scripting.FileSystemObject,** tüm Windows PowerShell içinde çalışacak.</span><span class="sxs-lookup"><span data-stu-id="96985-127">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="96985-128">Örneğin, Windows Script Host kullanabileceğiniz **Scripting.FileSystem COM** C: ' üzere sınıfı\\c: boot.ini\\boot.bak:</span><span class="sxs-lookup"><span data-stu-id="96985-128">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a><span data-ttu-id="96985-129">Dosya ve klasör oluşturma</span><span class="sxs-lookup"><span data-stu-id="96985-129">Creating Files and Folders</span></span>

<span data-ttu-id="96985-130">Yeni öğeler oluşturma, aynı tüm Windows PowerShell sağlayıcılarının çalışır.</span><span class="sxs-lookup"><span data-stu-id="96985-130">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="96985-131">Bir Windows PowerShell sağlayıcısı öğesi birden fazla türü olup olmadığını — Örneğin, dosya sistemi Windows PowerShell sağlayıcısını dizinler ve dosyalar arasında ayıran — öğesi türünü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="96985-131">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="96985-132">Bu komut yeni bir klasör C: oluşturur\\temp\\yeni klasör:</span><span class="sxs-lookup"><span data-stu-id="96985-132">This command creates a new folder C:\\temp\\New Folder:</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

<span data-ttu-id="96985-133">Bu komut yeni bir boş dosya C: oluşturur\\temp\\yeni klasör\\dosya.txt</span><span class="sxs-lookup"><span data-stu-id="96985-133">This command creates a new empty file C:\\temp\\New Folder\\file.txt</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="96985-134">Tüm dosya ve klasörleri bir klasördeki kaldırma</span><span class="sxs-lookup"><span data-stu-id="96985-134">Removing All Files and Folders Within a Folder</span></span>

<span data-ttu-id="96985-135">İçerilen öğelerin kullanarak kaldırabilirsiniz **Kaldır öğesini**, ancak başka bir öğe içeriyorsa, kaldırma işlemini onaylamanız istenir.</span><span class="sxs-lookup"><span data-stu-id="96985-135">You can remove contained items using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="96985-136">Örneğin, C: klasör silmeye çalışıyorsanız\\temp\\diğer öğeleri içeren DeleteMe Windows PowerShell sizden onay klasörü silmeden önce:</span><span class="sxs-lookup"><span data-stu-id="96985-136">For example, if you attempt to delete the folder C:\\temp\\DeleteMe that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="96985-137">İçindeki her öğe için sorulmasını istemiyorsanız belirtin **Recurse** parametresi:</span><span class="sxs-lookup"><span data-stu-id="96985-137">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a><span data-ttu-id="96985-138">Bir Windows erişilebilir sürücü gibi yerel bir klasöre eşleme</span><span class="sxs-lookup"><span data-stu-id="96985-138">Mapping a Local Folder as a Windows Accessible Drive</span></span>

<span data-ttu-id="96985-139">Yerel bir klasöre de eşleyebilirsiniz kullanarak **subst** komutu.</span><span class="sxs-lookup"><span data-stu-id="96985-139">You can also map a local folder, using the **subst** command.</span></span> <span data-ttu-id="96985-140">Aşağıdaki komut, yerel Program Files dizininde P: kök erişim izni verilmiş bir yerel sürücüye oluşturur:</span><span class="sxs-lookup"><span data-stu-id="96985-140">The following command creates a local drive P: rooted in the local Program Files directory:</span></span>

```powershell
subst p: $env:programfiles
```

<span data-ttu-id="96985-141">İle olduğu gibi ağ sürücülerini, eşlenen sürücülerini Windows PowerShell kullanarak içinde **subst** için Windows PowerShell Kabuk tarafından anında görülemez.</span><span class="sxs-lookup"><span data-stu-id="96985-141">Just as with network drives, drives mapped within Windows PowerShell using **subst** are immediately visible to the Windows PowerShell shell.</span></span>

## <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="96985-142">Bir diziye bir metin dosyası okuma</span><span class="sxs-lookup"><span data-stu-id="96985-142">Reading a Text File into an Array</span></span>

<span data-ttu-id="96985-143">Metin veriler için daha yaygın depolama biçimleri bir dosyada ayrı veri öğeleri olarak kabul ayrı satırlara ile biridir.</span><span class="sxs-lookup"><span data-stu-id="96985-143">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="96985-144">**Get-Content** cmdlet'i kullanılabilir tek bir adımda tüm dosyayı okumak için burada gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="96985-144">The **Get-Content** cmdlet can be used to read an entire file in one step, as shown here:</span></span>

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

<span data-ttu-id="96985-145">**Get-Content** zaten, dosya içeriğinin satır başına bir öğe dizisi olarak dosyadan okunan veriler değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="96985-145">**Get-Content** already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="96985-146">Bu denetleyerek doğrulayabilirsiniz **uzunluğu** döndürülen içerik:</span><span class="sxs-lookup"><span data-stu-id="96985-146">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="96985-147">Bu komut, doğrudan Windows PowerShell bilgilerini listesini almak için en kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="96985-147">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="96985-148">Örneğin, bilgisayar adlarını veya IP adreslerini listesini bir dosyada C: depolayabilir\\temp\\domainMembers.txt, dosya her satırda bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="96985-148">For example, you might store a list of computer names or IP addresses in a file C:\\temp\\domainMembers.txt, with one name on each line of the file.</span></span> <span data-ttu-id="96985-149">Kullanabileceğiniz **Get-Content** dosya içeriğini almak ve bunları değişkeninde yerleştirebilirsiniz **$Computers**:</span><span class="sxs-lookup"><span data-stu-id="96985-149">You can use **Get-Content** to retrieve the file contents and put them in the variable **$Computers**:</span></span>

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="96985-150">**$Computers** , artık her öğe bir bilgisayar adını içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="96985-150">**$Computers** is now an array containing a computer name in each element.</span></span>
