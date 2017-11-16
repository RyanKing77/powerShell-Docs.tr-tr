---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Kayıt defteri girdileri ile çalışma"
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 039203a1a6549d4ba33424a278e4803a5e143d4d
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="4f911-103">Kayıt defteri girdileri ile çalışma</span><span class="sxs-lookup"><span data-stu-id="4f911-103">Working with Registry Entries</span></span>
<span data-ttu-id="4f911-104">Kayıt defteri girişleri anahtarların özelliklerini ve bu nedenle, doğrudan gözatılamaz olduğundan, bunları ile çalışırken, biraz daha farklı bir yaklaşım uygular gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f911-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

### <a name="listing-registry-entries"></a><span data-ttu-id="4f911-105">Kayıt defteri girdileri listeleme</span><span class="sxs-lookup"><span data-stu-id="4f911-105">Listing Registry Entries</span></span>
<span data-ttu-id="4f911-106">Kayıt defteri girdileri incelemek için birçok farklı yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="4f911-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="4f911-107">En basit yolu, bir anahtar ile ilişkili özellik adlarının almaktır.</span><span class="sxs-lookup"><span data-stu-id="4f911-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="4f911-108">Örneğin, kayıt defteri anahtarı girişleri adlarını görmek için **HKEY_LOCAL_MACHINE\\yazılım\\Microsoft\\Windows\\CurrentVersion**, kullanın **Get-öğesi** .</span><span class="sxs-lookup"><span data-stu-id="4f911-108">For example, to see the names of the entries in the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, use **Get-Item**.</span></span> <span data-ttu-id="4f911-109">Kayıt defteri anahtarlarını bir özellik olması "Özelliği" Genel adı ile kayıt defteri girdileri anahtarındaki bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="4f911-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span> <span data-ttu-id="4f911-110">Aşağıdaki komutu özellik özelliğini seçer ve böylece bir listede görüntülenen öğelerin genişletir:</span><span class="sxs-lookup"><span data-stu-id="4f911-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="4f911-111">Kayıt defteri girdilerini daha okunabilir bir formda görüntülemek için kullanın **Get-ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="4f911-111">To view the registry entries in a more readable form, use **Get-ItemProperty**:</span></span>

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

<span data-ttu-id="4f911-112">Windows PowerShell ile ilgili özellikler anahtarı için tüm "PS ile" gibi önek **PSPath**, **PSParentPath**, **PSChildName**, ve **PSProvider** .</span><span class="sxs-lookup"><span data-stu-id="4f911-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="4f911-113">Kullanabileceğiniz "**.**" geçerli konuma başvuran gösterimi.</span><span class="sxs-lookup"><span data-stu-id="4f911-113">You can use the "**.**" notation for referring to the current location.</span></span> <span data-ttu-id="4f911-114">Kullanabileceğiniz **Set-Location** değiştirmek için **CurrentVersion** kayıt defteri kapsayıcı ilk:</span><span class="sxs-lookup"><span data-stu-id="4f911-114">You can use **Set-Location** to change to the **CurrentVersion** registry container first:</span></span>

```
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="4f911-115">Alternatif olarak, yerleşik HKLM PSDrive ile kullanabileceğiniz **Set-Location**:</span><span class="sxs-lookup"><span data-stu-id="4f911-115">Alternatively, you can use the built-in HKLM PSDrive with **Set-Location**:</span></span>

```
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="4f911-116">Daha sonra "**.**" gösterimini bir tam yol belirtmeden özellikleri listelemek geçerli konumu için:</span><span class="sxs-lookup"><span data-stu-id="4f911-116">You can then use the "**.**" notation for the current location to list the properties without specifying a full path:</span></span>

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="4f911-117">Yolu genişletme çalışır, aynı, bu konumdan, böylece dosya sisteminde olduğu gibi **ItemProperty** için listeleme **HKLM:\\yazılım\\Microsoft\\Windows \\Yardımcı** kullanarak **Get-ItemProperty-yol... \\Yardımcı**.</span><span class="sxs-lookup"><span data-stu-id="4f911-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** by using **Get-ItemProperty -Path ..\\Help**.</span></span>

### <a name="getting-a-single-registry-entry"></a><span data-ttu-id="4f911-118">Bir tek kayıt defteri girişi alma</span><span class="sxs-lookup"><span data-stu-id="4f911-118">Getting a Single Registry Entry</span></span>
<span data-ttu-id="4f911-119">Bir kayıt defteri anahtarında belirli bir girdi almak istiyorsanız, birkaç olası yaklaşımlardan birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f911-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="4f911-120">Bu örnek değerini bulur **DevicePath** içinde **HKEY_LOCAL_MACHINE\\yazılım\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="4f911-120">This example finds the value of **DevicePath** in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span>

<span data-ttu-id="4f911-121">Kullanarak **Get-ItemProperty**, kullanın **yolu** anahtarın adını belirtmek için parametre ve **adı** adını belirtmek için parametresini **DevicePath** girişi.</span><span class="sxs-lookup"><span data-stu-id="4f911-121">Using **Get-ItemProperty**, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="4f911-122">Bu komut, standart Windows PowerShell özellikleri döndürür. yanı sıra **DevicePath** özelliği.</span><span class="sxs-lookup"><span data-stu-id="4f911-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="4f911-123">Ancak **Get-ItemProperty** sahip **filtre**, **INCLUDE**, ve **hariç** parametreleri, özellik adına göre filtre uygulamak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4f911-123">Although **Get-ItemProperty** has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="4f911-124">Bu parametreler kayıt defteri anahtarlarını başvurmak — öğesi yolları olduğu — ve kayıt defteri girdilerini — öğe özellikleri olduğu.</span><span class="sxs-lookup"><span data-stu-id="4f911-124">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="4f911-125">Başka bir seçenek Reg.exe komut satırı aracını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="4f911-125">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="4f911-126">Reg.exe ile daha fazla yardım için şunu yazın **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="4f911-126">For help with reg.exe, type **reg.exe /?**</span></span> <span data-ttu-id="4f911-127">bir komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="4f911-127">at a command prompt.</span></span> <span data-ttu-id="4f911-128">DevicePath girişi bulmak için aşağıdaki komutta gösterildiği gibi reg.exe kullanın:</span><span class="sxs-lookup"><span data-stu-id="4f911-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="4f911-129">Aynı zamanda **WshShell COM** bu yöntem karakter gibi içeren kayıt defteri girişi adları veya büyük ikili veri ile çalışmaz ancak bazı kayıt defteri girdilerini de bulunacak nesne "\\").</span><span class="sxs-lookup"><span data-stu-id="4f911-129">You can also use the **WshShell COM** object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="4f911-130">Özellik adı ile öğe yolu sonuna bir \\ ayırıcı:</span><span class="sxs-lookup"><span data-stu-id="4f911-130">Append the property name to the item path with a \\ separator:</span></span>

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a><span data-ttu-id="4f911-131">Yeni kayıt defteri girdileri oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="4f911-131">Creating New Registry Entries</span></span>
<span data-ttu-id="4f911-132">"PowerShellPath" adlı yeni bir giriş eklemek için **CurrentVersion** anahtar, kullanım **yeni ItemProperty** anahtarı, giriş adı ve girdisinin değeri yoluyla.</span><span class="sxs-lookup"><span data-stu-id="4f911-132">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use **New-ItemProperty** with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="4f911-133">Bu örnekte, biz Windows PowerShell değişkenin değerini sürer **$PSHome**, Windows PowerShell için yükleme dizini yolunu depolar.</span><span class="sxs-lookup"><span data-stu-id="4f911-133">For this example, we will take the value of the Windows PowerShell variable **$PSHome**, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="4f911-134">Aşağıdaki komutu kullanarak yeni giriş anahtarına ekleyebilirsiniz ve komut ayrıca yeni giriş hakkında bilgi verir:</span><span class="sxs-lookup"><span data-stu-id="4f911-134">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="4f911-135">**PropertyType** adı olmalıdır bir **Microsoft.Win32.RegistryValueKind** numaralandırma üyesi aşağıdaki tablodan:</span><span class="sxs-lookup"><span data-stu-id="4f911-135">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="4f911-136">PropertyType değeri</span><span class="sxs-lookup"><span data-stu-id="4f911-136">PropertyType Value</span></span>|<span data-ttu-id="4f911-137">Anlamı</span><span class="sxs-lookup"><span data-stu-id="4f911-137">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="4f911-138">İkili</span><span class="sxs-lookup"><span data-stu-id="4f911-138">Binary</span></span>|<span data-ttu-id="4f911-139">İkili veriler</span><span class="sxs-lookup"><span data-stu-id="4f911-139">Binary data</span></span>|
|<span data-ttu-id="4f911-140">DWord</span><span class="sxs-lookup"><span data-stu-id="4f911-140">DWord</span></span>|<span data-ttu-id="4f911-141">Geçerli bir Uınt32 bir sayı</span><span class="sxs-lookup"><span data-stu-id="4f911-141">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="4f911-142">Dizeyi Genişlet</span><span class="sxs-lookup"><span data-stu-id="4f911-142">ExpandString</span></span>|<span data-ttu-id="4f911-143">Dinamik olarak genişletilen ortam değişkenleri içerebilir bir dize</span><span class="sxs-lookup"><span data-stu-id="4f911-143">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="4f911-144">MultiString</span><span class="sxs-lookup"><span data-stu-id="4f911-144">MultiString</span></span>|<span data-ttu-id="4f911-145">Çok satırlı bir dize</span><span class="sxs-lookup"><span data-stu-id="4f911-145">A multiline string</span></span>|
|<span data-ttu-id="4f911-146">Dize</span><span class="sxs-lookup"><span data-stu-id="4f911-146">String</span></span>|<span data-ttu-id="4f911-147">Herhangi bir dize değeri</span><span class="sxs-lookup"><span data-stu-id="4f911-147">Any string value</span></span>|
|<span data-ttu-id="4f911-148">QWord</span><span class="sxs-lookup"><span data-stu-id="4f911-148">QWord</span></span>|<span data-ttu-id="4f911-149">8 bayt ikili veri</span><span class="sxs-lookup"><span data-stu-id="4f911-149">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="4f911-150">Değer bir dizi belirterek birden fazla konuma bir kayıt defteri girişi ekleyebilirsiniz **yolu** parametre:</span><span class="sxs-lookup"><span data-stu-id="4f911-150">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

<span data-ttu-id="4f911-151">Ekleyerek önceden var olan bir kayıt defteri girdisinin değeri kılabilirsiniz **zorla** herhangi bir parametre **yeni ItemProperty** komutu.</span><span class="sxs-lookup"><span data-stu-id="4f911-151">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any **New-ItemProperty** command.</span></span>

### <a name="renaming-registry-entries"></a><span data-ttu-id="4f911-152">Kayıt defteri girdileri yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="4f911-152">Renaming Registry Entries</span></span>
<span data-ttu-id="4f911-153">Yeniden adlandırmak için **PowerShellPath** "PSHome," kullanım girişe **yeniden adlandırma ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="4f911-153">To rename the **PowerShellPath** entry to "PSHome," use **Rename-ItemProperty**:</span></span>

```
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="4f911-154">Yeniden adlandırılmış değerini görüntülemek için ekleme **PassThru** komut parametresi.</span><span class="sxs-lookup"><span data-stu-id="4f911-154">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a><span data-ttu-id="4f911-155">Kayıt defteri girişlerini silme</span><span class="sxs-lookup"><span data-stu-id="4f911-155">Deleting Registry Entries</span></span>
<span data-ttu-id="4f911-156">PSHome ve PowerShellPath kayıt defteri girdilerini silmek için kullanın **Kaldır ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="4f911-156">To delete both the PSHome and PowerShellPath registry entries, use **Remove-ItemProperty**:</span></span>

```
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```

