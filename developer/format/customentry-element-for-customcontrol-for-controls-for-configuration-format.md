---
title: Yapılandırma (biçimi) için denetimler için özel denetim için CustomEntry öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849479"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>Yapılandırma Denetimleri için CustomControl CustomEntry Öğesi (Biçim)

Bir ortak denetimi tanımını sağlar. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi

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
|[İçin yapılandırma (biçimi) için denetimleri için CustomEntry EntrySelectedBy öğesi](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Ortak denetim ya da bu denetim için kullanılacak bulunmalıdır koşul tanımı kullanan .NET türlerini tanımlar.|
|[Yapılandırma için denetimleri için CustomEntry için CustomItem öğesi](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Gerekli öğe.<br /><br /> Hangi veri denetimi tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Yapılandırma (biçimi) için özel denetim için CustomEntries öğesi](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|Tanımları ortak denetimi sağlar.|

## <a name="remarks"></a>Açıklamalar

Çoğu durumda, yalnızca bir tanımı için ortak her özel denetimi gereklidir, ancak farklı .NET nesneleri görüntülemek için aynı denetimi kullanmak istiyorsanız birden çok tanım olması mümkündür. Bu gibi durumlarda, her bir nesne veya nesne için ayrı bir tanımı sağlayabilir.

## <a name="see-also"></a>Ayrıca bkz:

[Yapılandırma (biçimi) için özel denetim için CustomEntries öğesi](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[Yapılandırma için denetimleri için CustomEntry için CustomItem öğesi](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
