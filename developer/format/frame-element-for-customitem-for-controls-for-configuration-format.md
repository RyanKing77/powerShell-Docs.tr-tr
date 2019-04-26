---
title: Çerçeve öğesi için CustomItem denetimleri için yapılandırma (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065572"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Yapılandırma Denetimleri için CustomItem Çerçeve Öğesi (Biçim)

Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) CustomItem öğesinin CustomEntry CustomItem denetimleri için yapılandırma (biçimi) için yapılandırma çerçeve öğesinin denetimleri için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi

## <a name="syntax"></a>Sözdizimi

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `Frame` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|`CustomItem Element`|Gerekli öğe|
|[Denetimler için yapılandırma (biçimi) için bir çerçeve için FirstLineHanging öğesi](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Verilerin ilk satırı, sola kaydırılacak karakterlerinin kaçının tutulacağını belirtir.|
|[Denetimler için yapılandırma (biçimi) için bir çerçeve için FirstLineIndent öğesi](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> İlk veri satırını sağa kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.|
|[Denetimler için yapılandırma (biçimi) için bir çerçeve için LeftIndent öğesi](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Sol kenar boşluğu uzağa veri kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.|
|[Denetimler için yapılandırma (biçimi) için bir çerçeve için RightIndent öğesi](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Sağ kenar boşluğu uzağa veri kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Yapılandırma için denetimleri için CustomEntry için CustomItem öğesi](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Hangi veri denetimi tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar.|

## <a name="remarks"></a>Açıklamalar

Belirtemezsiniz [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) ve [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) aynı öğeleri `Frame` öğesi.

## <a name="see-also"></a>Ayrıca bkz:

[Denetimler için yapılandırma (biçimi) için bir çerçeve için FirstLineHanging öğesi](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[Denetimler için yapılandırma (biçimi) için bir çerçeve için FirstLineIndent öğesi](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[Denetimler için yapılandırma (biçimi) için bir çerçeve için LeftIndent öğesi](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[Denetimler için yapılandırma (biçimi) için bir çerçeve için RightIndent öğesi](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[Yapılandırma için denetimleri için CustomEntry için CustomItem öğesi](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
