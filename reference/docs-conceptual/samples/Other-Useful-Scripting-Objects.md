---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Diğer Kullanışlı Betik Oluşturma Nesneleri
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: ff494f375c0d43d83b2a067dbe4f2ab35a90d564
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405681"
---
# <a name="other-useful-scripting-objects"></a>Diğer Kullanışlı Betik Oluşturma Nesneleri

Aşağıdaki nesneler, Windows PowerShell ıse'de betik ek işlevsellik sağlar. Olmadıkları parçası **$psISE** hiyerarşisi.

## <a name="useful-scripting-objects"></a>Kullanışlı betik oluşturma nesneleri

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications

Windows PowerShell ISE'de konsol uygulamaları ile nasıl etkileştiğini bazı sınırlamalar vardır. Bir komut veya kullanıcı etkileşimi gerektiren bir Otomasyon betiği Windows PowerShell konsolundan çalışma şeklini çalışmayabilir. Bu komutları veya betikleri Windows PowerShell ISE komutunu bölmesinde çalışmasını engellemek isteyebilirsiniz. **$PsUnsupportedConsoleApplications** nesne bu tür komutların bir listesini tutar. Bu listede komutları çalıştırmayı denerseniz, bunlar desteklenmez bir ileti alırsınız. Aşağıdaki betik, bir giriş listesine ekler.

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a>$psLocalHelp

Bağlama duyarlı Yardım konularını ve bunların ilişkili bağlantılarını yerel derlenmiş HTML Yardım dosyasında eşlemesini tutan bir sözlük nesnesi budur. Belirli bir konu için yerel Yardım bulmak için kullanılır. Ekleyebilir veya konular bu listeden silin. Aşağıdaki kod örneğinde bulunan anahtar-değer çiftleri bazı örnek gösterir `$psLocalHelp`.

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

Aşağıdaki betik, bir giriş listesine ekler.

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp

Bağlama duyarlı Yardım konuları, konu başlıkları ve bunların ilişkili dış URL'lerini eşlemesini tutan bir sözlük nesnesi budur. Web üzerinde belirli bir konu için Yardım bulmak için kullanılır. Ekleyebilir veya konular bu listeden silin.

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : http://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : http://go.microsoft.com/fwlink/p/?LinkID=113278
```

Aşağıdaki betik, bir giriş listesine ekler.

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell ISE betik oluşturma nesne modelinin amacı](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)