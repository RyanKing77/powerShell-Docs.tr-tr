---
title: EnumerableExpansion öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066150"
---
# <a name="enumerableexpansion-element-format"></a>EnumerableExpansion Öğesi (Biçim)

Bir görünümü'nde görüntülendiğinde nesneleri genişletilir belirli .NET koleksiyonu tanımlar.

Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi) EnumerableExpansions öğesi (biçimi) EnumerableExpansion öğesi (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `EnumerableExpansion` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[EntrySelectedBy öğesi EnumerableExpansion (biçimi) için](./entryselectedby-element-for-enumerableexpansion-format.md)|İsteğe bağlı öğe.<br /><br /> Bu tanımı tarafından hangi .NET koleksiyon nesnelerini genişletilir tanımlar.|
|[Öğesi (biçimi) genişletin](./expand-element-format.md)|Koleksiyon nesnesi bu tanım için nasıl genişletilmiş belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[EnumerableExpansions öğesi (biçimi)](./enumerableexpansions-element-format.md)|Farklı şekilde Görünümü'nde görüntülendiğinde nesneleri genişletilir, .NET koleksiyonu tanımlar.|

## <a name="remarks"></a>Açıklamalar

Bu öğe, koleksiyon nesnelerini ve koleksiyondaki nesnelerin nasıl görüntüleneceğini tanımlamak için kullanılır. Bu durumda, destekleyen herhangi bir nesne için bir koleksiyon nesnesini ifade eder **System.Collections.ICollection** arabirimi.

Koleksiyonda yalnızca nesnelerin özelliklerini görüntülemek için varsayılan davranıştır.

## <a name="see-also"></a>Ayrıca bkz:

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
