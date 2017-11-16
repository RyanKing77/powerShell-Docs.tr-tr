---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
title: Katalog cmdlet'leri
ms.openlocfilehash: f0869e8c174ab127996866775ad20d056f877345
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/27/2017
---
# <a name="catalog-cmdlets"></a>Katalog cmdlet'leri  

İki yeni cmdlet'leri ekledik [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) oluşturmak ve windows katalog dosyaları doğrulamak için modülü.  

## <a name="new-filecatalog"></a>FileCatalog yeni 
--------------------------------

`New-FileCatalog`Dosya ve klasörleri kümesi için bir windows katalog dosyası oluşturur. Bir katalog dosyası belirtilen yolda tüm dosyalar için karmaları içerir. Kullanıcılar bu klasörleri temsil eden katalog dosyası karşılık gelen birlikte klasörler kümesi dağıtabilirsiniz. Bir katalog dosyası içeriği alıcı tarafından katalog oluşturulduktan sonra klasörlere hiçbir değişiklik yapılmadan olup olmadığını doğrulamak için kullanılabilir.    

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
Oluşturma katalog sürüm 1 ve 2 destekliyoruz. Sürüm 1 dosya karmaları ve sürüm 2 SHA256 kullanır oluşturmak için SHA1 karma algoritmasını kullanır. Katalog sürüm 2 desteklenmiyor *Windows Server 2008 R2* ve *Windows 7*. Katalog sürüm 2 platformları kullanıyorsanız kullanmak için önerilen *Windows 8*, *Windows Server 2012* ve üstü.  

Var olan bir modül üzerinde bu komutu kullanmak için modül bildirimi konumunu eşleşecek şekilde CatalogFilePath ve yol değişkenleri belirtin. Aşağıdaki örnekte, C:\Program Files\Windows PowerShell\Modules\Pester modülü bildirimidir. 

![](../images/NewFileCatalog.jpg)

Bu, katalog dosyası oluşturur. 

![](../images/CatalogFile1.jpg)  

![](../images/CatalogFile2.jpg) 

Bir katalog dosyası (exmaple yukarıda içinde Pester.cat) bütünlüğünü doğrulamak için bu kullanılarak imzalanmalıdır [kümesi AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet'i.   


## <a name="test-filecatalog"></a>Test-FileCatalog 
--------------------------------

`Test-FileCatalog`klasörleri kümesini temsil eden katalog doğrular. 

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Bu cmdlet, tüm dosyaları ve bunların göreli yollar diske kaydedilmiş bulunanlarla katalog dosyasında bulunan karmaları karşılaştırır. Herhangi dosya karmaları ve yolları arasında uyuşmazlık algılarsa durumunu döndürür `ValidationFailed`. Kullanıcılar, tüm bu bilgileri kullanarak alabilir `Detailed` geçin. Kataloğun imzalama durumu görüntülenir `Signature` çağırmak kadar aynı alan [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) katalog dosyası cmdlet'ini. Kullanıcılar ayrıca atlayabilirsiniz herhangi bir dosya doğrulama sırasında kullanarak `FilesToSkip` parametresi. 

