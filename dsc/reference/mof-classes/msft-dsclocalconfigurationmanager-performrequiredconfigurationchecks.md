---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının PerformRequiredConfigurationChecks yöntemi
ms.openlocfilehash: b92eefb7fbea6d96afa31f6b802ba10fe20d4103
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078445"
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager sınıfının PerformRequiredConfigurationChecks yöntemi

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