---
title: TableControl (biçimi) için TableRowEntry için EntrySelectedBy öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066167"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a>TableControl TableRowEntry için EntrySelectedBy Öğesi (Biçim)

Tablo görünümü veya bu tanım için kullanılacak bulunmalıdır koşul bu tanımı kullanan .NET türlerini tanımlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi (biçimi) TableRowEntry öğesi (biçimi) EntrySelectedBy öğesi (biçimi)

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
|[TableControl (biçimi) için EntrySelectedBy için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Bu tablo görünümü tanımını kullanılacak bulunmalıdır koşulu tanımlar.|
|[TableControl (biçimi) için EntrySelectedBy için SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Bu tabloda görünüm tanımını kullanma .NET türleri kümesini belirtir.|
|[TableControl (biçimi) için EntrySelectedBy için TypeName öğesi](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Bu tablo görünümü tanımını kullanan bir .NET türü belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TableControl (biçimi) için TableRowEntry öğesi](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Bir tablonun satırında görüntülenen verileri tanımlar.|

## <a name="remarks"></a>Açıklamalar

En az bir türü, seçim kümesi veya bir tablo görünümü tanımını seçim koşulu belirtmeniz gerekir. Kullanabileceğiniz bir alt öğe sayısı maksimum sınırı yoktur.

Seçimi koşullar bir nesne belirli bir özelliğine sahip olduğunda gibi kullanılacak tanımı için bulunması gereken bir koşul tanımlamak için kullanılır veya bir özel özellik değerini veya betik değerlendiren `true`. Seçimi koşullar hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).

Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte gösterildiği bir `TableRowEntry` özelliklerini görüntülemek için kullanılan öğe [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesne.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir tablo görünümü oluşturma](./creating-a-table-view.md)

[TableControl (biçimi) için EntrySelectedBy için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[TableControl (biçimi) için EntrySelectedBy için SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[TableControl (biçimi) için TableRowEntry öğesi](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[TableControl (biçimi) için EntrySelectedBy için TypeName öğesi](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
