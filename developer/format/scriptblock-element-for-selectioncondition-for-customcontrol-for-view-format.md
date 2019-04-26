---
title: ScriptBlock öğesi görünümü (biçimi) için özel denetim için SelectionCondition için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064569"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a>Görünüm CustomControl için SelectionCondition ScriptBlock Öğesi (Biçim)

Koşul tetikleyen betiği belirtir. Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve tanımı kullanılır. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi görünümü (biçimi) CustomEntries öğesinin CustomEntries için özel denetim için View (Görünüm (biçimi) CustomEntry öğesinin özel denetim Biçimi) CustomItem öğesi görünümü (biçimi) SelectionCondition öğesinin EntrySelectedBy SelectionCondition Görünüm (biçimi) için özel denetim için View (biçimi) ScriptBlock öğesinin özel denetim için özel denetim için CustomEntry için

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
|[SelectionCondition öğesi görünümü (biçimi) için özel denetim için EntrySelectedBy için](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Kullanılacak denetimi tanımı bulunması gereken bir koşulu tanımlar.|

## <a name="text-value"></a>Metin değeri

Yürütülecek betiği belirtin.

## <a name="remarks"></a>Açıklamalar

Seçim koşulu değerlendirmek için bir en az bir betik veya özellik adı belirtmeniz gerekir ancak ikisini birden belirtemezsiniz. Seçimi koşulları nasıl kullanılabileceği hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Ayrıca bkz:

[SelectionCondition öğesi görünümü (biçimi) için özel denetim için EntrySelectedBy için](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
