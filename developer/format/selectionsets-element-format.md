---
title: SelectionSets öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063790"
---
# <a name="selectionsets-element-format"></a>SelectionSets Öğesi (Biçim)

Biçimlendirme dosyanın tüm görünümler tarafından kullanılan .NET nesneleri ortak kümesini tanımlar. Görünüm ve biçimlendirme dosyasının tam nesne kümesini yalnızca seçimi kümesinin adını kullanarak başvurabilirsiniz.

Yapılandırma öğesi SelectionSets öğesi biçimi

## <a name="syntax"></a>Sözdizimi

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `SelectionSets` öğesi. Her alt öğe kümesi adı tarafından başvurulan bir nesne tanımlar. Alt öğelerin sırası önemli değildir.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[SelectionSet öğesi (biçimi)](./selectionset-element-format.md)|Gerekli öğe.<br /><br /> Tek bir küme adı tarafından başvurulan .NET nesneleri kümesini tanımlar.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Yapılandırma öğesi](./configuration-element-format.md)|Biçimlendirme bir dosyanın üst düzey öğesi temsil eder.|

## <a name="remarks"></a>Açıklamalar

Devralma yoluyla ilişkili bir nesne gibi tek bir adı kullanarak başvurmak istediğiniz bir ilgili nesne varsa, seçim kümeleri kullanabilirsiniz. Kendi görünümlerinizi tanımlarken, her bir görünüm içindeki tüm nesneleri listelemek yerine ayarlamak seçimi adını kullanarak nesne kümesini belirtebilirsiniz.

Ortak seçimi ayarlar, biçimlendirme dosyası görünümlerini veya görünümlerinin tanımlarını tanımlarken adlarına göre belirtilir. Bu gibi durumlarda, `SelectionSetName` alt öğesi `ViewSelectedBy` ve `EntrySelectedBy` öğeleri kullanılacak kümesi belirtir. Seçimi kümeleri hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).

## <a name="see-also"></a>Ayrıca bkz:

[Yapılandırma öğesi](./configuration-element-format.md)

[Seçimi ayarlar tanımlama](./defining-selection-sets.md)

[SelectionSet öğesi (biçimi)](./selectionset-element-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
