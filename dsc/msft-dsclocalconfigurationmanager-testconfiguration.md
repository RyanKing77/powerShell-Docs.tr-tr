---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının TestConfiguration yöntemi
ms.openlocfilehash: 2df04d317bd5e7a5c2a713d92be57c5c9a9f5e8c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219020"
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

*configurationData* \[içinde\] confuguration için ortam verileri.

*InDesiredState* \[çıkışı\] getirisi, yönetilen düğüm yapılandırması belgesi tarafından belirtilen durumda olup olmadığını belirtir.

*ResourcesInDesiredState* \[çıkışı\] getirisi, katıştırılmış örneğini içeren **MSFT_ResourceInDesiredState** istenilen durumda olan kaynakların belirten sınıf.

*ResourcesNotInDesiredState* \[çıkışı\] getirisi, katıştırılmış örneğini içeren **MSFT_ResourceNotInDesiredState** istenilen durumda olmayan kaynakları belirleyen sınıf.

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