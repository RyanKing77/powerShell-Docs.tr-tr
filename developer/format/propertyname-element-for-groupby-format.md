---
title: GroupBy (biçimi) için PropertyName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075877"
---
# <a name="propertyname-element-for-groupby-format"></a>GroupBy için PropertyName Öğesi (Biçim)

.NET özelliğinin değeri değiştiğinde yeni bir grup başlatan belirtir.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi görünümü (biçimi) PropertyName öğesinin GroupBy (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `PropertyName` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[GroupBy öğesi görünümü (biçimi)](./groupby-element-for-view-format.md)|.NET nesne grubu nasıl görüntüleneceğini tanımlar.|

## <a name="text-value"></a>Metin değeri

.NET özellik adı belirtin.

## <a name="remarks"></a>Açıklamalar

Bu özelliğin değeri değiştiğinde yeni bir grup Windows PowerShell başlatır.

Bu öğe belirtildiğinde, belirtemezsiniz [ScriptBlock](./scriptblock-element-for-groupby-format.md) yeni bir grup başlatmak için öğesi.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir özellik değeri değiştiğinde yeni bir Grup Başlat gösterilmektedir.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Bu öğe içeren tam bir biçimlendirme dosyası örneği için bkz: [geniş Görünüm (gruplandırma ölçütü)](./wide-view-groupby.md).

## <a name="see-also"></a>Ayrıca bkz:

[GroupBy öğesi görünümü (biçimi)](./groupby-element-for-view-format.md)

[GroupBy (biçimi) için ScriptBlock öğesi](./scriptblock-element-for-groupby-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
