---
title: GroupBy (biçimi) için bir çerçeve için FirstLineHanging öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846546"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a>GroupBy Çerçevesi için FirstLineHanging Öğesi (Biçim)

Verilerin ilk satırı, sola kaydırılacak karakterlerinin kaçının tutulacağını belirtir. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi Özel denetim GroupBy (biçimi) CustomItem öğesinin CustomEntry CustomItem GroupBy (biçimi) FirstLineHanging öğesinin GroupBy (biçimi) için çerçeve çerçeve öğesinin GroupBy (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `FirstLineHanging` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[GroupBy (biçimi) için CustomItem için çerçeve öğesi](./frame-element-for-customitem-for-groupby-format.md)|Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar.|

## <a name="text-value"></a>Metin Değeri

Verilerin ilk satırı geçirmek istediğiniz karakter sayısını belirtin.

## <a name="remarks"></a>Açıklamalar

Bu öğe belirtilmezse belirtemezsiniz [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) öğesi.

## <a name="see-also"></a>Ayrıca bkz:

[GroupBy (biçimi) için bir çerçeve için FirstLineIndent öğesi](./firstlineindent-element-for-frame-for-groupby-format.md)

[GroupBy (biçimi) için CustomItem için çerçeve öğesi](./frame-element-for-customitem-for-groupby-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
