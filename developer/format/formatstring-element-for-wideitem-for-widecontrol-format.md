---
title: WideItem WideControl (biçimi) için için FormatString öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065691"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a>WideControl WideItem için FormatString Öğesi (Biçim)

Özellik veya betik değeri Görünümü'nde nasıl görüntüleneceğini tanımlayan bir biçim deseni belirtir.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi WideControl (biçimi) FormatString öğesi WideItem öğesinin WideControl (biçimi) için WideItem WideControl (biçimi) için

## <a name="syntax"></a>Sözdizimi

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `FormatString` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[WideItem öğesi WideControl (biçimi) için](./wideitem-element-for-widecontrol-format.md)|Betik değeri liste görünümünün bir satır görüntülenir ve özelliği tanımlar.|

## <a name="text-value"></a>Metin değeri

Verilerin biçimlendirilmesi için kullanılan desen belirtin. Örneğin, türünde herhangi bir özelliği değerini biçimlendirmek için bu düzeni kullanabilirsiniz [System.Timespan](/dotnet/api/System.TimeSpan): {0: aaa} {0} {0:HH}: {0:mm}.

## <a name="remarks"></a>Açıklamalar

Tablo görünümleri, liste görünümleri, geniş görünümleri veya özel görünümlerini oluşturma biçim dizeleri kullanılabilir. Bir görünümü'nde görüntülenen bir değeri biçimlendirme hakkında daha fazla bilgi için bkz. [görüntülenen verileri biçimlendirme](./formatting-displayed-data.md).

Geniş görünümlerde biçim dizeleri kullanma hakkında daha fazla bilgi için bkz. [geniş bir görünüm oluşturma](./creating-a-wide-view.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir biçimlendirme dizesi değerini tanımlamak gösterilmektedir `StartTime` özelliği.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a>Ayrıca bkz:

[Geniş bir görünüm oluşturma](./creating-a-wide-view.md)

[WideItem öğesi WideControl (biçimi) için](./wideitem-element-for-widecontrol-format.md)

[Biçimlendirme bir Windows PowerShell yazma ve dosya türleri](./writing-a-powershell-formatting-file.md)
