---
title: ExpressionBinding öğesi görünümü (biçimi) için özel denetim için CustomItem için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065929"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>Görünüm CustomControl için CustomItem ExpressionBinding Öğesi (Biçim)

Denetimi tarafından görüntülenen verileri tanımlar. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi görünümü (biçimi) CustomEntries öğesinin CustomEntries için özel denetim için View (Görünüm (biçimi) CustomEntry öğesinin özel denetim Biçimi) CustomItem öğesi görünümü (biçimi) ExpressionBinding öğesinin CustomItem Görünüm (biçimi) için özel denetim için özel denetim için CustomEntry için

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

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ExpressionBinding` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|`CustomControl Element`|İsteğe bağlı öğe.<br /><br /> Bu denetim tarafından kullanılan bir denetimi tanımlar.|
|[CustomControlName öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Bir ortak denetimi veya bir görünüm denetimi adını belirtir.|
|[EnumerateCollection öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Belirtilen koleksiyonun öğeleri görüntülenir.|
|[ItemSelectionCondition öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|İsteğe bağlı öğe.<br /><br /> Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar.|
|[PropertyName öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> .NET özelliğinin denetimi tarafından görüntülenen değeri belirtir.|
|[İçin görünümün (biçimi) CustomCustomControl ExpressionBinding için ScriptBlock öğesi](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Denetimi tarafından görüntülenen değeri betiğini belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CustomItem öğesi görünümü (biçimi) için özel denetim için CustomEntry için](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Özel denetim görünüm tarafından hangi veriler görüntülenir ve nasıl görüntüleneceğini tanımlar.|

## <a name="remarks"></a>Açıklamalar

## <a name="see-also"></a>Ayrıca bkz:

[CustomControlName öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[EnumerateCollection öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[ItemSelectionCondition öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[PropertyName öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[ScriptBlock öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomItem öğesi görünümü (biçimi) için özel denetim için CustomEntry için](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
