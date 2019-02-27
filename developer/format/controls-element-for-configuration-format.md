---
title: (Biçimi) için yapılandırma öğesi denetimlerini | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850438"
---
# <a name="controls-element-for-configuration-format"></a>Yapılandırma için Denetimler Öğesi (Biçim)

Tüm biçimlendirme dosya görünümler tarafından kullanılabilen ortak denetimleri tanımlar.

Yapılandırma öğesi (biçimi) denetimleri öğesi yapılandırma (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `Controls` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Yapılandırma (biçimi) için denetimleri için Denetim öğesi](./control-element-for-controls-for-configuration-format.md)|Gerekli öğe.<br /><br /> Tüm biçimlendirme dosya görünümler tarafından kullanılan ortak bir denetimi tanımlar.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Yapılandırma öğesi (biçimi)](./configuration-element-format.md)|Biçimlendirme bir dosyanın üst düzey öğesi temsil eder.|

## <a name="remarks"></a>Açıklamalar

Herhangi bir sayıda ortak denetimleri oluşturabilirsiniz. Her denetim için Denetim ve denetim bileşenlerinin başvurmak için kullanılan adı belirtmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz:

[Yapılandırma öğesi (biçimi)](./configuration-element-format.md)

[Yapılandırma (biçimi) için denetimleri için Denetim öğesi](./control-element-for-controls-for-configuration-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
