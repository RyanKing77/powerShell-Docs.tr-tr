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
ms.openlocfilehash: f2f6b9af7740b1231881294c2f32bf97b5a1568b
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054434"
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

## <a name="text-value"></a>Metin Değeri

Yürütülecek betiği belirtin.

## <a name="remarks"></a>Açıklamalar

Bu betiğin değeri değiştiğinde yeni bir grup Windows PowerShell başlatır.

Bu öğe belirtildiğinde, belirtemezsiniz [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) yeni bir grup başlatmak için öğesi.

## <a name="see-also"></a>Ayrıca bkz:

[GroupBy (biçimi) için PropertyName öğesi](./propertyname-element-for-groupby-format.md)

[GroupBy öğesi görünümü (biçimi)](./groupby-element-for-view-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
