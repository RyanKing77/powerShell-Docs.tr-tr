---
title: Çerçeve öğesi için CustomItem denetimleri için görüntüleme (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849486"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>Görünüm Denetimleri için CustomItem Çerçeve Öğesi (Biçim)

Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) denetimleri (biçimi) öğesi denetim öğesi denetimi için CustomEntries öğesi görünümü (biçimi) için denetimleri için özel denetim öğesi görünümü (biçimi) için denetimleri için Özel denetim CustomEntry öğesinin CustomEntries CustomEntry CustomItem Görünüm (biçimi) için denetimleri için görüntüleme (biçimi) çerçeve öğesinin denetimleri için görüntüleme (biçimi) CustomItem öğesinin denetimleri için görüntüleme (biçimi)

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
|[FirstLineHanging öğesi çerçevesinin denetimlerinin görünümün (biçimi)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> İlk satır, sola kaydırılacak karakterlerinin kaçının tutulacağını belirtir.|
|[FirstLineIndent öğesi çerçevesinin denetimlerinin görünümün (biçimi)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> İlk satır, sağa kaydırılacak karakterlerinin kaçının tutulacağını belirtir.|
|[LeftIndent öğesi çerçevesinin denetimlerinin görünümün (biçimi)](./leftindent-element-for-frame-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Sol kenar boşluğu uzağa veri kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.|
|[RightIndent öğesi çerçevesinin denetimlerinin görünümün (biçimi)](./rightindent-element-for-frame-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Sağ kenar boşluğu uzağa veri kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CustomItem öğesi görünümü (biçimi) için denetimleri için CustomEntry için](./customitem-element-for-customentry-for-controls-for-view-format.md)|Hangi veri denetimi tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar.|

## <a name="remarks"></a>Açıklamalar

Belirtemezsiniz [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) ve [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) aynı öğeleri `Frame` öğesi.

## <a name="see-also"></a>Ayrıca bkz:

[FirstLineHanging öğesi çerçevesinin denetimlerinin görünümün (biçimi)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[FirstLineIndent öğesi çerçevesinin denetimlerinin görünümün (biçimi)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[LeftIndent öğesi çerçevesinin denetimlerinin görünümün (biçimi)](./leftindent-element-for-frame-for-controls-for-view-format.md)

[RightIndent öğesi çerçevesinin denetimlerinin görünümün (biçimi)](./rightindent-element-for-frame-for-controls-for-view-format.md)

[CustomItem öğesi görünümü (biçimi) için denetimleri için CustomEntry için](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
