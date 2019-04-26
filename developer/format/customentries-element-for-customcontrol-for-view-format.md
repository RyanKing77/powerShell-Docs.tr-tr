---
title: CustomEntries öğesi görünümü (biçimi) için özel denetim için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066524"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>Görünüm CustomControl için CustomEntries Öğesi (Biçim)

Özel denetim görünüm tanımını sağlar. Özel denetimin görünümü, bir veya daha fazla tanımları belirtmeniz gerekir.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) için özel denetim için

## <a name="syntax"></a>Sözdizimi

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomControlEntries` öğesi. Bir veya daha fazla alt öğeleri belirtmeniz gerekir.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[İçin görünümün (biçimi) CustomEntries CustomEntry öğesi](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Gerekli öğe.<br /><br /> Özel denetim görünüm tanımını sağlar.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Özel denetim öğesi görünümü (biçimi)](./customcontrol-element-for-view-format.md)|Gerekli öğe.<br /><br /> Görünüm için bir özel denetim biçimini tanımlar.|

## <a name="remarks"></a>Açıklamalar

Çoğu durumda, tek bir tanımlı yalnızca bir tanımı kontrolünde `CustomEntry` öğesi. Ancak farklı .NET nesneleri görüntülemek için aynı denetimi kullanmak istiyorsanız birden çok tanım olması mümkündür. Bu gibi durumlarda, tanımladığınız bir `CustomEntry` her nesne veya nesneler için öğesi.

## <a name="see-also"></a>Ayrıca bkz:

[Özel denetim öğesi görünümü (biçimi)](./customcontrol-element-for-view-format.md)

[İçin görünümün (biçimi) CustomEntries CustomEntry öğesi](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
