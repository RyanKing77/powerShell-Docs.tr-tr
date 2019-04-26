---
title: TableControl (biçimi) için EntrySelectedBy için SelectionCondition öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075673"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a>TableControl EntrySelectedBy için SelectionCondition Öğesi (Biçim)

Bu tablo görünümü tanımı için kullanılmak üzere mevcut olmalıdır koşulu tanımlar. Tablo tanımı için belirtilen seçim koşullar sayısı sınırı yoktur.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi (biçimi) TableRowEntry öğesi (biçimi) EntrySelectedBy öğesi TableRowEntry (biçimi) için EntrySelectedBy TableRowEntry (biçimi) için için SelectionCondition öğesi

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

Aşağıdaki bölümlerde, öznitelikleri ve alt öğeleri SelectionCondition öğesinin üst öğesi açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[PropertyName öğesi SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen .NET alan özelliği belirtir.|
|[SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için ScriptBlock öğesi](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen betiği belirtir.|
|[SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için SelectionSetName öğesi](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Tetikleme koşulu .NET türleri kümesini belirtir.|
|[TypeName öğesi SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen bir .NET türünü belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy öğesi TableRowEntry (biçimi) için](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Bu tablo girişi kullanıp bu giriş için kullanılacak bulunmalıdır koşul .NET türlerini tanımlar.|

## <a name="remarks"></a>Açıklamalar

Her liste girişi, en az bir tür adı, seçim kümesi veya seçim koşulu tanımlanmış olmalıdır.

Bir seçim koşulu tanımlarken, aşağıdaki gereksinimler geçerlidir:

- Seçim koşulu en az bir özellik adı veya bir betik bloğu belirtmelisiniz, ancak ikisini birden belirtemezsiniz.

- Seçim koşulu .NET türleri herhangi bir sayıda belirtebilirsiniz veya seçimi ayarlar, ancak ikisini birden belirtemezsiniz.

Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).

Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).

## <a name="see-also"></a>Ayrıca bkz:

[Bir tablo görünümü oluşturma](./creating-a-table-view.md)

[Veri görüntülendiğinde koşulları tanımlama](./defining-conditions-for-displaying-data.md)

[EntrySelectedBy öğesi (biçimi)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[PropertyName öğesi SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için ScriptBlock öğesi](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için SelectionSetName öğesi](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[TypeName öğesi SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Biçimlendirme bir Windows PowerShell yazma ve dosya türleri](./writing-a-powershell-formatting-file.md)
