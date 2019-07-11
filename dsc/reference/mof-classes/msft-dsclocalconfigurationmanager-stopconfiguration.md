---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: StopConfiguration yöntemi
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726993"
---
# <a name="stopconfiguration-method"></a>StopConfiguration yöntemi

Devam eden yapılandırma değişikliğini durdurur.

## <a name="syntax"></a>Sözdizimi

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parametreler

*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.

## <a name="return-value"></a>Dönüş değeri

Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar

Statik bir yöntem budur.

## <a name="requirements"></a>Gereksinimler

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Ayrıca bkz.

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
