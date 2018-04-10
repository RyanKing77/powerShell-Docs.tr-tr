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
---
# <a name="the-isefile-object"></a>ISEFile Nesnesi

Bir **ISEFile** nesnesi, bir dosya olarak Windows PowerShell® Tümleşik komut dosyası ortamı (ISE) temsil eder. Microsoft.PowerShell.Host.ISE.ISEFile sınıfının bir örneğidir. Bu konu, üye yöntemleri ve üye özellikleri listeler. **$PsISE.CurrentFile** ve bir PowerShell sekmede dosyaları koleksiyonundaki dosyalar Microsoft.PowerShell.Host.ISE.ISEFile sınıfın tüm örnekleri.

## <a name="methods"></a>Yöntemler

### <a name="save-saveencoding-"></a>Kaydet\( \[saveEncoding\] \)

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Dosyayı diske kaydeder.

**\[saveEncoding\]**  - isteğe bağlı [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) isteğe bağlı bir karakter parametresi kaydedilen dosya için kullanılacak kodlama. Varsayılan değer **UTF8**.

### <a name="exceptions"></a>Özel Durumlar

- **System.IO.ıoexception**: dosya kaydedilemedi.

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a>Farklı Kaydet\(filename, \[saveEncoding\]\)

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Dosyayı belirtilen dosya adıyla kaydeder ve kodlama.

**Dosya adı** -adlı dosyayı kaydetmek için kullanılacak dize.

**\[saveEncoding\]**  - isteğe bağlı [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) isteğe bağlı bir karakter parametresi kaydedilen dosya için kullanılacak kodlama. Varsayılan değer **UTF8**.

### <a name="exceptions"></a>Özel Durumlar

- **System.ArgumentNullException**: **filename** parametresi null.
- **System.ArgumentException**: **filename** parametre boş.
- **System.IO.ıoexception**: dosya kaydedilemedi.

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a>Özellikler

### <a name="displayname"></a>Görünen Ad

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Bu dosya görünen adını içeren dize alır salt okunur özellik. Adı gösterilir **dosya** Düzenleyicisi üstündeki sekmesi. Bir yıldız işareti varlığını \( \* \) dosyasına kaydedilmemiş değişiklikler var. adının sonuna gösterir.

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a>Düzenleyicisi

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Alır salt okunur özellik [editor nesnesi](The-ISEEditor-Object.md) için belirtilen dosya kullanılır.

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a>Kodlama

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Özgün dosya kodlamasını alır salt okunur özellik. Bu bir **System.Text.Encoding** nesnesi.

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a>FullPath

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Dizeyi alır salt okunur özellik açılan dosyasının tam yolunu belirtir.

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a>Kaydedilirken

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Döndüren özelliği salt okunur Boolean **$true** en son değiştirildiği sonra dosya kaydedilmişse.

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a>IsUntitled

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Döndüren salt okunur özelliği **$true** dosya hiçbir zaman bir başlık verildiyse.

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a>Ayrıca bkz:

- [The ISEFileCollectionObject](The-ISEFileCollection-Object.md)
- [Nesne modeli komut dosyası Windows PowerShell ISE amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)