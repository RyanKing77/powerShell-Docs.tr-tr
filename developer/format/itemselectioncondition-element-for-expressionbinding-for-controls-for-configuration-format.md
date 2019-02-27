---
title: İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850795"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a>Yapılandırma Denetimleri için ExpressionBinding ItemSelectionCondition Öğesi (Biçim)

Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) CustomItem öğesinin CustomEntry CustomItem denetimleri için yapılandırma (biçimi) için yapılandırma ExpressionBinding öğesinin denetimleri için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi

## <a name="syntax"></a>Sözdizimi

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ItemSelectionCondition` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[İçin yapılandırma (biçimi) için denetimleri için ItemSelectionCondition PropertyName öğesi](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen .NET alan özelliği belirtir.|
|[Denetimler için yapılandırma (biçimi) için ItemSelectionCondition için ScriptBlock öğesi](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen betiği belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[İçin yapılandırma (biçimi) için denetimleri için CustomItem ExpressionBinding öğesi](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Denetimi tarafından görüntülenen verileri tanımlar.|

## <a name="remarks"></a>Açıklamalar

Bir özellik adı veya bu koşul için bir betik belirtebilirsiniz, ancak ikisini birden belirtemezsiniz.

## <a name="see-also"></a>Ayrıca bkz:

[İçin yapılandırma (biçimi) için denetimleri için ItemSelectionCondition PropertyName öğesi](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Denetimler için yapılandırma (biçimi) için ItemSelectionCondition için ScriptBlock öğesi](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[İçin yapılandırma (biçimi) için denetimleri için CustomItem ExpressionBinding öğesi](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
