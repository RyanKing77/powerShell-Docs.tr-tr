---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Kayıt Defteri Anahtarları ile Çalışma
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: a9d08f2f6b5803980dec45a4e266ad66879c8c8d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="578ee-103">Kayıt Defteri Anahtarları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="578ee-103">Working with Registry Keys</span></span>

<span data-ttu-id="578ee-104">Kayıt defteri anahtarları öğeler Windows PowerShell sürücülerde olduğundan, bunlarla çalışmaya dosyalar ve klasörlerle çalışmaya çok benzer.</span><span class="sxs-lookup"><span data-stu-id="578ee-104">Because registry keys are items on Windows PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="578ee-105">Bir kritik fark her öğe bir kayıt defteri tabanlı Windows PowerShell sürücüsünde bir dosya sistemi sürücüsündeki bir klasörde bulunan gibi bir kapsayıcı olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="578ee-105">One critical difference is that every item on a registry-based Windows PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="578ee-106">Ancak, kayıt defteri girdileri ve ilişkili değerleri değil ayrı öğeleri öğeleri özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="578ee-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

### <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="578ee-107">Tüm alt anahtarlarının kayıt defteri anahtarının listeleme</span><span class="sxs-lookup"><span data-stu-id="578ee-107">Listing All Subkeys of a Registry Key</span></span>

<span data-ttu-id="578ee-108">Kullanarak doğrudan bir kayıt defteri anahtarı içinde tüm öğeleri gösterebilir **Get-Childıtem**.</span><span class="sxs-lookup"><span data-stu-id="578ee-108">You can show all items directly within a registry key by using **Get-ChildItem**.</span></span> <span data-ttu-id="578ee-109">İsteğe bağlı eklemek **zorla** görüntüleme gizli veya sistem öğelere parametresi.</span><span class="sxs-lookup"><span data-stu-id="578ee-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="578ee-110">Örneğin, bu komut öğeleri doğrudan Windows PowerShell sürücüsü HKCU görüntüler:, HKEY_CURRENT_USER kayıt defteri kovanı karşılık gelir:</span><span class="sxs-lookup"><span data-stu-id="578ee-110">For example, this command displays the items directly within Windows PowerShell drive HKCU:, which corresponds to the HKEY_CURRENT_USER registry hive:</span></span>

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

<span data-ttu-id="578ee-111">Kayıt Defteri Düzenleyicisi (Regedit.exe) HKEY_CURRENT_USER altında görünür üst düzey anahtarları şunlardır.</span><span class="sxs-lookup"><span data-stu-id="578ee-111">These are the top-level keys visible under HKEY_CURRENT_USER in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="578ee-112">Ardından kayıt defteri sağlayıcının adı belirterek bu kayıt defteri yolu da belirtebilirsiniz "**::**".</span><span class="sxs-lookup"><span data-stu-id="578ee-112">You can also specify this registry path by specifying the registry provider's name, followed by "**::**".</span></span> <span data-ttu-id="578ee-113">Kayıt defteri sağlayıcının tam ad **Microsoft.PowerShell.Core\\kayıt defteri**, ancak bu yalnızca için kısaltılmış **kayıt defteri**.</span><span class="sxs-lookup"><span data-stu-id="578ee-113">The registry provider's full name is **Microsoft.PowerShell.Core\\Registry**, but this can be shortened to just **Registry**.</span></span> <span data-ttu-id="578ee-114">Aşağıdaki komutlardan herhangi birini içeriği doğrudan HKCU altında listelenir:</span><span class="sxs-lookup"><span data-stu-id="578ee-114">Any of the following commands will list the contents directly under HKCU:</span></span>

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="578ee-115">Bu komutları liste Cmd.exe's kullanarak benzer doğrudan içerilen öğelerin yalnızca **DIR** komut veya **ls** UNIX Kabuğu'nda.</span><span class="sxs-lookup"><span data-stu-id="578ee-115">These commands list only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="578ee-116">Kapsanan öğeleri gösterecek şekilde belirtmeniz gerekir **Recurse** parametresi.</span><span class="sxs-lookup"><span data-stu-id="578ee-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="578ee-117">HKCU tüm kayıt defteri anahtarlarında listelemek için (Bu işlem çok uzun bir süre devam edebilir.) aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="578ee-117">To list all registry keys in HKCU, use the following command (This operation can take an extremely long time.):</span></span>

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

<span data-ttu-id="578ee-118">**Get-Childıtem** aracılığıyla karmaşık filtreleme yetenekleri gerçekleştirebilirsiniz kendi **yolu**, **filtre**, **INCLUDE**, ve **hariç**parametreleri, ancak bu parametreler yalnızca adına bağlı genellikle.</span><span class="sxs-lookup"><span data-stu-id="578ee-118">**Get-ChildItem** can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="578ee-119">Karmaşık öğelerinin diğer özellikleri kullanarak göre filtreleme gerçekleştirebilirsiniz **Where-Object** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="578ee-119">You can perform complex filtering based on other properties of items by using the **Where-Object** cmdlet.</span></span> <span data-ttu-id="578ee-120">Tüm anahtarları HKCU içinde aşağıdaki komutu bulur:\\Hayır birden fazla alt anahtar ve ayrıca tam olarak dört değerlere sahip olan yazılım:</span><span class="sxs-lookup"><span data-stu-id="578ee-120">The following command finds all keys within HKCU:\\Software that have no more than one subkey and also have exactly four values:</span></span>

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a><span data-ttu-id="578ee-121">Anahtarları kopyalama</span><span class="sxs-lookup"><span data-stu-id="578ee-121">Copying Keys</span></span>

<span data-ttu-id="578ee-122">Kopyalama ile yapılır **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="578ee-122">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="578ee-123">Aşağıdaki komut kopyalar HKLM:\\yazılım\\Microsoft\\Windows\\CurrentVersion ve tüm özelliklerini HKCU:\\, "CurrentVersion" adlı yeni bir anahtar oluşturma:</span><span class="sxs-lookup"><span data-stu-id="578ee-123">The following command copies HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion and all of its properties to HKCU:\\, creating a new key named "CurrentVersion":</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

<span data-ttu-id="578ee-124">Bu yeni bir anahtar kullanarak veya Kayıt Defteri Düzenleyicisi'nde inceleyin, **Get-Childıtem**, içerdiği alt anahtarlarını kopyalarını yeni konuma sahip olmadığını göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="578ee-124">If you examine this new key in the registry editor or by using **Get-ChildItem**, you will notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="578ee-125">Tüm kapsayıcı içeriğini kopyalamak için belirtmeniz gerekir **Recurse** parametresi.</span><span class="sxs-lookup"><span data-stu-id="578ee-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="578ee-126">Önceki kopyalama komut özyinelemeli yapmak için bu komutu kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="578ee-126">To make the preceding copy command recursive, you would use this command:</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

<span data-ttu-id="578ee-127">Zaten sahip olduğunuz kullanılabilir dosya sistemi kopyaları gerçekleştirmek üzere diğer araçlarını kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="578ee-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="578ee-128">Hiçbir kayıt defteri düzenleme araçları — (wscript.Shell nesnesinin ve WMI'ın StdRegProv sınıfı gibi) kayıt defteri düzenlemesini destekleyecek reg.exe, regini.exe ve regedit.exe—and COM nesneleri dahil olmak üzere kullanılabilir gelen Windows PowerShell içinde.</span><span class="sxs-lookup"><span data-stu-id="578ee-128">Any registry editing tools—including reg.exe, regini.exe, and regedit.exe—and COM objects that support registry editing (such as WScript.Shell and WMI's StdRegProv class) can be used from within Windows PowerShell.</span></span>

### <a name="creating-keys"></a><span data-ttu-id="578ee-129">Anahtarları oluşturma</span><span class="sxs-lookup"><span data-stu-id="578ee-129">Creating Keys</span></span>

<span data-ttu-id="578ee-130">Kayıt defterinde yeni anahtarları oluşturma, bir dosya sisteminde yeni bir öğe oluşturmaktan daha basittir.</span><span class="sxs-lookup"><span data-stu-id="578ee-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="578ee-131">Tüm kayıt defteri anahtarları kapsayıcıları olduğundan, öğe türü belirtmeniz gerekmez; yalnızca açık bir yolu gibi sağladığınız:</span><span class="sxs-lookup"><span data-stu-id="578ee-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

<span data-ttu-id="578ee-132">Sağlayıcı tabanlı bir yolu, bir anahtarı belirtmek üzere de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="578ee-132">You can also use a provider-based path to specify a key:</span></span>

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a><span data-ttu-id="578ee-133">Anahtarları silme</span><span class="sxs-lookup"><span data-stu-id="578ee-133">Deleting Keys</span></span>

<span data-ttu-id="578ee-134">Öğeleri silme temelde tüm sağlayıcılar için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="578ee-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="578ee-135">Aşağıdaki komutları sessizce öğeleri kaldıracak:</span><span class="sxs-lookup"><span data-stu-id="578ee-135">The following commands will silently remove items:</span></span>

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="578ee-136">Belirli bir anahtarın altında tüm anahtarları kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="578ee-136">Removing All Keys Under a Specific Key</span></span>

<span data-ttu-id="578ee-137">İçerilen öğelerin kullanarak kaldırabilirsiniz **Kaldır öğesini**, ancak başka bir şey öğe içeriyorsa, kaldırma işlemini onaylamanız istenir.</span><span class="sxs-lookup"><span data-stu-id="578ee-137">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="578ee-138">Örneğin, HKCU silmeye çalışırsanız:\\CurrentVersion alt anahtarının oluşturduğumuz, biz bunu bakın:</span><span class="sxs-lookup"><span data-stu-id="578ee-138">For example, if we attempt to delete the HKCU:\\CurrentVersion subkey we created, we see this:</span></span>

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="578ee-139">Sormadan içerilen öğelerin silmek için belirtmek **-Recurse** parametre:</span><span class="sxs-lookup"><span data-stu-id="578ee-139">To delete contained items without prompting, specify the **-Recurse** parameter:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="578ee-140">HKCU içindeki tüm öğeleri kaldırmak istiyorsanız:\\CurrentVersion ancak değil HKCU:\\CurrentVersion kendisi, bunun yerine kullanabileceğiniz:</span><span class="sxs-lookup"><span data-stu-id="578ee-140">If you wanted to remove all items within HKCU:\\CurrentVersion but not HKCU:\\CurrentVersion itself, you could instead use:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```