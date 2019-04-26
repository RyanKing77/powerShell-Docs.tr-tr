---
title: SelectionCondition öğesi görünümü (biçimi) için denetimleri için EntrySelectedBy için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064253"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>Görünüm Denetimleri için EntrySelectedBy SelectionCondition Öğesi (Biçim)

Kullanılacak denetimi tanımı bulunması gereken bir koşulu tanımlar. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) denetimleri (biçimi) öğesi denetim öğesi denetimi için CustomEntries öğesi görünümü (biçimi) için denetimleri için özel denetim öğesi görünümü (biçimi) için denetimleri için Görünümü (biçimi) CustomEntry öğesinin CustomEntries CustomEntry EntrySelectedBy denetimleri için View (Görünüm (biçimi) SelectionCondition öğesinin denetimleri için görüntüleme (biçimi) EntrySelectedBy öğesinin denetimleri için denetimler için özel denetim Biçimi)

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
|[PropertyName öğesi görünümü (biçimi) için denetimleri için SelectionCondition için](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen .NET özelliği belirtir.|
|[ScriptBlock öğesi görünümü (biçimi) için denetimleri için SelectionCondition için](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen betiği belirtir.|
|[SelectionSetName öğesi görünümü (biçimi) için denetimleri için SelectionCondition için](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen .NET türleri kümesini belirtir.|
|[TypeName öğesi görünümü (biçimi) için denetimleri için SelectionCondition için](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen bir .NET türünü belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy öğesi görünümü (biçimi) için denetimleri için CustomEntry için](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Bu denetim tanımı veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.|

## <a name="remarks"></a>Açıklamalar

Bir seçim koşulu tanımlarken, aşağıdaki gereksinimler geçerlidir:

- Seçim koşulu en az bir özellik adı veya bir betik bloğu belirtmelisiniz, ancak ikisini birden belirtemezsiniz.

- Seçim koşulu .NET türleri herhangi bir sayıda belirtebilirsiniz veya seçimi ayarlar, ancak ikisini birden belirtemezsiniz.

Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Ayrıca bkz:

[PropertyName öğesi görünümü (biçimi) için denetimleri için SelectionCondition için](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[ScriptBlock öğesi görünümü (biçimi) için denetimleri için SelectionCondition için](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[SelectionSetName öğesi görünümü (biçimi) için denetimleri için SelectionCondition için](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[TypeName öğesi görünümü (biçimi) için denetimleri için SelectionCondition için](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[EntrySelectedBy öğesi görünümü (biçimi) için denetimleri için CustomEntry için](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
