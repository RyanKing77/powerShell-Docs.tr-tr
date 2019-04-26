---
title: TableControl (biçimi) için TableColumnItem için PropertyName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064623"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a>TableControl TableColumnItem için PropertyName Öğesi (Biçim)

Değeri satır sütununda görüntülenen alan özelliği belirtir.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi (biçimi) TableRowEntry öğesi (biçimi) TableColumnItems öğesi (biçimi) TableColumnItem öğesi (biçimi) PropertyName öğesi TableColumnItem (biçimi) için

## <a name="syntax"></a>Sözdizimi

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `PropertyName` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TableColumnItem öğesi (biçimi)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Özellik veya betik değeri satırın sütunda görüntülenen tanımlar.|

## <a name="text-value"></a>Metin değeri

Özellik değeri görüntülenen adını belirtin.

## <a name="remarks"></a>Açıklamalar

Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).

## <a name="example"></a>Örnek

Bu örnek gösterir bir `TableColumnItem` belirten öğesi `Status` özelliği [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesne.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Ayrıca bkz:

[Bir tablo görünümü oluşturma](./creating-a-table-view.md)

[TableColumnItem öğesi (biçimi)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
