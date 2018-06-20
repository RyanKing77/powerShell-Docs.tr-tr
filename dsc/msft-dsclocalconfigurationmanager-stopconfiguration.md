---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının StopConfiguration yöntemi
ms.openlocfilehash: aaed29cb81e2079c4673b621b81c52e109aa7b48
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218884"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager sınıfının StopConfiguration yöntemi

Devam ediyor yapılandırma değişikliği durdurur.

<a name="syntax"></a>Sözdizimi
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a>Parametreler
----------

*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.

## <a name="return-value"></a>Dönüş değeri
------------

Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar

Bu statik bir yöntemdir.

## <a name="requirements"></a>Gereksinimler
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>Ayrıca bkz:


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)