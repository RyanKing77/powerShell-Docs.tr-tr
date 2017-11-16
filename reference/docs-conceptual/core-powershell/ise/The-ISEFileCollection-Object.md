---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: ISEFileCollection nesnesi
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: 60bf4dae33f3a71c31e7fdbed0f4fd6ab27a8bd1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefilecollection-object"></a>ISEFileCollection nesnesi
  **ISEFileCollection** nesnesidir koleksiyonu **ISEFile** nesneleri. Örnek $psISE.CurrentPowerShellTab.Files koleksiyonudur.

## <a name="methods"></a>Yöntemler

### <a name="add-fullpath-"></a>Ekleme\( \[fullPath\]\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Oluşturur ve yeni bir adsız dosyası döndürür ve koleksiyona ekler. **IsUntitled** yeni oluşturulan dosya özelliğidir **$true**.

 **\[fullPath\]**  - isteğe bağlı dosyasının tam olarak belirtilen yol dizesi. Dahil ederseniz bir özel durum oluşturdu **fullPath** parametre ve göreli bir yol veya dosya adı yerine tam yolu kullanın.

```
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")

```

### <a name="remove-file-force-"></a>Kaldırma\( dosyası \[zorla\]\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Belirtilen dosya geçerli PowerShell sekmesinden kaldırır.

 **Dosya** -koleksiyondan kaldırmak istediğiniz dize ISEFile dosya. Dosyası kaydettiyseniz değil, bu yöntem bir özel durum oluşturur. Kullanım **zorla** anahtar parametresinin kaydedilmemiş dosya kaldırılmasını zorla.

 **\[Zorla\]**  -isteğe bağlı Boole ayarlayın **$true**, dosyayı son kullanıldıktan sonra kaydedilmedi olsa bile kaldırmak için izin verir. Varsayılan değer **$false**.

```
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a>SetSelectedFile\( selectedFile\)
  Windows PowerShell ISE 2.0 ve sonrasında desteklenir. 

 Tarafından belirtilen dosya seçer **selectedFile** parametresi.

 **selectedFile** -seçmek istediğiniz Microsoft.PowerShell.Host.ISE.ISEFile ISEFile dosya.

```

# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)

```

## <a name="see-also"></a>Ayrıca bkz:
- [ISEFile nesnesi](The-ISEFile-Object.md) 
- [Windows PowerShell ISE nesne modeli komut dosyası oluşturma](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE nesne modeli başvurusu](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [ISE nesne modeli hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)
