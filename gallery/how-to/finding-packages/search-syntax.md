---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Galeri arama söz dizimi
ms.openlocfilehash: 9aadb6771c85845cc3fa05cb56f0194b060d1c1b
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004146"
---
# <a name="gallery-search-syntax"></a>Galeri arama söz dizimi

PowerShell Galerisi, burada sözcük ve tümcecikleri anahtar ifadeleri arama sonuçları daraltmak için kullanabileceğiniz bir metin searchbox sunar.

## <a name="search-by-keywords"></a>Anahtar sözcüklere göre ara

    dsc azure sql

Arama tüm 3 anahtar sözcükleri içeren ilgili belgeleri bulmak için en iyi deneme yapın ve eşleşen belgeleri döndürür.

## <a name="search-using-phrases-and-keywords"></a>İfadeler ve anahtar sözcükleri kullanarak arama

    "azure sql" deployment

Tırnak işaretleri arasına tümcecik girerek ("") yerine ayrı bir anahtar sözcük belirli tümceciği aramak için arama değiştirin.
Eşleşen belgelerin genellikle "azure sql" büyük/küçük harf çeşidi örn dahil olmak üzere, tam tümcecik içermelidir "Azure SQL" ve de genellikle 'dağıtımı' sözcük içerir.

## <a name="filtering-on-fields"></a>Alanlarda filtreleme

Bir belirli bir paket kimliği (veya 'Id' veya 'id') arama yapabilirsiniz veya alan adı şartlarını önek tarafından diğer belirli alanları arama yapın.

Şu anda aranabilir alanları 'Id', 'Version', 'Etiketleri', 'Yazma', 'Owner', 'İşlevler', 'Cmdlet'leri', 'DscResources' ve 'PowerShellVersion' ' dir.

[ID ve başlık arasındaki fark nedir? Kimliği konsolda kullandığınız addır. Arama sonuçlarında paket sayfanın üstünde gösterilen başlıktır.]

## <a name="examples"></a>Örnekler

    ID:"PSReadline"
    id:"AzureRM.Profile"

"PSReadline" veya "AzureRM.Profile" olan paketleri kendi Kimliği alanında sırasıyla bulur.

    Id:"AzureRM.Profile"

"AzureRM.Profile" paketlerle kendi Kimliği alanı bulmak için başka bir yoludur.

'Id' filtresi, bir alt dizesi eşleşiyorsa, bu nedenle aşağıdakiler için arama şöyledir:

    Id:"azure"

'AzureRM.Profile' ve 'Azure.Storage' benzer bir sonuç elde edersiniz.

Tek bir alanda birden çok anahtar sözcük için arama da yapabilirsiniz. Veya karıştırıp eşleştirebilirsiniz alanları.

    id:azure tags:intellisense
    id:azure id:storage

Ve tümcecik aramaları gerçekleştirebilirsiniz:

    id:"azure.storage"


DSC etikete sahip tüm paketleri aramak için kullanılır.

    Tags:"DSC"

Belirtilen işlev olan tüm paketleri aramak için kullanılır.

    Functions:"Update-AzureRM"

Belirtilen cmdlet'i ile tüm paketleri aramak için kullanılır.

    Cmdlets:"Get-AzureRmEnvironment"

Belirtilen DSC kaynak adına sahip tüm paketleri aramak için kullanılır.

    DscResources:"xArchive"

Belirtilen PowerShellVersion olan tüm paketleri aramak için

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


Son olarak, bir alan, 'komutları gibi' desteklemiyoruz kullanırsanız, biz yalnızca yoksayabilir ve tüm alanları arayın. Bu nedenle sorguyu aşağıdaki

    commands:blobs storage

Olduğu aynı şekilde bu sorgu yorumlanır:

    blobs storage
