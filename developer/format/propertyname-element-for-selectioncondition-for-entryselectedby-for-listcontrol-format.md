---
title: PropertyName öğesi SelectionCondition EntrySelectedBy ListControl (biçimi) için için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064911"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>ListControl EntrySelectedBy için SelectionCondition PropertyName Öğesi (Biçim)

Koşul tetikleyen .NET alan özelliği belirtir. Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve liste girdisini kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi) EntrySelectedBy öğesi SelectionCondition öğesinin ListEntry (biçimi) EntrySelectedBy EntrySelectedBy ListEntry (biçimi) için için SelectionCondition PropertyName öğesinin ListEntry (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `PropertyName` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy ListEntry (biçimi) için için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Bu liste girişi kullanılacak bulunmalıdır koşulu tanımlar.|

## <a name="text-value"></a>Metin değeri

.NET özellik adı belirtin.

## <a name="remarks"></a>Açıklamalar

Seçim koşulu en az bir özellik adı veya bir betik bloğu belirtmelisiniz, ancak ikisini birden belirtemezsiniz. Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).

Bir liste görünümü diğer bileşenler hakkında daha fazla bilgi için bkz. [liste görünümü oluşturma](./creating-a-list-view.md).

## <a name="see-also"></a>Ayrıca bkz:

[Bir liste görünümü oluşturma](./creating-a-list-view.md)

[Verilerinin koşulları tanımlama görüntülenir](./defining-conditions-for-displaying-data.md)

[ListEntry öğesi (biçimi)](./listentry-element-for-listcontrol-format.md)

[SelectionCondition ListEntry (biçimi) için EntrySelectedBy için için ScriptBlock öğesi](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
