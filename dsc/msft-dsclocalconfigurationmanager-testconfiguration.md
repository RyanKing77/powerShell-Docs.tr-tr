---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının TestConfiguration yöntemi"
ms.openlocfilehash: 8e9986837aaf41b1396a2399c58675bc51b0b708
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager sınıfının TestConfiguration yöntemi

Yönetilen düğüme yapılandırma belgesini gönderir ve geçerli yapılandırma belge karşı doğrular.

<a name="syntax"></a>Sözdizimi
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a>Parametreler
----------

*configurationData* \[içinde\]  
Ortam verilerini confuguration için.

*InDesiredState* \[çıkışı\]  
Getirisi, yönetilen düğüm yapılandırması belgesi tarafından belirtilen durumda olup olmadığını belirtir.

*ResourcesInDesiredState* \[çıkışı\]  
Getirisi, katıştırılmış örneğini içeren **MSFT_ResourceInDesiredState** istenilen durumda olan kaynakların belirten sınıf.

*ResourcesNotInDesiredState* \[çıkışı\]  
Getirisi, katıştırılmış örneğini içeren **MSFT_ResourceNotInDesiredState** istenilen durumda olmayan kaynakları belirleyen sınıf.

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


 

 



