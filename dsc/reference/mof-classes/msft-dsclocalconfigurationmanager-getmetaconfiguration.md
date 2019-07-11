---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: GetMetaConfiguration yöntemi
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734434"
---
# <a name="getmetaconfiguration-method"></a>GetMetaConfiguration yöntemi

Yapılandırma Aracı denetlemek için kullanılan yerel Configuration Manager ayarlarını alır.

## <a name="syntax"></a>Sözdizimi

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a>Parametreler

*MetaConfiguration* \[kullanıma\] getirisi, katıştırılmış örneğini içeren **MSFT_DSCMetaConfiguration** ayarları tanımlayan sınıf.

## <a name="return-value"></a>Dönüş değeri

Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar

Statik bir yöntem budur.

## <a name="requirements"></a>Gereksinimler

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Ayrıca bkz.

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
