---
title: WideItem öğesi WideControl (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083646"
---
# <a name="wideitem-element-for-widecontrol-format"></a>WideControl için WideItem Öğesi (Biçim)

Betik değeri görüntülenir ve özelliği tanımlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi (biçimi) WideItem öğesi (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `WideItem` öğesi. `FormatString` Öğesi, isteğe bağlıdır. Ancak, belirtmeniz gereken bir `PropertyName` veya `ScriptBlock` öğesi, ancak belirtemez hem de.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[WideItem WideControl (biçimi) için için FormatString öğesi](./formatstring-element-for-wideitem-for-widecontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Özellik veya betik değeri Görünümü'nde nasıl görüntüleneceğini tanımlayan bir biçim deseni belirtir.|
|[PropertyName öğesi WideItem (biçimi) için](./propertyname-element-for-wideitem-for-widecontrol-format.md)|Özellik değeri geniş görünümünde görüntülenen nesne belirtir.|
|[ScriptBlock öğesi WideItem (biçimi) için](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|Değeri, geniş görünümde görüntülenir betiğini belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[WideEntry öğesi (biçimi)](./wideentry-element-for-widecontrol-format.md)|Geniş bir görünüm tanımını sağlar.|

## <a name="remarks"></a>Açıklamalar

Geniş bir görünüm bileşenleri hakkında daha fazla bilgi için bkz. [geniş Görünüm](./creating-a-wide-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte gösterildiği bir `WideEntry` tanımlayan tek bir öğe `WideItem` öğesi. `WideItem` Öğe tanımlar özelliği veya betik değeri Görünümü'nde görüntülenir.

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

Geniş bir görünüm tam bir örnek için bkz: [geniş Görünüm (Temel)](./wide-view-basic.md).

## <a name="see-also"></a>Ayrıca bkz:

[WideItem WideControl (biçimi) için için FormatString öğesi](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[PropertyName öğesi WideItem (biçimi) için](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[ScriptBlock öğesi WideItem (biçimi) için](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[WideEntry öğesi (biçimi)](./wideentry-element-for-widecontrol-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
