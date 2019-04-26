---
title: ViewDefinitions öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083714"
---
# <a name="viewdefinitions-element-format"></a>ViewDefinitions Öğesi (Biçim)

.NET nesneleri görüntülemek için kullanılan görünümleri tanımlar. Bu görünümler, özelliklerini ve betik değerlerini bir nesnenin bir tablo biçiminde, liste biçimini, geniş bir biçim ve özel denetim biçimi görüntüleyebilirsiniz.

Yapılandırma öğesi (biçimi) ViewDefinitions (XML biçimi) öğesi

## <a name="syntax"></a>Sözdizimi

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `ViewDefinitions` öğesi. Bir biçimlendirme dosyasında tanımlanan görünümleri sayısına bir sınır yoktur ve herhangi bir sırada eklenebilir.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Görünüm öğesi (biçimi)](./view-element-format.md)|Bir veya daha fazla .NET nesneleri görüntülemek için kullanılan bir görünüm tanımlar.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Yapılandırma öğesi (biçimi)](./configuration-element-format.md)|Biçimlendirme bir dosyanın üst düzey öğesi temsil eder.|

## <a name="remarks"></a>Açıklamalar

Görünüm türlerini farklı bileşenleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Bir tablo görünümü oluşturma](./creating-a-table-view.md)

- [Bir liste görünümü oluşturma](./creating-a-list-view.md)

- [Geniş bir görünüm oluşturma](./creating-a-wide-view.md)

- [Özel denetimler](./creating-custom-controls.md)

## <a name="example"></a>Örnek

Bu örnek gösterir bir `ViewDefinitions` Tablo görünümü ve liste görünümü üst öğe içeren öğe.

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a>Ayrıca bkz:

[Yapılandırma öğesi (biçimi)](./configuration-element-format.md)

[Görünüm öğesi (biçimi)](./view-element-format.md)

[Bir tablo görünümü oluşturma](./creating-a-table-view.md)

[Bir liste görünümü oluşturma](./creating-a-list-view.md)

[Geniş bir görünüm oluşturma](./creating-a-wide-view.md)

[Özel denetimler](./creating-custom-controls.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
