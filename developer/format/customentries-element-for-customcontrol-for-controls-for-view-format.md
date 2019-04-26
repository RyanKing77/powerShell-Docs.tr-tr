---
title: CustomEntries öğesi görünümü (biçimi) için denetimler için özel denetim için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066592"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>Görünüm Denetimleri için CustomControl CustomEntries Öğesi (Biçim)

Denetim için tanımları sağlar. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) denetimleri (biçimi) öğesi denetim öğesi denetimi için CustomEntries öğesi görünümü (biçimi) için denetimleri için özel denetim öğesi görünümü (biçimi) için denetimleri için Görünüm (biçimi) için denetimler için özel denetim

## <a name="syntax"></a>Sözdizimi

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki bölümlerde, öznitelikler, alt ve üst öğeleri açıklayan `CustomEntries` öğesi. Hiçbir belirtilebilir alt öğe sayısı üst sınırı yoktur.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[CustomEntry öğesi görünümü (biçimi) için denetimleri için CustomEntries için](./customentry-element-for-customentries-for-controls-for-view-format.md)|Gerekli öğe.<br /><br /> Denetim tanımını sağlar.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Özel denetim öğesi denetimi için Görünüm (biçimi) için denetimleri](./customcontrol-element-for-control-for-controls-for-view-format.md)|Görünüm tarafından kullanılan denetimini tanımlar.|

## <a name="remarks"></a>Açıklamalar

Çoğu durumda, tek bir belirtilen sadece bir tanım kontrolünde `CustomEntry` öğesi. Ancak, farklı .NET nesneleri görüntülemek için aynı denetimi kullanmak istiyorsanız birden çok tanım sağlamak mümkündür. Bu gibi durumlarda, tanımladığınız bir `CustomEntry` her nesne veya nesneler için öğesi.

## <a name="see-also"></a>Ayrıca bkz:

[CustomEntry öğesi görünümü (biçimi) için denetimleri için CustomEntries için](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Özel denetim öğesi denetimi için Görünüm (biçimi) için denetimleri](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
