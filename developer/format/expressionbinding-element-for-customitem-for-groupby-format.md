---
title: GroupBy (biçimi) için CustomItem için ExpressionBinding öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846063"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>GroupBy CustomItem için ExpressionBinding Öğesi (Biçim)

Denetimi tarafından görüntülenen verileri tanımlar. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) CustomItem öğesinin CustomEntry GroupBy (biçimi) ExpressionBinding öğesinin CustomItem GroupBy (biçimi) için özel denetim

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
|[GroupBy (biçimi) için ExpressionBinding için CustomControlName öğesi](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Bir ortak denetimi veya bir görünüm denetimi adını belirtir.|
|[GroupBy (biçimi) için ExpressionBinding için EnumerateCollection öğesi](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)ExpressionBinding GroupBy (biçimi) için için EnumerateCollection öğesi|İsteğe bağlı öğe.<br /><br /> Belirtilen koleksiyonun öğeleri görüntülenir.|
|[GroupBy (biçimi) için ExpressionBinding için ItemSelectionCondition öğesi](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar.|
|[GroupBy (biçimi) için ExpressionBinding için PropertyName öğesi](./propertyname-element-for-expressionbinding-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> .NET özelliğinin denetimi tarafından görüntülenen değeri belirtir.|
|[GroupBy (biçimi) için ExpressionBinding için ScriptBlock öğesi](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Denetimi tarafından görüntülenen değeri betiğini belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[GroupBy (biçimi) için CustomEntry için CustomItem öğesi](./customitem-element-for-customentry-for-groupby-format.md)|Özel denetim görünüm tarafından hangi veriler görüntülenir ve nasıl görüntüleneceğini tanımlar.|

## <a name="see-also"></a>Ayrıca bkz:

[GroupBy (biçimi) için ExpressionBinding için CustomControlName öğesi](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy (biçimi) için ExpressionBinding için EnumerateCollection öğesi](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[GroupBy (biçimi) için ExpressionBinding için ItemSelectionCondition öğesi](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[GroupBy (biçimi) için ExpressionBinding için PropertyName öğesi](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy (biçimi) için ExpressionBinding için ScriptBlock öğesi](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[GroupBy (biçimi) için CustomEntry için CustomItem öğesi](./customitem-element-for-customentry-for-groupby-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
