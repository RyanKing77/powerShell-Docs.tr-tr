---
title: SelectionSet öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850424"
---
# <a name="selectionset-element-format"></a>SelectionSet Öğesi (Biçim)

Küme adı tarafından başvurulan bir .NET nesne tanımlar.

Yapılandırma öğesi (biçimi) SelectionSets öğesi (biçimi) SelectionSet öğesi (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `SelectionSet` öğesi. Her seçim kümesinin bir adı olması gerekir ve .NET nesneleri kümesinin belirtmeniz gerekir.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Name öğesi SelectionSet (biçimi) için](./name-element-for-selectionset-format.md)|Gerekli öğe.<br /><br /> Seçimi kümesi başvurmak için kullanılan adını belirtir.|
|[Türleri öğesi (biçimi)](./types-element-for-selectionset-format.md)|Gerekli öğe.<br /><br /> Seçimdeki ayarlanan .NET nesneleri tanımlar.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[SelectionSets öğesi biçimi](./selectionsets-element-format.md)|Biçimlendirme dosyanın tüm görünümler tarafından kullanılan .NET nesneleri ortak kümesini tanımlar.|

## <a name="remarks"></a>Açıklamalar

Devralma yoluyla ilişkili bir nesne gibi tek bir adı kullanarak başvurmak istediğiniz bir ilgili nesne varsa, seçim kümeleri kullanabilirsiniz. Kendi görünümlerinizi tanımlarken, her bir görünüm içindeki tüm nesneleri listelemek yerine ayarlamak seçimi adını kullanarak nesne kümesini belirtebilirsiniz.

Ortak seçimi ayarlar, biçimlendirme dosyası görünümlerini veya görünümlerinin tanımlarını tanımlarken adlarına göre belirtilir. Bu gibi durumlarda, `SelectionSetName` alt öğesi `ViewSelectedBy` ve `EntrySelectedBy` öğeleri kullanılacak kümesi belirtir. Seçimi kümeleri hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte gösterildiği bir `SelectionSet` dört .NET türlerini tanımlayan öğe.

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

[SelectionSet (biçimi) öğesinin adı](./name-element-for-selectionset-format.md)

[SelectionSets öğesi (biçimi)](./selectionsets-element-format.md)

[Türleri öğesi (biçimi)](./types-element-for-selectionset-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
