---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: SendConfigurationApplyAsync yöntemi
ms.openlocfilehash: c0e6dc9418757ee719e848fa8e7006dd73d91ad8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734310"
---
# <a name="sendconfigurationapplyasync-method"></a>SendConfigurationApplyAsync yöntemi

Yapılandırma belgelerini yönetilen düğüme zaman uyumsuz olarak gönderir ve yapılandırmayı uygulamak için yapılandırma aracısı kullanır.

## <a name="syntax"></a>Sözdizimi

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a>Parametreler

*ConfigurationData* \[içinde\] ortam verilerini.

*zorla* \[içinde\] **true** durdurmak için yapılandırmayı zorla uygulamak için.

*JobId* \[içinde\] yapılandırma göndermek istediğiniz işin kimliği.

## <a name="return-value"></a>Dönüş değeri

Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar

Statik bir yöntem budur.

## <a name="requirements"></a>Gereksinimler

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Ayrıca bkz.

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
