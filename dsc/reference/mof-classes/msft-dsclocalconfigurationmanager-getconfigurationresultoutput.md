---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: GetConfigurationResultOutput yöntemi
ms.openlocfilehash: 480e710ce1a208253f0e664474c3e9bab296066a
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727122"
---
# <a name="getconfigurationresultoutput-method"></a>GetConfigurationResultOutput yöntemi

Belirli bir işi ile ilişkili yapılandırma aracı çıkış alır.

## <a name="syntax"></a>Sözdizimi

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a>Parametreler

*JobId* \[içinde\] iş için çıktı verilerini almak için kimliği.

*resumeOutputBookmark* \[içinde\] çıkış bir önceki yer işareti gelen bir devamlılık olması gerektiğini belirtir.

*Çıkış* \[kullanıma\] belirtilen işin çıktısı.

## <a name="return-value"></a>Dönüş değeri

Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar

Statik bir yöntem budur.

## <a name="requirements"></a>Gereksinimler

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Ayrıca bkz.

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
