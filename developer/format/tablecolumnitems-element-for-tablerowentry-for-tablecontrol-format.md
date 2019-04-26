---
title: TableControl (biçimi) için TableRowEntry için TableColumnItems öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075401"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a>TableControl TableRowEntry için TableColumnItems Öğesi (Biçim)

Betikleri değerleri bir satır görüntülenir ve özellikleri tanımlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi TableControl (biçimi) için TableRowEntries TableRowEntry öğesinin TableControl (biçimi) TableControl (biçimi) için TableControlEntry için TableColumnItems öğesi

## <a name="syntax"></a>Sözdizimi

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `TableColumnItems` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[TableControl (biçimi) için TableColumnItems için TableColumnItem öğesi](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Gerekli öğe.<br /><br /> Komut satırının sütundaki değeri görüntülenir ve özelliği tanımlar.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TableControl (biçimi) için TableRowEntries için TableRowEntry öğesi](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Bir tablonun satırında görüntülenen verileri tanımlar.|

## <a name="remarks"></a>Açıklamalar

A `TableColumnItem` öğesi satırın her sütun için gereklidir. İlk girişi, ilk sütunda, ikinci sütun ve benzeri ikinci girdi görüntülenir.

Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte gösterildiği bir `TableColumnItems` üç özelliklerini tanımlayan öğe [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesne.

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a>Ayrıca bkz:

[Bir tablo görünümü oluşturma](./creating-a-table-view.md)

[TableColumnItem öğesi (biçimi)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[TableRowEntry öğesi (biçimi)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
