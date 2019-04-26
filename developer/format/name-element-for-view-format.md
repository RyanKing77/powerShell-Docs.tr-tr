---
title: Öğesi görünümü (biçimi) için ad | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065079"
---
# <a name="name-element-for-view-format"></a>Görünüm için Ad Öğesi (Biçim)

Görünümü tanımlamak için kullanılan adı belirtir.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) Name öğesi (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `Name` öğesi. Yalnızca bir `Name` öğesi her görünüm için izin verilir.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Görünüm öğesi (biçimi)](./view-element-format.md)|Bir veya daha fazla .NET nesneleri üyelerini görüntülemek için kullanılan bir görünüm tanımlar.|

## <a name="text-value"></a>Metin değeri

Görünüm için benzersiz bir kolay ad belirtin. Bu ad, hangi nesnesini veya nesne kümesini kullanın hangi komut nesneleri ya da bunların bir kombinasyonunu döndürür görünümü görünümün (örneğin, bir tablo görünümü veya liste görünümü), türe başvuru içerebilir.

## <a name="remarks"></a>Açıklamalar

Farklı görünüm türleri hakkında daha fazla bilgi için aşağıdaki konulara bakın: [Tablo görünümü](./creating-a-table-view.md), [liste görünümü](./creating-a-list-view.md), [geniş Görünüm](./creating-a-wide-view.md), ve [Özel Görünüm](./creating-custom-controls.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte gösterildiği bir `View` için bir tablo görünümü tanımlayan öğe [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) nesne. "Hizmet" görünümü adıdır.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a>Ayrıca bkz:

[Bir liste görünümü oluşturma](./creating-a-list-view.md)

[Bir tablo görünümü oluşturma](./creating-a-table-view.md)

[Geniş bir görünüm oluşturma](./creating-a-wide-view.md)

[Özel denetimler oluşturma](./creating-custom-controls.md)

[Görünüm öğesi (biçimi)](./view-element-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
