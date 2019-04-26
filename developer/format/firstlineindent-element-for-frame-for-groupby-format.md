---
title: GroupBy (biçimi) için bir çerçeve için FirstLineIndent öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33be3b9e-53c8-433f-8c11-c65b0d46744c
caps.latest.revision: 6
ms.openlocfilehash: 9ba6fc1b9924a4b0d5b56ee15290a2293217403c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065861"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a>GroupBy Çerçevesi için FirstLineIndent Öğesi (Biçim)

İlk veri satırını sağa kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi Özel denetim GroupBy (biçimi) CustomItem öğesinin CustomEntry CustomItem GroupBy (biçimi) FirstLineIndent öğesinin GroupBy (biçimi) için çerçeve çerçeve öğesinin GroupBy (biçimi)

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
|[GroupBy (biçimi) için CustomItem için çerçeve öğesi](./frame-element-for-customitem-for-groupby-format.md)|Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar.|

## <a name="text-value"></a>Metin değeri

Verilerin ilk satırı geçirmek istediğiniz karakter sayısını belirtin.

## <a name="remarks"></a>Açıklamalar

Bu öğe belirtilmezse belirtemezsiniz [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) öğesi.

## <a name="see-also"></a>Ayrıca bkz:

[GroupBy (biçimi) için bir çerçeve için FirstLineHanging öğesi](./firstlinehanging-element-for-frame-for-groupby-format.md)

[GroupBy (biçimi) için CustomItem için çerçeve öğesi](./frame-element-for-customitem-for-groupby-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
