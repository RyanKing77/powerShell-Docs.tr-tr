---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISEFileCollection Nesnesi
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: eb4b2784820cbe51f662fd2fd945d8760ef9dbff
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953098"
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="52ab6-103">ISEFileCollection Nesnesi</span><span class="sxs-lookup"><span data-stu-id="52ab6-103">The ISEFileCollection Object</span></span>

<span data-ttu-id="52ab6-104">**ISEFileCollection** nesnesidir koleksiyonu **ISEFile** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="52ab6-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="52ab6-105">Örnek $psISE.CurrentPowerShellTab.Files koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="52ab6-105">An example is the $psISE.CurrentPowerShellTab.Files collection.</span></span>

## <a name="methods"></a><span data-ttu-id="52ab6-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="52ab6-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="52ab6-107">Ekleme\( \[fullPath\] \)</span><span class="sxs-lookup"><span data-stu-id="52ab6-107">Add\( \[fullPath\] \)</span></span>

<span data-ttu-id="52ab6-108">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="52ab6-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="52ab6-109">Oluşturur ve yeni bir adsız dosyası döndürür ve koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="52ab6-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="52ab6-110">**IsUntitled** yeni oluşturulan dosya özelliğidir **$true**.</span><span class="sxs-lookup"><span data-stu-id="52ab6-110">The **IsUntitled** property of the newly created file is **$true**.</span></span>

<span data-ttu-id="52ab6-111">**\[fullPath\]**  - isteğe bağlı dosyasının tam olarak belirtilen yol dizesi.</span><span class="sxs-lookup"><span data-stu-id="52ab6-111">**\[fullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="52ab6-112">Dahil ederseniz bir özel durum oluşturdu **fullPath** parametre ve göreli bir yol veya dosya adı yerine tam yolu kullanın.</span><span class="sxs-lookup"><span data-stu-id="52ab6-112">An exception is generated if you include the **fullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a><span data-ttu-id="52ab6-113">Kaldırma\( dosyası \[zorla\] \)</span><span class="sxs-lookup"><span data-stu-id="52ab6-113">Remove\( File, \[Force\] \)</span></span>

<span data-ttu-id="52ab6-114">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="52ab6-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="52ab6-115">Belirtilen dosya geçerli PowerShell sekmesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="52ab6-115">Removes a specified file from the current PowerShell tab.</span></span>

<span data-ttu-id="52ab6-116">**Dosya** -koleksiyondan kaldırmak istediğiniz dize ISEFile dosya.</span><span class="sxs-lookup"><span data-stu-id="52ab6-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="52ab6-117">Dosyası kaydettiyseniz değil, bu yöntem bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="52ab6-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="52ab6-118">Kullanım **zorla** anahtar parametresinin kaydedilmemiş dosya kaldırılmasını zorla.</span><span class="sxs-lookup"><span data-stu-id="52ab6-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

<span data-ttu-id="52ab6-119">**\[Zorla\]**  -isteğe bağlı Boole ayarlayın **$true**, dosyayı son kullanıldıktan sonra kaydedilmedi olsa bile kaldırmak için izin verir.</span><span class="sxs-lookup"><span data-stu-id="52ab6-119">**\[Force\]** - optional Boolean If set to **$true**, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="52ab6-120">Varsayılan değer **$false**.</span><span class="sxs-lookup"><span data-stu-id="52ab6-120">The default is **$false**.</span></span>

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="52ab6-121">SetSelectedFile\( selectedFile \)</span><span class="sxs-lookup"><span data-stu-id="52ab6-121">SetSelectedFile\( selectedFile \)</span></span>

<span data-ttu-id="52ab6-122">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="52ab6-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="52ab6-123">Tarafından belirtilen dosya seçer **selectedFile** parametresi.</span><span class="sxs-lookup"><span data-stu-id="52ab6-123">Selects the file that is specified by the **selectedFile** parameter.</span></span>

<span data-ttu-id="52ab6-124">**selectedFile** -seçmek istediğiniz Microsoft.PowerShell.Host.ISE.ISEFile ISEFile dosya.</span><span class="sxs-lookup"><span data-stu-id="52ab6-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a><span data-ttu-id="52ab6-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="52ab6-125">See Also</span></span>

- [<span data-ttu-id="52ab6-126">The ISEFile Object</span><span class="sxs-lookup"><span data-stu-id="52ab6-126">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="52ab6-127">Nesne modeli komut dosyası Windows PowerShell ISE amacı</span><span class="sxs-lookup"><span data-stu-id="52ab6-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="52ab6-128">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="52ab6-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)