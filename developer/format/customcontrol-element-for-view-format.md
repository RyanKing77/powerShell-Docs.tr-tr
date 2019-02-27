---
title: Özel denetim öğesi görünümü (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850494"
---
# <a name="customcontrol-element-for-view-format"></a>Görünüm için CustomControl Öğesi (Biçim)

Görünüm için bir özel denetim biçimini tanımlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomControl` öğesi. Bir alt öğe belirtmeniz gerekir.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CustomEntries öğesi görünümü (biçimi) için özel denetim için](./customentries-element-for-customcontrol-for-view-format.md)|Gerekli öğe.<br /><br /> Özel denetim görünüm tanımını sağlar.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Görünüm öğesi (biçimi)](./view-element-format.md)|Bir veya daha fazla .NET nesneleri görüntülemek için kullanılan bir görünüm tanımlar.|

## <a name="remarks"></a>Açıklamalar

Çoğu durumda, yalnızca bir tanımı için her denetim görünüm gereklidir, ancak farklı .NET nesneleri görüntülemek için aynı görünümde kullanmak istiyorsanız birden çok tanım sağlamak mümkündür. Bu gibi durumlarda, her bir nesne veya nesne için ayrı bir tanımı sağlayabilir.

## <a name="see-also"></a>Ayrıca bkz:

[CustomEntries öğesi görünümü (biçimi) için özel denetim için](./customentries-element-for-customcontrol-for-view-format.md)

[Görünüm öğesi (biçimi)](./view-element-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
