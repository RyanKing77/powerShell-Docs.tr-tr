---
title: EnumerableExpansions öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849794"
---
# <a name="enumerableexpansions-element-format"></a>EnumerableExpansions Öğesi (Biçim)

Bir görünümü'nde görüntülendiğinde .NET koleksiyon nesnelerini nasıl genişletilir tanımlar.

Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi) EnumerableExpansions öğesi (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `EnumerableExpansions` öğesi. Kullanabileceğiniz bir alt öğe sayısı sınırı yoktur.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EnumerableExpansion öğesi (biçimi)](./enumerableexpansion-element-format.md)|İsteğe bağlı öğe.<br /><br /> Bir görünümü'nde görüntülendiğinde, genişletilmiş belirli .NET koleksiyon nesnelerini tanımlar.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[DefaultSettings öğesi (biçimi)](./defaultsettings-element-format.md)|Biçimlendirme dosyanın tüm görünümleri için geçerli genel ayarlarını tanımlar.|

## <a name="remarks"></a>Açıklamalar

Bu öğe, koleksiyon nesnelerini ve koleksiyondaki nesnelerin nasıl görüntüleneceğini tanımlamak için kullanılır. Bu durumda, destekleyen herhangi bir nesne için bir koleksiyon nesnesini ifade eder **System.Collections.ICollection** arabirimi.

## <a name="see-also"></a>Ayrıca bkz:

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
