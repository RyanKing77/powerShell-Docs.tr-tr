---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının PerformRequiredConfigurationChecks yöntemi
ms.openlocfilehash: c3fdaa23875815b1cf5cbf0b6e21c633e00664aa
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager sınıfının PerformRequiredConfigurationChecks yöntemi

Görev Zamanlayıcısı'nı kullanarak bir tutarlılık denetimi başlatır.

<a name="syntax"></a>Sözdizimi
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a>Parametreler
----------

*Bayrakları* \[içinde\] çalıştırmak için tutarlılık denetimi türünü belirten bir bit maskesi. Aşağıdaki değerler geçerlidir ve bit kullanılarak birleştirilebilir **veya** işlemi:

|Değer |Açıklama |
|:--- |:---|
|**1** | Normal tutarlılık denetimi. |
|**2** | Tutarlılık denetimi devamlılık bir yeniden başlatma işleminden sonra. Bu değer diğer değerlerle birleştirilmemelidir. |
|**4** | Yapılandırma meta yapılandırmasını düğümü için belirtilen çekme sunucusundan çekilen. Bu değer her zaman ile birleştirilmelidir **1**, değeri için **5**. |
|**8** | Durum rapor sunucusuna gönderir. |

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