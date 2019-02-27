---
title: GroupBy (biçimi) için CustomEntry için EntrySelectedBy öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851586"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a>GroupBy CustomEntry için EntrySelectedBy Öğesi (Biçim)

Bu denetim tanımı veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) EntrySelectedBy öğesinin CustomEntry GroupBy (biçimi) için özel denetim

## <a name="syntax"></a>Sözdizimi

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `EntrySelectedBy` öğesi. En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir. Kullanabileceğiniz bir alt öğe sayısı maksimum sınırı yoktur.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[GroupBy (biçimi) için EntrySelectedBy için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Bu tanım için kullanılacak bulunmalıdır koşulu tanımlar.|
|[GroupBy (biçimi) için EntrySelectedBy için SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Denetimin bu tanımı kullanan .NET türleri kümesini belirtir.|
|[GroupBy (biçimi) için EntrySelectedBy için TypeName öğesi](./typename-element-for-entryselectedby-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Denetimin bu tanımı kullanan bir .NET türü belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[GroupBy (biçimi) için özel denetim için CustomEntry öğesi](./customentry-element-for-customcontrol-for-groupby-format.md)|Denetim tanımını sağlar.|

## <a name="remarks"></a>Açıklamalar

Seçimi koşullar bulunması gereken bir koşul için kullanılacak tanım, bir nesne belirli bir özelliğine sahip olduğunda gibi veya özel özellik değerini tanımlamak için kullanılır veya komut dosyası değerlendirilen `true`. Seçimi koşullar hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Ayrıca bkz:

[GroupBy (biçimi) için EntrySelectedBy için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[GroupBy (biçimi) için EntrySelectedBy için SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[GroupBy (biçimi) için EntrySelectedBy için TypeName öğesi](./typename-element-for-entryselectedby-for-groupby-format.md)

[CustomEntry öğesi görünümü (biçimi) için denetimleri için CustomEntries için](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
