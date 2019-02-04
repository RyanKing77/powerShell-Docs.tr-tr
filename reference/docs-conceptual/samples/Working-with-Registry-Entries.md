---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Kayıt Defteri Girdileri ile Çalışma
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 8483b6f98739697b24a13055dfffbc7b5bacc2cc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686813"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="351c2-103">Kayıt Defteri Girdileri ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="351c2-103">Working with Registry Entries</span></span>

<span data-ttu-id="351c2-104">Kayıt defteri girdileri tuşunun özelliklerini ve bu nedenle, doğrudan gözatılamaz olduğundan bunlarla çalışırken biraz farklı bir yaklaşım olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="351c2-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

### <a name="listing-registry-entries"></a><span data-ttu-id="351c2-105">Kayıt defteri girdileri listeleme</span><span class="sxs-lookup"><span data-stu-id="351c2-105">Listing Registry Entries</span></span>

<span data-ttu-id="351c2-106">Kayıt defteri girdilerini incelemek için birçok farklı yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="351c2-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="351c2-107">En basit yolu, bir anahtar ile ilişkili özellik adlarını almaktır.</span><span class="sxs-lookup"><span data-stu-id="351c2-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="351c2-108">Örneğin, kayıt defteri anahtarı girişleri adlarını görmek için `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, kullanın `Get-Item`.</span><span class="sxs-lookup"><span data-stu-id="351c2-108">For example, to see the names of the entries in the registry key `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, use `Get-Item`.</span></span> <span data-ttu-id="351c2-109">Kayıt defteri anahtarlarını bir özelliğe sahip genel "Özelliği" adı ile kayıt defteri girdileri anahtarında bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="351c2-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span>
<span data-ttu-id="351c2-110">Aşağıdaki komut, özellik özelliğini seçer ve böylece bunlar bir listede görüntülenen öğelerin genişletir:</span><span class="sxs-lookup"><span data-stu-id="351c2-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="351c2-111">Kayıt defteri girdilerini daha okunabilir bir formda görüntülemek için kullanın `Get-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="351c2-111">To view the registry entries in a more readable form, use `Get-ItemProperty`:</span></span>

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
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

<span data-ttu-id="351c2-112">Anahtar için Windows PowerShell ile ilgili özelliklerin tümünü "PS ile" gibi ön ekli **pspath değeri**, **PSParentPath**, **PSChildName**, ve **PSProvider** .</span><span class="sxs-lookup"><span data-stu-id="351c2-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="351c2-113">Kullanabileceğiniz `*.*` geçerli konuma başvuran için gösterimi.</span><span class="sxs-lookup"><span data-stu-id="351c2-113">You can use the `*.*` notation for referring to the current location.</span></span> <span data-ttu-id="351c2-114">Kullanabileceğiniz `Set-Location` değiştirmek için **CurrentVersion** kapsayıcı kayıt defteri ilk:</span><span class="sxs-lookup"><span data-stu-id="351c2-114">You can use `Set-Location` to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="351c2-115">Alternatif olarak, yerleşik HKLM PSDrive ile kullanabileceğiniz `Set-Location`:</span><span class="sxs-lookup"><span data-stu-id="351c2-115">Alternatively, you can use the built-in HKLM PSDrive with `Set-Location`:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="351c2-116">Ardından `*.*` gösterimi tam bir yol belirtmeden özellikleri listelemek şu anki konum için:</span><span class="sxs-lookup"><span data-stu-id="351c2-116">You can then use the `*.*` notation for the current location to list the properties without specifying a full path:</span></span>

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="351c2-117">Yolu genişletme çalışır, aynı, bu konumdan, yani, dosya sisteminde çalıştığı gibi **Itemproperty** için listeleme `HKLM:\SOFTWARE\Microsoft\Windows\Help` kullanarak `Get-ItemProperty -Path ..\Help`.</span><span class="sxs-lookup"><span data-stu-id="351c2-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for `HKLM:\SOFTWARE\Microsoft\Windows\Help` by using `Get-ItemProperty -Path ..\Help`.</span></span>

### <a name="getting-a-single-registry-entry"></a><span data-ttu-id="351c2-118">Tek bir kayıt defteri girişi alınırken</span><span class="sxs-lookup"><span data-stu-id="351c2-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="351c2-119">Bir kayıt defteri anahtarı içinde belirli bir girdi almak istiyorsanız, birkaç olası yaklaşımlardan birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="351c2-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="351c2-120">Bu örnekte değerini bulur **DevicePath** içinde `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span><span class="sxs-lookup"><span data-stu-id="351c2-120">This example finds the value of **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

<span data-ttu-id="351c2-121">Kullanarak `Get-ItemProperty`, kullanın **yolu** anahtarın adını belirtmek için parametre ve **adı** adını belirtmek için parametre **DevicePath** girişi.</span><span class="sxs-lookup"><span data-stu-id="351c2-121">Using `Get-ItemProperty`, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="351c2-122">Bu komut, standart Windows PowerShell özellikleri döndürür. yanı sıra **DevicePath** özelliği.</span><span class="sxs-lookup"><span data-stu-id="351c2-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="351c2-123">Ancak `Get-ItemProperty` sahip **filtre**, **Ekle**, ve **hariç** parametreleri, özellik adına göre filtre uygulamak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="351c2-123">Although `Get-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="351c2-124">Bu parametreleri öğe yolları ve kayıt defteri girişleri kayıt defteri anahtarları için bakın.</span><span class="sxs-lookup"><span data-stu-id="351c2-124">These parameters refer to registry keys, which are item paths and not registry entries.</span></span> <span data-ttu-id="351c2-125">Öğe özellikleri olan kayıt defteri girdileri.</span><span class="sxs-lookup"><span data-stu-id="351c2-125">Registry entries which are item properties.</span></span>

<span data-ttu-id="351c2-126">Başka bir seçenek Reg.exe komut satırı aracını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="351c2-126">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="351c2-127">Reg.exe ile daha fazla yardım için şunu yazın `reg.exe /?` bir komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="351c2-127">For help with reg.exe, type `reg.exe /?` at a command prompt.</span></span> <span data-ttu-id="351c2-128">Reg.exe DevicePath giriş bulmak için aşağıdaki komutta gösterildiği gibi kullanın:</span><span class="sxs-lookup"><span data-stu-id="351c2-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="351c2-129">Ayrıca **WshShell** bu yöntem, büyük ikili veri gibi karakterler kayıt defteri girişi adları ile veya çalışmıyor olsa da, bazı kayıt defteri girdilerini bulmak için de COM nesnesi "\\").</span><span class="sxs-lookup"><span data-stu-id="351c2-129">You can also use the **WshShell** COM object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="351c2-130">Öğe yolu ile özellik adının sonuna bir \\ ayırıcı:</span><span class="sxs-lookup"><span data-stu-id="351c2-130">Append the property name to the item path with a \\ separator:</span></span>

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

### <a name="setting-a-single-registry-entry"></a><span data-ttu-id="351c2-131">Tek bir kayıt defteri girdisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="351c2-131">Setting a Single Registry Entry</span></span>

<span data-ttu-id="351c2-132">Belirli bir girdi kayıt defteri anahtarında değiştirmek istiyorsanız, birkaç olası yaklaşımlardan birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="351c2-132">If you want to change a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="351c2-133">Bu örnek **yolu** altında girdisi `HKEY_CURRENT_USER\Environment`.</span><span class="sxs-lookup"><span data-stu-id="351c2-133">This example modifies the **Path** entry under `HKEY_CURRENT_USER\Environment`.</span></span> <span data-ttu-id="351c2-134">**Yolu** giriş yürütülebilir dosyaları nerede bulacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="351c2-134">The **Path** entry specifies where to find executable files.</span></span>

1. <span data-ttu-id="351c2-135">Geçerli değerini almak **yolu** girişini kullanarak `Get-ItemProperty`.</span><span class="sxs-lookup"><span data-stu-id="351c2-135">Retrieve the current value of the **Path** entry using `Get-ItemProperty`.</span></span>
2. <span data-ttu-id="351c2-136">İle ayırarak, yeni değer eklemek bir `;`.</span><span class="sxs-lookup"><span data-stu-id="351c2-136">Add the new value, separating it with a `;`.</span></span>
3. <span data-ttu-id="351c2-137">Kullanım `Set-ItemProperty` belirtilen anahtar, giriş adı ve kayıt defteri girişini değiştirmek için değer.</span><span class="sxs-lookup"><span data-stu-id="351c2-137">Use `Set-ItemProperty` with the specified key, entry name, and value to modify the registry entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> <span data-ttu-id="351c2-138">Ancak `Set-ItemProperty` sahip **filtre**, **Ekle**, ve **hariç** parametreleri, özellik adına göre filtre uygulamak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="351c2-138">Although `Set-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="351c2-139">Bu parametreler kayıt defteri anahtarlarını başvuran — öğe yolları olduğu — ve kayıt defteri girdilerini — öğesi özellikleri olan.</span><span class="sxs-lookup"><span data-stu-id="351c2-139">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="351c2-140">Başka bir seçenek Reg.exe komut satırı aracını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="351c2-140">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="351c2-141">Reg.exe ile daha fazla yardım için şunu yazın **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="351c2-141">For help with reg.exe, type **reg.exe /?**</span></span>
<span data-ttu-id="351c2-142">bir komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="351c2-142">at a command prompt.</span></span>

<span data-ttu-id="351c2-143">Aşağıdaki örnek değişiklikleri **yolu** yukarıdaki örnekte eklenen yolun kaldırarak girişi.</span><span class="sxs-lookup"><span data-stu-id="351c2-143">The following example changes the **Path** entry by removing the path added in the example above.</span></span>
<span data-ttu-id="351c2-144">`Get-ItemProperty` öğesinden döndürülen dizeyi ayrıştırmak zorunda kalmamak için geçerli değerini almak için kullanılır `reg query`.</span><span class="sxs-lookup"><span data-stu-id="351c2-144">`Get-ItemProperty` is still used to retrieve the current value to avoid having to parse the string returned from `reg query`.</span></span> <span data-ttu-id="351c2-145">**SubString** ve **lastIndexOf** eklenen son yolunu almak için kullanılan yöntemleri **yolu** girişi.</span><span class="sxs-lookup"><span data-stu-id="351c2-145">The **SubString** and **LastIndexOf** methods are used to retrieve the last path added to the **Path** entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

### <a name="creating-new-registry-entries"></a><span data-ttu-id="351c2-146">Yeni kayıt defteri girdileri oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="351c2-146">Creating New Registry Entries</span></span>

<span data-ttu-id="351c2-147">"PowerShellPath" adlı yeni bir giriş eklemek için **CurrentVersion** anahtar, kullanım `New-ItemProperty` yoluyla anahtar, giriş adı ve giriş değeri.</span><span class="sxs-lookup"><span data-stu-id="351c2-147">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use `New-ItemProperty` with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="351c2-148">Bu örnekte, biz Windows PowerShell değişkeninin değeri sürer `$PSHome`, Windows PowerShell için yükleme dizini yolunu depolar.</span><span class="sxs-lookup"><span data-stu-id="351c2-148">For this example, we will take the value of the Windows PowerShell variable `$PSHome`, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="351c2-149">Aşağıdaki komutu kullanarak yeni giriş anahtarı ekleyebilirsiniz ve komut ayrıca yeni giriş hakkındaki bilgileri döndürür:</span><span class="sxs-lookup"><span data-stu-id="351c2-149">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="351c2-150">**PropertyType** adı olmalıdır bir **Microsoft.Win32.RegistryValueKind** numaralandırma üyesi aşağıdaki tabloda:</span><span class="sxs-lookup"><span data-stu-id="351c2-150">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="351c2-151">PropertyType değeri</span><span class="sxs-lookup"><span data-stu-id="351c2-151">PropertyType Value</span></span>|<span data-ttu-id="351c2-152">Anlamı</span><span class="sxs-lookup"><span data-stu-id="351c2-152">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="351c2-153">İkili</span><span class="sxs-lookup"><span data-stu-id="351c2-153">Binary</span></span>|<span data-ttu-id="351c2-154">İkili veriler</span><span class="sxs-lookup"><span data-stu-id="351c2-154">Binary data</span></span>|
|<span data-ttu-id="351c2-155">DWord</span><span class="sxs-lookup"><span data-stu-id="351c2-155">DWord</span></span>|<span data-ttu-id="351c2-156">Geçerli bir UInt32 bir sayı</span><span class="sxs-lookup"><span data-stu-id="351c2-156">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="351c2-157">Dizeyi Genişlet</span><span class="sxs-lookup"><span data-stu-id="351c2-157">ExpandString</span></span>|<span data-ttu-id="351c2-158">Dinamik olarak genişletilen ortam değişkenleri içerebilir bir dize</span><span class="sxs-lookup"><span data-stu-id="351c2-158">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="351c2-159">MultiString</span><span class="sxs-lookup"><span data-stu-id="351c2-159">MultiString</span></span>|<span data-ttu-id="351c2-160">Çok satırlı string</span><span class="sxs-lookup"><span data-stu-id="351c2-160">A multiline string</span></span>|
|<span data-ttu-id="351c2-161">Dize</span><span class="sxs-lookup"><span data-stu-id="351c2-161">String</span></span>|<span data-ttu-id="351c2-162">Herhangi bir dize değeri</span><span class="sxs-lookup"><span data-stu-id="351c2-162">Any string value</span></span>|
|<span data-ttu-id="351c2-163">QWord</span><span class="sxs-lookup"><span data-stu-id="351c2-163">QWord</span></span>|<span data-ttu-id="351c2-164">8 bayt ikili veri</span><span class="sxs-lookup"><span data-stu-id="351c2-164">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="351c2-165">Bir dizi değerlerini belirterek, birden fazla konuma bir kayıt defteri girişi ekleyebilirsiniz **yolu** parametresi:</span><span class="sxs-lookup"><span data-stu-id="351c2-165">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="351c2-166">Önceden var olan bir kayıt defteri girdisinin değeri ekleyerek de kılabilirsiniz **zorla** herhangi bir parametre `New-ItemProperty` komutu.</span><span class="sxs-lookup"><span data-stu-id="351c2-166">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any `New-ItemProperty` command.</span></span>

### <a name="renaming-registry-entries"></a><span data-ttu-id="351c2-167">Kayıt defteri girdileri yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="351c2-167">Renaming Registry Entries</span></span>

<span data-ttu-id="351c2-168">Yeniden adlandırmak için **PowerShellPath** "PSHome," kullanım girişe `Rename-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="351c2-168">To rename the **PowerShellPath** entry to "PSHome," use `Rename-ItemProperty`:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="351c2-169">Yeniden adlandırılan değerini görüntülemek için Ekle **PassThru** komut parametresi.</span><span class="sxs-lookup"><span data-stu-id="351c2-169">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a><span data-ttu-id="351c2-170">Kayıt defteri girdileri silme</span><span class="sxs-lookup"><span data-stu-id="351c2-170">Deleting Registry Entries</span></span>

<span data-ttu-id="351c2-171">PSHome ve PowerShellPath kayıt defteri girdileri silmek için kullanın `Remove-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="351c2-171">To delete both the PSHome and PowerShellPath registry entries, use `Remove-ItemProperty`:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
