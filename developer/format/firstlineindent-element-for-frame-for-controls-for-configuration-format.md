---
title: Denetimler için yapılandırma (biçimi) için bir çerçeve için FirstLineIndent öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f489720-11f6-4019-940e-07f423d4278d
caps.latest.revision: 6
ms.openlocfilehash: c5b2d971fe1590116f96b024ae8769334768acf2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065997"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a>Yapılandırma Denetimleri için Çerçeve FirstLineIndent Öğesi (Biçim)

İlk veri satırını sağa kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) CustomItem öğesinin CustomEntry CustomItem çerçevesi için yapılandırma (biçimi) FirstLineIndent öğe için denetimler için yapılandırma çerçeve öğesinin denetimleri için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi Denetimler için yapılandırma (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `FirstLineIndent` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Çerçeve öğesi CustomItem yapılandırması (biçimi) için denetimleri için](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar.|

## <a name="text-value"></a>Metin değeri

Verilerin ilk satırı geçirmek istediğiniz karakter sayısını belirtin.

## <a name="remarks"></a>Açıklamalar

Bu öğe belirtilmezse belirtemezsiniz [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) öğesi.

## <a name="see-also"></a>Ayrıca bkz:

[Denetimler için yapılandırma (biçimi) için bir çerçeve için FirstLineHanging öğesi](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[Çerçeve öğesi CustomItem yapılandırması (biçimi) için denetimleri için](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
