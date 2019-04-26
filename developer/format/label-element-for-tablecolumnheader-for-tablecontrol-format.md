---
title: Etiket öğesi için TableColumnHeader TableControl (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065759"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl TableColumnHeader için Etiket Öğesi (Biçim)

Bir sütunun en üstünde gösterilen etiketi tanımlar. Bu öğe, bir tablo görünümü tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableHeaders öğesi TableControl (biçimi) etiketi öğesinin TableHeaders TableColumnHeader öğesinin TableControl (biçimi) TableControl (biçimi) için TableColumnHeader

## <a name="syntax"></a>Sözdizimi

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `Label` öğesi. Yalnızca bir etiket, her sütun için izin verilir.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TableControl (biçimi) için TableHeaders için TableColumnHeader öğesi](./tablecolumnheader-element-format.md)|Bir etiket, genişliğini ve hizalamasını tablosunun bir sütunu için veri tanımlar.|

## <a name="text-value"></a>Metin değeri

Tablonun sütun üst kısmında görüntülenen metni belirtin. Sütun etiket için kısıtlı hiçbir karakter vardır.

## <a name="remarks"></a>Açıklamalar

Hiçbir etiket belirtilirse, değeri satırlarda gösterilen özelliğin adı kullanılır.

Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).

## <a name="example"></a>Örnek

Bu örnek gösterir bir `TableColumnHeader` olan etiketi olan "Sütun 1" öğesi.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir tablo görünümü oluşturma](./creating-a-table-view.md)

[TableColumnHeader öğesi (biçimi)](./tablecolumnheader-element-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
