---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının RollBack yöntemi
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405811"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager sınıfının RollBack yöntemi

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

## <a name="see-also"></a>Ayrıca bkz:

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)