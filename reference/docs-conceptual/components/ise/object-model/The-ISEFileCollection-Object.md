---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISEFileCollection Nesnesi
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: eb4b2784820cbe51f662fd2fd945d8760ef9dbff
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53406035"
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="9e67e-103">ISEFileCollection Nesnesi</span><span class="sxs-lookup"><span data-stu-id="9e67e-103">The ISEFileCollection Object</span></span>

<span data-ttu-id="9e67e-104">**Isefilecollection** nesnedir koleksiyonu **Isefile** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9e67e-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="9e67e-105">Bir örnek $psISE.CurrentPowerShellTab.Files koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="9e67e-105">An example is the $psISE.CurrentPowerShellTab.Files collection.</span></span>

## <a name="methods"></a><span data-ttu-id="9e67e-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9e67e-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="9e67e-107">Ekleme\( \[fullPath\] \)</span><span class="sxs-lookup"><span data-stu-id="9e67e-107">Add\( \[fullPath\] \)</span></span>

<span data-ttu-id="9e67e-108">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9e67e-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="9e67e-109">Oluşturur ve yeni bir adsız dosya döndürür ve onu koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="9e67e-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="9e67e-110">**IsUntitled** özelliği yeni oluşturulan dosyanın **$true**.</span><span class="sxs-lookup"><span data-stu-id="9e67e-110">The **IsUntitled** property of the newly created file is **$true**.</span></span>

<span data-ttu-id="9e67e-111">**\[fullPath\]**  : isteğe bağlı dize dosyasının tam yolu.</span><span class="sxs-lookup"><span data-stu-id="9e67e-111">**\[fullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="9e67e-112">Eklerseniz, bir özel durum üretilir **fullPath** parametresi ve göreli bir yol veya bir dosya adı yerine tam yolu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e67e-112">An exception is generated if you include the **fullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a><span data-ttu-id="9e67e-113">Kaldırma\( dosyası \[zorla\] \)</span><span class="sxs-lookup"><span data-stu-id="9e67e-113">Remove\( File, \[Force\] \)</span></span>

<span data-ttu-id="9e67e-114">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9e67e-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="9e67e-115">Belirtilen dosya geçerli PowerShell sekmesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9e67e-115">Removes a specified file from the current PowerShell tab.</span></span>

<span data-ttu-id="9e67e-116">**Dosya** -koleksiyondan kaldırmak istediğiniz dize Isefile dosya.</span><span class="sxs-lookup"><span data-stu-id="9e67e-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="9e67e-117">Bu yöntem, dosyanın kaydedilmedi, özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e67e-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="9e67e-118">Kullanım **zorla** kaydedilmemiş bir dosyada kaldırılmasını zorlamak için parametre geçin.</span><span class="sxs-lookup"><span data-stu-id="9e67e-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

<span data-ttu-id="9e67e-119">**\[Zorla\]**  -isteğe bağlı Boolean ayarlayın **$true**, dosyayı son kullanımdan sonra kaydedilmemiş olsa bile kaldırmak için izin verir.</span><span class="sxs-lookup"><span data-stu-id="9e67e-119">**\[Force\]** - optional Boolean If set to **$true**, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="9e67e-120">Varsayılan değer **$false**.</span><span class="sxs-lookup"><span data-stu-id="9e67e-120">The default is **$false**.</span></span>

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="9e67e-121">SetSelectedFile\( selectedFile \)</span><span class="sxs-lookup"><span data-stu-id="9e67e-121">SetSelectedFile\( selectedFile \)</span></span>

<span data-ttu-id="9e67e-122">Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9e67e-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="9e67e-123">Tarafından belirtilen dosya seçer **selectedFile** parametresi.</span><span class="sxs-lookup"><span data-stu-id="9e67e-123">Selects the file that is specified by the **selectedFile** parameter.</span></span>

<span data-ttu-id="9e67e-124">**selectedFile** -seçmek istediğiniz Microsoft.PowerShell.Host.ISE.ISEFile Isefile dosya.</span><span class="sxs-lookup"><span data-stu-id="9e67e-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a><span data-ttu-id="9e67e-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="9e67e-125">See Also</span></span>

- [<span data-ttu-id="9e67e-126">Isefile nesnesi</span><span class="sxs-lookup"><span data-stu-id="9e67e-126">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="9e67e-127">Windows PowerShell ISE betik oluşturma nesne modelinin amacı</span><span class="sxs-lookup"><span data-stu-id="9e67e-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="9e67e-128">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="9e67e-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)