---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının ApplyConfiguration yöntemi
ms.openlocfilehash: ef8488246b2c8614452d32009e45535f0ff2e184
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222148"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager sınıfının ApplyConfiguration yöntemi

Bekleyen yapılandırmayı uygulamak için yapılandırma Aracısı'nı kullanır.

Bekleyen yapılandırma yoksa, bu yöntem geçerli yapılandırmasını yeniden uygular.


## <a name="syntax"></a>Sözdizimi
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parametreler
----------

*zorla* \[içinde\] bu ise **doğru**, bekleyen bir yapılandırma olsa bile geçerli yapılandırmasını yeniden.

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