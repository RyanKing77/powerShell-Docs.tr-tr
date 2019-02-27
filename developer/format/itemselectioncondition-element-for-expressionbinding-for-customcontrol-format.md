---
title: Özel denetim (biçimi) için ExpressionBinding için ItemSelectionCondition öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848345"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a>CustomControl ExpressionBinding için ItemSelectionCondition Öğesi (Biçim)

Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar. Bir denetim öğesi için belirtilip seçimi koşullar sayısı sınırı yoktur. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomItem öğesinin CustomEntries görünümü (biçimi) CustomEntry öğesinin özel denetim için CustomEntry ExpressionBinding öğesinin CustomItem görüntüleme (biçimi) ItemSelectionCondition öğesi görünümü (biçimi) için özel denetim için ifade bağlama için özel denetim için View (biçimi)

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
|[PropertyName öğesi görünümü (biçimi için özel denetim için ItemSelectionCondition için](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen .NET alan özelliği belirtir.|
|[ScriptBlock öğesi görünümü (biçimi) için özel denetim için ItemSelectionCondition için](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen betiği belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ExpressionBinding öğesi görünümü (biçimi) için özel denetim için CustomItem için](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Denetimi tarafından görüntülenen verileri tanımlar.|

## <a name="remarks"></a>Açıklamalar

Bir özellik adı veya bu koşul için bir betik belirtebilirsiniz, ancak ikisini birden belirtemezsiniz.

## <a name="see-also"></a>Ayrıca bkz:

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)

[ExpressionBinding öğesi görünümü (biçimi) için özel denetim için CustomItem için](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
