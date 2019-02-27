---
title: ExpressionBinding öğesi görünümü (biçimi) için denetimleri için CustomItem için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848422"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>Görünüm Denetimleri için CustomItem ExpressionBinding Öğesi (Biçim)

Denetimi tarafından görüntülenen verileri tanımlar. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) denetimleri (biçimi) öğesi denetim öğesi denetimi için CustomEntries öğesi görünümü (biçimi) için denetimleri için özel denetim öğesi görünümü (biçimi) için denetimleri için Özel denetim CustomEntry öğesinin CustomEntries CustomEntry CustomItem Görünüm (biçimi) için denetimleri için görüntüleme (biçimi) ExpressionBinding öğesinin denetimleri için görüntüleme (biçimi) CustomItem öğesinin denetimleri için görüntüleme (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ExpressionBinding` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`CustomControl Element`|İsteğe bağlı öğe.<br /><br /> Bu denetim tarafından kullanılan bir denetimi tanımlar.|
|[CustomControlName öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Bir ortak denetimi veya bir görünüm denetimi adını belirtir.|
|[EnumerateCollection öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Koleksiyon öğelerini görüntüleneceğini belirtir.|
|[Görünüm (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar.|
|[PropertyName öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> .NET özelliğinin denetimi tarafından görüntülenen değeri belirtir.|
|[ScriptBlock öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Denetimi tarafından görüntülenen değeri betiğini belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CustomItem öğesi görünümü (biçimi) için denetimleri için CustomEntry için](./customitem-element-for-customentry-for-controls-for-view-format.md)|Hangi veri denetimi tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar.|

## <a name="remarks"></a>Açıklamalar

## <a name="see-also"></a>Ayrıca bkz:

[CustomItem öğesi görünümü (biçimi) için denetimleri için CustomEntry için](./customitem-element-for-customentry-for-controls-for-view-format.md)

[CustomControlName öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[EnumerateCollection öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[Görünüm (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[PropertyName öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[ScriptBlock öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
