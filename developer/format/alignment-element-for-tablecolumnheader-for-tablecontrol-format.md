---
title: TableControl (biçimi) için TableColumnHeader için hizalama öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845244"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl TableColumnHeader için Hizalama Öğesi (Biçim)

Sütun üst bilgisindeki verilerin nasıl görüntüleneceğini tanımlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableHeaders öğesi (biçimi) TableColumnHeader öğesi (biçimi) hizalama öğesi TableColumnHeader (biçimi) için

## <a name="syntax"></a>Sözdizimi

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `Alignment` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TableColumnHeader öğesi (biçimi)](./tablecolumnheader-element-format.md)|Bir etiket, genişliğini ve hizalamasını tablosunun bir sütunu için veri tanımlar.|

## <a name="text-value"></a>Metin Değeri

Aşağıdaki değerlerden birini belirtin. Bu değerler büyük küçük harfe duyarlı değildir.

Bu öğe belirtilmemişse, sol sütundaki verilerin görüntülenme sola hizalanır. Bu varsayılan değerdir.

Sağa hizalar, sağdaki sütundaki veriler görüntülenir.

Merkezi merkezleri sütunda görüntülenen veri.

## <a name="remarks"></a>Açıklamalar

Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).

## <a name="example"></a>Örnek

Bu örnek gösterir bir `TableColumnHeader` öğesi verisini, sol taraftaki hizalanır.

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
