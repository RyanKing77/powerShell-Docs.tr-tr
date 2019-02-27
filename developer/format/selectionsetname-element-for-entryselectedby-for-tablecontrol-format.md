---
title: TableControl (biçimi) için EntrySelectedBy için SelectionSetName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846882"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a>TableControl EntrySelectedBy için SelectionSetName Öğesi (Biçim)

.NET bir dizi tablo görünümü, bu girdi kullanım türleri belirtir. Bir giriş için belirtilen seçim kümeleri sayısı sınırı yoktur.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi (biçimi) TableRowEntry öğesi (biçimi) EntrySelectedBy öğesi (biçimi) SelectionSetName öğesi EntrySelectedBy TableRowEntry (biçimi) için

## <a name="syntax"></a>Sözdizimi

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy öğesi (biçimi)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Bu girdi veya kullanılmak üzere bu giriş için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.|

## <a name="text-value"></a>Metin Değeri

Seçimi kümesinin adını belirtin.

## <a name="remarks"></a>Açıklamalar

Seçimi ayarlar, genellikle kullanılan nesnelerin bir grup içinde birden çok görünüm tanımlamak istediğinizde kullanılır. Örneğin, bir tablo görünümü ve aynı nesne kümesini bir liste görünümü oluşturmak isteyebilirsiniz. Seçimi ayarlar tanımlama hakkında daha fazla bilgi için bkz. [bir görünüm için nesneleri tanımlayan ayarlar](./defining-selection-sets.md).

Bir seçim için bir giriş ayarlamak belirtirseniz, bir tür adı belirtilemez. Bir .NET türü belirtme hakkında daha fazla bilgi için bkz. [TypeName öğesi EntrySelectedBy TableRowEntry (biçimi) için için](./typename-element-for-entryselectedby-for-tablecontrol-format.md).

Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).

## <a name="see-also"></a>Ayrıca bkz:

[EntrySelectedBy öğesi (biçimi)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Görünüm için nesneleri kümesini tanımlama](./defining-selection-sets.md)

[Bir tablo görünümü oluşturma](./creating-a-table-view.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
