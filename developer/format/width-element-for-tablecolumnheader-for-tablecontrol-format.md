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
ms.openlocfilehash: a38fcbef457e69e3ea08d25ba3a9843621036f1e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844789"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl TableColumnHeader için Genişlik Öğesi (Biçim)

Bir sütunun genişliğini (karakter cinsinden) tanımlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableHeaders öğesi TableControl (biçimi) genişliği öğesinin TableColumnHeader öğesi TableHeaders TableControl (biçimi) için TableControl (biçimi) için TableColumnHeader

## <a name="syntax"></a>Sözdizimi

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `Width` sütun üst bilgilerini tanımlarken kullanılan öğe.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TableHeaders TbleControl (biçimi) için için TableColumnHeader öğesi](./tablecolumnheader-element-format.md)|Bir etiket, genişliği ve hizalamasını tablosunda bir sütun için verilerin tanımlar.|

## <a name="text-value"></a>Metin Değeri

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
