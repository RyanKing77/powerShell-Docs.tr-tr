---
title: SelectionCondition öğesi EntrySelectedBy ListControl (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: 633204f3b181316761746ea2679910216fb74657
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064110"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a>ListControl EntrySelectedBy için SelectionCondition Öğesi (Biçim)

Bu liste görünümü tanımını kullanılacak bulunmalıdır koşulu tanımlar. Bir liste tanımı için belirtilen seçim koşullar sayısı sınırı yoktur.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi) EntrySelectedBy öğesi SelectionCondition öğesinin ListEntry (biçimi) EntrySelectedBy ListEntry (biçimi) için

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
|[PropertyName öğesi SelectionCondition ListEntry (biçimi) için EntrySelectedBy için için](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen .NET alan özelliği belirtir.|
|[SelectionCondition ListEntry (biçimi) için EntrySelectedBy için için ScriptBlock öğesi](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen betiği belirtir.|
|[SelectionCondition ListEntry (biçimi) için EntrySelectedBy için için SelectionSetName öğesi](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|İsteğe bağlı öğe.<br /><br /> Tetikleme koşulu .NET türleri kümesini belirtir.|
|[TypeName öğesi SelectionCondition ListEntry (biçimi) için EntrySelectedBy için için](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen bir .NET türünü belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy öğesi TableRowEntry (biçimi) için](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Bu tablo girişi kullanıp bu giriş için kullanılacak bulunmalıdır koşul .NET türlerini tanımlar.|

## <a name="remarks"></a>Açıklamalar

lWhen seçim koşulu tanımlıyorsanız, aşağıdaki gereksinimler geçerlidir:

- Seçim koşulu en az bir özellik adı veya bir betik bloğu belirtmelisiniz, ancak ikisini birden belirtemezsiniz.

- Seçim koşulu .NET türleri herhangi bir sayıda belirtebilirsiniz veya seçimi ayarlar, ancak ikisini birden belirtemezsiniz.

Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).

Bir liste görünümü diğer bileşenler hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).

## <a name="see-also"></a>Ayrıca bkz:

[Bir liste görünümü oluşturma](./creating-a-list-view.md)

[Veri görüntülendiğinde koşulları tanımlama](./defining-conditions-for-displaying-data.md)

[ListEntry öğesi (biçimi)](./listentry-element-for-listcontrol-format.md)

[EntrySelectedBy ListEntry (biçimi) için için SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[TypeName öğesi için EntrySelectedBy ListEntry (biçimi) için](http://msdn.microsoft.com/en-us/fcd4daa6-f3fd-43f7-a468-03c582d34533)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
