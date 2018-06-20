---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISEFile Nesnesi
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 276e8f04a827e18999b5b3ecb08f47de4f4b23b1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951401"
---
# <a name="the-isefile-object"></a><span data-ttu-id="e98a4-103">ISEFile Nesnesi</span><span class="sxs-lookup"><span data-stu-id="e98a4-103">The ISEFile Object</span></span>

<span data-ttu-id="e98a4-104">Bir **ISEFile** nesnesi, bir dosya olarak Windows PowerShell® Tümleşik komut dosyası ortamı (ISE) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e98a4-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="e98a4-105">Microsoft.PowerShell.Host.ISE.ISEFile sınıfının bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="e98a4-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="e98a4-106">Bu konu, üye yöntemleri ve üye özellikleri listeler.</span><span class="sxs-lookup"><span data-stu-id="e98a4-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="e98a4-107">**$PsISE.CurrentFile** ve bir PowerShell sekmede dosyaları koleksiyonundaki dosyalar Microsoft.PowerShell.Host.ISE.ISEFile sınıfın tüm örnekleri.</span><span class="sxs-lookup"><span data-stu-id="e98a4-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="e98a4-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e98a4-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="e98a4-109">Kaydet\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="e98a4-109">Save\( \[saveEncoding\] \)</span></span>

<span data-ttu-id="e98a4-110">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e98a4-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e98a4-111">Dosyayı diske kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e98a4-111">Saves the file to disk.</span></span>

<span data-ttu-id="e98a4-112">**\[saveEncoding\]**  - isteğe bağlı [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) isteğe bağlı bir karakter parametresi kaydedilen dosya için kullanılacak kodlama.</span><span class="sxs-lookup"><span data-stu-id="e98a4-112">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="e98a4-113">Varsayılan değer **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="e98a4-113">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="e98a4-114">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="e98a4-114">Exceptions</span></span>

- <span data-ttu-id="e98a4-115">**System.IO.ıoexception**: dosya kaydedilemedi.</span><span class="sxs-lookup"><span data-stu-id="e98a4-115">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="e98a4-116">Farklı Kaydet\(filename, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="e98a4-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>

<span data-ttu-id="e98a4-117">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e98a4-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e98a4-118">Dosyayı belirtilen dosya adıyla kaydeder ve kodlama.</span><span class="sxs-lookup"><span data-stu-id="e98a4-118">Saves the file with the specified file name and encoding.</span></span>

<span data-ttu-id="e98a4-119">**Dosya adı** -adlı dosyayı kaydetmek için kullanılacak dize.</span><span class="sxs-lookup"><span data-stu-id="e98a4-119">**filename** - String The name to be used to save the file.</span></span>

<span data-ttu-id="e98a4-120">**\[saveEncoding\]**  - isteğe bağlı [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) isteğe bağlı bir karakter parametresi kaydedilen dosya için kullanılacak kodlama.</span><span class="sxs-lookup"><span data-stu-id="e98a4-120">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="e98a4-121">Varsayılan değer **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="e98a4-121">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="e98a4-122">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="e98a4-122">Exceptions</span></span>

- <span data-ttu-id="e98a4-123">**System.ArgumentNullException**: **filename** parametresi null.</span><span class="sxs-lookup"><span data-stu-id="e98a4-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>
- <span data-ttu-id="e98a4-124">**System.ArgumentException**: **filename** parametre boş.</span><span class="sxs-lookup"><span data-stu-id="e98a4-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>
- <span data-ttu-id="e98a4-125">**System.IO.ıoexception**: dosya kaydedilemedi.</span><span class="sxs-lookup"><span data-stu-id="e98a4-125">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a><span data-ttu-id="e98a4-126">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e98a4-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="e98a4-127">Görünen Ad</span><span class="sxs-lookup"><span data-stu-id="e98a4-127">DisplayName</span></span>

<span data-ttu-id="e98a4-128">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e98a4-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e98a4-129">Bu dosya görünen adını içeren dize alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="e98a4-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="e98a4-130">Adı gösterilir **dosya** Düzenleyicisi üstündeki sekmesi.</span><span class="sxs-lookup"><span data-stu-id="e98a4-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="e98a4-131">Bir yıldız işareti varlığını \( \* \) dosyasına kaydedilmemiş değişiklikler var. adının sonuna gösterir.</span><span class="sxs-lookup"><span data-stu-id="e98a4-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a><span data-ttu-id="e98a4-132">Düzenleyicisi</span><span class="sxs-lookup"><span data-stu-id="e98a4-132">Editor</span></span>

<span data-ttu-id="e98a4-133">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e98a4-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e98a4-134">Alır salt okunur özellik [editor nesnesi](The-ISEEditor-Object.md) için belirtilen dosya kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e98a4-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a><span data-ttu-id="e98a4-135">Kodlama</span><span class="sxs-lookup"><span data-stu-id="e98a4-135">Encoding</span></span>

<span data-ttu-id="e98a4-136">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e98a4-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e98a4-137">Özgün dosya kodlamasını alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="e98a4-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="e98a4-138">Bu bir **System.Text.Encoding** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e98a4-138">This is a **System.Text.Encoding** object.</span></span>

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a><span data-ttu-id="e98a4-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="e98a4-139">FullPath</span></span>

<span data-ttu-id="e98a4-140">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e98a4-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e98a4-141">Dizeyi alır salt okunur özellik açılan dosyasının tam yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e98a4-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a><span data-ttu-id="e98a4-142">Kaydedilirken</span><span class="sxs-lookup"><span data-stu-id="e98a4-142">IsSaved</span></span>

<span data-ttu-id="e98a4-143">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e98a4-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e98a4-144">Döndüren özelliği salt okunur Boolean **$true** en son değiştirildiği sonra dosya kaydedilmişse.</span><span class="sxs-lookup"><span data-stu-id="e98a4-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a><span data-ttu-id="e98a4-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="e98a4-145">IsUntitled</span></span>

<span data-ttu-id="e98a4-146">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e98a4-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e98a4-147">Döndüren salt okunur özelliği **$true** dosya hiçbir zaman bir başlık verildiyse.</span><span class="sxs-lookup"><span data-stu-id="e98a4-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a><span data-ttu-id="e98a4-148">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e98a4-148">See Also</span></span>

- [<span data-ttu-id="e98a4-149">The ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="e98a4-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md)
- [<span data-ttu-id="e98a4-150">Nesne modeli komut dosyası Windows PowerShell ISE amacı</span><span class="sxs-lookup"><span data-stu-id="e98a4-150">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="e98a4-151">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="e98a4-151">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)