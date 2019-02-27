---
title: EntrySelectedBy öğesi görünümü (biçimi) için denetimleri için CustomEntry için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849290"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a>Görünüm Denetimleri için CustomEntry EntrySelectedBy Öğesi (Biçim)

Bu denetim tanımı veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) denetimleri (biçimi) öğesi denetim öğesi denetimi için CustomEntries öğesi görünümü (biçimi) için denetimleri için özel denetim öğesi görünümü (biçimi) için denetimleri için Görünümü (biçimi) CustomEntry öğesinin CustomEntries CustomEntry Görünüm (biçimi) için denetimleri için görüntüleme (biçimi) EntrySelectedBy öğesinin denetimleri için denetimler için özel denetim

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
|[SelectionCondition öğesi görünümü (biçimi) için denetimleri için EntrySelectedBy için](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Bu tanım için kullanılacak bulunmalıdır koşulu tanımlar.|
|[SelectionSetName öğesi görünümü (biçimi) için denetimleri için EntrySelectedBy için](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Denetimin bu tanımı kullanan .NET türleri kümesini belirtir.|
|[TypeName öğesi görünümü (biçimi) için denetimleri için EntrySelectedBy için](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Denetimin bu tanımı kullanan bir .NET türü belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CustomEntry öğesi görünümü (biçimi) için denetimleri için CustomEntries için](./customentry-element-for-customentries-for-controls-for-view-format.md)|Denetim tanımını sağlar.|

## <a name="remarks"></a>Açıklamalar

Seçimi koşullar bulunması gereken bir koşul için kullanılacak tanım, bir nesne belirli bir özelliğine sahip olduğunda gibi veya özel özellik değerini tanımlamak için kullanılır veya komut dosyası değerlendirilen `true`. Seçimi koşullar hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Ayrıca bkz:

[CustomEntry öğesi görünümü (biçimi) için denetimleri için CustomEntries için](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
