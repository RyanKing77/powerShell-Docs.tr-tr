---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationResultOutput yöntemi
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893952"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationResultOutput yöntemi

Belirli bir işi ile ilişkili yapılandırma aracı çıkış alır.

## <a name="syntax"></a>Sözdizimi

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
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

## <a name="see-also"></a>Ayrıca bkz:

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)