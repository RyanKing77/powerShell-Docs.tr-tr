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
ms.openlocfilehash: 59dfd40b95d5088a711eb89cf101eb31a4b159f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846875"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl TableColumnHeader için Etiket Öğesi (Biçim)

Bir sütunun en üstünde gösterilen etiketi tanımlar. Bu öğe, bir tablo görünümü tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableHeaders öğesi TableControl (biçimi) etiketi öğesinin TableHeaders TableColumnHeader öğesinin TableControl (biçimi) TableColumnHeader TablControl (biçimi) için

## <a name="syntax"></a>Sözdizimi

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `Label` öğesi. Yalnızca bir etiket, her sütun için izin verilir.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TableControl (biçimi) için TableHeaders için TableColumnHeader öğesi](./tablecolumnheader-element-format.md)|Bir etiket, genişliğini ve hizalamasını tablosunun bir sütunu için veri tanımlar.|

## <a name="text-value"></a>Metin Değeri

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
