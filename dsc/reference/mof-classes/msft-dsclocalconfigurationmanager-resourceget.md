---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: ResourceGet yöntemi
ms.openlocfilehash: dbe610dfcef5ef6c79783801ecb6fdb7408bdfa5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727117"
---
# <a name="resourceget-method"></a>ResourceGet yöntemi

Doğrudan çağıran **alma** DSC kaynağı yöntemi.

## <a name="syntax"></a>Sözdizimi

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a>Parametreler

*ResourceType* \[içinde\] çağırmak için kaynağın adı.

*ModuleName* \[içinde\] çağırmak için kaynak içeren modül adı.

*resourceProperty* \[içinde\] kaynak özellik adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir. Kullanım [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet'ini kaynak özelliklerini ve bunların türlerini keşfedin.

*yapılandırmaları* \[kullanıma\] getirisi, yapılandırmaları katıştırılmış bir örneğini içerir.

## <a name="return-value"></a>Dönüş değeri

Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar

Statik bir yöntem budur.

## <a name="requirements"></a>Gereksinimler

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Ayrıca bkz.

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
