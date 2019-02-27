---
title: GroupBy (biçimi) için EntrySelectedBy için SelectionCondition öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846231"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a>GroupBy EntrySelectedBy için SelectionCondition Öğesi (Biçim)

Bir denetim tanımı kullanılacak bulunması gereken bir koşulu tanımlar. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) EntrySelectedBy öğesinin CustomEntry GroupBy (biçimi) SelectionCondition öğesinin EntrySelectedBy GroupBy (biçimi) için özel denetim

## <a name="syntax"></a>Sözdizimi

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionCondition` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[GroupBy (biçimi) için SelectionCondition için PropertyName öğesi](./propertyname-element-for-selectioncondition-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen .NET özelliği belirtir.|
|[GroupBy (biçimi) için SelectionCondition için ScriptBlock öğesi](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen betiği belirtir.|
|[GroupBy (biçimi) için SelectionCondition için SelectionSetName öğesi](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen .NET türleri kümesini belirtir.|
|[GroupBy (biçimi) için SelectionCondition için TypeName öğesi](./typename-element-for-selectioncondition-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen bir .NET türünü belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[GroupBy (biçimi) için CustomEntry için EntrySelectedBy öğesi](./entryselectedby-element-for-customentry-for-groupby-format.md)|Bu denetim tanımı veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.|

## <a name="remarks"></a>Açıklamalar

Bir seçim koşulu tanımlarken, aşağıdaki gereksinimler geçerlidir:

- Seçim koşulu en az bir özellik adı veya bir betik bloğu belirtmelisiniz, ancak ikisini birden belirtemezsiniz.

- Seçim koşulu .NET türleri herhangi bir sayıda belirtebilirsiniz veya seçimi ayarlar, ancak ikisini birden belirtemezsiniz.

Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Ayrıca bkz:

[PropertyName öğesi görünümü (biçimi) için özel denetim için SelectionCondition için](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[ScriptBlock öğesi görünümü (biçimi) için özel denetim için SelectionCondition için](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[SelectionSetName öğesi görünümü (biçimi) için özel denetim için SelectionCondition için](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[GroupBy (biçimi) için SelectionCondition için TypeName öğesi](./typename-element-for-selectioncondition-for-groupby-format.md)

[GroupBy (biçimi) için CustomEntry için EntrySelectedBy öğesi](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
