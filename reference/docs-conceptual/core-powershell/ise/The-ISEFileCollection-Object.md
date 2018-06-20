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
# <a name="the-isefilecollection-object"></a>ISEFileCollection Nesnesi

**ISEFileCollection** nesnesidir koleksiyonu **ISEFile** nesneleri. Örnek $psISE.CurrentPowerShellTab.Files koleksiyonudur.

## <a name="methods"></a>Yöntemler

### <a name="add-fullpath-"></a>Ekleme\( \[fullPath\] \)

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Oluşturur ve yeni bir adsız dosyası döndürür ve koleksiyona ekler. **IsUntitled** yeni oluşturulan dosya özelliğidir **$true**.

**\[fullPath\]**  - isteğe bağlı dosyasının tam olarak belirtilen yol dizesi. Dahil ederseniz bir özel durum oluşturdu **fullPath** parametre ve göreli bir yol veya dosya adı yerine tam yolu kullanın.

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a>Kaldırma\( dosyası \[zorla\] \)

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Belirtilen dosya geçerli PowerShell sekmesinden kaldırır.

**Dosya** -koleksiyondan kaldırmak istediğiniz dize ISEFile dosya. Dosyası kaydettiyseniz değil, bu yöntem bir özel durum oluşturur. Kullanım **zorla** anahtar parametresinin kaydedilmemiş dosya kaldırılmasını zorla.

**\[Zorla\]**  -isteğe bağlı Boole ayarlayın **$true**, dosyayı son kullanıldıktan sonra kaydedilmedi olsa bile kaldırmak için izin verir. Varsayılan değer **$false**.

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

Windows PowerShell ISE 2.0 ve sonrasında desteklenir.

Tarafından belirtilen dosya seçer **selectedFile** parametresi.

**selectedFile** -seçmek istediğiniz Microsoft.PowerShell.Host.ISE.ISEFile ISEFile dosya.

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a>Ayrıca bkz:

- [The ISEFile Object](The-ISEFile-Object.md)
- [Nesne modeli komut dosyası Windows PowerShell ISE amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)