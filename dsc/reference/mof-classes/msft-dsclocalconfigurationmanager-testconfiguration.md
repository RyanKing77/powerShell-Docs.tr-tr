---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: TestConfiguration yöntemi
ms.openlocfilehash: 384134212e3b29b63dc045aee4b708c87c970302
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726950"
---
# <a name="testconfiguration-method"></a>TestConfiguration yöntemi

Yapılandırma belgelerini yönetilen düğüme gönderir ve belgeyi karşı geçerli yapılandırmasını doğrular.

## <a name="syntax"></a>Sözdizimi

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a>Parametreler

*configurationData* \[içinde\] confuguration ortam verileri.

*InDesiredState* \[kullanıma\] getirisi, yönetilen düğüme yapılandırma belgesi tarafından belirtilen durumda olup olmadığını belirtir.

*ResourcesInDesiredState* \[kullanıma\] getirisi, katıştırılmış örneğini içeren **MSFT_ResourceInDesiredState** istenen durumda olan kaynakların belirten sınıf.

*ResourcesNotInDesiredState* \[kullanıma\] getirisi, katıştırılmış örneğini içeren **MSFT_ResourceNotInDesiredState** istenen durumda olmayan kaynaklar belirten sınıf.

## <a name="return-value"></a>Dönüş değeri

Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar

Statik bir yöntem budur.

## <a name="requirements"></a>Gereksinimler

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Ayrıca bkz.

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
