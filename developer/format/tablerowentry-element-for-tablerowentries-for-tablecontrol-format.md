---
title: TableControl (biçimi) için TableRowEntries için TableRowEntry öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58059857"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a>TableControl (biçimi) için TableRowEntries için TableRowEntry öğesi

Bir tablonun satırında görüntülenen verileri tanımlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi TableControl (biçimi) için TableRowEntries TableRowEntry öğesinin TableControl (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `TableRowEntry` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TableControl (biçimi) için TableRowEntry için EntrySelectedBy öğesi](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Gerekli öğe.<br /><br /> Özellik değerleri satır içinde görüntülenen nesneleri tanımlar.|
|[TableControl (biçimi) için TableRowEntry için TableColumnItems öğesi](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Gerekli öğe.<br /><br /> Betikleri değerleri görüntülenir ve özellikleri tanımlar.|
|[Öğe için TableRowEntry TableControl (biçimi) için kaydır.](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Sütun genişliğini aşıyor metin ve sonraki satırda görüntüleneceğini belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TableControl (biçimi) için TableRowEntries öğesi](./tablerowentries-element-for-tablecontrol-format.md)|Tablonun satırlarını tanımlar.|

## <a name="remarks"></a>Açıklamalar

Bir `TableColumnItems` öğesi ve bir `EntrySelectedBy` öğesi belirtilmelidir.

Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte gösterildiği bir `TableRowEntry` tanımlayan iki özelliklerinin değerlerini görüntüleyen bir satır öğesi [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesne.

```xml
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
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir tablo görünümü oluşturma](./creating-a-table-view.md)

[TableControl (biçimi) için TableRowEntry için EntrySelectedBy öğesi](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl (biçimi) için TableRowEntry için TableColumnItems öğesi](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl (biçimi) için TableRowEntries öğesi](./tablerowentries-element-for-tablecontrol-format.md)

[Öğe için TableRowEntry TableControl (biçimi) için kaydır.](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
