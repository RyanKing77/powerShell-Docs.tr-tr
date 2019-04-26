---
title: SelectionCondition öğesi EntrySelectedBy EnumerableExpansion (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064144"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a>EnumerableExpansion EntrySelectedBy için SelectionCondition Öğesi (Biçim)

Bu tanımın koleksiyon nesnelerini genişletmek için bulunması gereken koşulu tanımlar.

Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi) EnumerableExpansions öğesi (biçimi) EnumerableExpansion öğesi (biçimi) EntrySelectedBy öğesi için EntrySelectedBy SelectionCondition öğesinin EnumerableExpansion (biçimi) EnumerableExpansion (biçimi)

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

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionCondition` öğesi. Tek bir belirtmelisiniz `PropertyName` veya `ScriptBlock` öğesi. `SelectionSetName` Ve `TypeName` öğeler isteğe bağlıdır. Her iki öğe birini belirtebilirsiniz.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[PropertyName öğesi SelectionCondition EnumerableExpansion (biçimi) için EntrySelectedBy için için](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen .NET alan özelliği belirtir.|
|[SelectionCondition EnumerableExpansion (biçimi) için EntrySelectedBy için için ScriptBlock öğesi](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen betiği belirtir.|
|[SelectionCondition EnumerableExpansion (biçimi) için EntrySelectedBy için için SelectionSetName öğesi](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen .NET türleri kümesini belirtir.|
|[TypeName öğesi SelectionCondition EnumerableExpansion (biçimi) için EntrySelectedBy için için](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen bir .NET türünü belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy öğesi EnumerableExpansion (biçimi) için](./entryselectedby-element-for-enumerableexpansion-format.md)|Bu tanımı tarafından hangi .NET koleksiyon nesnelerini genişletilir tanımlar.|

## <a name="remarks"></a>Açıklamalar

Her tanımı en az bir tür adı, seçim kümesi veya seçim koşulu tanımlanmış olması gerekir.

Bir seçim koşulu tanımlarken, aşağıdaki gereksinimler geçerlidir:

- Seçim koşulu en az bir özellik adı veya bir betik bloğu belirtmelisiniz, ancak ikisini birden belirtemezsiniz.

- Seçim koşulu .NET türleri herhangi bir sayıda belirtebilirsiniz veya seçimi ayarlar, ancak ikisini birden belirtemezsiniz.

Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [Diplaying veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).

Geniş bir görünüm diğer bileşenler hakkında daha fazla bilgi için bkz. [geniş Görünüm](./creating-a-wide-view.md).

## <a name="see-also"></a>Ayrıca bkz:

[Veri görüntülendiğinde koşulları tanımlama](./defining-conditions-for-displaying-data.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
