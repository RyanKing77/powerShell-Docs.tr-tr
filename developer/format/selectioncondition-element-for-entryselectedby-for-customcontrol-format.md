---
title: Özel denetim (biçimi) için EntrySelectedBy için SelectionCondition öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075758"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a>CustomControl EntrySelectedBy için SelectionCondition Öğesi (Biçim)

Bir denetim tanımı kullanılacak bulunması gereken bir koşulu tanımlar. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi görünümü (biçimi) CustomEntries öğesinin CustomEntries için özel denetim için View (Görünüm (biçimi) CustomEntry öğesinin özel denetim Biçimi) CustomItem öğesi görünümü (biçimi) EntrySelectedBy öğesinin CustomEntry EntrySelectedBy Görünüm (biçimi) için özel denetim için View (biçimi) SelectionCondition öğesinin özel denetim için özel denetim için CustomEntry için

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
|[PropertyName öğesi görünümü (biçimi) için özel denetim için SelectionCondition için](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen .NET özelliği belirtir.|
|[ScriptBlock öğesi görünümü (biçimi) için özel denetim için SelectionCondition için](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen betiği belirtir.|
|[SelectionSetName öğesi görünümü (biçimi) için özel denetim için SelectionCondition için](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen .NET türleri kümesini belirtir.|
|[TypeName öğesi görünümü (biçimi) için özel denetim için SelectionCondition için](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen bir .NET türünü belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy öğesi görünümü (biçimi) için özel denetim için CustomEntry için](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Bu denetim tanımı veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.|

## <a name="remarks"></a>Açıklamalar

Bir seçim koşulu tanımlarken, aşağıdaki gereksinimler geçerlidir:

- Seçim koşulu en az bir özellik adı veya bir betik bloğu belirtmelisiniz, ancak ikisini birden belirtemezsiniz.

- Seçim koşulu .NET türleri herhangi bir sayıda belirtebilirsiniz veya seçimi ayarlar, ancak ikisini birden belirtemezsiniz.

Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Ayrıca bkz:

[PropertyName öğesi görünümü (biçimi) için özel denetim için SelectionCondition için](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[ScriptBlock öğesi görünümü (biçimi) için özel denetim için SelectionCondition için](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[SelectionSetName öğesi görünümü (biçimi) için özel denetim için SelectionCondition için](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[TypeName öğesi görünümü (biçimi) için özel denetim için SelectionCondition için](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[EntrySelectedBy öğesi görünümü (biçimi) için özel denetim için CustomEntry için](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
