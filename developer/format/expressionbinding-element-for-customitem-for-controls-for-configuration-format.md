---
title: İçin yapılandırma (biçimi) için denetimleri için CustomItem ExpressionBinding öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065960"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>Yapılandırma Denetimleri için CustomItem ExpressionBinding Öğesi (Biçim)

Denetimi tarafından görüntülenen verileri tanımlar. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) CustomItem öğesinin CustomEntry CustomItem denetimleri için yapılandırma (biçimi) için yapılandırma ExpressionBinding öğesinin denetimleri için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi

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
|[İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding CustomControlName öğesi](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Bir ortak denetimi veya bir görünüm denetimi adını belirtir.|
|[İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding EnumerateCollection öğesi](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Koleksiyon öğelerini denetimi tarafından görüntülenen belirtildi.|
|[İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Bu yaygın bir denetim kullanılacak bulunmalıdır koşulu tanımlar.|
|[İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding PropertyName öğesi](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Ortak denetimi tarafından görüntülenen değeri .NET alan özelliği belirtir.|
|[Denetimler için yapılandırma (biçimi) için ExpressionBinding için ScriptBlock öğesi](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Ortak denetimi tarafından görüntülenen değeri betiğini belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Yapılandırma için denetimleri için CustomEntry için CustomItem öğesi](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Özel denetim görünüm tarafından hangi veriler görüntülenir ve nasıl görüntüleneceğini tanımlar.|

## <a name="remarks"></a>Açıklamalar

## <a name="see-also"></a>Ayrıca bkz:

[Yapılandırma için denetimleri için CustomEntry için CustomItem öğesi](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
