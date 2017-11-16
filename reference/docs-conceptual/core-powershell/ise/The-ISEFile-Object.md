---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: ISEFile nesnesi
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: a1fbd48e872684cc578adb03f52430eabdc54c2c
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefile-object"></a><span data-ttu-id="fa9c5-103">ISEFile nesnesi</span><span class="sxs-lookup"><span data-stu-id="fa9c5-103">The ISEFile Object</span></span>
  <span data-ttu-id="fa9c5-104">Bir **ISEFile** nesnesi, bir dosya olarak Windows PowerShell® Tümleşik komut dosyası ortamı (ISE) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="fa9c5-105">Microsoft.PowerShell.Host.ISE.ISEFile sınıfının bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="fa9c5-106">Bu konu, üye yöntemleri ve üye özellikleri listeler.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="fa9c5-107">**$PsISE.CurrentFile** ve bir PowerShell sekmede dosyaları koleksiyonundaki dosyalar Microsoft.PowerShell.Host.ISE.ISEFile sınıfın tüm örnekleri.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="fa9c5-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fa9c5-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="fa9c5-109">Kaydet\( \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="fa9c5-109">Save\( \[saveEncoding\] \)</span></span>
  <span data-ttu-id="fa9c5-110">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="fa9c5-111">Dosyayı diske kaydeder.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-111">Saves the file to disk.</span></span>

 <span data-ttu-id="fa9c5-112">**\[saveEncoding\]**  - isteğe bağlı [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) isteğe bağlı bir karakter parametresi kaydedilen dosya için kullanılacak kodlama.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-112">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="fa9c5-113">Varsayılan değer **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-113">The default value is **UTF8**.</span></span>

 <span data-ttu-id="fa9c5-114">**Özel durumlar**</span><span class="sxs-lookup"><span data-stu-id="fa9c5-114">**Exceptions**</span></span>
 -   <span data-ttu-id="fa9c5-115">**System.IO.ıoexception**: dosya kaydedilemedi.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-115">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="fa9c5-116">Farklı Kaydet\(filename, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="fa9c5-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>
  <span data-ttu-id="fa9c5-117">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="fa9c5-118">Dosyayı belirtilen dosya adıyla kaydeder ve kodlama.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-118">Saves the file with the specified file name and encoding.</span></span>

 <span data-ttu-id="fa9c5-119">**Dosya adı** -adlı dosyayı kaydetmek için kullanılacak dize.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-119">**filename** - String The name to be used to save the file.</span></span>

 <span data-ttu-id="fa9c5-120">**\[saveEncoding\]**  - isteğe bağlı [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) isteğe bağlı bir karakter parametresi kaydedilen dosya için kullanılacak kodlama.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-120">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="fa9c5-121">Varsayılan değer **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-121">The default value is **UTF8**.</span></span>

 <span data-ttu-id="fa9c5-122">**Özel durumlar**</span><span class="sxs-lookup"><span data-stu-id="fa9c5-122">**Exceptions**</span></span>
 -   <span data-ttu-id="fa9c5-123">**System.ArgumentNullException**: **filename** parametresi null.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>

- <span data-ttu-id="fa9c5-124">**System.ArgumentException**: **filename** parametre boş.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>

- <span data-ttu-id="fa9c5-125">**System.IO.ıoexception**: dosya kaydedilemedi.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-125">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a><span data-ttu-id="fa9c5-126">Özellikler</span><span class="sxs-lookup"><span data-stu-id="fa9c5-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="fa9c5-127">Görünen Ad</span><span class="sxs-lookup"><span data-stu-id="fa9c5-127">DisplayName</span></span>
  <span data-ttu-id="fa9c5-128">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="fa9c5-129">Bu dosya görünen adını içeren dize alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="fa9c5-130">Adı gösterilir **dosya** Düzenleyicisi üstündeki sekmesi.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="fa9c5-131">Bir yıldız işareti varlığını \( \* \) dosyasına kaydedilmemiş değişiklikler var. adının sonuna gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

### <a name="editor"></a><span data-ttu-id="fa9c5-132">Düzenleyicisi</span><span class="sxs-lookup"><span data-stu-id="fa9c5-132">Editor</span></span>
  <span data-ttu-id="fa9c5-133">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="fa9c5-134">Alır salt okunur özellik [editor nesnesi](The-ISEEditor-Object.md) için belirtilen dosya kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

### <a name="encoding"></a><span data-ttu-id="fa9c5-135">Kodlama</span><span class="sxs-lookup"><span data-stu-id="fa9c5-135">Encoding</span></span>
  <span data-ttu-id="fa9c5-136">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="fa9c5-137">Özgün dosya kodlamasını alır salt okunur özellik.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="fa9c5-138">Bu bir **System.Text.Encoding** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-138">This is a **System.Text.Encoding** object.</span></span>

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

### <a name="fullpath"></a><span data-ttu-id="fa9c5-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="fa9c5-139">FullPath</span></span>
  <span data-ttu-id="fa9c5-140">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="fa9c5-141">Dizeyi alır salt okunur özellik açılan dosyasının tam yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

### <a name="issaved"></a><span data-ttu-id="fa9c5-142">Kaydedilirken</span><span class="sxs-lookup"><span data-stu-id="fa9c5-142">IsSaved</span></span>
  <span data-ttu-id="fa9c5-143">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="fa9c5-144">Döndüren özelliği salt okunur Boolean **$true** en son değiştirildiği sonra dosya kaydedilmişse.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

### <a name="isuntitled"></a><span data-ttu-id="fa9c5-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="fa9c5-145">IsUntitled</span></span>
  <span data-ttu-id="fa9c5-146">Windows PowerShell ISE 2.0 ve sonrasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="fa9c5-147">Döndüren salt okunur özelliği **$true** dosya hiçbir zaman bir başlık verildiyse.</span><span class="sxs-lookup"><span data-stu-id="fa9c5-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a><span data-ttu-id="fa9c5-148">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="fa9c5-148">See Also</span></span>
- [<span data-ttu-id="fa9c5-149">ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="fa9c5-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md) 
- [<span data-ttu-id="fa9c5-150">Windows PowerShell ISE nesne modeli komut dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa9c5-150">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="fa9c5-151">Windows PowerShell ISE nesne modeli başvurusu</span><span class="sxs-lookup"><span data-stu-id="fa9c5-151">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="fa9c5-152">ISE nesne modeli hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="fa9c5-152">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
