---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Katalog cmdlet’leri
ms.openlocfilehash: ec5fc866fe27a894b23b93d3ea46ad9c0cba288e
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522897"
---
# <a name="catalog-cmdlets"></a>Katalog cmdlet'leri

İçinde iki yeni cmdlet ekledik [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) oluşturmak ve windows katalog dosyaları doğrulamak için modülü.

## <a name="new-filecatalog"></a>Yeni FileCatalog
--------------------------------

`New-FileCatalog` klasörleri ve dosyaları kümesi için bir windows katalog dosyası oluşturur. Bir katalog dosyası belirtilen yolda tüm dosyaların karmalarını içerir. Kullanıcılar, bu klasörleri temsil eden bir katalog dosyası karşılık gelen birlikte klasör kümesi dağıtabilirsiniz. Bir katalog dosyası içeriği alıcı tarafından Kataloğu oluşturulduktan sonra klasörlere yapılan herhangi bir değişiklik olup olmadığını doğrulamak için kullanılabilir.

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
Oluşturma Kataloğu sürüm 1 ve 2 destekliyoruz. Sürüm 1, dosya karmalarını ve sürüm 2 SHA256 kullanan oluşturmak için SHA1 karma algoritmasını kullanır. Katalog sürümü 2 üzerinde desteklenmiyor *Windows Server 2008 R2* ve *Windows 7*. Katalog sürüm 2 platformlarını kullanıyorsa kullanmak için önerilen *Windows 8*, *Windows Server 2012* ve üstü.

Var olan bir modülde bu komutu kullanmak için modül bildirimini konumunu eşleşecek şekilde CatalogFilePath ve yol değişkenleri belirtin. Aşağıdaki örnekte C:\Program Files\Windows PowerShell\Modules\Pester modülü bildirimidir.

![](../images/NewFileCatalog.jpg)

Bu, katalog dosyası oluşturur.

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

Bir katalog dosyası (Yukarıdaki örneği de Pester.cat) bütünlüğünü doğrulamak için bu kullanılarak imzalanıp imzalanmayacağını [kümesi AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet'i.


## <a name="test-filecatalog"></a>Test-FileCatalog
--------------------------------

`Test-FileCatalog` klasörleri kümesini temsil eden Kataloğu doğrular.

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Bu cmdlet, tüm dosyaları ve diske kaydedilmiş bulunanlarla katalog dosyasında bulunan kendi göreli yolları karma değerlerini karşılaştırır. Dosya karmalarını ve yolları arasında herhangi bir uyuşmazlık algılarsa durumunu döndürür. `ValidationFailed`.
Kullanıcılar, tüm bu bilgileri kullanarak alabilir `Detailed` geçin. Katalog imzalama durumu görüntülenir `Signature` çağırmak kadar aynı alanı [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet'i katalog dosyası üzerinde.
Kullanıcılar ayrıca atlayabilirsiniz herhangi bir dosya doğrulama sırasında kullanarak `FilesToSkip` parametresi.
