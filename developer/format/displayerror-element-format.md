---
title: DisplayError öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066269"
---
# <a name="displayerror-element-format"></a>DisplayError Öğesi (Biçim)

Bir hata oluştuğunda bir veri parçasını görüntüleme dizesi #ERR görüntüleneceğini belirtir.

Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi) DisplayError öğesi (biçimi)

## <a name="syntax"></a>Sözdizimi

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `DisplayError` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[DefaultSettings öğesi (biçimi)](./defaultsettings-element-format.md)|Biçimlendirme dosyanın tüm görünümleri için geçerli genel ayarlarını tanımlar.|

## <a name="remarks"></a>Açıklamalar

Varsayılan olarak, bir veri parçasını görüntülemeye çalışırken bir hata oluştuğunda verilerin konumu boş bırakılır. Bu öğe #ERR dize true olarak ayarlandığında görüntülenir.

## <a name="see-also"></a>Ayrıca bkz:

[DefaultSettings öğesi (biçimi)](./defaultsettings-element-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
