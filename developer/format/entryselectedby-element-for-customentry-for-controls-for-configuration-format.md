---
title: İçin yapılandırma (biçimi) için denetimleri için CustomEntry EntrySelectedBy öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059227"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>Yapılandırma Denetimleri için CustomEntry EntrySelectedBy Öğesi (Biçim)

Ortak denetim ya da bu denetim için kullanılacak bulunmalıdır koşul tanımı kullanan .NET türlerini tanımlar. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için CustomEntry denetimleri için yapılandırma (biçimi) için yapılandırma (biçimi) EntrySelectedBy öğesinin denetimler için özel denetim için biçim) CustomEntry öğesi

## <a name="syntax"></a>Sözdizimi

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
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
|[İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Kullanılacak ortak denetim tanımı bulunmalıdır koşulu tanımlar.|
|[İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionSetName öğesi](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Bir ortak denetimi bu tanımı kullanan .NET türleri kümesini belirtir.|
|[TypeName öğesi EntrySelectedBy yapılandırması (biçimi) için denetimleri için](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Ortak denetimi bu tanımı kullanan bir .NET türü belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Yapılandırma (biçimi) için denetimler için özel denetim için CustomEntry öğesi](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Bir ortak denetimi tanımını sağlar.|

## <a name="remarks"></a>Açıklamalar

En azından her tanımı en az bir .NET türü, seçim kümesi veya belirtilen seçim koşulu olmalıdır. Türler, seçimi ayarlar veya belirtebileceğiniz seçimi koşullar sayısı maksimum sınırı yoktur.

## <a name="see-also"></a>Ayrıca bkz:

[İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionSetName öğesi](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Yapılandırma (biçimi) için denetimler için özel denetim için CustomEntry öğesi](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[TypeName öğesi EntrySelectedBy yapılandırması (biçimi) için denetimleri için](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
