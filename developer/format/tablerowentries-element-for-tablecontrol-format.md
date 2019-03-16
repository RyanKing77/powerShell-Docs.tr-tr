---
title: TableControl (biçimi) için TableRowEntries öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055742"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a>TableControl için TableRowEntries Öğesi (Biçim)

Tablonun satırlarını tanımlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi TableControl (biçimi) için

## <a name="syntax"></a>Sözdizimi

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `TableRowEntries` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TableControl (biçimi) için TableRowEntries için TableRowEntry öğesi](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Gerekli öğe.<br /><br /> Bir tablonun satırında görüntülenen verileri tanımlar.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TableControl öğesi (biçimi)](./tablecontrol-element-format.md)|Bir görünüm için bir tablo biçiminde tanımlar.|

## <a name="remarks"></a>Açıklamalar

Bir veya daha fazla belirtmelisiniz `TableRowEntry` Tablo görünümü için öğeleri. En fazla sınırsız sayıda `TableRowEntry` eklenebilir öğeleri ve bunların sırası önemlidir.

Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte gösterildiği bir `TableRowEntries` tanımlayan iki özelliklerinin değerlerini görüntüleyen bir satır öğesi [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesne.

```xml
<TableRowEntries>
  <TableRowEntry>
    <EntrySelectedBy>
      <TypeName>System.Diagnostics.Process</TypeName>
    </EntrySelectedBy>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName> Property for first column</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName> Property for second column</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>

```

## <a name="see-also"></a>Ayrıca bkz:

[Bir tablo görünümü oluşturma](./creating-a-table-view.md)

[TableControl öğesi (biçimi)](./tablecontrol-element-format.md)

[TableRowEntry öğesi (biçimi)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
