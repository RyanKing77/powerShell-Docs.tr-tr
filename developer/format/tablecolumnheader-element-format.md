---
title: TableColumnHeader öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: 15f47c97ac5d55cb76e153af86672b3ffaf176c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848632"
---
# <a name="tablecolumnheader-element-format"></a>TableColumnHeader Öğesi (Biçim)

Etiketi, bir sütunun genişliğini ve hizalamasını tablosunun bir sütunu etiketi tanımlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableHeaders öğesi TableControl (biçimi) için TableHeaders TableColumnHeader öğesinin TableControl (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `TableColumnHeader` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TableControl (biçimi) için TableColumnHeader için etiket öğesi](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Sütun üst kısmında görüntülenen etiketi tanımlar. Hiçbir etiket belirtilirse, değeri satırlarda gösterilen özelliğin adı kullanılır.|
|[TableControl (biçimi) için TableColumnHeader için genişliği öğesi](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|Gerekli öğe.<br /><br /> Sütun genişliğini (karakter cinsinden) belirtir.|
|[TableControl (biçimi) için TableColumbnHeader için hizalama öğesi](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Sütunun etiketi nasıl görüntüleneceğini belirtir. Hizalama yok belirtilirse, etiket sol tarafta hizalanır.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TableHeaders öğesi (biçimi)](./tableheaders-element-format.md)|Tablo görünümü sütunlarını tanımlar.|

## <a name="remarks"></a>Açıklamalar

Tablonun her sütunu için bir üstbilgi belirtin. Hangi sırayla görüntülenen sütunlar `TableColumnHeader` öğeleri tanımlanır.

Bir tablo aynı sayıda olmalıdır `TableColumnHeader` öğeleri olarak `TableRowEntry` öğeleri. Sütun üst bilgisine Tablo üst kısmındaki metni nasıl görüntüleneceğini tanımlar. Satır girişleri tablonun satırlarını hangi verilerin gösterileceğini belirler.

Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [Tablo görünümü](./creating-a-table-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek iki gösterir `TableColumnHeader` öğeleri. İlk öğe etiketini "sütun 1", 16 karakter genişliği sahiptir ve sol tarafta, etiketi hizalanacağını bir sütun tanımlar. İkinci öğe etiketini "Sütun 2", 10 karakter genişliği sahiptir ve sütunu etiketini ortalanır bir sütun tanımlar.

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

[Hizalama öğesi için TableColumnHeader TableContrl (biçimi) için](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Bir tablo görünümü oluşturma](./creating-a-table-view.md)

[TableControl (biçimi) için TableColumnHeader için etiket öğesi](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[TableControl (biçimi) için TableHeaders öğesi](./tableheaders-element-format.md)

[TableControl öğe (biçimi) için TableColumnHeader genişliği](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
