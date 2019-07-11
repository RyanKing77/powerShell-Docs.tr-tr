---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: GetConfiguration yöntemi
ms.openlocfilehash: eabc536cfe69abe1144ff031a6f64c09a772e638
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734532"
---
# <a name="getconfiguration-method"></a>GetConfiguration yöntemi

Yönetilen düğüme yapılandırma belgesi gönderir ve kullandığı **alma** yapılandırmayı uygulamak için yapılandırma aracısı yöntemi.

## <a name="syntax"></a>Sözdizimi

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a>Parametreler

*configurationData* \[içinde\] göndermek için yapılandırma verilerini belirtir.

*yapılandırmaları* \[kullanıma\] getirisi, yapılandırmaları katıştırılmış bir örneğini içerir.

## <a name="return-value"></a>Dönüş değeri

Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar

Statik bir yöntem budur.

## <a name="requirements"></a>Gereksinimler

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Ayrıca bkz.

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
