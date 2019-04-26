---
title: GroupBy (biçimi) için CustomEntry için CustomItem öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066408"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>GroupBy CustomEntry için CustomItem Öğesi (Biçim)

Özel denetim görünüm tarafından hangi veriler görüntülenir ve nasıl görüntüleneceğini tanımlar. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomItem öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) için CustomEntry

## <a name="syntax"></a>Sözdizimi

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomItem` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[GroupBy (biçimi) için CustomItem için ExpressionBinding öğesi](./expressionbinding-element-for-customitem-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Denetimi tarafından görüntülenen verileri tanımlar.|
|[GroupBy (biçimi) için CustomItem için çerçeve öğesi](./frame-element-for-customitem-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Özel denetim görünüm tarafından hangi veriler görüntülenir ve nasıl görüntüleneceğini tanımlar.|
|[GroupBy (biçimi) için CustomItem için yeni satır öğesi](./newline-element-for-customitem-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Boş bir satır denetimi görüntüye ekler.|
|[GroupBy (biçimi) için CustomItem için metin öğesi](./text-element-for-customitem-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Ek metin denetimi tarafından görüntülenen verilere belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[GroupBy (biçimi) için özel denetim için CustomEntry öğesi](./customentry-element-for-customcontrol-for-groupby-format.md)|Özel denetim görünüm tanımını sağlar.|

## <a name="remarks"></a>Açıklamalar

## <a name="see-also"></a>Ayrıca bkz:

[GroupBy (biçimi) için özel denetim için CustomEntry öğesi](./customentry-element-for-customcontrol-for-groupby-format.md)

[GroupBy (biçimi) için CustomItem için ExpressionBinding öğesi](./expressionbinding-element-for-customitem-for-groupby-format.md)

[GroupBy (biçimi) için CustomItem için çerçeve öğesi](./frame-element-for-customitem-for-groupby-format.md)

[GroupBy (biçimi) için CustomItem için yeni satır öğesi](./newline-element-for-customitem-for-groupby-format.md)

[GroupBy (biçimi) için CustomItem için metin öğesi](./text-element-for-customitem-for-groupby-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
