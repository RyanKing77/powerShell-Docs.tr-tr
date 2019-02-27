---
title: Öğesi (biçimi) genişletin | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848618"
---
# <a name="expand-element-format"></a>Genişletme Öğesi (Biçim)

Koleksiyon nesnesi bu tanım için nasıl genişletilmiş belirtir.

Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi) EnumerableExpansions öğesi (biçimi) EnumerableExpansion öğesi (biçimi) öğesi (biçimi) genişletin

## <a name="syntax"></a>Sözdizimi

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `Expand` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EnumerableExpansion öğesi (biçimi)](./enumerableexpansion-element-format.md)|Bir görünümü'nde görüntülendiğinde nesneleri genişletilir belirli .NET koleksiyonu tanımlar.|

## <a name="text-value"></a>Metin Değeri

Aşağıdaki değerlerden birini belirtin:

- EnumOnly: Koleksiyonda yalnızca nesnelerin özelliklerini görüntüler.

- CoreOnly: Yalnızca koleksiyon nesnesinin özelliklerini görüntüler.

- Her ikisi: Nesnelerin özelliklerini, koleksiyon ve koleksiyon nesnesinin özelliklerini görüntüler.

## <a name="remarks"></a>Açıklamalar

Bu öğe, koleksiyon nesnelerini ve koleksiyondaki nesnelerin nasıl görüntüleneceğini tanımlamak için kullanılır. Bu durumda, destekleyen herhangi bir nesne için bir koleksiyon nesnesini ifade eder **System.Collections.ICollection** arabirimi.

Koleksiyonda yalnızca nesnelerin özelliklerini görüntülemek için varsayılan davranıştır.

## <a name="see-also"></a>Ayrıca bkz:

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
