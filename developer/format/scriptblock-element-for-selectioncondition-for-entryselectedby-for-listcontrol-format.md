---
title: ScriptBlock öğesi SelectionCondition EntrySelectedBy ListControl (biçimi) için için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: fd708473d04a76bcf6cf3a8f8278e1d15fb9addf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848674"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>ListControl EntrySelectedBy için SelectionCondition ScriptBlock Öğesi (Biçim)

Koşul tetikleyen betiği belirtir. Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve liste girdisini kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi) EntrySelectedBy öğesi SelectionCondition öğesinin ListEntry (biçimi) EntrySelectedBy SelectionCondition EntrySelectedBy ListEntry (biçimi) için için ScriptBlock öğesinin ListEntry (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ScriptBlock` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy ListEntry (biçimi) için için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Bu liste girişi kullanılacak bulunmalıdır koşulu tanımlar.|

## <a name="text-value"></a>Metin Değeri

Yürütülecek betiği belirtin.

## <a name="remarks"></a>Açıklamalar

Seçim koşulu değerlendirmek için bir en az bir betik veya özellik adı belirtmeniz gerekir ancak ikisini birden belirtemezsiniz. (Seçimi koşulları nasıl kullanılabileceği hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).)

Bir liste görünümü diğer bileşenler hakkında daha fazla bilgi için bkz. [liste görünümü](./creating-a-list-view.md).

## <a name="see-also"></a>Ayrıca bkz:

[ListEntry öğesi (biçimi)](./listentry-element-for-listcontrol-format.md)

[PropertyName öğesi SelectionCondition ListEntry (biçimi) için EmtrySelectedBy için için](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[EntrySelectedBy ListEntry (biçimi) için için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Liste Görünümü](./creating-a-list-view.md)

[Bir görünümü girişi veya öğeyi kullanıldığında koşulları tanımlama](./defining-conditions-for-displaying-data.md)

[Biçimlendirme bir Windows PowerShell yazma ve dosya türleri](./writing-a-powershell-formatting-file.md)
