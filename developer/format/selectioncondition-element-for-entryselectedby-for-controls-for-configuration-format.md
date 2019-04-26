---
title: İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075775"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>Yapılandırma Denetimleri için EntrySelectedBy SelectionCondition Öğesi (Biçim)

Kullanılacak ortak bir denetim tanımı için bulunması gereken bir koşulu tanımlar. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) denetimleri öğesinin yapılandırma (biçimi) denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğe için denetimler için özel denetim için denetimleri için Yapılandırma (biçimi) EntrySelectedBy öğesinin CustomEntry EntrySelectedBy CustomEntry için için yapılandırma (biçimi) SelectionCondition öğesinin denetimleri için denetimler için özel denetim için yapılandırma (biçimi) CustomEntry öğesi Yapılandırma (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionCondition` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[İçin yapılandırma (biçimi) için denetimleri için SelectionCondition PropertyName öğesi](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen .NET özelliği belirtir.|
|[Denetimler için yapılandırma (biçimi) için SelectionCondition için ScriptBlock öğesi](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen betiği belirtir.|
|[İçin yapılandırma (biçimi) için denetimleri için SelectionCondition SelectionSetName öğesi](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen .NET türleri kümesini belirtir.|
|[TypeName öğesi SelectionCondition yapılandırması (biçimi) için denetimleri için](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen bir .NET türünü belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[İçin yapılandırma (biçimi) için denetimleri için CustomEntry EntrySelectedBy öğesi](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Bu giriş ortak denetim tanımının kullanan .NET türlerini tanımlar.|

## <a name="remarks"></a>Açıklamalar

Aşağıdaki yönergeler, bir seçim koşulu tanımlarken gelmelidir:

- Seçim koşulu en az bir özellik adı veya bir betik bloğu belirtmelisiniz, ancak ikisini birden belirtemezsiniz.

- Seçim koşulu .NET türleri herhangi bir sayıda belirtebilirsiniz veya seçimi ayarlar, ancak ikisini birden belirtemezsiniz.

Seçimi koşulları nasıl kullanılabileceği hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Ayrıca bkz:

[İçin yapılandırma (biçimi) için denetimleri için SelectionCondition PropertyName öğesi](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Denetimler için yapılandırma (biçimi) için SelectionCondition için ScriptBlock öğesi](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[İçin yapılandırma (biçimi) için denetimleri için SelectionCondition SelectionSetName öğesi](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[TypeName öğesi SelectionCondition yapılandırması (biçimi) için denetimleri için](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[İçin yapılandırma (biçimi) için denetimleri için CustomEntry EntrySelectedBy öğesi](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Biçimlendirme bir Windows PowerShell yazma ve dosya türleri](./writing-a-powershell-formatting-file.md)
