---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: PerformRequiredConfigurationChecks yöntemi
ms.openlocfilehash: 909e3a48d08e0220ab0efc6a03bea7ead5d9843e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734413"
---
# <a name="performrequiredconfigurationchecks-method"></a>PerformRequiredConfigurationChecks yöntemi

Görev Zamanlayıcısı'nı kullanarak bir tutarlılık denetimi başlatır.

## <a name="syntax"></a>Sözdizimi

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a>Parametreler

*Bayrakları* \[içinde\] çalıştırmak için tutarlılık denetimi türünü belirten bir bit maskesi. Aşağıdaki değerler geçerlidir ve bit düzeyinde kullanarak birleştirilebilir **veya** işlemi:

|Değer |Açıklama |
|:--- |:---|
|**1** | Normal bir tutarlılık denetimi. |
|**2** | Bir tutarlılık denetimi bir yeniden başlatma işleminden sonra devam etmesi. Bu değer, diğer değerlerle birleştirilmemelidir. |
|**4** | Çekme sunucusundan metaconfiguration düğümü için belirtilen yapılandırma çekilmesi. Bu değer her zaman ile birleştirilmelidir **1**, değeri için **5**. |
|**8** | Durum rapor sunucusuna gönderir. |

## <a name="return-value"></a>Dönüş değeri

Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar

Statik bir yöntem budur.

## <a name="requirements"></a>Gereksinimler

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Ayrıca bkz.

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
