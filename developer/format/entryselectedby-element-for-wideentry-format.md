---
title: EntrySelectedBy öğesi WideEntry (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066184"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>WideEntry için EntrySelectedBy Öğesi (Biçim)

Geniş bir görünüm veya bu tanım için kullanılacak bulunmalıdır koşul bu tanımı kullanan .NET türlerini tanımlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi (biçimi) EntrySelectedBy öğesi WideEntry (biçimi) için

## <a name="syntax"></a>Sözdizimi

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `EntrySelectedBy` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy WideEntry (biçimi) için için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Bu geniş görünüm tanımı kullanılmak üzere mevcut olmalıdır koşulu tanımlar.|
|[EntrySelectedBy WideEntry (biçimi) için için SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Bu geniş görünüm tanımını kullanma .NET türleri kümesini belirtir.|
|[TypeName öğesi için EntrySelectedBy WideEntry (biçimi) için](./typename-element-for-entryselectedby-for-wideentry-format.md)|İsteğe bağlı öğe.<br /><br /> Bu geniş görünüm tanımı kullanan bir .NET türü belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[WideEntry öğesi (biçimi)](./wideentry-element-for-widecontrol-format.md)|Geniş bir görünüm tanımını sağlar.|

## <a name="remarks"></a>Açıklamalar

En az bir türü, seçim kümesi veya geniş görünüm tanımı için seçim koşulu belirtmeniz gerekir. Kullanabileceğiniz bir alt öğe sayısı maksimum sınırı yoktur.

Seçimi koşullar bir nesne belirli bir özelliğine sahip olduğunda gibi kullanılacak tanımı için bulunması gereken bir koşul tanımlamak için kullanılır veya bir özel özellik değerini veya komut dosyası değerini değerlendiren `true`. Seçimi koşullar hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).

Geniş bir görünüm diğer bileşenler hakkında daha fazla bilgi için bkz. [geniş bir görünüm oluşturma](./creating-a-wide-view.md).

## <a name="see-also"></a>Ayrıca bkz:

[WideEntry öğesi (biçimi)](./wideentry-element-for-widecontrol-format.md)

[EntrySelectedBy WideEntry (biçimi) için için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[EntrySelectedBy WideEntry (biçimi) için için SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[TypeName öğesi için EntrySelectedBy WideEntry (biçimi) için](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Geniş bir görünüm oluşturma](./creating-a-wide-view.md)

[Verileri görüntülemek için koşulları tanımlama](./defining-conditions-for-displaying-data.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
