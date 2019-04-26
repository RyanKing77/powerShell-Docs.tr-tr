---
title: ScriptBlock öğesi WideItem WideControl (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064212"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>WideControl WideItem için ScriptBlock Öğesi (Biçim)

Değeri, geniş görünümde görüntülenir betiğini belirtir.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi (biçimi) WideItem öğesi (biçimi) ScriptBlock öğesi WideItem (biçimi) için

## <a name="syntax"></a>Sözdizimi

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `ScriptBlock` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[WideItem öğesi (biçimi)](./wideitem-element-for-widecontrol-format.md)|Değeri, geniş görünümde görüntülenir özelliği veya betik bloğu tanımlar.|

## <a name="text-value"></a>Metin değeri

Değeri görüntülenen komut dosyasını belirtin.

## <a name="remarks"></a>Açıklamalar

Geniş bir görünüm bileşenleri hakkında daha fazla bilgi için bkz. [geniş bir görünüm oluşturma](./creating-a-wide-view.md).

## <a name="example"></a>Örnek

Bu örnek gösterir bir `WideItem` değeri görünümünde görüntülenen bir komut dosyası tanımlayan öğe.

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>Ayrıca bkz:

[WideItem öğesi (biçimi)](./wideitem-element-for-widecontrol-format.md)

[Geniş bir görünüm oluşturma](./creating-a-wide-view.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
