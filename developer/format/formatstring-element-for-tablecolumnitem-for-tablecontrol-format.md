---
title: TableControl (biçimi) için TableColumnItem için FormatString öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065646"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a>TableControl TableColumnItem için FormatString Öğesi (Biçim)

Tablo özelliği veya komut dosyası değerini nasıl görüntüleneceğini tanımlayan bir biçim desenini belirtir.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi (biçimi) TableRowEntry öğesi (biçimi) TableColumnItems öğesi (biçimi) TableColumnItem öğesi (biçimi) TableColumnItem (biçimi) için FormatString öğesi

## <a name="syntax"></a>Sözdizimi

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `FormatString` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TableColumnItem öğesi (biçimi)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Özellik veya betik değeri satırın sütunda görüntülenen tanımlar.|

## <a name="text-value"></a>Metin değeri

Verilerin biçimlendirilmesi için kullanılan desen belirtin. Örneğin, bu düzen türü herhangi bir özelliği değerini biçimlendirmek için kullanılabilir [System.Timespan](/dotnet/api/System.TimeSpan): {0: aaa} {0} {0:HH}: {0:mm}.

## <a name="remarks"></a>Açıklamalar

Tablo görünümleri, liste görünümleri, geniş görünümleri veya özel görünümlerini oluşturma biçim dizeleri kullanılabilir. Bir görünümü'nde görüntülenen bir değeri biçimlendirme hakkında daha fazla bilgi için bkz. [görüntülenen verileri biçimlendirme](./formatting-displayed-data.md).

Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [Tablo görünümü](./creating-a-table-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir biçimlendirme dizesi değerini tanımlamak gösterilmektedir `StartTime` özelliği.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir tablo görünümü oluşturma](./creating-a-table-view.md)

[Görüntülenen veriler biçimlendirme](./formatting-displayed-data.md)

[TableColumnItem öğesi (biçimi)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
