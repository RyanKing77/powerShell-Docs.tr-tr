---
title: Yapılandırma öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066830"
---
# <a name="configuration-element-format"></a>Yapılandırma Öğesi (Biçim)

Biçimlendirme bir dosyanın üst düzey öğesi temsil eder.

Yapılandırma öğesi

## <a name="syntax"></a>Sözdizimi

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `Configuration` öğesi. Bu öğe biçimlendirme her dosya için kök öğesi olmalıdır ve bu öğe en az bir alt öğe içermelidir.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Yapılandırma (biçimi) için Denetim öğesi](./controls-element-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Tüm biçimlendirme dosya görünümler tarafından kullanılabilen ortak denetimleri tanımlar.|
|[DefaultSettings öğesi (biçimi)](./defaultsettings-element-format.md)|İsteğe bağlı öğe.<br /><br /> Biçimlendirme dosyanın tüm görünümleri için geçerli genel ayarlarını tanımlar.|
|[SelectionSets öğesi biçimi](./selectionsets-element-format.md)|İsteğe bağlı öğe.<br /><br /> Biçimlendirme dosyanın tüm görünümler tarafından kullanılan .NET nesneleri ortak kümesini tanımlar.|
|[ViewDefinitions öğesi (biçimi)](./viewdefinitions-element-format.md)|İsteğe bağlı öğe.<br /><br /> Nesneleri görüntülemek için kullanılan görünümleri tanımlar.|

### <a name="parent-elements"></a>Üst öğeler

Yok.

## <a name="remarks"></a>Açıklamalar

Biçimlendirme dosyaları nesnelerin nasıl görüntüleneceğini tanımlar. Çoğu durumda, bu kök öğesi içeren bir [ViewDefinitions](./viewdefinitions-element-format.md) tablo, liste ve biçimlendirme dosyanın geniş görünümleri tanımlayan öğe. Görünüm tanımları ek olarak, biçimlendirme dosyası ortak seçimi ayarlar, ayarları ve bu görünümleri kullanabileceğiniz denetimler tanımlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz:

[Yapılandırma (biçimi) için Denetim öğesi](./controls-element-for-configuration-format.md)

[DefaultSettings öğesi (biçimi)](./defaultsettings-element-format.md)

[SelectionSets öğesi (biçimi)](./selectionsets-element-format.md)

[ViewDefinitions öğesi (biçimi)](./viewdefinitions-element-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
