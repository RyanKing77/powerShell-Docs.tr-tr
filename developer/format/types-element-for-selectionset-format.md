---
title: SelectionSet (biçimi) için öğe türleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851278"
---
# <a name="types-element-for-selectionset-format"></a>SelectionSet için Türler Öğesi (Biçim)

Seçimdeki ayarlanan .NET nesneleri tanımlar.

Yapılandırma öğesi (biçimi) SelectionSets öğesi (biçimi) SelectionSet öğesi (biçimi) (biçimi) öğe türleri

## <a name="syntax"></a>Sözdizimi

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `Types` öğesi. En az bir alt öğesi olmalıdır, ancak eklenebilir alt öğe sayısı için en fazla bir sınır yoktur.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TypeName öğesi türleri (biçimi)](./typename-element-for-types-format.md)|Gerekli öğe.<br /><br /> Seçimi kümesine ait olan bir .NET nesnesini belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[SelectionSet öğesi (biçimi)](./selectionset-element-format.md)|Küme adı tarafından başvurulan bir .NET nesne tanımlar.|

## <a name="remarks"></a>Açıklamalar

Bu öğe tarafından tanımlanan nesneler tarafından bir görünüm, görünüm tanımı tarafından kullanılabilecek seçim kümesi oluşturan (görünümler birden çok tanım olabilir) veya seçim koşulu belirtmek için.  Seçimi kümeleri hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).

## <a name="example"></a>Örnek

Bu örnek gösterir bir `SelectionSet` dört .NET türlerini tanımlayan öğe.

```xml
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

[Nesne kümesi tanımlama](./defining-selection-sets.md)

[SelectionSet öğesi (biçimi)](./selectionset-element-format.md)

[TypeName öğesi türleri (biçimi)](./typename-element-for-types-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
