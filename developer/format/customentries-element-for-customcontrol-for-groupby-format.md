---
title: GroupBy (biçimi) için özel denetim için CustomEntries öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066556"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>GroupBy CustomControl için CustomEntries Öğesi (Biçim)

Denetim için tanımları sağlar. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) için özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi

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
|[GroupBy (biçimi) için özel denetim için CustomEntry öğesi](./customentry-element-for-customcontrol-for-groupby-format.md)|Gerekli öğe.<br /><br /> Denetim tanımını sağlar.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[GroupBy (biçimi) için özel denetim öğesi](./customcontrol-element-for-groupby-format.md)|Yeni grubu gösteren özel bir denetimi tanımlar.|

## <a name="remarks"></a>Açıklamalar

Çoğu durumda, tek bir belirtilen sadece bir tanım kontrolünde `CustomEntry` öğesi. Ancak, farklı gruplarını görüntülemek için aynı denetimi kullanmak istiyorsanız birden çok tanım sağlamak mümkündür. Bu gibi durumlarda, tanımladığınız bir `CustomEntry` bir grup için öğesi.

## <a name="see-also"></a>Ayrıca bkz:

[CustomEntry öğesi görünümü (biçimi) için denetimleri için CustomEntries için](./customentry-element-for-customentries-for-controls-for-view-format.md)

[GroupBy (biçimi) için özel denetim öğesi](./customcontrol-element-for-groupby-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
