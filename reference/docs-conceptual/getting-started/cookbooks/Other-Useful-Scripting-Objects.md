---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Diğer Kullanışlı Betik Oluşturma Nesneleri
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 0e87e9919199e011ab5abec5b07dccc8494ad64a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="other-useful-scripting-objects"></a>Diğer Kullanışlı Betik Oluşturma Nesneleri

Aşağıdaki nesneler Windows PowerShell ISE komut dosyası ek işlevsellik sağlar. Olmadıkları parçası **$psISE** hiyerarşisi.

## <a name="useful-scripting-objects"></a>Yararlı komut dosyası nesneleri

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications

Windows PowerShell ISE konsol uygulamaları ile nasıl etkileşim kurduğu bazı sınırlamalar vardır. Bir komut veya kullanıcı etkileşimi gerektiren bir otomasyon komut dosyası Windows PowerShell konsolundan çalışma biçimini çalışmayabilir. Bu komutlar veya komut dosyaları Windows PowerShell ISE komutu bölmesinde çalışmasını engellemek isteyebilirsiniz. **$PsUnsupportedConsoleApplications** nesnesi gibi komutların listesini tutar. Bu listede komutları çalıştırmayı deneyin, bunlar desteklenmez bir ileti alırsınız. Aşağıdaki komut dosyasını bir giriş listesine ekler.

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a>$psLocalHelp

Bu Yardım konuları ve yerel koda derlenmiş HTML Yardım dosyasındaki ilişkili bağlantılarını arasında bağlama duyarlı bir eşleme tutan bir sözlük nesnesidir. Belirli bir konu için yerel Yardım bulmak için kullanılır. Ekleyebilir veya bu listeden konuları silebilirsiniz. Aşağıdaki kod örneğinde bazı örnek bulunan anahtar-değer çiftleri gösterir **$psLocalHelp**.

```powershell
# See the local help map
$psLocalHelp | Format-List
```

### <a name="sample-output"></a>Örnek Çıkış

|||
|-|-|
|Anahtar:-Bilgisayar Ekle|Değer: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm|
|Anahtar:-İçerik Ekle|Değer: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm|

Aşağıdaki komut dosyasını bir giriş listesine ekler.

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp

Bu Yardım konuları konu başlıklarını ve bunların ilişkili dış URL'lerini arasında bağlama duyarlı bir eşleme tutan bir sözlük nesnesidir. Web üzerinde belirli bir konu için Yardım bulmak için kullanılır. Ekleyebilir veya bu listeden konuları silebilirsiniz.

```powershell
$psOnlineHelp | Format-List
```

### <a name="sample-output"></a>Örnek Çıkış

|||
|-|-|
|Anahtar:-Bilgisayar Ekle|Değer: http://go.microsoft.com/fwlink/p/?LinkID=135194|
|Anahtar:-İçerik Ekle|Değer: http://go.microsoft.com/fwlink/p/?LinkID=113278|

 Aşağıdaki komut dosyasını bir giriş listesine ekler.

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Ayrıca bkz:

- [Nesne modeli komut dosyası Windows PowerShell ISE amacı](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)