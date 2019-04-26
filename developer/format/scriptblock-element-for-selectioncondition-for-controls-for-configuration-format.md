---
title: ScriptBlock öğesi için yapılandırma (biçimi) için denetimleri için SelectionCondition | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064433"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a>Yapılandırma Denetimleri için SelectionCondition ScriptBlock Öğesi (Biçim)

Koşul tetikleyen betiği belirtir. Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve tanımı kullanılır. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) EntrySelectedBy öğesinin CustomEntry EntrySelectedBy denetimleri için yapılandırma (biçimi) için yapılandırma (biçimi) SelectionCondition öğesinin denetimleri için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi Denetimler için yapılandırma (biçimi) için SelectionCondition için ScriptBlock öğesi

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
|[İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Kullanılacak ortak denetim tanımı bulunması gereken bir koşulu tanımlar.|

## <a name="text-value"></a>Metin değeri

Yürütülecek betiği belirtin.

## <a name="remarks"></a>Açıklamalar

Seçim koşulu değerlendirmek için bir en az bir betik veya özellik adı belirtmeniz gerekir ancak ikisini birden belirtemezsiniz. Seçimi koşulları nasıl kullanılabileceği hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Ayrıca bkz:

[İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
