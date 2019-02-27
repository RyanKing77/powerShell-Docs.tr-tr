---
title: TypeName öğesi EntrySelectedBy ListControl (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 3f0c0ba1fe85d70557e67a30b3a9a59a33043475
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846889"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a>ListControl EntrySelectedBy için TypeName Öğesi (Biçim)

Bu giriş liste görünümünün kullanan bir .NET türü belirtir. Bir liste girişi için belirtilebilen türleri sayısı sınırı yoktur.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi) EntrySelectedBy öğesi TypeName öğesinin ListEntry (biçimi) EntrySelectedBy ListControl (biçimi) için

## <a name="syntax"></a>Sözdizimi

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `TypeName` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy öğesi ListEntry (biçimi) için](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Bu liste girişi kullanıp bu giriş için kullanılacak bulunmalıdır koşul .NET türlerini tanımlar.|

## <a name="text-value"></a>Metin Değeri

.NET türünün tam adını belirttiğinizden `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Açıklamalar

Her liste girişi, en az bir tür adı, seçim kümesi veya seçim koşulu tanımlanmış olmalıdır.

Bu öğe listesi görünümü'nde nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [liste görünümü](./creating-a-list-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir liste görünümü için bir giriş ayarlamak seçim belirtmek gösterilmektedir.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir liste görünümü oluşturma](./creating-a-list-view.md)

[EntrySelectedBy öğesi ListEntry (biçimi) için](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[EnrtySelectedBy ListEntry (biçimi) için için SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
