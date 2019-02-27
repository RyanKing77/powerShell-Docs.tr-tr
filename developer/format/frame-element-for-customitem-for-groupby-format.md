---
title: Çerçeve öğesi için CustomItem GroupBy (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846007"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>GroupBy CustomItem için Çerçeve Öğesi (Biçim)

Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) CustomItem öğesinin CustomEntry GroupBy (biçimi) çerçeve öğesinin CustomItem GroupBy (biçimi) için özel denetim

## <a name="syntax"></a>Sözdizimi

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `Frame` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`CustomItem Element`|Gerekli öğe|
|[GroupBy (biçimi) için bir çerçeve için FirstLineHanging öğesi](./firstlinehanging-element-for-frame-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Verilerin ilk satırı, sola kaydırılacak karakterlerinin kaçının tutulacağını belirtir.|
|[GroupBy (biçimi) için bir çerçeve için FirstLineIndent öğesi](./firstlineindent-element-for-frame-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> İlk veri satırını sağa kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.|
|[GroupBy (biçimi) için bir çerçeve için LeftIndent öğesi](./leftindent-element-for-frame-for-groupby-format.md)|İsteğe bağlı öğe.<br /><br /> Sol kenar boşluğu uzağa veri kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.|
|[GroupBy (biçimi) için bir çerçeve için RightIndent öğesi](./rightindent-element-for-frame-for-groupby-format.md)RightIndent öğesi|İsteğe bağlı öğe.<br /><br /> Sağ kenar boşluğu uzağa veri kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[GroupBy (biçimi) için CustomEntry için CustomItem öğesi](./customitem-element-for-customentry-for-groupby-format.md)|Hangi veri denetimi tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar.|

## <a name="remarks"></a>Açıklamalar

Belirtemezsiniz [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) ve [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) aynı öğeleri `Frame` öğesi.

## <a name="see-also"></a>Ayrıca bkz:

[GroupBy (biçimi) için bir çerçeve için FirstLineHanging öğesi](./firstlinehanging-element-for-frame-for-groupby-format.md)

[GroupBy (biçimi) için bir çerçeve için FirstLineIndent öğesi](./firstlineindent-element-for-frame-for-groupby-format.md)

[GroupBy (biçimi) için bir çerçeve için LeftIndent öğesi](./leftindent-element-for-frame-for-groupby-format.md)

[GroupBy (biçimi) için bir çerçeve için RightIndent öğesi](./rightindent-element-for-frame-for-groupby-format.md)

[GroupBy (biçimi) için CustomEntry için CustomItem öğesi](./customitem-element-for-customentry-for-groupby-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
