---
title: GroupBy (biçimi) için ScriptBlock öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229305"
---
# <a name="scriptblock-element-for-groupby-format"></a>GroupBy için ScriptBlock Öğesi (Biçim)

Yeni bir grup değeri değiştiğinde başlatan betiği belirtir.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi görünümü (biçimi) ScriptBlock öğesinin GroupBy (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ScriptBlock` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[GroupBy öğesi görünümü (biçimi)](./groupby-element-for-view-format.md)|.NET nesne grubu nasıl görüntüleneceğini tanımlar.|

## <a name="text-value"></a>Metin değeri

Yürütülecek betiği belirtin.

## <a name="remarks"></a>Açıklamalar

Bu betiğin değeri değiştiğinde yeni bir grup PowerShell başlatır.

Bu öğe belirtildiğinde, belirtemezsiniz [PropertyName](propertyname-element-for-groupby-format.md) yeni bir grup başlatmak için öğesi.

## <a name="see-also"></a>Ayrıca bkz:

[GroupBy (biçimi) için PropertyName öğesi](propertyname-element-for-groupby-format.md)

[GroupBy öğesi görünümü (biçimi)](groupby-element-for-view-format.md)

[Dosya biçimlendirme bir PowerShell yazma](writing-a-powershell-formatting-file.md)
