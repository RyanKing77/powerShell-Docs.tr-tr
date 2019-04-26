---
title: SelectionSetName öğesi görünümü (biçimi) için özel denetim için EntrySelectedBy için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063992"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a>Görünüm CustomControl için EntrySelectedBy SelectionSetName Öğesi (Biçim)

.NET nesnelerinin listesi girişi için bir dizi belirtir. Bir giriş için belirtilen seçim kümeleri sayısı sınırı yoktur.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomEntry öğesinin CustomEntries EntrySelectedBy görünümü (biçimi) için özel denetim için Öğe için CustomEntry SelectionSetName öğesinin EntrySelectedBy CustomEntry (biçimi) için View (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionSetName` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[İçin görünümün (biçimi) CustomEntry EntrySelectedBy öğesi](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Bu özel giriş veya kullanılmak üzere bu giriş için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.|

## <a name="text-value"></a>Metin değeri

Seçimi kümesinin adını belirtin.

## <a name="remarks"></a>Açıklamalar

Her özel denetim girişi, en az bir tür adı, seçim kümesi veya seçim koşulu tanımlanmış olmalıdır.

Seçimi ayarlar, genellikle kullanılan nesnelerin bir grup içinde birden çok görünüm tanımlamak istediğinizde kullanılır. Örneğin, bir tablo görünümü ve aynı nesne kümesini bir liste görünümü oluşturmak isteyebilirsiniz. Seçimi ayarlar tanımlama hakkında daha fazla bilgi için bkz. [tanımlama seçimi](./defining-selection-sets.md).

Bir özel denetim görünüm bileşenleri hakkında daha fazla bilgi için bkz. [özel denetimler oluşturma](./creating-custom-controls.md).

## <a name="see-also"></a>Ayrıca bkz:

[İçin görünümün (biçimi) CustomEntry EntrySelectedBy öğesi](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Özel denetim görünümü](./creating-custom-controls.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
