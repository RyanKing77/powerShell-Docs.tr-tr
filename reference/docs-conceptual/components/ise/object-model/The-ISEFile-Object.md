---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISEFile Nesnesi
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 24549720b8bc35435882533b0eb138de432ede65
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685140"
---
# <a name="the-isefile-object"></a>ISEFile Nesnesi

Bir **Isefile** nesnesi bir dosya içinde Windows PowerShell® Tümleşik komut dosyası ortamı (ISE) temsil eder. Microsoft.PowerShell.Host.ISE.ISEFile sınıfının bir örneğidir. Bu konu, üye yöntemleri ve üye özellikleri listeler. **$PsISE.CurrentFile** ve bir PowerShell sekmesi dosyaları koleksiyonda dosyalarında Microsoft.PowerShell.Host.ISE.ISEFile sınıfın tüm örnekleri.

## <a name="methods"></a>Yöntemler

### <a name="save-saveencoding-"></a>Kaydet\( \[saveEncoding\] \)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Dosyayı diske kaydeder.

**\[saveEncoding\]**  : isteğe bağlı [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) kaydedilen dosya için kullanılacak parametre kodlama isteğe bağlı bir karakter. Varsayılan değer **UTF8**.

### <a name="exceptions"></a>Özel Durumlar

- **System.IO.ıoexception**: Dosya kaydedilemedi.

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a>Farklı Kaydet\(dosya \[saveEncoding\]\)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Dosyayı belirtilen dosya adı ile kaydeder ve kodlama.

**filename** -adı, dosyayı kaydetmek için kullanılacak dize.

**\[saveEncoding\]**  : isteğe bağlı [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) kaydedilen dosya için kullanılacak parametre kodlama isteğe bağlı bir karakter. Varsayılan değer **UTF8**.

### <a name="exceptions"></a>Özel Durumlar

- **System.ArgumentNullException**: **Filename** parametresi null.
- **System.ArgumentException**: **Filename** parametresi boş.
- **System.IO.ıoexception**: Dosya kaydedilemedi.

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a>Özellikler

### <a name="displayname"></a>Görünen Ad

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Bu dosya görünen adını içeren dize alan salt okunur özelliği. Şirket adı gösterilir **dosya** Düzenleyici üst kısmındaki sekme. Bir yıldız işareti varlığını \( \* \) adın sonunda dosya kaydedilmemiş değişiklikler sahip olduğunu gösterir.

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a>Düzenleyici

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Salt okunur özelliği [Düzenleyici nesnesi](The-ISEEditor-Object.md) belirtilen dosya için kullanılır.

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a>Kodlama

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Özgün dosya kodlamasını alır salt okunur özellik. Bu bir **System.Text.Encoding** nesne.

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a>FullPath

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Dize, salt okunur özelliği açık dosyanın tam yolunu belirtir.

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a>Kaydedilirken

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Döndürür salt okunur Boolean özelliği **$true** dosyanın son değiştirilme zamanı sonra kaydedilmişse.

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a>IsUntitled

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Döndüren salt okunur özelliği **$true** dosya hiçbir zaman bir başlık verilmişse.

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a>Ayrıca bkz:

- [The ISEFileCollectionObject](The-ISEFileCollection-Object.md)
- [Windows PowerShell ISE betik oluşturma nesne modelinin amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)