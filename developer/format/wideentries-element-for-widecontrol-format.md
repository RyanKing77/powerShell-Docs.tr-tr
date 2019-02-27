---
title: WideEntries öğesi WideControl (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844908"
---
# <a name="wideentries-element-for-widecontrol-format"></a>WideControl için WideEntries Öğesi (Biçim)

Geniş bir görünüm tanımını sağlar. Geniş bir görünüm, bir veya daha fazla tanımları belirtmeniz gerekir.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `WideEntries` öğesi. En az bir alt öğesi belirtilmesi gerekir.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[WideEntry öğesi (biçimi)](./wideentry-element-for-widecontrol-format.md)|Geniş bir görünüm tanımını sağlar.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[WideControl öğesi (biçimi)](./widecontrol-element-format.md)|Bir geniş (çoklu değer) tanımlar görünüm için liste biçimini.|

## <a name="remarks"></a>Açıklamalar

Geniş bir görünüm tek özellik değeri ya da her nesne için betik değer görüntüleyen bir liste biçimidir. Geniş bir görünüm bileşenleri hakkında daha fazla bilgi için bkz. [geniş görünüm bileşenleri](./creating-a-wide-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte gösterildiği bir `WideEntries` tanımlayan tek bir öğe `WideEntry` öğesi. `WideEntry` Tek bir öğe içeriyorsa `WideItem` tanımlayan hangi özelliğinin veya betik değeri görünümünde görüntülenen öğe.

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

Geniş bir görünüm tam bir örnek için bkz: [geniş Görünüm (Temel)](./wide-view-basic.md).

## <a name="see-also"></a>Ayrıca bkz:

[Geniş bir görünüm oluşturma](./creating-a-wide-view.md)

[WideControl öğesi (biçimi)](./widecontrol-element-format.md)

[WideEntry öğesi (biçimi)](./wideentry-element-for-widecontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
