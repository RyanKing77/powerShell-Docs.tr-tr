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
# <a name="the-isefile-object"></a>ISEFile nesnesi
  Bir **ISEFile** nesnesi, bir dosya olarak Windows PowerShell® Tümleşik komut dosyası ortamı (ISE) temsil eder. Microsoft.PowerShell.Host.ISE.ISEFile sınıfının bir örneğidir. Bu konu, üye yöntemleri ve üye özellikleri listeler. **$PsISE.CurrentFile** ve bir PowerShell sekmede dosyaları koleksiyonundaki dosyalar Microsoft.PowerShell.Host.ISE.ISEFile sınıfın tüm örnekleri.

## <a name="methods"></a>Yöntemler

### <a name="save-saveencoding-"></a>Kaydet\( \[saveEncoding\]\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Dosyayı diske kaydeder.

 **\[saveEncoding\]**  - isteğe bağlı [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) isteğe bağlı bir karakter parametresi kaydedilen dosya için kullanılacak kodlama. Varsayılan değer **UTF8**.

 **Özel durumlar**
 -   **System.IO.ıoexception**: dosya kaydedilemedi.

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

### <a name="saveasfilename-saveencoding"></a>Farklı Kaydet\(filename, \[saveEncoding\]\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Dosyayı belirtilen dosya adıyla kaydeder ve kodlama.

 **Dosya adı** -adlı dosyayı kaydetmek için kullanılacak dize.

 **\[saveEncoding\]**  - isteğe bağlı [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) isteğe bağlı bir karakter parametresi kaydedilen dosya için kullanılacak kodlama. Varsayılan değer **UTF8**.

 **Özel durumlar**
 -   **System.ArgumentNullException**: **filename** parametresi null.

- **System.ArgumentException**: **filename** parametre boş.

- **System.IO.ıoexception**: dosya kaydedilemedi.

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a>Özellikler

### <a name="displayname"></a>Görünen Ad
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

 Bu dosya görünen adını içeren dize alır salt okunur özellik. Adı gösterilir **dosya** Düzenleyicisi üstündeki sekmesi. Bir yıldız işareti varlığını \( \* \) dosyasına kaydedilmemiş değişiklikler var. adının sonuna gösterir.

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

### <a name="editor"></a>Düzenleyicisi
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Alır salt okunur özellik [editor nesnesi](The-ISEEditor-Object.md) için belirtilen dosya kullanılır.

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

### <a name="encoding"></a>Kodlama
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Özgün dosya kodlamasını alır salt okunur özellik. Bu bir **System.Text.Encoding** nesnesi.

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

### <a name="fullpath"></a>FullPath
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Dizeyi alır salt okunur özellik açılan dosyasının tam yolunu belirtir.

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

### <a name="issaved"></a>Kaydedilirken
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Döndüren özelliği salt okunur Boolean **$true** en son değiştirildiği sonra dosya kaydedilmişse.

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

### <a name="isuntitled"></a>IsUntitled
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Döndüren salt okunur özelliği **$true** dosya hiçbir zaman bir başlık verildiyse.

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a>Ayrıca bkz:
- [ISEFileCollectionObject](The-ISEFileCollection-Object.md) 
- [Windows PowerShell ISE nesne modeli komut dosyası oluşturma](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE nesne modeli başvurusu](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [ISE nesne modeli hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)
