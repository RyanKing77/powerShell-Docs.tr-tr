---
title: CustomItem öğesi görünümü (biçimi) için özel denetim için CustomEntry için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846945"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>Görünüm CustomControl için CustomEntry CustomItem Öğesi (Biçim)

Özel denetim görünüm tarafından hangi veriler görüntülenir ve nasıl görüntüleneceğini tanımlar. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomItem öğesinin CustomEntries görünümü (biçimi) CustomEntry öğesinin özel denetim için CustomEntry görünümü (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomItem` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ExpressionBinding öğesi görünümü (biçimi) için özel denetim için CustomItem için](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Denetimi tarafından görüntülenen verileri tanımlar.|
|[Çerçeve öğesi görünümü (biçimi) için özel denetim için CustomItem için](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Özel denetim görünüm tarafından hangi veriler görüntülenir ve nasıl görüntüleneceğini tanımlar.|
|[Yeni satır öğesi görünümü (biçimi) için özel denetim için CustomItem için](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Boş bir satır denetimi görüntüye ekler.|
|[Metin öğesi görünümü (biçimi) için özel denetim için CustomItem için](./text-element-for-customitem-for-customview-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Ek metin denetimi tarafından görüntülenen verilere belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CustomEntry öğesi görünümü (biçimi) için özel denetim için CustomEntries için](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Özel denetim görünüm tanımını sağlar.|

## <a name="remarks"></a>Açıklamalar

## <a name="see-also"></a>Ayrıca bkz:

[İçin görünümün (biçimi) CustomEntries CustomEntry öğesi](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[ExpressionBinding öğesi görünümü (biçimi) için özel denetim için CustomItem için](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[Çerçeve öğesi görünümü (biçimi) için özel denetim için CustomItem için](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Yeni satır öğesi görünümü (biçimi) için özel denetim için CustomItem için](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[Metin öğesi görünümü (biçimi) için özel denetim için CustomItem için](./text-element-for-customitem-for-customview-for-view-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
