---
title: PropertyName öğesi için yapılandırma (biçimi) için denetimleri için SelectionCondition | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064736"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a>Yapılandırma Denetimleri için SelectionCondition PropertyName Öğesi (Biçim)

Koşul tetikleyen .NET alan özelliği belirtir. Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve giriş kullanılır. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) EntrySelectedBy öğesinin CustomEntry EntrySelectedBy için yapılandırma (CustomEntry için yapılandırma (biçimi) SelectionCondition öğesinin denetimleri için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi EntrySelectedBy ListEntry (biçimi) için için SelectionCondition için PropertyName öğesi biçimi)

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
|[İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Kullanılacak ortak bir denetim tanımı için bulunması gereken bir koşulu tanımlar.|

## <a name="text-value"></a>Metin değeri

.NET özellik adı belirtin.

## <a name="remarks"></a>Açıklamalar

Seçim koşulu en az bir özellik adı veya komut dosyasını belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz. Seçimi koşulları nasıl kullanılabileceği hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Ayrıca bkz:

[İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
