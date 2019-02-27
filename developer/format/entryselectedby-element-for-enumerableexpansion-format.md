---
title: EntrySelectedBy öğesi EnumerableExpansion (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846525"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a>EnumerableExpansion için EntrySelectedBy Öğesi (Biçim)

Bu tanım veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.

Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi) EnumerableExpansions öğesi (biçimi) EnumerableExpansion öğesi (biçimi) EntrySelectedBy öğesi EnumerableExpansion (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `EntrySelectedBy` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|İsteğe bağlı öğe.<br /><br /> Bu tanımın koleksiyon nesnelerini genişletmek için bulunması gereken koşulu tanımlar.|
|[EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|İsteğe bağlı öğe.<br /><br /> Koleksiyon nesnelerini nasıl genişletilir bu tanımı kullanan .NET türleri kümesini belirtir.|
|[TypeName öğesi için EntrySelectedBy EnumerableExpansion (biçimi) için](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|İsteğe bağlı öğe.<br /><br /> Koleksiyon nesnelerini nasıl genişletilir bu tanımı kullanan bir .NET türü belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EnumerableExpansion öğesi (biçimi)](./enumerableexpansion-element-format.md)|Bir görünümü'nde görüntülendiğinde nesneleri genişletilir belirli .NET koleksiyonu tanımlar.|

## <a name="remarks"></a>Açıklamalar

En az bir türü, seçim kümesi veya tanımı girişi için seçim koşulu belirtmeniz gerekir. Kullanabileceğiniz bir alt öğe sayısı maksimum sınırı yoktur.

Seçimi koşullar bir nesne belirli bir özelliğine sahip olduğunda gibi kullanılacak tanımı için bulunması gereken bir koşul tanımlamak için kullanılır veya bir özel özellik değerini veya betik değerlendiren `true`. Seçimi koşullar hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Ayrıca bkz:

[Verileri görüntülemek için koşulları tanımlama](./defining-conditions-for-displaying-data.md)

[EnumerableExpansion öğesi (biçimi)](./enumerableexpansion-element-format.md)

[EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[TypeName öğesi için EntrySelectedBy EnumerableExpansion (biçimi) için](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
