---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: ApplyConfiguration yöntemi
ms.openlocfilehash: 0425b9a7db37e421830ba37da8f5c0a4877a1b72
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727186"
---
# <a name="applyconfiguration-method"></a>ApplyConfiguration yöntemi

Yapılandırma Aracı, bekleyen yapılandırmayı uygulamak için kullanır.

Bekleyen herhangi bir yapılandırma varsa, bu yöntem geçerli yapılandırmasını yeniden uygular.

## <a name="syntax"></a>Sözdizimi

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parametreler

*zorla* \[içinde\] buysa **true**, bekleyen bir yapılandırma olsa bile geçerli yapılandırmasını yeniden uygulanır.

## <a name="return-value"></a>Dönüş değeri

Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar

Statik bir yöntem budur.

## <a name="requirements"></a>Gereksinimler

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Ayrıca bkz.

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
