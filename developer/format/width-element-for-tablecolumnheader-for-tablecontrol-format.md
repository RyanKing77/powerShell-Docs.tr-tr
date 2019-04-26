---
title: TableControl (biçimi) için TableColumnHeader için genişliği öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083629"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl TableColumnHeader için Genişlik Öğesi (Biçim)

Bir sütunun genişliğini (karakter cinsinden) tanımlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableHeaders öğesi TableControl (biçimi) genişliği öğesinin TableColumnHeader öğesi TableHeaders TableControl (biçimi) için TableControl (biçimi) için TableColumnHeader

## <a name="syntax"></a>Sözdizimi

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `Width` sütun üst bilgilerini tanımlarken kullanılan öğe.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TableControl (biçimi) için TableHeaders için TableColumnHeader öğesi](./tablecolumnheader-element-format.md)|Bir etiket, genişliği ve hizalamasını tablosunda bir sütun için verilerin tanımlar.|

## <a name="text-value"></a>Metin değeri

Tüm mümkün olduğunda sırasında görüntülenen özellik değerlerini uzunluğundan daha büyük bir genişlik (karakter cinsinden) belirtin.

## <a name="remarks"></a>Açıklamalar

Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte gösterildiği bir `TableColumnHeader` genişliğini 16 karakter olan öğe.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir tablo görünümü oluşturma](./creating-a-table-view.md)

[TableControl (biçimi) için TableHeader için TableColumnHeader öğesi](./tablecolumnheader-element-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
