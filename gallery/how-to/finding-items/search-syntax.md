---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Galeri arama söz dizimi
ms.openlocfilehash: 52fca21a00bcc6e3789bceb331acf5bc771bb0f2
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="gallery-search-syntax"></a>Galeri arama söz dizimi

Arama sonuçları daraltmak için sözcükler, ifadeler ve anahtar sözcüğü ifadeler burada kullanabilirsiniz metin searchbox PowerShell Galerisi sunar.

## <a name="search-by-keywords"></a>Anahtar sözcükler göre ara

    dsc azure sql

Arama tüm 3 anahtar sözcükler içeren ilgili belgeleri bulmak için en iyi çaba yapın ve eşleşen belgeleri döndürür.

## <a name="search-using-phrases-and-keywords"></a>Tümcecikleri ve anahtar sözcükler kullanarak arama

    "azure sql" deployment

Tırnak işaretleri arasında tümcecik girerek ("") ayrı anahtar sözcükler yerine belirli tümceciği aramak için arama değiştirin.
Eşleşen belgelerin genellikle "azure sql" büyük/küçük harf çeşidi örneğin de dahil olmak üzere, tam deyim içermelidir "Azure SQL" ve de genellikle word 'dağıtım' içermelidir.

## <a name="filtering-on-fields"></a>Alanları filtreleme

Bir özel öğesi kimliği (veya 'Id' veya 'ID') arayabilirsiniz veya alan adı şartlarını bazı diğer alanlar önek olarak arama yapın.

Şu anda aranabilir 'Id', 'Version', 'Etiketleri', 'Yazar', 'Sahibi', 'İşlevleri', 'Cmdlet'leri', 'DscResources' ve 'PowerShellVersion' alanlardır.

[Başlık kimliği arasındaki fark nedir? Kimliği konsolda kullandığınız addır. Başlık sayfanın üst kısmındaki öğe arama sonuçlarında gösterilen yer alır.]

## <a name="examples"></a>Örnekler

    ID:"PSReadline"
    id:"AzureRM.Profile"

"PSReadline" veya "AzureRM.Profile" öğeleriyle kendi Kimliği alanında sırasıyla bulur.

    Id:"AzureRM.Profile"

kendi Kimliği alanında "AzureRM.Profile" ile öğelerini bulmak için başka bir yoludur.

'Id' filtre, bir alt dizesi eşleşiyorsa, bunu aşağıdakiler için arama şöyledir:

    Id:"azure"

'AzureRM.Profile' ve 'Azure.Storage' gibi sonuçları elde edersiniz.

Tek bir alanda birden çok anahtar kelimeleri arayabilirsiniz. Karışık ve alanların eşleştiği.

    id:azure tags:intellisense
    id:azure id:storage

Ayrıca, deyim aramalarını gerçekleştirebilirsiniz:

    id:"azure.storage"


DSC etikete sahip tüm öğeleri aramak için kullanılır.

    Tags:"DSC"

Belirtilen işlevi olan tüm öğeleri aramak için kullanılır.

    Functions:"Update-AzureRM"

Belirtilen cmdlet'ini tüm öğeleri aramak için kullanılır.

    Cmdlets:"Get-AzureRmEnvironment"

Belirtilen DSC kaynağı ada sahip tüm öğeleri aramak için kullanılır.

    DscResources:"xArchive"

Belirtilen PowerShellVersion tüm öğeleri aramak için

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


Son olarak, 'gibi komutları' desteklemiyoruz alan kullanırsanız, biz yalnızca yok sayın ve tüm alanları arayın. Bu nedenle sorgu aşağıdaki

    commands:blobs storage

Olan tam olarak aynı bu sorguyu yorumlanır:

    blobs storage