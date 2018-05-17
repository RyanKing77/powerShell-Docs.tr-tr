---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationStatus yöntemi
ms.openlocfilehash: 725b1a2a62510a4e9b59aabdec8a7e502c737bfc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationStatus yöntemi

Yapılandırma durumu geçmişi alın.

<a name="syntax"></a>Sözdizimi
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a>Parametreler
----------

*Tüm* \[içinde\] **true** bu yöntem tüm ilgili bilgileri yapılandırma çalıştıran makinede döndürmelidir, yapılandırma uygulama ve tutarlılık denetimi dahil olmak üzere.

*configurationStatus* \[çıkışı\] getirisi, katıştırılmış örneğini içeren **MSFT_DSCConfigurationStatus** ayarları tanımlayan sınıf.

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