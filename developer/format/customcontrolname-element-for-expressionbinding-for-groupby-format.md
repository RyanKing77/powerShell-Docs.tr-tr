---
title: GroupBy (biçimi) için ExpressionBinding için CustomControlName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845622"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>GroupBy ExpressionBinding için CustomControlName Öğesi (Biçim)

Bir ortak denetimi veya bir görünüm denetimi adını belirtir. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) CustomItem öğesinin CustomEntry GroupBy (biçimi) ExpressionBinding öğesinin CustomItem GroupBy (biçimi) CustomControlName öğesinin ExpressionBinding GroupBy (biçimi) için özel denetim

## <a name="syntax"></a>Sözdizimi

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomControlName` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[GroupBy (biçimi) için CustomItem için ExpressionBinding öğesi](./expressionbinding-element-for-customitem-for-groupby-format.md)|Denetimi tarafından görüntülenen verileri tanımlar.|

## <a name="text-value"></a>Metin Değeri

Denetimin adını belirtin.

## <a name="remarks"></a>Açıklamalar

Biçimlendirme bir dosyanın tüm görünümler tarafından kullanılabilen ortak denetimleri oluşturabilirsiniz ve belirli bir görünüm tarafından kullanılabilmesi için görünüm denetimleri oluşturabilirsiniz. Aşağıdaki öğeler bu denetimlerin adlarını belirtin:

- [Name öğesi denetimi için yapılandırma (biçimi) için denetimler](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name öğesi denetimi için Görünüm (biçimi) için denetimleri](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Ayrıca bkz:

[Name öğesi denetimi için yapılandırma (biçimi) için denetimler](./name-element-for-control-for-controls-for-configuration-format.md)

[Name öğesi denetimi için Görünüm (biçimi) için denetimleri](./name-element-for-control-for-controls-for-view-format.md)

[GroupBy (biçimi) için CustomItem için ExpressionBinding öğesi](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
