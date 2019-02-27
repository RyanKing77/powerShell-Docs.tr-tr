---
title: TableHeaders öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847428"
---
# <a name="tableheaders-element-format"></a>TableHeaders Öğesi (Biçim)

Üstbilgileri için bir tablonun sütunlarını tanımlar.

TableControl (biçimi) için ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableHeaders öğesi

## <a name="syntax"></a>Sözdizimi

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki bölümlerde, öznitelikler, alt ve üst öğeleri açıklayan `TableHeaders` öğesi. Görüntülenecek olan nesnenin her bir özellik için bir alt öğesi olmalıdır. Sütun üst bilgisini, alt öğeler belirttiğiniz sırada görüntülenir.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TableColumnHeader öğesi (biçimi)](./tablecolumnheader-element-format.md)|İsteğe bağlı öğe.<br /><br /> Etiket, genişliğini ve Tablo görünümüne içeren bir sütun için verilerin hizalama tanımlar.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TableControl öğesi (biçimi)](./tablecontrol-element-format.md)|Bir görünüm için bir tablo biçiminde tanımlar.|

## <a name="remarks"></a>Açıklamalar

Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).

## <a name="example"></a>Örnek

Bu örnek gösterir bir `TableHeaders` tanımlayan iki sütun üst öğe.

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
  <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir tablo görünümü oluşturma](./creating-a-table-view.md)

[TableColumnHeader öğesi (biçimi)](./tablecolumnheader-element-format.md)

[TableControl öğesi (biçimi)](./tablecontrol-element-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
