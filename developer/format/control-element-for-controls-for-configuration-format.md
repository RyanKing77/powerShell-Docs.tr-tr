---
title: Denetim öğesi için denetimleri için yapılandırma (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848835"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Yapılandırma Denetimleri için Denetim Öğesi (Biçim)

Biçimlendirme dosya ve denetime başvurmak için kullanılan ad tüm görünümler tarafından kullanılan ortak bir denetimi tanımlar.

Yapılandırma öğesi (biçimi) denetimleri öğesi denetimleri yapılandırma (biçimi) için yapılandırma (biçimi) denetim öğesi

## <a name="syntax"></a>Sözdizimi

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğe için aşağıdaki bölümlerde açıklanmaktadır `Control` öğesi. Her alt öğenin yalnızca bir tane belirtmeniz gerekir.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Özel denetim öğesi denetimi için yapılandırma (biçimi) için denetimler](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Gerekli öğe.<br /><br /> Denetimini tanımlar.|
|[Name öğesi denetimi için yapılandırma (biçimi)](./name-element-for-control-for-controls-for-configuration-format.md)|Gerekli öğe.<br /><br /> Denetime başvurmak için kullanılan adı belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Denetim öğesi yapılandırmasının (biçimi)](./controls-element-for-configuration-format.md)|Tüm görünümlere biçimlendirme dosyasının veya diğer denetimleri tarafından kullanılabilen ortak denetimleri tanımlar.|

## <a name="remarks"></a>Açıklamalar

Bu denetim için verilen ad, aşağıdaki öğeleri başvurulabilir:

- [ExpressionBinding öğesi CustomItem (biçimi) için](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [GroupBy öğesi View(Format) için](./groupby-element-for-view-format.md)

## <a name="see-also"></a>Ayrıca bkz:

[Denetim öğesi yapılandırmasının (biçimi)](./controls-element-for-configuration-format.md)

[Özel denetim öğesi denetimi için yapılandırma (biçimi)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[ExpressionBinding öğesi CustomItem (biçimi) için](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[GroupBy öğesi View(Format) için](./groupby-element-for-view-format.md)

[Name öğesi denetimi için yapılandırma (biçimi) için denetimler](./name-element-for-control-for-controls-for-configuration-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
