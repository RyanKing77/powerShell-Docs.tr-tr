---
title: CustomEntry öğesi görünümü (biçimi) için özel denetim için CustomEntries için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850886"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>Görünüm CustomControl için CustomEntries CustomEntry Öğesi (Biçim)

Özel denetim görünüm tanımını sağlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomEntry öğesinin CustomEntries Görünüm (biçimi) için özel denetim için

## <a name="syntax"></a>Sözdizimi

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomEntry` öğesi. Tanımına göre görüntülenen öğeler belirtmeniz gerekir.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[İçin görünümün (biçimi) CustomEntry EntrySelectedBy öğesi](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Özel denetim görünümü veya bu tanım için kullanılacak bulunmalıdır koşul tanımı kullanan .NET türlerini tanımlar.|
|[İçin görünümün (biçimi) CustomEntry CustomItem öğesi](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Özel denetim tanımı için bir denetimi tanımlar.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CustomEntries öğesi görünümü (biçimi) için özel denetim için](./customentries-element-for-customcontrol-for-view-format.md)|Özel denetim görünüm tanımını sağlar. Özel denetimin görünümü, bir veya daha fazla tanımları belirtmeniz gerekir.|

## <a name="remarks"></a>Açıklamalar

Çoğu durumda, sadece bir tanım her özel denetim görünüm için gereklidir, ancak farklı .NET nesneleri görüntülemek için aynı görünümde kullanmak istiyorsanız birden çok tanım olması mümkündür. Bu gibi durumlarda, her bir nesne veya nesne için ayrı bir tanımı sağlayabilir.

## <a name="see-also"></a>Ayrıca bkz:

[Özel denetim öğesi görünümü (biçimi)](./customcontrol-element-for-view-format.md)

[İçin görünümün (biçimi) CustomEntry CustomItem öğesi](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[İçin görünümün (biçimi) CustomEntry EntrySelectedBy öğesi](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
