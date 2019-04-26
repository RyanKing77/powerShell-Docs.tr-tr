---
title: TableControl (biçimi) için TableColumnItems için TableColumnItem öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 159f943f6bfb33c5403b5714380631351523789f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063947"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>TableControl TableColumnItems için TableColumnItem Öğesi (Biçim)

Özellik veya betik değeri satırın sütunda görüntülenen tanımlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi TableControl (biçimi) için TableRowEntries TableRowEntry öğesinin TableControl (biçimi) TableControl (biçimi) için TableColumnItems TableControl (biçimi) TableColumnItem öğesinin TableControlEntry için TableColumnItems öğesi

## <a name="syntax"></a>Sözdizimi

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `TableColumnItem` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[TableControl (biçimi) için TableColumnItem için hizalama öğesi](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Satır bir sütundaki verilerin nasıl görüntüleneceğini tanımlar.|
|[TableControl (biçimi) için TableColumnItem için FormatString öğesi](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|Satırın sütundaki verilerin biçimlendirilmesi için kullanılan biçimi desen belirtir.|
|[TableControl (biçimi) için TableColumnItem için PropertyName öğesi](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Özellik değeri görüntülenen adını belirtir.|
|[TableControl (biçimi) için TableColumnItem için ScriptBlock öğesi](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Değeri bir satır sütununda görüntülenen komut dosyasını belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TableControl (biçimi) için TableControlEntry için TableColumnItems öğesi](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Komut satırında değerleri görüntülenir ve özellikleri tanımlar.|

## <a name="remarks"></a>Açıklamalar

Satırın her sütun bir özelliği bir nesne veya bir betik belirtebilirsiniz. Alt öğe yok belirtilirse, öğeyi bir yer tutucudur ve veri görüntülenir.

Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).

## <a name="example"></a>Örnek

Bu örnek gösterir bir `TableColumnItem` değerini görüntüler öğesi `Status` özelliği [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesne.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Ayrıca bkz:

[Bir tablo görünümü oluşturma](./creating-a-table-view.md)

[TableControl (biçimi) için TableColumnItem için hizalama öğesi](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableColumnItems öğesi (biçimi)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl (biçimi) için TableColumnItem için FormatString öğesi](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableControl (biçimi) için TableColumnItem için PropertyName öğesi](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableControl (biçimi) için TableColumnItem için ScriptBlock öğesi](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
