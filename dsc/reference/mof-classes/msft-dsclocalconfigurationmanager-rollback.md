---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Geri alma yöntemi
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727030"
---
# <a name="rollback-method"></a>Geri alma yöntemi

Yeniden yapılandırma, önceki bir sürüme yapar.

## <a name="syntax"></a>Sözdizimi

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a>Parametreler

*configurationNumber* \[içinde\] istenen yapılandırmanın belirtir.

## <a name="return-value"></a>Dönüş değeri

Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar

Statik bir yöntem budur.

## <a name="requirements"></a>Gereksinimler

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Ayrıca bkz.

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
