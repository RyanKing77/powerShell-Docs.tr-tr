---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Kayıt Defteri Girdileri ile Çalışma
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405912"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="4f649-103">Kayıt Defteri Girdileri ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="4f649-103">Working with Registry Entries</span></span>

<span data-ttu-id="4f649-104">Kayıt defteri girdileri tuşunun özelliklerini ve bu nedenle, doğrudan gözatılamaz olduğundan bunlarla çalışırken biraz farklı bir yaklaşım olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f649-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

### <a name="listing-registry-entries"></a><span data-ttu-id="4f649-105">Kayıt defteri girdileri listeleme</span><span class="sxs-lookup"><span data-stu-id="4f649-105">Listing Registry Entries</span></span>

<span data-ttu-id="4f649-106">Kayıt defteri girdilerini incelemek için birçok farklı yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="4f649-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="4f649-107">En basit yolu, bir anahtar ile ilişkili özellik adlarını almaktır.</span><span class="sxs-lookup"><span data-stu-id="4f649-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="4f649-108">Örneğin, kayıt defteri anahtarı girişleri adlarını görmek için **HKEY_LOCAL_MACHINE\\yazılım\\Microsoft\\Windows\\CurrentVersion**, kullanın **Get-öğe** .</span><span class="sxs-lookup"><span data-stu-id="4f649-108">For example, to see the names of the entries in the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, use **Get-Item**.</span></span> <span data-ttu-id="4f649-109">Kayıt defteri anahtarlarını bir özelliğe sahip genel "Özelliği" adı ile kayıt defteri girdileri anahtarında bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="4f649-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span> <span data-ttu-id="4f649-110">Aşağıdaki komut, özellik özelliğini seçer ve böylece bunlar bir listede görüntülenen öğelerin genişletir:</span><span class="sxs-lookup"><span data-stu-id="4f649-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="4f649-111">Kayıt defteri girdilerini daha okunabilir bir formda görüntülemek için kullanın **Get-Itemproperty**:</span><span class="sxs-lookup"><span data-stu-id="4f649-111">To view the registry entries in a more readable form, use **Get-ItemProperty**:</span></span>

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

<span data-ttu-id="4f649-112">Anahtar için Windows PowerShell ile ilgili özelliklerin tümünü "PS ile" gibi ön ekli **pspath değeri**, **PSParentPath**, **PSChildName**, ve **PSProvider** .</span><span class="sxs-lookup"><span data-stu-id="4f649-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="4f649-113">Kullanabileceğiniz "**.**" için geçerli konuma başvuran gösterimi.</span><span class="sxs-lookup"><span data-stu-id="4f649-113">You can use the "**.**" notation for referring to the current location.</span></span> <span data-ttu-id="4f649-114">Kullanabileceğiniz **Set-Location** değiştirmek için **CurrentVersion** kapsayıcı kayıt defteri ilk:</span><span class="sxs-lookup"><span data-stu-id="4f649-114">You can use **Set-Location** to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="4f649-115">Alternatif olarak, yerleşik HKLM PSDrive ile kullanabileceğiniz **Set-Location**:</span><span class="sxs-lookup"><span data-stu-id="4f649-115">Alternatively, you can use the built-in HKLM PSDrive with **Set-Location**:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="4f649-116">Daha sonra "**.**" gösterim tam bir yol belirtmeden özellikleri listelemek şu anki konum için:</span><span class="sxs-lookup"><span data-stu-id="4f649-116">You can then use the "**.**" notation for the current location to list the properties without specifying a full path:</span></span>

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="4f649-117">Yolu genişletme çalışır, aynı, bu konumdan, yani, dosya sisteminde çalıştığı gibi **Itemproperty** için listeleme **HKLM:\\yazılım\\Microsoft\\Windows \\Yardımcı** kullanarak **Itemproperty Get-yolu... \\Yardımcı**.</span><span class="sxs-lookup"><span data-stu-id="4f649-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** by using **Get-ItemProperty -Path ..\\Help**.</span></span>

### <a name="getting-a-single-registry-entry"></a><span data-ttu-id="4f649-118">Tek bir kayıt defteri girişi alınırken</span><span class="sxs-lookup"><span data-stu-id="4f649-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="4f649-119">Bir kayıt defteri anahtarı içinde belirli bir girdi almak istiyorsanız, birkaç olası yaklaşımlardan birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f649-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="4f649-120">Bu örnekte değerini bulur **DevicePath** içinde **HKEY_LOCAL_MACHINE\\yazılım\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="4f649-120">This example finds the value of **DevicePath** in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span>

<span data-ttu-id="4f649-121">Kullanarak **Get-Itemproperty**, kullanın **yolu** anahtarın adını belirtmek için parametre ve **adı** adını belirtmek için parametre **DevicePath** girişi.</span><span class="sxs-lookup"><span data-stu-id="4f649-121">Using **Get-ItemProperty**, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

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

<span data-ttu-id="4f649-122">Bu komut, standart Windows PowerShell özellikleri döndürür. yanı sıra **DevicePath** özelliği.</span><span class="sxs-lookup"><span data-stu-id="4f649-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="4f649-123">Ancak **Get-Itemproperty** sahip **filtre**, **Ekle**, ve **hariç** parametreleri, özellik adına göre filtre uygulamak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4f649-123">Although **Get-ItemProperty** has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="4f649-124">Bu parametreler kayıt defteri anahtarlarını başvuran — öğe yolları olduğu — ve kayıt defteri girdilerini — öğesi özellikleri olan.</span><span class="sxs-lookup"><span data-stu-id="4f649-124">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="4f649-125">Başka bir seçenek Reg.exe komut satırı aracını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="4f649-125">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="4f649-126">Reg.exe ile daha fazla yardım için şunu yazın **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="4f649-126">For help with reg.exe, type **reg.exe /?**</span></span> <span data-ttu-id="4f649-127">bir komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="4f649-127">at a command prompt.</span></span> <span data-ttu-id="4f649-128">Reg.exe DevicePath giriş bulmak için aşağıdaki komutta gösterildiği gibi kullanın:</span><span class="sxs-lookup"><span data-stu-id="4f649-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="4f649-129">Ayrıca **WshShell COM** büyük ikili veri gibi karakterler kayıt defteri girişi adları ile veya bu yöntem çalışmaz ancak bazı kayıt defteri girdilerini de bulunacak nesne "\\").</span><span class="sxs-lookup"><span data-stu-id="4f649-129">You can also use the **WshShell COM** object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="4f649-130">Öğe yolu ile özellik adının sonuna bir \\ ayırıcı:</span><span class="sxs-lookup"><span data-stu-id="4f649-130">Append the property name to the item path with a \\ separator:</span></span>

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a><span data-ttu-id="4f649-131">Yeni kayıt defteri girdileri oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="4f649-131">Creating New Registry Entries</span></span>

<span data-ttu-id="4f649-132">"PowerShellPath" adlı yeni bir giriş eklemek için **CurrentVersion** anahtar, kullanım **yeni Itemproperty** yoluyla anahtar, giriş adı ve giriş değeri.</span><span class="sxs-lookup"><span data-stu-id="4f649-132">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use **New-ItemProperty** with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="4f649-133">Bu örnekte, biz Windows PowerShell değişkeninin değeri sürer **$PSHome**, Windows PowerShell için yükleme dizini yolunu depolar.</span><span class="sxs-lookup"><span data-stu-id="4f649-133">For this example, we will take the value of the Windows PowerShell variable **$PSHome**, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="4f649-134">Aşağıdaki komutu kullanarak yeni giriş anahtarı ekleyebilirsiniz ve komut ayrıca yeni giriş hakkındaki bilgileri döndürür:</span><span class="sxs-lookup"><span data-stu-id="4f649-134">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

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

<span data-ttu-id="4f649-135">**PropertyType** adı olmalıdır bir **Microsoft.Win32.RegistryValueKind** numaralandırma üyesi aşağıdaki tabloda:</span><span class="sxs-lookup"><span data-stu-id="4f649-135">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="4f649-136">PropertyType değeri</span><span class="sxs-lookup"><span data-stu-id="4f649-136">PropertyType Value</span></span>|<span data-ttu-id="4f649-137">Anlamı</span><span class="sxs-lookup"><span data-stu-id="4f649-137">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="4f649-138">İkili</span><span class="sxs-lookup"><span data-stu-id="4f649-138">Binary</span></span>|<span data-ttu-id="4f649-139">İkili veriler</span><span class="sxs-lookup"><span data-stu-id="4f649-139">Binary data</span></span>|
|<span data-ttu-id="4f649-140">DWord</span><span class="sxs-lookup"><span data-stu-id="4f649-140">DWord</span></span>|<span data-ttu-id="4f649-141">Geçerli bir UInt32 bir sayı</span><span class="sxs-lookup"><span data-stu-id="4f649-141">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="4f649-142">Dizeyi Genişlet</span><span class="sxs-lookup"><span data-stu-id="4f649-142">ExpandString</span></span>|<span data-ttu-id="4f649-143">Dinamik olarak genişletilen ortam değişkenleri içerebilir bir dize</span><span class="sxs-lookup"><span data-stu-id="4f649-143">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="4f649-144">MultiString</span><span class="sxs-lookup"><span data-stu-id="4f649-144">MultiString</span></span>|<span data-ttu-id="4f649-145">Çok satırlı string</span><span class="sxs-lookup"><span data-stu-id="4f649-145">A multiline string</span></span>|
|<span data-ttu-id="4f649-146">Dize</span><span class="sxs-lookup"><span data-stu-id="4f649-146">String</span></span>|<span data-ttu-id="4f649-147">Herhangi bir dize değeri</span><span class="sxs-lookup"><span data-stu-id="4f649-147">Any string value</span></span>|
|<span data-ttu-id="4f649-148">QWord</span><span class="sxs-lookup"><span data-stu-id="4f649-148">QWord</span></span>|<span data-ttu-id="4f649-149">8 bayt ikili veri</span><span class="sxs-lookup"><span data-stu-id="4f649-149">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="4f649-150">Bir dizi değerlerini belirterek, birden fazla konuma bir kayıt defteri girişi ekleyebilirsiniz **yolu** parametresi:</span><span class="sxs-lookup"><span data-stu-id="4f649-150">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

<span data-ttu-id="4f649-151">Önceden var olan bir kayıt defteri girdisinin değeri ekleyerek de kılabilirsiniz **zorla** herhangi bir parametre **yeni Itemproperty** komutu.</span><span class="sxs-lookup"><span data-stu-id="4f649-151">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any **New-ItemProperty** command.</span></span>

### <a name="renaming-registry-entries"></a><span data-ttu-id="4f649-152">Kayıt defteri girdileri yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="4f649-152">Renaming Registry Entries</span></span>

<span data-ttu-id="4f649-153">Yeniden adlandırmak için **PowerShellPath** "PSHome," kullanım girişe **yeniden adlandırma Itemproperty**:</span><span class="sxs-lookup"><span data-stu-id="4f649-153">To rename the **PowerShellPath** entry to "PSHome," use **Rename-ItemProperty**:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="4f649-154">Yeniden adlandırılan değerini görüntülemek için Ekle **PassThru** komut parametresi.</span><span class="sxs-lookup"><span data-stu-id="4f649-154">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a><span data-ttu-id="4f649-155">Kayıt defteri girdileri silme</span><span class="sxs-lookup"><span data-stu-id="4f649-155">Deleting Registry Entries</span></span>

<span data-ttu-id="4f649-156">PSHome ve PowerShellPath kayıt defteri girdileri silmek için kullanın **Remove-Itemproperty**:</span><span class="sxs-lookup"><span data-stu-id="4f649-156">To delete both the PSHome and PowerShellPath registry entries, use **Remove-ItemProperty**:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```