---
title: Denetim öğesi denetimleri için görüntüleme (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066779"
---
# <a name="control-element-for-controls-for-view--format"></a>Görünüm Denetimleri için Denetim Öğesi (Biçim)

Görünüm ve denetimin başvurmak için kullanılan ad tarafından kullanılabilecek bir denetimi tanımlar.

Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) öğesi (biçimi) denetim öğesi denetimleri için görüntüleme (biçimi) için denetler.

## <a name="syntax"></a>Sözdizimi

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `Control` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Name öğesi denetimi için Görünüm (biçimi)](./name-element-for-control-for-controls-for-view-format.md)|Gerekli öğe.<br /><br /> Denetimin adını belirtir.|
|[Özel denetim öğesi denetimi için Görünüm (biçimi) için denetimleri](./customcontrol-element-for-control-for-controls-for-view-format.md)|Gerekli öğe.<br /><br /> Bu görünüm tarafından kullanılan denetimini tanımlar.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Denetim öğesi (biçimi)](./controls-element-for-view-format.md)|Belirli bir görünüm tarafından kullanılabilen görünüm denetimlerini tanımlar.|

## <a name="remarks"></a>Açıklamalar

Bu denetim, şu öğeler tarafından belirtilebilir:

- [CustomControlName öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [CustomControlName öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [GroupBy (biçimi) için ExpressionBinding için CustomControlName öğesi](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [GroupBy (biçimi) için CustomControlName öğesi](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>Ayrıca bkz:

[Özel denetim öğesi denetimi için Görünüm (biçimi) için denetimleri](./customcontrol-element-for-control-for-controls-for-view-format.md)

[CustomControlName öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[CustomControlName öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[GroupBy (biçimi) için ExpressionBinding için CustomControlName öğesi](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy (biçimi) için ExpressionBinding için CustomControlName öğesi](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Denetim öğesi (biçimi)](./controls-element-for-view-format.md)

[Name öğesi denetimi için Görünüm (biçimi) için denetimleri](./name-element-for-control-for-controls-for-view-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
