---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Diğer kullanışlı komut dosyası nesneleri"
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 8334d0b346e59dea3643a93bf52b780b361d1945
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="other-useful-scripting-objects"></a>Diğer kullanışlı komut dosyası nesneleri
  Aşağıdaki nesneler Windows PowerShell ISE komut dosyası ek işlevsellik sağlar. Olmadıkları parçası **$psISE** hiyerarşisi.

## <a name="useful-scripting-objects"></a>Yararlı komut dosyası nesneleri

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications
 Windows PowerShell ISE konsol uygulamaları ile nasıl etkileşim kurduğu bazı sınırlamalar vardır. Bir komut veya kullanıcı etkileşimi gerektiren bir otomasyon komut dosyası Windows PowerShell konsolundan çalışma biçimini çalışmayabilir. Bu komutlar veya komut dosyaları Windows PowerShell ISE komutu bölmesinde çalışmasını engellemek isteyebilirsiniz. **$PsUnsupportedConsoleApplications** nesnesi gibi komutların listesini tutar. Bu listede komutları çalıştırmayı deneyin, bunlar desteklenmez bir ileti alırsınız. Aşağıdaki komut dosyasını bir giriş listesine ekler.

```
# List the unsupported commands
psUnsupportedConsoleApplications
# Add a command to this list
psUnsupportedConsoleApplications.Add(“Mycommand”)
#Show the augmented list of commands
psUnsupportedConsoleApplications

```

### <a name="pslocalhelp"></a>$psLocalHelp
 Bu Yardım konuları ve yerel koda derlenmiş HTML Yardım dosyasındaki ilişkili bağlantılarını arasında bağlama duyarlı bir eşleme tutan bir sözlük nesnesidir. Belirli bir konu için yerel Yardım bulmak için kullanılır. Ekleyebilir veya bu listeden konuları silebilirsiniz. Aşağıdaki kod örneğinde bazı örnek bulunan anahtar-değer çiftleri gösterir **$psLocalHelp**.

```
# See the local help map
$psLocalHelp | Format-List

```

### <a name="sample-output"></a>Örnek Çıkış

|||
|-|-|
|Anahtar:-Bilgisayar Ekle|Değer: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm|
|Anahtar:-İçerik Ekle|Değer: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm|

 Aşağıdaki komut dosyasını bir giriş listesine ekler.

```
$psLocalHelp.Add("get-myNoun","c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp
 Bu Yardım konuları konu başlıklarını ve bunların ilişkili dış URL'lerini arasında bağlama duyarlı bir eşleme tutan bir sözlük nesnesidir. Web üzerinde belirli bir konu için Yardım bulmak için kullanılır. Ekleyebilir veya bu listeden konuları silebilirsiniz.

```
$psOnlineHelp | Format-List

```

### <a name="sample-output"></a>Örnek Çıkış

|||
|-|-|
|Anahtar:-Bilgisayar Ekle|Değer: http://go.microsoft.com/fwlink/p/?LinkID=135194|
|Anahtar:-İçerik Ekle|Değer: http://go.microsoft.com/fwlink/p/?LinkID=113278|

 Aşağıdaki komut dosyasını bir giriş listesine ekler.

```
$psOnlineHelp.Add("get-myNoun","http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Ayrıca bkz:
- [Windows PowerShell ISE nesne modeli komut dosyası oluşturma](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
