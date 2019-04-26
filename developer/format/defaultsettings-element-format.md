---
title: DefaultSettings öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066354"
---
# <a name="defaultsettings-element-format"></a>DefaultSettings Öğesi (Biçim)

Biçimlendirme dosyanın tüm görünümleri için geçerli genel ayarlarını tanımlar. Ortak ayarları hataları görüntüleme koleksiyonları nasıl genişletilir, tanımlama, tabloları ve diğer metin kaydırma içerir.

Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `DefaultSettings` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[DisplayError öğesi (biçimi)](./displayerror-element-format.md)|İsteğe bağlı öğe.<br /><br /> Bir veri parçasını görüntülenirken bir hata oluştuğunda #ERR dize görüntüleneceğini belirtir.|
|[EnumerableExpansions öğesi (biçimi)](./enumerableexpansions-element-format.md)|İsteğe bağlı öğe.<br /><br /> Bir görünümü'nde görüntülendiğinde genişletilmiş .NET nesneleri farklı yollarını tanımlar.|
|[PropertyCountForTable (biçimi)](./propertycountfortable-element-format.md)|İsteğe bağlı öğe.<br /><br /> Bir nesne, nesne Tablo görünümünde görüntülemek için gereken özellikleri en az sayısını belirtir.|
|[ShowError öğesi (biçimi)](./showerror-element-format.md)|İsteğe bağlı öğe.<br /><br /> Bir veri parçasını görüntülenirken bir hata oluştuğunda tam hata kaydı görüntüleneceğini belirtir.|
|[WrapTables öğesi (biçimi)](./wraptables-element-format.md)|İsteğe bağlı öğe.<br /><br /> Sütun genişliğini uygun değilse, bir tablodaki verileri sonraki satıra taşınır belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Yapılandırma öğesi](./configuration-element-format.md)|Biçimlendirme bir dosyanın üst düzey öğesi temsil eder.|

## <a name="remarks"></a>Açıklamalar

## <a name="see-also"></a>Ayrıca bkz:

[Yapılandırma öğesi](./configuration-element-format.md)

[DisplayError öğesi (biçimi)](./displayerror-element-format.md)

[EnumerableExpansions öğesi (biçimi)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (biçimi)](./propertycountfortable-element-format.md)

[ShowError öğesi (biçimi)](./showerror-element-format.md)

[WrapTables öğesi (biçimi)](./wraptables-element-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
