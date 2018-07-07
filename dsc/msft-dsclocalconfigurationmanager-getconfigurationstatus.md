---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationStatus yöntemi
ms.openlocfilehash: c66ccc4eefaef2d0c3a68fa8a96c5abb9bda6e4c
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893068"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationStatus yöntemi

Yapılandırma durumu geçmişi Al

## <a name="syntax"></a>Sözdizimi

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a>Parametreler

*Tüm* \[içinde\] **true** bu yöntem, yapılandırma makine üzerinde çalışan tüm hakkında bilgiler döndürmelidir, yapılandırma uygulama ve tutarlılık denetimi dahil olmak üzere.

*configurationStatus* \[kullanıma\] getirisi, katıştırılmış örneğini içeren **MSFT_DSCConfigurationStatus** ayarları tanımlayan sınıf.

## <a name="return-value"></a>Dönüş değeri

Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar

Statik bir yöntem budur.

## <a name="requirements"></a>Gereksinimler

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Ayrıca bkz:

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)