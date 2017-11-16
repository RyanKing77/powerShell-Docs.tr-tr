---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationResultOutput yöntemi"
ms.openlocfilehash: 09862fd3c19e1e517c9bf5df878113ba3f10d8a6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationResultOutput yöntemi

Belirli bir iş ile ilgili yapılandırma aracısı çıktısını alır.

<a name="syntax"></a>Sözdizimi
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a>Parametreler
----------

*JobId* \[içinde\]  
Proje çıktı verileri almak istediğiniz için kimliği.

*resumeOutputBookmark* \[içinde\]  
Çıktı devamlılığı önceki yer işareti gelen olması gerektiğini belirtir.

*Çıktı* \[çıkışı\]  
Belirtilen iş için çıktı.

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

 

 



