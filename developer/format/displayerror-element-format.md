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
ms.openlocfilehash: 431e5d8407b9f689a5224b329d8c7b52802e19e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846056"
---
# <a name="displayerror-element-format"></a>DisplayError Öğesi (Biçim)

Bir hata oluştuğunda bir veri parçasını görüntüleme dizesi #ERR görüntüleneceğini belirtir.

Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi) DisplayError öğesi (Frmat)

## <a name="syntax"></a>Sözdizimi

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `DisplayError` öğesi.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[DefaultSettings öğesi (biçimi)](./defaultsettings-element-format.md)|Biçimlendirme dosyanın tüm görünümleri için geçerli genel ayarlarını tanımlar.|

## <a name="remarks"></a>Açıklamalar

Varsayılan olarak, bir veri parçasını görüntülemeye çalışırken bir hata oluştuğunda verilerin konumu boş bırakılır. Bu öğe #ERR dize true olarak ayarlandığında görüntülenir.

## <a name="see-also"></a>Ayrıca bkz:

[DefaultSettings öğesi (biçimi)](./defaultsettings-element-format.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
