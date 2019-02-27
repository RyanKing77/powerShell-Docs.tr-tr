---
title: GroupBy (biçimi) için CustomControlName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849829"
---
# <a name="customcontrolname-element-for-groupby-format"></a>GroupBy için CustomControlName Öğesi (Biçim)

Yeni grubunu görüntülemek için kullanılan özel bir denetimin adını belirtir. Bu öğe, bir tablo, liste, geniş veya özel denetimi görünüm tanımlarken, kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi görünümü (biçimi) CustomControlName GroupBy (biçimde) bir öğe için

## <a name="syntax"></a>Sözdizimi

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki bölümlerde, öznitelikler, alt ve üst öğeleri açıklayan `CustomControlName` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[GroupBy öğesi görünümü (biçimi)](./groupby-element-for-view-format.md)|Windows PowerShell yeni bir grup nesnelerin biçimini tanımlar.|

## <a name="text-value"></a>Metin Değeri

Yeni bir grup görüntülemek için kullanılan özel denetimin adını belirtin.

## <a name="remarks"></a>Açıklamalar

Biçimlendirme bir dosyanın tüm görünümler tarafından kullanılabilen ortak denetimleri oluşturabilirsiniz ve belirli bir görünüm tarafından kullanılabilmesi için görünüm denetimleri oluşturabilirsiniz. Aşağıdaki öğeler bu özel denetimlerin adlarını belirtin:

- [Name öğesi denetimi için yapılandırma (biçimi) için denetimler](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name öğesi denetimi için Görünüm (biçimi) için denetimleri](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Ayrıca bkz:

[GroupBy öğesi görünümü (biçimi)](./groupby-element-for-view-format.md)

[Name öğesi denetimi için yapılandırma (biçimi) için denetimler](./name-element-for-control-for-controls-for-configuration-format.md)

[Name öğesi denetimi için Görünüm (biçimi) için denetimleri](./name-element-for-control-for-controls-for-view-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
