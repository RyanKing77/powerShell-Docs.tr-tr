---
title: SelectionSetName öğesi EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionCondition için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063869"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>EnumerableExpansion EntrySelectedBy için SelectionCondition SelectionSetName Öğesi (Biçim)

Tetikleme koşulu .NET türleri kümesini belirtir. Bu türlerinden herhangi birini mevcut olduğunda, koşul karşılanır.

Yapılandırma öğesi DefaultSettings öğesi (biçimi) EnumerableExpansions öğesi (biçimi) EnumerableExpansions öğesi (biçimi) EntrySelectedBy öğesi için EntrySelectedBy SelectionCondition öğesinin EnumerableExpansion (biçimi) SelectionCondition EnumerableExpansion (biçimi) için EntrySelectedBy için için EnumerableExpansion (biçimi) SelectionSetName öğesi

## <a name="syntax"></a>Sözdizimi

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `SelectionSetName` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Bu tanımın koleksiyon nesnelerini genişletmek için bulunması gereken koşulu tanımlar.|

## <a name="text-value"></a>Metin değeri

Seçimi kümesinin adını belirtin.

## <a name="remarks"></a>Açıklamalar

Seçim koşulu, bir seçim kümesi veya .NET türü belirtebilirsiniz, ancak ikisini birden belirtemezsiniz. Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).

Seçimi ayarlar biçimlendirme dosyayı tanımlayan herhangi bir görünüm tarafından kullanılan .NET nesneleri ortak gruplarıdır. Oluşturma ve başvuran seçimi ayarlar hakkında daha fazla bilgi için bkz. [tanımlama seçimi](./defining-selection-sets.md).

## <a name="see-also"></a>Ayrıca bkz:

[Seçimi ayarlar tanımlama](./defining-selection-sets.md)

[EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
