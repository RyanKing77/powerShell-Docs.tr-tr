---
title: İçin yapılandırma (biçimi) için denetimleri için CustomEntry CustomItem öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851670"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>Yapılandırma Denetimleri için CustomEntry CustomItem Öğesi (Biçim)

Hangi veri denetimi tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) CustomItem öğesinin CustomEntry yapılandırması için denetimleri için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi

## <a name="syntax"></a>Sözdizimi

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomItem` öğesi. Daha fazla bilgi için açıklamalara bakın.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[İçin yapılandırma (biçimi) için denetimleri için CustomItem ExpressionBinding öğesi](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Denetimi tarafından görüntülenen verileri tanımlar.|
|[Çerçeve öğesi CustomItem yapılandırması (biçimi) için denetimleri için](./frame-element-for-customitem-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar.|
|[Yeni satır öğesi CustomItem yapılandırması (biçimi) için denetimleri için](./newline-element-for-customitem-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Boş bir satır denetimi görüntüye ekler.|
|[Denetimler için yapılandırma (biçimi) için CustomItem için metin öğesi](./text-element-for-customitem-for-controls-for-configuration-format.md)|İsteğe bağlı öğe.<br /><br /> Parantez veya parantez gibi bir metin denetimi görüntüye ekler.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Yapılandırma (biçimi) için denetimler için özel denetim için CustomEntry öğesi](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Denetim tanımını sağlar.|

## <a name="remarks"></a>Açıklamalar

Alt öğeleri belirtirken `CustomItem` öğesi, aşağıdakileri göz önünde bulundurun:

- Alt öğeleri aşağıdaki sırayla eklenmelidir: `ExpressionBinding`, `NewLine`, `Text`, ve `Frame`.

- Belirtebileceğiniz dizileri sayısı maksimum sınırı yoktur.

- Her sırada sayısı maksimum sınırı yoktur `ExpressionBinding` öğeleri kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz:

[İçin yapılandırma (biçimi) için denetimleri için CustomItem ExpressionBinding öğesi](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Çerçeve öğesi CustomItem yapılandırması (biçimi) için denetimleri için](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Yeni satır öğesi CustomItem yapılandırması (biçimi) için denetimleri için](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[Denetimler için yapılandırma (biçimi) için CustomItem için metin öğesi](./text-element-for-customitem-for-controls-for-configuration-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
