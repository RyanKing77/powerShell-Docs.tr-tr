---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: EnableDebugConfiguration yöntemi
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727140"
---
# <a name="enabledebugconfiguration-method"></a>EnableDebugConfiguration yöntemi

DSC kaynak hata ayıklamasını etkinleştirir.

## <a name="syntax"></a>Sözdizimi

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a>Parametreler

*BreakAll* \[içinde\] kaynak betiği her satırında bir kesme noktası ayarlar.

## <a name="return-value"></a>Dönüş değeri

Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar

Statik bir yöntem budur.

## <a name="requirements"></a>Gereksinimler

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Ayrıca bkz.

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
