---
title: GroupBy (biçimi) için etiket öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065419"
---
# <a name="label-element-for-groupby-format"></a>GroupBy için Etiket Öğesi (Biçim)

Yeni bir grup ile karşılaşıldığında görüntülenen etiketi belirtir.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) GroupBy öğesi görünümü (biçimi) etiketi öğesinin GroupBy (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `Label` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[GroupBy öğesi görünümü (biçimi)](./groupby-element-for-view-format.md)|Yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlar.|

## <a name="text-value"></a>Metin değeri

Windows PowerShell bir yeni özellik veya komut dosyası değerini karşılaştığında görüntülenen metni belirtin.

## <a name="remarks"></a>Açıklamalar

Bu öğe tarafından belirtilen metin ek olarak, Windows PowerShell grubu başlayıp önce ve sonra grubu boş bir satır ekler. yeni değeri görüntüler.

## <a name="example"></a>Örnek

Aşağıdaki örnek yeni bir Grup etiketi gösterilir. Görüntülenen etiket şuna benzer şekilde görünür: `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Bu öğe içeren tam bir biçimlendirme dosyası örneği için bkz: [geniş Görünüm (gruplandırma ölçütü)](./wide-view-groupby.md).

## <a name="see-also"></a>Ayrıca bkz:

[GroupBy öğesi görünümü (biçimi)](./groupby-element-for-view-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
