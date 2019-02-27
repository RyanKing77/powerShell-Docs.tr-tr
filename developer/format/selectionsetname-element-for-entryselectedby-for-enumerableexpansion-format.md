---
title: SelectionSetName öğesi EntrySelectedBy EnumerableExpansion (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851537"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a>EnumerableExpansion EntrySelectedBy için SelectionSetName Öğesi (Biçim)

Bu tanımı tarafından genişletilen .NET türleri kümesini belirtir.

Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi) EnumerableExpansions öğesi (biçimi) EnumerableExpansion öğesi (biçimi) EntrySelectedBy öğesi için EntrySelectedBy SelectionSetName öğesinin EnumerableExpansion (biçimi) EnumerableExpansion (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionSetName` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy öğesi EnumerableExpansion (biçimi) için](./entryselectedby-element-for-enumerableexpansion-format.md)|Bu tanımı tarafından genişletilen .NET koleksiyon nesnelerini tanımlar.|

## <a name="text-value"></a>Metin Değeri

Seçimi kümesinin adını belirtin.

## <a name="remarks"></a>Açıklamalar

Her tanım, bir veya daha fazla tür adları, seçim kümesi veya bir seçim koşulu belirtmeniz gerekir.

Seçimi ayarlar, genellikle kullanılan nesnelerin bir grup içinde birden çok görünüm tanımlamak istediğinizde kullanılır. Örneğin, bir tablo görünümü ve aynı nesne kümesini bir liste görünümü oluşturmak isteyebilirsiniz. Seçimi ayarlar tanımlama hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin bir görünüm için](./defining-selection-sets.md).

## <a name="see-also"></a>Ayrıca bkz:

[Seçimi ayarlar tanımlama](./defining-selection-sets.md)

[EntrySelectedBy öğesi EnumerableExpansion (biçimi) için](./entryselectedby-element-for-enumerableexpansion-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
