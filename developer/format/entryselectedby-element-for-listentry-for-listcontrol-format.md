---
title: EntrySelectedBy öğesi ListEntry ListControl (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054952"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>ListControl ListEntry için EntrySelectedBy Öğesi (Biçim)

Bu liste görünüm tanımını kullanma .NET türleri veya bu tanım için kullanılacak bulunmalıdır koşulu tanımlar. Çoğu durumda, yalnızca bir tanımı bir liste görünümü için gereklidir. Ancak, farklı nesneler için farklı veri görüntülemek için aynı liste görünümü kullanmak istiyorsanız, liste görünümü için birden çok tanım sağlayabilirsiniz.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi ListControl (biçimi) EntrySelectedBy öğesinin ListEntry ListEntry öğesinin ListControl (biçimi) ListEntry ListControl (biçimi) için

## <a name="syntax"></a>Sözdizimi

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `EntrySelectedBy` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy ListControl (biçimi) için için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Bu liste görünümü tanımını kullanılacak bulunmalıdır koşulu tanımlar.|
|[EntrySelectedBy ListControl (biçimi) için için SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Bu liste görünüm tanımını kullanma .NET türleri kümesini belirtir.|
|[TypeName öğesi için EntrySelectedBy ListControl (biçimi) için](./typename-element-for-entryselectedby-for-listcontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Bu liste görünüm tanımı kullanan bir .NET türü belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ListEntry öğesi ListControl (biçimi) için](./listentry-element-for-listcontrol-format.md)|Satırları listesinin nasıl görüntüleneceğini tanımlar.|

## <a name="remarks"></a>Açıklamalar

En az bir türü, seçim kümesi veya bir liste görünüm tanımı için seçim koşulu belirtmeniz gerekir. Kullanabileceğiniz bir alt öğe sayısı maksimum sınırı yoktur.

Seçimi koşullar bir nesne belirli bir özelliğine sahip olduğunda gibi kullanılacak tanımı için bulunması gereken bir koşul tanımlamak için kullanılır veya bir özel özellik değerini veya betik değerlendiren `true`. Seçimi koşullar hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).

Bir liste görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, kendi .NET türü adını kullanarak bir liste görünümü nesneleri tanımlamak gösterilmektedir.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>Ayrıca bkz:

[ListEntry öğesi ListControl (biçimi) için](./listentry-element-for-listcontrol-format.md)

[EntrySelectedBy ListControl (biçimi) için için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[EntrySelectedBy ListControl (biçimi) için için SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[TypeName öğesi için EntrySelectedBy ListControl (biçimi) için](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[Bir liste görünümü oluşturma](./creating-a-list-view.md)

[Veri görüntülendiğinde koşulları tanımlama](./defining-conditions-for-displaying-data.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
