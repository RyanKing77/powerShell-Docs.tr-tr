---
title: ItemSelectionCondition öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065487"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a>Görünüm Denetimleri için ExpressionBinding ItemSelectionCondition Öğesi (Biçim)

Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) denetimleri (biçimi) öğesi denetim öğesi denetimi için CustomEntries öğesi görünümü (biçimi) için denetimleri için özel denetim öğesi görünümü (biçimi) için denetimleri için Özel denetim CustomEntry öğesinin CustomEntries CustomEntry CustomItem Görünüm (biçimi) için denetimleri için görüntüleme (biçimi) ExpressionBinding öğesinin denetimleri için görüntüleme (biçimi) CustomItem öğesinin denetimleri için görüntüleme (biçimi) Görünüm (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi

## <a name="syntax"></a>Sözdizimi

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ItemSelectionCondition` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[PropertyName öğesi görünümü (biçimi) için denetimleri için ItemSelectionCondition için](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen .NET alan özelliği belirtir.|
|[ScriptBlock öğesi görünümü (biçimi) için denetimleri için ItemSelectionCondition için](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Koşul tetikleyen betiği belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ExpressionBinding öğesi görünümü (biçimi) için denetimleri için CustomItem için](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Denetimi tarafından görüntülenen verileri tanımlar.|

## <a name="remarks"></a>Açıklamalar

Bir özellik adı veya bu koşul için bir betik belirtebilirsiniz, ancak ikisini birden belirtemezsiniz.

## <a name="see-also"></a>Ayrıca bkz:

[PropertyName öğesi görünümü (biçimi) için denetimleri için ItemSelectionCondition için](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[ScriptBlock öğesi görünümü (biçimi) için denetimleri için ItemSelectionCondition için](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[ExpressionBinding öğesi görünümü (biçimi) için denetimleri için CustomItem için](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
