---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Geçerli konumu yönetme"
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: cbdebb84b3191e3bd549a1cf344cbeefaa91a23c
ms.sourcegitcommit: c5251755c4442487f99ff74fadf7e37bbf039089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="managing-current-location"></a><span data-ttu-id="1bdaa-103">Geçerli konumu yönetme</span><span class="sxs-lookup"><span data-stu-id="1bdaa-103">Managing Current Location</span></span>
<span data-ttu-id="1bdaa-104">Dosya Gezgini'nde klasörü sistemleri gezinirken genellikle belirli bir çalışma konumu - yani, geçerli klasör Aç sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-104">When navigating folder systems in File Explorer, you usually have a specific working location - namely, the current open folder.</span></span> <span data-ttu-id="1bdaa-105">Geçerli klasöründeki öğeler tıklatarak kolayca yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-105">Items in the current folder can be manipulated easily by clicking them.</span></span> <span data-ttu-id="1bdaa-106">Belirli bir dosya ile aynı klasörde olduğunda Cmd.exe gibi komut satırı arabirimlerinden için onu tüm dosyasının yolunu belirtmek gerek yerine daha kısa bir adı belirterek erişebilir.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-106">For command-line interfaces such as Cmd.exe, when you are in the same folder as a particular file, you can access it by specifying a relatively short name, rather than needing to specify the entire path to the file.</span></span> <span data-ttu-id="1bdaa-107">Geçerli dizin çalışma dizini olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-107">The current directory is called the working directory.</span></span>

<span data-ttu-id="1bdaa-108">Windows PowerShell kullanan isim **konumu** çalışma dizini belirtmek için ve bir ailesi cmdlet'lerini inceleyin ve konumunuz işlemek için uygular.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-108">Windows PowerShell uses the noun **Location** to refer to the working directory, and implements a family of cmdlets to examine and manipulate your location.</span></span>

### <a name="getting-your-current-location-get-location"></a><span data-ttu-id="1bdaa-109">Geçerli konumunuz (Get-konum) alma</span><span class="sxs-lookup"><span data-stu-id="1bdaa-109">Getting Your Current Location (Get-Location)</span></span>
<span data-ttu-id="1bdaa-110">Geçerli dizin konumun yolunu belirlemek için girdiğiniz **Get-Location** komutu:</span><span class="sxs-lookup"><span data-stu-id="1bdaa-110">To determine the path of your current directory location, enter the **Get-Location** command:</span></span>

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="1bdaa-111">Get-Location cmdlet benzer **pwd** BASH kabuğunda komutu.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-111">The Get-Location cmdlet is similar to the **pwd** command in the BASH shell.</span></span> <span data-ttu-id="1bdaa-112">Set-Location cmdlet benzer **cd** Cmd.exe içinde komutu.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-112">The Set-Location cmdlet is similar to the **cd** command in Cmd.exe.</span></span>

### <a name="setting-your-current-location-set-location"></a><span data-ttu-id="1bdaa-113">Geçerli konumunuz (Set-Location) ayarlama</span><span class="sxs-lookup"><span data-stu-id="1bdaa-113">Setting Your Current Location (Set-Location)</span></span>
<span data-ttu-id="1bdaa-114">**Get-Location** komutu ile kullanıldığında **Set-Location** komutu.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-114">The **Get-Location** command is used with the **Set-Location** command.</span></span> <span data-ttu-id="1bdaa-115">**Set-Location** komutu, geçerli dizin konumunu belirtmenize olanak verir.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-115">The **Set-Location** command allows you to specify your current directory location.</span></span>

```
PS> Set-Location -Path C:\Windows
```

<span data-ttu-id="1bdaa-116">Komutu girdikten sonra komutun etkisini hakkında doğrudan Microsoft'a almazsınız fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-116">After you enter the command, you will notice that you do not receive any direct feedback about the effect of the command.</span></span> <span data-ttu-id="1bdaa-117">Çıktı her zaman yararlı olmadığından bir eylem gerçekleştirmek çoğu Windows PowerShell komutlarını çok az kayıpla veya hiç çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-117">Most Windows PowerShell commands that perform an action produce little or no output because the output is not always useful.</span></span> <span data-ttu-id="1bdaa-118">Girdiğiniz zaman başarılı dizin değişikliği oluştuğunu doğrulamak için **Set-Location** içeriyor, komut **- PassThru** , girdiğiniz zaman parametresi **Set-Location**komutu:</span><span class="sxs-lookup"><span data-stu-id="1bdaa-118">To verify that a successful directory change has occurred when you enter the **Set-Location** command, include the **-PassThru** parameter when you enter the **Set-Location** command:</span></span>

```
PS> Set-Location -Path C:\Windows -PassThru
Path
----
C:\WINDOWS
```

<span data-ttu-id="1bdaa-119">**- PassThru** parametresi birçok Set komutları Windows PowerShell ile hiçbir varsayılan çıkış olduğu durumlarda sonucu hakkında bilgi döndürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-119">The **-PassThru** parameter can be used with many Set commands in Windows PowerShell to return information about the result in cases in which there is no default output.</span></span>

<span data-ttu-id="1bdaa-120">Kabukları çoğu UNIX ve Windows komut gibi aynı şekilde, geçerli konumuna göre yol belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-120">You can specify paths relative to your current location in the same way as you would in most UNIX and Windows command shells.</span></span> <span data-ttu-id="1bdaa-121">Standart gösteriminde göreli yollar için bir süre (**.**) iki kat süre ve geçerli klasörünüzü temsil eder (**..** ) geçerli konumunuz üst dizini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-121">In standard notation for relative paths, a period (**.**)represents your current folder, and a doubled period (**..**) represents the parent directory of your current location.</span></span>

<span data-ttu-id="1bdaa-122">Örneğin, içinde olup olmadığını **C:\\Windows** klasörü, bir süre (**.**) temsil eden **C:\\Windows** ve çift nokta (**..** ) temsil eden **C:**.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-122">For example, if you are in the **C:\\Windows** folder, a period (**.**)represents **C:\\Windows** and double periods (**..**) represent **C:**.</span></span> <span data-ttu-id="1bdaa-123">Yazarak C: sürücüsünün kökündeki geçerli konumundan değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1bdaa-123">You can change from your current location to the root of the C: drive by typing:</span></span>

```powershell
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

<span data-ttu-id="1bdaa-124">Dosya sistemi sürücülerine gibi olmayan Windows PowerShell sürücülerde aynı tekniği çalışır **HKLM:**.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-124">The same technique works on Windows PowerShell drives that are not file system drives, such as **HKLM:**.</span></span> <span data-ttu-id="1bdaa-125">Konumunuz HKLM ayarlayabilirsiniz\\yazarak kayıt defteri anahtarında yazılım:</span><span class="sxs-lookup"><span data-stu-id="1bdaa-125">You can set your location to the HKLM\\Software key in the registry by typing:</span></span>

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

<span data-ttu-id="1bdaa-126">Windows PowerShell HKLM köküdür üst dizini için dizin konumunu değiştirebilirsiniz: göreli bir yol kullanarak sürücü:</span><span class="sxs-lookup"><span data-stu-id="1bdaa-126">You can then change the directory location to the parent directory, which is the root of the Windows PowerShell HKLM: drive, by using a relative path:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

<span data-ttu-id="1bdaa-127">Set-Location yazın ya da yerleşik Windows PowerShell diğer adlar birini Set-Location için (cd, chdir, sl) kullanın.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-127">You can type Set-Location or use any of the built-in Windows PowerShell aliases for Set-Location (cd, chdir, sl).</span></span> <span data-ttu-id="1bdaa-128">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="1bdaa-128">For example:</span></span>

```
cd -Path C:\Windows
```

```
chdir -Path .. -PassThru
```

```
sl -Path HKLM:\SOFTWARE -PassThru
```

### <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a><span data-ttu-id="1bdaa-129">Kaydetme ve yeni konumlar (anında iletme-konumu ve Pop konumları) geri çağırma</span><span class="sxs-lookup"><span data-stu-id="1bdaa-129">Saving and Recalling Recent Locations (Push-Location and Pop-Location)</span></span>
<span data-ttu-id="1bdaa-130">Konumları değiştirirken, burada size verilmiş olması izlenmesi ve önceki konumuna geri döndürmek için yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-130">When changing locations, it is helpful to keep track of where you have been and to be able to return to your previous location.</span></span> <span data-ttu-id="1bdaa-131">**İtme konumu** Windows PowerShell cmdlet oluşturur burada size verilmiş olması ve Tamamlayıcı kullanarak geri dizin yolları geçmişinde geçebilirsiniz dizin yolları sıralı geçmişini (bir "yığını")  **POP-Location** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-131">The **Push-Location** cmdlet in Windows PowerShell creates a ordered history (a "stack") of directory paths where you have been, and you can step back through the history of directory paths by using the complementary **Pop-Location** cmdlet.</span></span>

<span data-ttu-id="1bdaa-132">Örneğin, Windows PowerShell, genellikle kullanıcının giriş dizininde başlar.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-132">For example, Windows PowerShell typically starts in the user's home directory.</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="1bdaa-133">Word *yığın* .NET Framework dahil olmak üzere pek çok programlama ayarlarında, özel bir anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-133">The word *stack* has a special meaning in many programming settings, including .NET Framework.</span></span> <span data-ttu-id="1bdaa-134">Öğeleri gibi bir fiziksel yığını yığına put son öğeyi yığın çekebilir ilk öğesidir.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-134">Like a physical stack of items, the last item you put onto the stack is the first item that you can pull off the stack.</span></span> <span data-ttu-id="1bdaa-135">Bir öğe için yığın ekleme mikroişlemciye "yığına öğesi Ftp'den olarak" adı verilir.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-135">Adding an item to a stack is colloquially known as "pushing" the item onto the stack.</span></span> <span data-ttu-id="1bdaa-136">Bir öğe yığından çekme mikroişlemciye "yığından öğesi pencerelerinin olarak" adı verilir.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-136">Pulling an item off the stack is colloquially known as "popping" the item off the stack.</span></span>

<span data-ttu-id="1bdaa-137">Geçerli konumu yığına itme ve yerel ayarlar klasörüne taşımak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="1bdaa-137">To push the current location onto the stack, and then move to the Local Settings folder, type:</span></span>

```
PS> Push-Location -Path "Local Settings"
```

<span data-ttu-id="1bdaa-138">Ardından yerel ayarları konumun yığına gönderebilir ve ve yazarak Temp klasöre gidin:</span><span class="sxs-lookup"><span data-stu-id="1bdaa-138">You can then push the Local Settings location onto the stack and and move to the Temp folder by typing:</span></span>

```
PS> Push-Location -Path Temp
```

<span data-ttu-id="1bdaa-139">Dizinleri girerek değiştiğini doğrulayın **Get-Location** komutu:</span><span class="sxs-lookup"><span data-stu-id="1bdaa-139">You can verify that you changed directories by entering the **Get-Location** command:</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

<span data-ttu-id="1bdaa-140">En son ziyaret edilen dizine girerek sonra pop **Pop-Location** komut ve değişikliği girerek doğrulayın **Get-Location** komutu:</span><span class="sxs-lookup"><span data-stu-id="1bdaa-140">You can then pop back into the most recently visited directory by entering the **Pop-Location** command, and verify the change by entering the **Get-Location** command:</span></span>

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

<span data-ttu-id="1bdaa-141">İle olarak yalnızca **Set-Location** cmdlet'ini içerebilir **- PassThru** , girdiğiniz zaman parametresi **Pop-Location** cmdlet girdiğiniz dizini görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="1bdaa-141">Just as with the **Set-Location** cmdlet, you can include the **-PassThru** parameter when you enter the **Pop-Location** cmdlet to display the directory that you entered:</span></span>

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

<span data-ttu-id="1bdaa-142">Ağ yolları ile konum cmdlet'leri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-142">You can also use the Location cmdlets with network paths.</span></span> <span data-ttu-id="1bdaa-143">Ortak adlı bir paylaşım ile FS01 adlı bir sunucunuz varsa, yazarak konumunuzu değiştirebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="1bdaa-143">If you have a server named FS01 with an share named Public, you can change your location by typing</span></span>

```
Set-Location \\FS01\Public
```

<span data-ttu-id="1bdaa-144">veya</span><span class="sxs-lookup"><span data-stu-id="1bdaa-144">or</span></span>

```
Push-Location \\FS01\Public
```

<span data-ttu-id="1bdaa-145">Kullanabileceğiniz **itme konumu** ve **Set-Location** komutların herhangi bir kullanılabilir sürücüye konumu değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-145">You can use the **Push-Location** and **Set-Location** commands to change the location to any available drive.</span></span> <span data-ttu-id="1bdaa-146">Bir veri CD içeren D sürücü harfine sahip yerel bir CD-ROM sürücüsü varsa, örneğin, konumun CD sürücüsüne girerek değiştirebileceğiniz **Set-Location D:** komutu.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-146">For example, if you have a local CD-ROM drive with drive letter D that contains a data CD, you can change the location to the CD drive by entering the **Set-Location D:** command.</span></span>

<span data-ttu-id="1bdaa-147">Sürücü boş ise, aşağıdaki hata iletisini alırsınız:</span><span class="sxs-lookup"><span data-stu-id="1bdaa-147">If the drive is empty, you will get the following error message:</span></span>

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

<span data-ttu-id="1bdaa-148">Bir komut satırı arabirimi kullanırken, kullanılabilir fiziksel sürücüleri incelemek için dosya Gezgini'ni kullanmak uygun değil.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-148">When you are using a command-line interface, it is not convenient to use File Explorer to examine the available physical drives.</span></span> <span data-ttu-id="1bdaa-149">Ayrıca, dosya Gezgini'nde, Windows PowerShell sürücüsü tüm göstermeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-149">Also, File Explorer would not show you the all of the Windows PowerShell drives.</span></span> <span data-ttu-id="1bdaa-150">Windows PowerShell sürücülerini yönetmek için Windows PowerShell komut kümesini sağlar ve biz bu sonraki hakkında konuşur.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-150">Windows PowerShell provides a set of commands for manipulating Windows PowerShell drives, and we will talk about these next.</span></span>

