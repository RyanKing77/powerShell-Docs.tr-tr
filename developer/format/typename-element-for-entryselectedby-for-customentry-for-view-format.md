---
title: TypeName öğesi görünümü (biçimi) için CustomEntry için EntrySelectedBy için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083986"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a>Görünüm CustomEntry için EntrySelectedBy TypeName Öğesi (Biçim)

Özel denetim görünümün bu tanımı kullanan bir .NET türü belirtir. Bir tanımı için belirtilebilen türleri sayısı sınırı yoktur.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomEntry öğesinin CustomEntries EntrySelectedBy görünümü (biçimi) için özel denetim için Öğe için CustomEntry TypeName öğesinin EntrySelectedBy CustomEntry görünümü (biçimi) için View (biçimi)

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
|[İçin görünümün (biçimi) CustomEntry EntrySelectedBy öğesi](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Bu özel denetimi görünüm tanımını kullanma .NET türleri veya bu tanım için kullanılacak bulunmalıdır koşulu tanımlar.|

## <a name="text-value"></a>Metin değeri

.NET türünün tam adını belirttiğinizden `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Açıklamalar

Her özel denetim görünüm tanımı, en az bir tür adı, seçim kümesi veya seçim koşulu tanımlanmış olması gerekir.

Bir özel denetim görünüm bileşenleri hakkında daha fazla bilgi için bkz. [özel denetimler oluşturma](./creating-custom-controls.md).

## <a name="see-also"></a>Ayrıca bkz:

[Özel denetimler oluşturma](./creating-custom-controls.md)

[İçin görünümün (biçimi) CustomEntry EntrySelectedBy öğesi](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
