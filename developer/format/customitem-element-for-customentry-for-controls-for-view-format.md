---
title: CustomItem öğesi görünümü (biçimi) için denetimleri için CustomEntry için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846539"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>Görünüm için Denetimler için CustomEntry için CustomItem Öğesi (Biçim)

Hangi veri denetimi tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) denetimleri (biçimi) öğesi denetim öğesi denetimi için CustomEntries öğesi görünümü (biçimi) için denetimleri için özel denetim öğesi görünümü (biçimi) için denetimleri için Özel denetim CustomEntry öğesinin CustomEntries CustomEntry Görünüm (biçimi) için denetimleri için görüntüleme (biçimi) CustomItem öğesinin denetimleri için görüntüleme (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomItem` öğesi. Daha fazla bilgi için açıklamalara bakın.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ExpressionBinding öğesi görünümü (biçimi) için denetimleri için CustomItem için](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Denetimi tarafından görüntülenen verileri tanımlar.|
|[Çerçeve öğesi görünümü (biçimi) için denetimleri için CustomItem için](./frame-element-for-customitem-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar.|
|[Yeni satır öğesi görünümü (biçimi) için denetimleri için CustomItem için](./newline-element-for-customitem-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Boş bir satır denetimi görüntüye ekler.|
|[Metin öğesi görünümü (biçimi) için denetimleri için CustomItem için](./text-element-for-customitem-for-controls-for-view-format.md)|İsteğe bağlı öğe.<br /><br /> Parantez veya parantez gibi bir metin denetimi görüntüye ekler.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CustomEntry öğesi görünümü (biçimi) için denetimleri için CustomEntries için](./customentry-element-for-customentries-for-controls-for-view-format.md)|Denetim tanımını sağlar.|

## <a name="remarks"></a>Açıklamalar

Alt öğeleri belirtirken `CustomItem` öğesi, aşağıdakileri göz önünde bulundurun:

- Alt öğeleri aşağıdaki sırayla eklenmelidir: `ExpressionBinding`, `NewLine`, `Text`, ve `Frame`.

- Belirtebileceğiniz dizileri sayısı maksimum sınırı yoktur.

- Her sırada sayısı maksimum sınırı yoktur `ExpressionBinding` öğeleri kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz:

[ExpressionBinding öğesi görünümü (biçimi) için denetimleri için CustomItem için](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Çerçeve öğesi görünümü (biçimi) için denetimleri için CustomItem için](./frame-element-for-customitem-for-controls-for-view-format.md)

[Yeni satır öğesi görünümü (biçimi) için denetimleri için CustomItem için](./newline-element-for-customitem-for-controls-for-view-format.md)

[Metin öğesi görünümü (biçimi) için denetimleri için CustomItem için](./text-element-for-customitem-for-controls-for-view-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
