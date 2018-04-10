---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının RemoveConfiguration yöntemi
ms.openlocfilehash: e0ae8a50212b70841d210d7b2d666a2855218d1a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager sınıfının RemoveConfiguration yöntemi

Yapılandırma dosyalarını kaldırır.

<a name="syntax"></a>Sözdizimi
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a>Parametreler
----------

*Aşama* \[içinde\] kaldırmak için hangi yapılandırma belgesini belirtir. Aşağıdaki değerler geçerlidir:

|Değer |Açıklama |
|:--- |:---|
|**1** | **Geçerli** yapılandırma belgesi (current.mof). |
|**2** | **Bekleyen** yapılandırma belgesi (pending.mof).  |
|**4** | **Önceki** yapılandırma belgesi (previous.mof). |

*Zorla* \[içinde\] **true** yapılandırma kaldırılmasını zorla için.

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