---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının GetConfiguration yöntemi
ms.openlocfilehash: 46eec896df643996bea5f2c371a9294034caae6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager sınıfının GetConfiguration yöntemi

Yapılandırma belgesini yönetilen düğüme gönderir ve kullandığı **almak** yapılandırmayı uygulamak için yapılandırma Aracısı'nın yöntemi.

<a name="syntax"></a>Sözdizimi
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a>Parametreler
----------

*configurationData* \[içinde\] göndermek için yapılandırma verilerini belirtir.

*yapılandırmaları* \[çıkışı\] getirisi, katıştırılmış yapılandırmaları örneğini içerir.

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