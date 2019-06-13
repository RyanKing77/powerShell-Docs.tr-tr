---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISEFileCollection Nesnesi
ms.openlocfilehash: 96db51ee921cc0fa34803091d563bc6e118643b6
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030525"
---
# <a name="the-isefilecollection-object"></a>ISEFileCollection Nesnesi

**Isefilecollection** nesnedir koleksiyonu **Isefile** nesneleri. Bir örnek $psISE.CurrentPowerShellTab.Files koleksiyonudur.

## <a name="methods"></a>Yöntemler

### <a name="add-fullpath-"></a>Ekleme\( \[fullPath\] \)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Oluşturur ve yeni bir adsız dosya döndürür ve onu koleksiyona ekler. **IsUntitled** özelliği yeni oluşturulan dosyanın **$true**.

**\[fullPath\]**  : isteğe bağlı dize dosyasının tam yolu. Eklerseniz, bir özel durum üretilir **fullPath** parametresi ve göreli bir yol veya bir dosya adı yerine tam yolu kullanın.

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a>Kaldırma\( dosyası \[zorla\] \)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Belirtilen dosya geçerli PowerShell sekmesinden kaldırır.

**Dosya** -koleksiyondan kaldırmak istediğiniz dize Isefile dosya. Bu yöntem, dosyanın kaydedilmedi, özel durum oluşturur. Kullanım **zorla** kaydedilmemiş bir dosyada kaldırılmasını zorlamak için parametre geçin.

**\[Zorla\]**  -isteğe bağlı Boolean ayarlayın **$true**, dosyayı son kullanımdan sonra kaydedilmemiş olsa bile kaldırmak için izin verir. Varsayılan değer **$false**.

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a>SetSelectedFile\( selectedFile \)

Windows PowerShell ISE 2.0 ve sonraki sürümlerde desteklenir.

Tarafından belirtilen dosya seçer **selectedFile** parametresi.

**selectedFile** -seçmek istediğiniz Microsoft.PowerShell.Host.ISE.ISEFile Isefile dosya.

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a>Ayrıca bkz:

- [Isefile nesnesi](The-ISEFile-Object.md)
- [Windows PowerShell ISE betik oluşturma nesne modelinin amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)
