---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Galeri arama söz dizimi
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084309"
---
# <a name="gallery-search-syntax"></a>Galeri arama söz dizimi

PowerShell Galerisi kullanılarak arama [PowerShell galerinin web sitesi](https://www.powershellgallery.com/).
Burada sözcük ve tümcecikleri anahtar ifadeleri arama sonuçları daraltmak için kullanabileceğiniz bir metin searchbox PowerShell Galerisi web sitesi sunar.

## <a name="search-by-keywords"></a>Anahtar sözcüklere göre ara

    dsc azure sql

Arama, tüm 3 anahtar sözcükleri içeren ilgili belgeleri bulun ve eşleşen belgelerin dönüş dener.

## <a name="search-using-phrases-and-keywords"></a>İfadeler ve anahtar sözcükleri kullanarak arama

    "azure sql" deployment

Tırnak işaretleri arasına tümcecik girerek ("") yerine ayrı bir anahtar sözcük belirli tümceciği aramak için arama değiştirin.
Eşleşen belgelerin genellikle "azure sql" büyük/küçük harf çeşidi örn dahil olmak üzere, tam tümcecik içermelidir "Azure SQL" ve de genellikle 'dağıtımı' sözcük içerir.

## <a name="filtering-on-fields"></a>Alanlarda filtreleme

Bir belirli bir paket kimliği (veya 'Id' veya 'id') arama yapabilirsiniz veya alan adı şartlarını önek tarafından diğer belirli alanları arama yapın.

Şu anda aranabilir alanları 'Id', 'Version', 'Etiketleri', 'Yazma', 'Owner', 'İşlevler', 'Cmdlet'leri', 'DscResources' ve 'PowerShellVersion' ' dir.

[ID ve başlık arasındaki fark nedir? Kimliği konsolda kullandığınız addır. Arama sonuçlarında paket sayfanın üstünde gösterilen başlıktır.]

## <a name="examples"></a>Örnekler

    ID:PSReadline
    
"PSReadline" içeren bir kimliği paketleri bulur.

    Id:"AzureRM.Profile"

"AzureRM.Profile" paketlerle kendi Kimliği alanı bulmak için başka bir yoludur.

'Id' filtresi, bir alt dizesi eşleşiyorsa, bu nedenle aşağıdakiler için arama şöyledir:

    Id:"azure"

Bu AzureRM.Profile içeren sonuçları sağlar ' ve 'Azure.Storage'.

Tek bir alanda birden çok anahtar sözcük için arama da yapabilirsiniz. 

    id:azure tags:intellisense

Ve tümcecik aramaları çift tırnak işareti kullanarak gerçekleştirebilirsiniz:

    id:"azure.storage"

DSC etikete sahip tüm paketleri aramak için kullanılır.

    Tags:DSC

Belirtilen işlev olan tüm paketleri aramak için kullanılır.

    Functions:Get-TreeSize

Belirtilen cmdlet'i ile tüm paketleri aramak için kullanılır.

    Cmdlets:Get-AzureRmEnvironment

Belirtilen DSC kaynak adına sahip tüm paketleri aramak için kullanılır.

    DscResources:xArchive

Belirtilen PowerShellVersion olan tüm paketleri aramak için

    PowerShellVersion:2.0

Son olarak, bir alan, 'komutları gibi' desteklemiyoruz kullanırsanız, biz yalnızca yoksayabilir ve tüm alanları arayın. Bu nedenle sorguyu aşağıdaki

    commands:blobs storage

Olduğu aynı şekilde bu sorgu yorumlanır:

    blobs storage
