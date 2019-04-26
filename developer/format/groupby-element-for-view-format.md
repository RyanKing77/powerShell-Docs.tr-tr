---
title: GroupBy öğesi görünümü (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065557"
---
# <a name="groupby-element-for-view-format"></a>Görünüm için GroupBy Öğesi (Biçim)

Yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlar. Bu öğe, bir tablo, liste, geniş veya özel denetimi görünüm tanımlarken, kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi görünümü (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[GroupBy (biçimi) için özel denetim öğesi](./customcontrol-element-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Yeni gruplar görüntüleyen bir özel denetim tanımlar.|
|[GroupBy (biçimi) için CustomControlName öğesi](./customcontrolname-element-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Yeni grubunu görüntülemek için kullanılan bir denetimin adını belirtir.|
|[GroupBy (biçimi) için etiket öğesi](./label-element-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Yeni bir grup ile karşılaşıldığında görüntülenen etiketi belirtir.|
|[GroupBy (biçimi) için PropertyName öğesi](./propertyname-element-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> .NET özelliğini başlatır belirtir, değeri değiştiğinde yeni bir grup.|
|[GroupBy (biçimi) için ScriptBlock öğesi](./scriptblock-element-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Yeni bir grup değeri değiştiğinde başlatan betiği belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Görünüm öğesi (biçimi)](./view-element-format.md)|Bir veya daha fazla .NET nesnelerini görüntüleyen bir görünüm tanımlar.|

## <a name="remarks"></a>Açıklamalar

Yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken, özellik veya yeni Grup başlatacak komut dosyasını belirtmeniz gerekir; Ancak, her ikisini birden belirtemezsiniz.

## <a name="see-also"></a>Ayrıca bkz:

[GroupBy (biçimi) için CustomControlName öğesi](./customcontrolname-element-for-groupby-format.md)

[GroupBy (biçimi) için etiket öğesi](./label-element-for-groupby-format.md)

[GroupBy (biçimi) için PropertyName öğesi](./propertyname-element-for-groupby-format.md)

[GroupBy (biçimi) için ScriptBlock öğesi](./scriptblock-element-for-groupby-format.md)

[Görünüm öğesi (biçimi)](./view-element-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
