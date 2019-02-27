---
title: TypeName öğesi türleri (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: 4f463ac6b70a00f628c5b93b112c5fa510ff3bfb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845118"
---
# <a name="typename-element-for-types-format"></a>Türler için TypeName Öğesi (Biçim)

.NET seçimi kümesine ait olan bir nesne türünü belirtir.

Yapılandırma öğesi (biçimi) SelectionSets öğesi (biçimi) SelectionSet öğesi (biçimi) türler (biçimi) öğesi (biçimi) TypeName öğesi türleri

## <a name="syntax"></a>Sözdizimi

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `TypeName` öğesi. En az bir `TypeName` öğe seçimi kümesinde eklenmesi gerekir.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Türleri öğesi (biçimi)](./types-element-for-selectionset-format.md)|Seçimdeki ayarlanan .NET nesneleri tanımlar.|

## <a name="text-value"></a>Metin Değeri

.NET türünün tam adını belirtin.

## <a name="remarks"></a>Açıklamalar

Devralma yoluyla ilişkili bir nesne gibi tek bir adı kullanarak başvurmak istediğiniz bir ilgili nesne varsa, seçim kümeleri kullanabilirsiniz. Kendi görünümlerinizi tanımlarken, her bir görünüm içindeki tüm nesneleri listelemek yerine ayarlamak seçimi adını kullanarak nesne kümesini belirtebilirsiniz.

Ortak seçimi ayarlar, biçimlendirme dosyası görünümlerini tanımlarken adlarına göre belirtilir. Bu gibi durumlarda, `SelectionSetName` alt öğesi `ViewSelectedBy` görünüm öğesi kümesi belirtir. Ancak, farklı bir görünüm girişlerinin yalnızca görünüm bu girişi için geçerli bir seçim kümesi belirtebilirsiniz. Seçimi kümeleri hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte gösterildiği bir `SelectionSet` dört .NET türlerini tanımlayan öğe.

```
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a>Ayrıca bkz:

[Seçimi ayarlar tanımlama](./defining-selection-sets.md)

[SelectionSet öğesi (biçimi)](./selectionset-element-format.md)

[SelectionSets öğesi (biçimi)](./selectionsets-element-format.md)

[Türleri öğesi (biçimi)](./types-element-for-selectionset-format.md)

[Dosya biçimlendirme bir Windows PowDefining kümesi ObjecterShell yazma](./writing-a-powershell-formatting-file.md)
