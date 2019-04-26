---
title: Çerçeve öğesi CustomItem için özel denetim için View (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065589"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>Görünüm CustomControl için CustomItem Çerçeve Öğesi (Biçim)

Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomItem öğesinin CustomEntries görünümü (biçimi) CustomEntry öğesinin özel denetim için CustomEntry CustomItem Görünüm (biçimi) için özel denetim için çerçeve öğesinin CustomControlView (biçimi)

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

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `Frame` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|`CustomItem Element`|Gerekli öğe|
|[FirstLineHanging öğesi](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Verilerin ilk satırı, sola kaydırılacak karakterlerinin kaçının tutulacağını belirtir.|
|[FirstLineIndent öğesi](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> İlk veri satırını sağa kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.|
|[LeftIndent öğesi](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Sol kenar boşluğu uzağa veri kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.|
|[RightIndent öğesi](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Sağ kenar boşluğu uzağa veri kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[İçin görünümün (biçimi) CustomEntry CustomItem öğesi](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Hangi veri denetimi tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar.|

## <a name="remarks"></a>Açıklamalar

Belirtemezsiniz [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) ve [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) aynı öğeleri `Frame` öğesi.

## <a name="see-also"></a>Ayrıca bkz:

[FirstLineHanging öğesi](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[FirstLineIndent öğesi](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[LeftIndent öğesi](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[RightIndent öğesi](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[İçin görünümün (biçimi) CustomEntry CustomItem öğesi](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
