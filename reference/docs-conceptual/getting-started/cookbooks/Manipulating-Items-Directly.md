---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Öğeleri Doğrudan İşleme
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
ms.openlocfilehash: 688f9194bd16793331325999c69e88df3e94c976
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="manipulating-items-directly"></a><span data-ttu-id="3732c-103">Öğeleri Doğrudan İşleme</span><span class="sxs-lookup"><span data-stu-id="3732c-103">Manipulating Items Directly</span></span>

<span data-ttu-id="3732c-104">Dosyaları ve dosya sistemi sürücülerine klasörlerde ve Windows PowerShell kayıt defteri sürücüleri, kayıt defteri anahtarlarında gibi Windows PowerShell sürücülerdeki gördüğünüz öğeleri adlı *öğeleri* Windows PowerShell'de.</span><span class="sxs-lookup"><span data-stu-id="3732c-104">The elements that you see in Windows PowerShell drives, such as the files and folders in the file system drives, and the registry keys in the Windows PowerShell registry drives, are called *items* in Windows PowerShell.</span></span> <span data-ttu-id="3732c-105">Öğesi bunlarla çalışmak için cmdlet'leri isim sahip **öğesi** adlarında.</span><span class="sxs-lookup"><span data-stu-id="3732c-105">The cmdlets for working with them item have the noun **Item** in their names.</span></span>

<span data-ttu-id="3732c-106">Çıktısını **Get-Command - isim öğesi** komut gösterir dokuz Windows PowerShell öğesi cmdlet'leri vardır.</span><span class="sxs-lookup"><span data-stu-id="3732c-106">The output of the **Get-Command -Noun Item** command shows that there are nine Windows PowerShell item cmdlets.</span></span>

```
PS> Get-Command -Noun Item

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Clear-Item                      Clear-Item [-Path] <String[]...
Cmdlet          Copy-Item                       Copy-Item [-Path] <String[]>...
Cmdlet          Get-Item                        Get-Item [-Path] <String[]> ...
Cmdlet          Invoke-Item                     Invoke-Item [-Path] <String[...
Cmdlet          Move-Item                       Move-Item [-Path] <String[]>...
Cmdlet          New-Item                        New-Item [-Path] <String[]> ...
Cmdlet          Remove-Item                     Remove-Item [-Path] <String[...
Cmdlet          Rename-Item                     Rename-Item [-Path] <String>...
Cmdlet          Set-Item                        Set-Item [-Path] <String[]> ...
```

### <a name="creating-new-items-new-item"></a><span data-ttu-id="3732c-107">Yeni öğeler (öğesi yeni) oluşturma</span><span class="sxs-lookup"><span data-stu-id="3732c-107">Creating New Items (New-Item)</span></span>

<span data-ttu-id="3732c-108">Dosya sisteminde yeni bir öğe oluşturmak üzere kullanmanız **yeni öğe** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="3732c-108">To create a new item in the file system, use the **New-Item** cmdlet.</span></span> <span data-ttu-id="3732c-109">Dahil **yolu** öğenin yolu parametresiyle ve **ItemType** parametresi "dosyası" veya "dizin" değerine sahip.</span><span class="sxs-lookup"><span data-stu-id="3732c-109">Include the **Path** parameter with path to the item, and the **ItemType** parameter with a value of "file" or "directory".</span></span>

<span data-ttu-id="3732c-110">Örneğin, adında yeni bir dizin oluşturmak için "New.Directory"in C:\\Temp dizininde, türü:</span><span class="sxs-lookup"><span data-stu-id="3732c-110">For example, to create a new directory named "New.Directory"in the C:\\Temp directory,  type:</span></span>

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

<span data-ttu-id="3732c-111">Bir dosya oluşturmak için değerini değiştirme **ItemType** "dosyası" parametresi.</span><span class="sxs-lookup"><span data-stu-id="3732c-111">To create a file, change the value of the **ItemType** parameter to "file".</span></span> <span data-ttu-id="3732c-112">Örneğin, New.Directory dizininde "Dosya1.ref" adlı bir dosya oluşturmak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="3732c-112">For example, to create a file named "file1.txt" in the New.Directory directory, type:</span></span>

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

<span data-ttu-id="3732c-113">Yeni bir kayıt defteri anahtarı oluşturmak için aynı tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3732c-113">You can use the same technique to create a new registry key.</span></span> <span data-ttu-id="3732c-114">Aslında, bir kayıt defteri anahtarı yalnızca Windows kayıt defteri öğesi türü bir anahtar olduğundan oluşturmak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="3732c-114">In fact, a registry key is easier to create because the only item type in the Windows registry is a key.</span></span> <span data-ttu-id="3732c-115">(Kayıt defteri girdileridir öğesi *özellikleri*.) Örneğin, CurrentVersion alt anahtarda "_Test" adlı bir anahtar oluşturmak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="3732c-115">(Registry entries are item *properties*.) For example, to create a key named "_Test" in the CurrentVersion subkey, type:</span></span>

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

<span data-ttu-id="3732c-116">Kayıt defteri yolu yazarken, iki nokta üst üste eklediğinizden emin olun (**:**) Windows PowerShell'de sürücü adları, HKLM: ve HKCU:.</span><span class="sxs-lookup"><span data-stu-id="3732c-116">When typing a registry path, be sure to include the colon (**:**) in the Windows PowerShell drive names, HKLM: and HKCU:.</span></span> <span data-ttu-id="3732c-117">İki nokta üst üste, Windows PowerShell yolunda sürücü adı tanımıyor.</span><span class="sxs-lookup"><span data-stu-id="3732c-117">Without the colon, Windows PowerShell does not recognize the drive name in the path.</span></span>

### <a name="why-registry-values-are-not-items"></a><span data-ttu-id="3732c-118">Neden kayıt defteri değerlerini öğeler değil</span><span class="sxs-lookup"><span data-stu-id="3732c-118">Why Registry Values are not Items</span></span>

<span data-ttu-id="3732c-119">Kullandığınızda **Get-Childıtem** bir kayıt defteri anahtarında öğeleri bulmak için cmdlet gerçek kayıt defteri girdileri veya değerlerine hiçbir zaman görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="3732c-119">When you use the **Get-ChildItem** cmdlet to find the items in a registry key, you will never see actual registry entries or their values.</span></span>

<span data-ttu-id="3732c-120">Örneğin, kayıt defteri anahtarı **HKEY_LOCAL_MACHINE\\yazılım\\Microsoft\\Windows\\CurrentVersion\\çalıştırmak** genellikle birkaç kayıt defteri girdileri içerir Bu, sistem başlatıldığında çalışan uygulamaları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3732c-120">For example, the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** usually contains several registry entries that represent applications that run when the system starts.</span></span>

<span data-ttu-id="3732c-121">Ancak, kullandığınızda **Get-Childıtem** anahtarında alt öğeleri aramak için tüm görürsünüz olan **OptionalComponents** anahtarının alt anahtar:</span><span class="sxs-lookup"><span data-stu-id="3732c-121">However, when you use **Get-ChildItem** to look for child items in the key, all you will see is the **OptionalComponents** subkey of the key:</span></span>

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

<span data-ttu-id="3732c-122">Kayıt defteri girdileri öğeleri olarak işlemek kullanışlı olsa da, bir kayıt defteri girdisi yoluna benzersiz sağlar bir biçimde belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="3732c-122">Although it would be convenient to treat registry entries as items, you cannot specify a path to a registry entry in a way that ensures that it is unique.</span></span> <span data-ttu-id="3732c-123">Yol gösterimi adlı kayıt defteri alt anahtarı arasında ayrım yapmaz **çalıştırmak** ve **(varsayılan)** kayıt defteri girişini **çalıştırmak** alt anahtarı.</span><span class="sxs-lookup"><span data-stu-id="3732c-123">The path notation does not distinguish between the registry subkey named **Run** and the **(Default)** registry entry in the **Run** subkey.</span></span> <span data-ttu-id="3732c-124">Ayrıca, kayıt defteri girişi adları ters eğik çizgi karakteri içerebileceğinden (**\\**), kayıt defteri girişleri öğeleri olsaydı adlı bir kayıt defteri girdisi ayırt etmek için yol gösterimi kullanılamadı sonra  **Windows\\CurrentVersion\\çalıştırmak** ilgili yolda bulunan alt.</span><span class="sxs-lookup"><span data-stu-id="3732c-124">Furthermore, because registry entry names can contain the backslash character (**\\**), if regsitry entries were items, then you could not use the path notation to distinguish a registry entry named **Windows\\CurrentVersion\\Run** from the subkey that is located in that path.</span></span>

### <a name="renaming-existing-items-rename-item"></a><span data-ttu-id="3732c-125">Varolan öğeleri (öğe yeniden adlandırılamadı) yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="3732c-125">Renaming Existing Items (Rename-Item)</span></span>

<span data-ttu-id="3732c-126">Bir dosya veya klasör adını değiştirmek için kullanmak **öğe yeniden adlandırılamadı** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="3732c-126">To change the name of a file or folder, use the **Rename-Item** cmdlet.</span></span> <span data-ttu-id="3732c-127">Aşağıdaki komut adını değiştirir **Dosya1.ref** dosya **fileOne.txt**.</span><span class="sxs-lookup"><span data-stu-id="3732c-127">The following command changes the name of the **file1.txt** file to **fileOne.txt**.</span></span>

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

<span data-ttu-id="3732c-128">**Öğe yeniden adlandırılamadı** cmdlet, bir dosya veya klasör adını değiştirebilirsiniz, ancak bir öğe taşınamıyor.</span><span class="sxs-lookup"><span data-stu-id="3732c-128">The **Rename-Item** cmdlet can change the name of a file or a folder, but it cannot move an item.</span></span> <span data-ttu-id="3732c-129">Temp Dizini New.Directory dizinden dosyayı taşımak denemesi için aşağıdaki komutu başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3732c-129">The following command fails because it attempts to move the file from the New.Directory directory to the Temp directory.</span></span>

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

### <a name="moving-items-move-item"></a><span data-ttu-id="3732c-130">Öğeleri (Move-Item) taşıma</span><span class="sxs-lookup"><span data-stu-id="3732c-130">Moving Items (Move-Item)</span></span>

<span data-ttu-id="3732c-131">Bir dosya veya klasöre taşımak için kullanın **taşıma öğesi** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="3732c-131">To move a file or folder, use the **Move-Item** cmdlet.</span></span>

<span data-ttu-id="3732c-132">Örneğin, aşağıdaki komutu New.Directory directory C: taşır\\C: sürücüsünün kökündeki geçici dizine.</span><span class="sxs-lookup"><span data-stu-id="3732c-132">For example, the following command moves the New.Directory directory from the C:\\temp directory to the root of the C: drive.</span></span> <span data-ttu-id="3732c-133">Öğe taşındı doğrulamak için dahil **PassThru** parametresinin **taşıma öğesi** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="3732c-133">To verify that the item was moved, include the **PassThru** parameter of the **Move-Item** cmdlet.</span></span> <span data-ttu-id="3732c-134">Olmadan **Passthru**, **taşıma öğesi** cmdlet herhangi bir sonuç görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="3732c-134">Without **Passthru**, the **Move-Item** cmdlet does not display any results.</span></span>

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

### <a name="copying-items-copy-item"></a><span data-ttu-id="3732c-135">Öğe (öğeyi Kopyala) kopyalama</span><span class="sxs-lookup"><span data-stu-id="3732c-135">Copying Items (Copy-Item)</span></span>

<span data-ttu-id="3732c-136">Diğer Kabukları kopyalama işlemleri biliyorsanız, davranışını bulabileceğiniz **Copy-Item** olağan dışı olması için Windows PowerShell cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="3732c-136">If you are familiar with the copy operations in other shells, you might find the behavior of the **Copy-Item** cmdlet in Windows PowerShell to be unusual.</span></span> <span data-ttu-id="3732c-137">Bir öğeyi tek bir konumdan diğerine kopyaladığınızda Copy-Item içeriğinin varsayılan olarak kopyalamaz.</span><span class="sxs-lookup"><span data-stu-id="3732c-137">When you copy an item from one location to another, Copy-Item does not copy its contents by default.</span></span>

<span data-ttu-id="3732c-138">Örneğin, kopyalama, **New.Directory** dizininden C: sürücüsündeki C:\\geçici dizin, komutun başarılı olur, ancak New.Directory dizindeki dosyaların kopyalanmadı.</span><span class="sxs-lookup"><span data-stu-id="3732c-138">For example, if you copy the **New.Directory** directory from the C: drive to the C:\\temp directory, the command succeeds, but the files in the New.Directory directory are not copied.</span></span>

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

<span data-ttu-id="3732c-139">İçeriğini görüntülerseniz **C:\\temp\\New.Directory**, dosya içermiyor bulacaksınız:</span><span class="sxs-lookup"><span data-stu-id="3732c-139">If you display the contents of **C:\\temp\\New.Directory**, you will find that it contains no files:</span></span>

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

<span data-ttu-id="3732c-140">Neden değil **Copy-Item** cmdlet kopyalama içeriğini yeni konuma?</span><span class="sxs-lookup"><span data-stu-id="3732c-140">Why doesn't the **Copy-Item** cmdlet copy the contents to the new location?</span></span>

<span data-ttu-id="3732c-141">**Copy-Item** cmdlet genel olacak şekilde tasarlanmıştır; bu dosya ve klasörleri kopyalama için yalnızca değil.</span><span class="sxs-lookup"><span data-stu-id="3732c-141">The **Copy-Item** cmdlet was designed to be generic; it is not just for copying files and folders.</span></span> <span data-ttu-id="3732c-142">Ayrıca, bile dosya ve klasörleri kopyalama sırasında yalnızca kapsayıcı ve içerisindeki öğeleri kopyalama isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3732c-142">Also, even when copying files and folders, you might want to copy only the container and not the items within it.</span></span>

<span data-ttu-id="3732c-143">Tüm bir klasörün içeriğini kopyalamak için eklemeniz **Recurse** parametresinin **Copy-Item** cmdlet komutu.</span><span class="sxs-lookup"><span data-stu-id="3732c-143">To copy all of the contents of a folder, include the **Recurse** parameter of the **Copy-Item** cmdlet in the command.</span></span> <span data-ttu-id="3732c-144">Dizin içeriğini olmadan kopyaladıysanız, ekleme **zorla** parametresi boş klasörünün üzerine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3732c-144">If you have already copied the directory without its contents, add the **Force** parameter, which allows you to overwrite the empty folder.</span></span>

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp -Recurse -Force -Passthru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18   1:53 PM            New.Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

### <a name="deleting-items-remove-item"></a><span data-ttu-id="3732c-145">Öğeleri silme (öğesi Kaldır)</span><span class="sxs-lookup"><span data-stu-id="3732c-145">Deleting Items (Remove-Item)</span></span>

<span data-ttu-id="3732c-146">Dosya ve klasörleri silmek için kullanın **Kaldır öğesini** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="3732c-146">To delete files and folders, use the **Remove-Item** cmdlet.</span></span> <span data-ttu-id="3732c-147">Windows PowerShell cmdlet'leri gibi **Kaldır öğesini**, yapabilir önemli, geri alınamaz değişiklikleri genellikle ister onaylama için kendi komutları girdiğinizde.</span><span class="sxs-lookup"><span data-stu-id="3732c-147">Windows PowerShell cmdlets, such as **Remove-Item**, that can make significant, irreversible changes will often prompt for confirmation when you enter its commands.</span></span> <span data-ttu-id="3732c-148">Örneğin, kaldırmayı denerseniz **New.Directory** klasörü, dosyaları içeren klasör için komutu onaylamanız istenir:</span><span class="sxs-lookup"><span data-stu-id="3732c-148">For example, if you try to remove the **New.Directory** folder, you will be prompted to confirm the command, because the folder contains files:</span></span>

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="3732c-149">Çünkü **Evet** klasör ve dosyaları, basın silmek için varsayılan yanıt **Enter** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="3732c-149">Because **Yes** is the default response, to delete the folder and its files, press the **Enter** key.</span></span> <span data-ttu-id="3732c-150">Onaylama olmadan klasörü kaldırmak üzere kullanın **-Recurse** parametresi.</span><span class="sxs-lookup"><span data-stu-id="3732c-150">To remove the folder without confirming, use the **-Recurse** parameter.</span></span>

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

### <a name="executing-items-invoke-item"></a><span data-ttu-id="3732c-151">Yürütülen öğeleri (çağırma öğe)</span><span class="sxs-lookup"><span data-stu-id="3732c-151">Executing Items (Invoke-Item)</span></span>

<span data-ttu-id="3732c-152">Windows PowerShell kullanan **Invoke-Item** bir dosya veya klasör için varsayılan bir eylem gerçekleştirmek için cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3732c-152">Windows PowerShell uses the **Invoke-Item** cmdlet to perform a default action for a file or folder.</span></span> <span data-ttu-id="3732c-153">Bu varsayılan eylem, kayıt defterinde varsayılan uygulama işleyicisi tarafından belirlenir; Dosya Gezgini'nde öğe çift tıklarsanız gibi etkisi aynıdır.</span><span class="sxs-lookup"><span data-stu-id="3732c-153">This default action is determined by the default application handler in the registry; the effect is the same as if you double-click the item in File Explorer.</span></span>

<span data-ttu-id="3732c-154">Örneğin, aşağıdaki komutu çalıştırın varsayın:</span><span class="sxs-lookup"><span data-stu-id="3732c-154">For example, suppose you run the following command:</span></span>

```powershell
Invoke-Item C:\WINDOWS
```

<span data-ttu-id="3732c-155">C: bulunan bir Explorer penceresi\\Windows görüntülenirse, yalnızca C: tıklattığınız sanki\\Windows klasörü.</span><span class="sxs-lookup"><span data-stu-id="3732c-155">An Explorer window that is located in C:\\Windows appears, just as if you had double-clicked the C:\\Windows folder.</span></span>

<span data-ttu-id="3732c-156">Çağırmayı varsa **Boot.ini** dosyasını, Windows Vista önce bir sistemde:</span><span class="sxs-lookup"><span data-stu-id="3732c-156">If you invoke the **Boot.ini** file on a system prior to Windows Vista:</span></span>

```powershell
Invoke-Item C:\boot.ini
```

<span data-ttu-id="3732c-157">Boot.ini dosyası, .ini dosya türü Notepad ile ilişkili ise, Not Defteri'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="3732c-157">If the .ini file type is associated with Notepad, the boot.ini file opens in Notepad.</span></span>