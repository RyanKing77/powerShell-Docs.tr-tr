---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Geçerli Konumu Yönetme
ms.openlocfilehash: 42ab56759dec882d140f813c8614e578957722b3
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030192"
---
# <a name="managing-current-location"></a><span data-ttu-id="95168-103">Geçerli Konumu Yönetme</span><span class="sxs-lookup"><span data-stu-id="95168-103">Managing Current Location</span></span>

<span data-ttu-id="95168-104">Dosya Gezgini'nde klasörü sistemleri gittiğinizde, genellikle belirli bir çalışma konumu - yani, geçerli açık klasör sahiptir.</span><span class="sxs-lookup"><span data-stu-id="95168-104">When navigating folder systems in File Explorer, you usually have a specific working location - namely, the current open folder.</span></span> <span data-ttu-id="95168-105">Geçerli klasördeki öğeleri tıklatarak kolayca yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="95168-105">Items in the current folder can be manipulated easily by clicking them.</span></span> <span data-ttu-id="95168-106">Belirli bir dosya aynı klasörde işiniz Cmd.exe gibi komut satırı arabirimleri için tüm dosya yolunu belirtmeniz gerek yerine görece kısa bir ad belirterek erişebildiğinizi.</span><span class="sxs-lookup"><span data-stu-id="95168-106">For command-line interfaces such as Cmd.exe, when you are in the same folder as a particular file, you can access it by specifying a relatively short name, rather than needing to specify the entire path to the file.</span></span> <span data-ttu-id="95168-107">Geçerli dizin, çalışma dizini olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="95168-107">The current directory is called the working directory.</span></span>

<span data-ttu-id="95168-108">Windows PowerShell kullanan isim **konumu** çalışma dizini belirtmek için ve bir ailesi cmdlet'lerini incelemek ve işlemek, konumunuz için uygular.</span><span class="sxs-lookup"><span data-stu-id="95168-108">Windows PowerShell uses the noun **Location** to refer to the working directory, and implements a family of cmdlets to examine and manipulate your location.</span></span>

## <a name="getting-your-current-location-get-location"></a><span data-ttu-id="95168-109">Geçerli konumunuz (Get-konumu)</span><span class="sxs-lookup"><span data-stu-id="95168-109">Getting Your Current Location (Get-Location)</span></span>

<span data-ttu-id="95168-110">Geçerli dizin konumunuzun yolunu belirlemek için girin **Get-Location** komutu:</span><span class="sxs-lookup"><span data-stu-id="95168-110">To determine the path of your current directory location, enter the **Get-Location** command:</span></span>

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="95168-111">Get-Location cmdlet benzer **pwd** BASH kabuğunda komutu.</span><span class="sxs-lookup"><span data-stu-id="95168-111">The Get-Location cmdlet is similar to the **pwd** command in the BASH shell.</span></span> <span data-ttu-id="95168-112">Set-Location cmdlet benzer **cd** Cmd.exe içinde komutu.</span><span class="sxs-lookup"><span data-stu-id="95168-112">The Set-Location cmdlet is similar to the **cd** command in Cmd.exe.</span></span>

## <a name="setting-your-current-location-set-location"></a><span data-ttu-id="95168-113">Geçerli konumunuzu (konum ayarlama) ayarlama</span><span class="sxs-lookup"><span data-stu-id="95168-113">Setting Your Current Location (Set-Location)</span></span>

<span data-ttu-id="95168-114">**Get-Location** komutu ile kullanıldığında **Set-Location** komutu.</span><span class="sxs-lookup"><span data-stu-id="95168-114">The **Get-Location** command is used with the **Set-Location** command.</span></span> <span data-ttu-id="95168-115">**Set-Location** komutu, geçerli dizin konumunu belirtmenize olanak verir.</span><span class="sxs-lookup"><span data-stu-id="95168-115">The **Set-Location** command allows you to specify your current directory location.</span></span>

```powershell
Set-Location -Path C:\Windows
```

<span data-ttu-id="95168-116">Komutu girdikten sonra komut etkisi hakkında Geri bildirimlerinizi doğrudan almazsınız fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="95168-116">After you enter the command, you will notice that you do not receive any direct feedback about the effect of the command.</span></span> <span data-ttu-id="95168-117">Çıkış her zaman kullanışlı olmadığı için bir eylem gerçekleştiren çoğu Windows PowerShell komutlarını çok az kayıpla veya hiç çıkış üretir.</span><span class="sxs-lookup"><span data-stu-id="95168-117">Most Windows PowerShell commands that perform an action produce little or no output because the output is not always useful.</span></span> <span data-ttu-id="95168-118">Girdiğiniz zaman başarılı dizin değişikliği oluştuğunu doğrulamak için **Set-Location** komutu, dahil **- PassThru** , girdiğinizde parametresi **Set-Location**komutu:</span><span class="sxs-lookup"><span data-stu-id="95168-118">To verify that a successful directory change has occurred when you enter the **Set-Location** command, include the **-PassThru** parameter when you enter the **Set-Location** command:</span></span>

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

<span data-ttu-id="95168-119">**- PassThru** parametre kümesi komutların çoğu Windows PowerShell ile varsayılan çıkış olduğu durumlarda sonuç hakkında bilgi döndürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="95168-119">The **-PassThru** parameter can be used with many Set commands in Windows PowerShell to return information about the result in cases in which there is no default output.</span></span>

<span data-ttu-id="95168-120">Kabuklar çoğu Windows ve UNIX komutunu gibi aynı şekilde geçerli konumunuza göre yolu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95168-120">You can specify paths relative to your current location in the same way as you would in most UNIX and Windows command shells.</span></span> <span data-ttu-id="95168-121">Göreli yollar için standart gösteriminde bir süre ( **.** ) Geçerli klasörünüzü ve iki kat bir süre temsil eder ( **..** ) geçerli konumunuzu üst dizinini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="95168-121">In standard notation for relative paths, a period (**.**)represents your current folder, and a doubled period (**..**) represents the parent directory of your current location.</span></span>

<span data-ttu-id="95168-122">Örneğin, bulunduğunuz **C:\\Windows** klasörü, nokta ( **.** ) temsil eden **C:\\Windows** ve çift nokta ( **..** ) temsil eden **C:** .</span><span class="sxs-lookup"><span data-stu-id="95168-122">For example, if you are in the **C:\\Windows** folder, a period (**.**)represents **C:\\Windows** and double periods (**..**) represent **C:**.</span></span> <span data-ttu-id="95168-123">Yazarak geçerli konumunuzdan C: sürücüsünün köküne değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="95168-123">You can change from your current location to the root of the C: drive by typing:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

<span data-ttu-id="95168-124">Dosya sistemi sürücüleri gibi olmayan Windows PowerShell sürücülerini aynı tekniği çalışır **HKLM:** .</span><span class="sxs-lookup"><span data-stu-id="95168-124">The same technique works on Windows PowerShell drives that are not file system drives, such as **HKLM:**.</span></span> <span data-ttu-id="95168-125">Konumunuz için HKLM ayarlayabilirsiniz\\yazarak kayıt defteri anahtarında yazılım:</span><span class="sxs-lookup"><span data-stu-id="95168-125">You can set your location to the HKLM\\Software key in the registry by typing:</span></span>

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

<span data-ttu-id="95168-126">Windows PowerShell HKLM köküdür üst dizine dizin konumunu değiştirebilirsiniz: göreli yolu kullanarak sürücü:</span><span class="sxs-lookup"><span data-stu-id="95168-126">You can then change the directory location to the parent directory, which is the root of the Windows PowerShell HKLM: drive, by using a relative path:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

<span data-ttu-id="95168-127">Set-Location yazın veya Set-Location için (cd, chdir, sl) herhangi bir yerleşik Windows PowerShell diğer adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="95168-127">You can type Set-Location or use any of the built-in Windows PowerShell aliases for Set-Location (cd, chdir, sl).</span></span> <span data-ttu-id="95168-128">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="95168-128">For example:</span></span>

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

## <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a><span data-ttu-id="95168-129">Kaydetme ve en son konumlar (anında iletme konumu ve bulunma noktası konumuna) geri çağırma</span><span class="sxs-lookup"><span data-stu-id="95168-129">Saving and Recalling Recent Locations (Push-Location and Pop-Location)</span></span>

<span data-ttu-id="95168-130">Konumları değiştirirken, burada size verilmiş olması, izlenmesi ve, önceki konumuna geri döndürmek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="95168-130">When changing locations, it is helpful to keep track of where you have been and to be able to return to your previous location.</span></span> <span data-ttu-id="95168-131">**Anında iletme konumu** Windows PowerShell cmdlet'i, burada size verilmiş olması ve Tamamlayıcı kullanarak geri dizin yolları geçmişinde geçebilirsiniz dizin yolları sıralı geçmişini ("yığın") oluşturur  **Bulunma noktası konumuna** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="95168-131">The **Push-Location** cmdlet in Windows PowerShell creates a ordered history (a "stack") of directory paths where you have been, and you can step back through the history of directory paths by using the complementary **Pop-Location** cmdlet.</span></span>

<span data-ttu-id="95168-132">Örneğin, Windows PowerShell, genellikle kullanıcının giriş dizininde başlar.</span><span class="sxs-lookup"><span data-stu-id="95168-132">For example, Windows PowerShell typically starts in the user's home directory.</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="95168-133">Word *yığın* .NET Framework dahil olmak üzere pek çok programlama Ayarları'nda özel bir anlamı vardır.</span><span class="sxs-lookup"><span data-stu-id="95168-133">The word *stack* has a special meaning in many programming settings, including .NET Framework.</span></span> <span data-ttu-id="95168-134">Öğeleri fiziksel yığını gibi yığın üstüne koymak son öğeyi, yığının çekebilirsiniz ilk öğedir.</span><span class="sxs-lookup"><span data-stu-id="95168-134">Like a physical stack of items, the last item you put onto the stack is the first item that you can pull off the stack.</span></span> <span data-ttu-id="95168-135">Bir yığın için bir öğe eklemeye mikroişlemciye "öğesi yığına göndermek" adı verilir.</span><span class="sxs-lookup"><span data-stu-id="95168-135">Adding an item to a stack is colloquially known as "pushing" the item onto the stack.</span></span> <span data-ttu-id="95168-136">Bir öğe yığından çekme mikroişlemciye "öğesi yığından pencerelerinin olarak" adı verilir.</span><span class="sxs-lookup"><span data-stu-id="95168-136">Pulling an item off the stack is colloquially known as "popping" the item off the stack.</span></span>

<span data-ttu-id="95168-137">Geçerli konumun yığına anında iletme ve ardından yerel ayarlar klasörüne taşımak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="95168-137">To push the current location onto the stack, and then move to the Local Settings folder, type:</span></span>

```powershell
Push-Location -Path "Local Settings"
```

<span data-ttu-id="95168-138">Yerel ayarlar konumunu yığına gönderin ve yazarak Temp klasörüne taşıyın:</span><span class="sxs-lookup"><span data-stu-id="95168-138">You can then push the Local Settings location onto the stack and move to the Temp folder by typing:</span></span>

```powershell
Push-Location -Path Temp
```

<span data-ttu-id="95168-139">Dizinleri girerek değiştiğini doğrulayın **Get-Location** komutu:</span><span class="sxs-lookup"><span data-stu-id="95168-139">You can verify that you changed directories by entering the **Get-Location** command:</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

<span data-ttu-id="95168-140">En son ziyaret edilen dizine girerek ardından açılan **bulunma noktası konumuna** komutunu ve girerek değişikliği doğrulayın **Get-Location** komutu:</span><span class="sxs-lookup"><span data-stu-id="95168-140">You can then pop back into the most recently visited directory by entering the **Pop-Location** command, and verify the change by entering the **Get-Location** command:</span></span>

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

<span data-ttu-id="95168-141">Olduğu gibi **Set-Location** cmdlet'ini içerebilir **- PassThru** , girdiğinizde parametresi **bulunma noktası konumuna** cmdlet'i girdiğiniz dizin görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="95168-141">Just as with the **Set-Location** cmdlet, you can include the **-PassThru** parameter when you enter the **Pop-Location** cmdlet to display the directory that you entered:</span></span>

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

<span data-ttu-id="95168-142">Ağ konumu cmdlet'leri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95168-142">You can also use the Location cmdlets with network paths.</span></span> <span data-ttu-id="95168-143">Ortak adlı bir paylaşım ile FS01 adlı bir sunucu varsa, konumunuzu yazarak değiştirebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="95168-143">If you have a server named FS01 with an share named Public, you can change your location by typing</span></span>

```powershell
Set-Location \\FS01\Public
```

<span data-ttu-id="95168-144">veya</span><span class="sxs-lookup"><span data-stu-id="95168-144">or</span></span>

```powershell
Push-Location \\FS01\Public
```

<span data-ttu-id="95168-145">Kullanabileceğiniz **anında iletme konumu** ve **Set-Location** herhangi bir kullanılabilir sürücü konumunu değiştirmek için komutları.</span><span class="sxs-lookup"><span data-stu-id="95168-145">You can use the **Push-Location** and **Set-Location** commands to change the location to any available drive.</span></span> <span data-ttu-id="95168-146">Bir veri CD içeren D sürücü harfine sahip yerel bir CD-ROM sürücüsü varsa, örneğin, konum CD sürücüsüne girerek değiştirebileceğiniz **Set-Location D:** komutu.</span><span class="sxs-lookup"><span data-stu-id="95168-146">For example, if you have a local CD-ROM drive with drive letter D that contains a data CD, you can change the location to the CD drive by entering the **Set-Location D:** command.</span></span>

<span data-ttu-id="95168-147">Sürücü boş ise, aşağıdaki hata iletisini alırsınız:</span><span class="sxs-lookup"><span data-stu-id="95168-147">If the drive is empty, you will get the following error message:</span></span>

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

<span data-ttu-id="95168-148">Bir komut satırı arabirimi kullanırken, kullanılabilir fiziksel sürücüleri incelemek için dosya Gezgini'ni kullanmak uygun değil.</span><span class="sxs-lookup"><span data-stu-id="95168-148">When you are using a command-line interface, it is not convenient to use File Explorer to examine the available physical drives.</span></span> <span data-ttu-id="95168-149">Ayrıca, dosya Gezgini'nde, tüm Windows PowerShell sürücüsü göstermeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="95168-149">Also, File Explorer would not show you the all of the Windows PowerShell drives.</span></span> <span data-ttu-id="95168-150">Windows PowerShell sürücülerini yönetmek için Windows PowerShell komut kümesini sağlar ve biz bu sonraki hakkında Bahsediyor.</span><span class="sxs-lookup"><span data-stu-id="95168-150">Windows PowerShell provides a set of commands for manipulating Windows PowerShell drives, and we will talk about these next.</span></span>
