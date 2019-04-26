---
title: Öğe SelectionSet (biçimi) için ad | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065164"
---
# <a name="name-element-for-selectionset-format"></a>SelectionSet için Ad Öğesi (Biçim)

Seçimi kümesi başvurmak için kullanılan adını belirtir.

Yapılandırma öğesi (biçimi) SelectionSets öğesi (biçimi) SelectionSet öğesi (biçimi) adı öğesi SelectionSet (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `Name` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[SelectionSet öğesi (biçimi)](./selectionset-element-format.md)|Tek bir küme adı tarafından başvurulan .NET nesneleri kümesini tanımlar.|

## <a name="text-value"></a>Metin değeri

Seçimi kümesi başvurmak için adını belirtin. Hangi karakter sınırlama kullanılabilir vardır.

## <a name="remarks"></a>Açıklamalar

Burada belirtilen ad kullanılır `SelectionSetName` öğesi. Göre görünümü, görünüm tanımı tarafından kullanılabilecek seçim kümesi (görünümler birden çok tanım olabilir) veya seçim koşulu belirtmek için. Seçimi kümeleri hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).

## <a name="example"></a>Örnek

Bu örnek gösterir bir `SelectionSet` dört .NET türlerini tanımlayan öğe. "FileSystemTypes" seçimi kümesinin adıdır.

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

[Seçimi ayarlar tanımlama](./defining-selection-sets.md)

[SelectionSet öğesi (biçimi)](./selectionset-element-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
