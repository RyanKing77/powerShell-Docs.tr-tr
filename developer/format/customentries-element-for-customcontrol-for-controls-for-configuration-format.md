---
title: Yapılandırma (biçimi) için denetimler için özel denetim için CustomEntries öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847029"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>Yapılandırma Denetimleri için CustomControl CustomEntries Öğesi (Biçim)

Tanımlarını bir ortak denetimi sağlar. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomEntries` öğesi. Bir veya daha fazla alt öğeleri belirtmeniz gerekir.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Yapılandırma (biçimi) için denetimler için özel denetim için CustomEntry öğesi](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Bir ortak denetimi tanımını sağlar.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Özel denetim öğesi denetimi için yapılandırma (biçimi)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Bir ortak denetimi tanımlar.|

## <a name="remarks"></a>Açıklamalar

Çoğu durumda, tek bir tanımlı yalnızca bir tanımı kontrolünde `CustomEntry` öğesi. Ancak farklı .NET nesneleri görüntülemek için aynı denetimi kullanmak istiyorsanız birden çok tanım olması mümkündür. Bu gibi durumlarda, tanımladığınız bir `CustomEntry` her nesne veya nesneler için öğesi.

## <a name="see-also"></a>Ayrıca bkz:

[Özel denetim öğesi denetimi için yapılandırma (biçimi)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[Yapılandırma (biçimi) için denetimler için özel denetim için CustomEntry öğesi](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
