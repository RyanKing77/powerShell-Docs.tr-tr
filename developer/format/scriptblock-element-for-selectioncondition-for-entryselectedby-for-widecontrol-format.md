---
title: ScriptBlock öğesi EntrySelectedBy WideControl (biçimi) için için SelectionCondition için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064331"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a>WideControl EntrySelectedBy için SelectionCondition ScriptBlock Öğesi (Biçim)

Koşul tetikleyen betiği belirtir. Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve geniş bir girdi tanımı kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi (biçimi) EntrySelectedBy öğesi SelectionCondition öğesinin WideEntry (biçimi) EntrySelectedBy SelectionCondition EntrySelectedBy WideEntry (biçimi) için için ScriptBlock öğesinin WideEntry (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ScriptBlock` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy WideEntry (biçimi) için için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Bu tanım için kullanılacak bulunmalıdır koşulu tanımlar.|

## <a name="text-value"></a>Metin değeri

Yürütülecek betiği belirtin.

## <a name="remarks"></a>Açıklamalar

Seçim koşulu değerlendirmek için en az bir betik veya özellik adı belirtmeniz gerekir ancak ikisini birden belirtemezsiniz. Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).

Geniş bir görünüm diğer bileşenler hakkında daha fazla bilgi için bkz. [geniş Görünüm](./creating-a-wide-view.md).

## <a name="see-also"></a>Ayrıca bkz:

[Geniş bir görünüm oluşturma](./creating-a-wide-view.md)

[Veri görüntülendiğinde koşulları tanımlama](./defining-conditions-for-displaying-data.md)

[PropertyName öğesi SelectionCondition WideEntry (biçimi) için EntrySelectedBy için için](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[EntrySelectedBy WideEntry (biçimi) için için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
