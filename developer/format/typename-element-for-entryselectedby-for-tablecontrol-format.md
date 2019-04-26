---
title: TableControl (biçimi) için EntrySelectedBy için TypeName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083969"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a>TableControl EntrySelectedBy için TypeName Öğesi (Biçim)

Tablo görünümü bu girişi kullanan bir .NET türü belirtir. Bir tablo girişi için belirtilebilen türleri sayısı sınırı yoktur.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi (biçimi) TableRowEntry öğesi (biçimi) EntrySelectedBy öğesi (biçimi) TypeName öğesi EntrySelectedBy için TableRowEntry (biçimi) için

## <a name="syntax"></a>Sözdizimi

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `TypeName` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy öğesi (biçimi)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Bu girdi veya kullanılmak üzere bu giriş için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.|

## <a name="text-value"></a>Metin değeri

.NET türü adını belirtin.

## <a name="remarks"></a>Açıklamalar

Her liste girişi, en az bir tür adı, seçim kümesi veya seçim koşulu tanımlanmış olmalıdır.

Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).

## <a name="see-also"></a>Ayrıca bkz:

[Bir tablo görünümü oluşturma](./creating-a-table-view.md)

[EntrySelectedBy öğesi (biçimi)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
