---
title: PropertyName öğesi WideItem WideControl (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850284"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>WideControl WideItem için PropertyName Öğesi (Biçim)

Özellik değeri geniş görünümünde görüntülenen nesne belirtir.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi (biçimi) WideItem öğesi (biçimi) PropertyName öğesi WideItem (biçimi) için

## <a name="syntax"></a>Sözdizimi

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `PropertyName` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[WideItem öğesi (biçimi)](./wideitem-element-for-widecontrol-format.md)|Özellik veya betik değeri geniş görünümünde görüntülenen tanımlar.|

## <a name="text-value"></a>Metin Değeri

Özellik değeri görüntülenen adını belirtin.

## <a name="remarks"></a>Açıklamalar

Geniş bir görünüm bileşenleri hakkında daha fazla bilgi için bkz. [geniş bir görünüm oluşturma](./creating-a-wide-view.md).

## <a name="example"></a>Örnek

Bu örnek, ProcessName özelliğinin değerini görüntüler geniş bir görünüm gösterir [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesne.

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a>Ayrıca bkz:

[WideItem öğesi (biçimi)](./wideitem-element-for-widecontrol-format.md)

[Geniş bir görünüm oluşturma](./creating-a-wide-view.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
