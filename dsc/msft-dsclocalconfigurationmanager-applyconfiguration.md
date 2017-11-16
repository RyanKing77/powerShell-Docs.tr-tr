---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının ApplyConfiguration yöntemi"
ms.openlocfilehash: febaf972a2a452eb9aaf3ec7fbc5e41f3f463a58
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
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

*zorla* \[içinde\]  
Bu ise **doğru**, bekleyen bir yapılandırma olsa bile geçerli yapılandırmasını yeniden.

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

 

 



