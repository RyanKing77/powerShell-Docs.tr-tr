---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: ResourceTest yöntemi
ms.openlocfilehash: ff06fd645a94055e79aa0f8d20f2f06e16483720
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727080"
---
# <a name="resourcetest-method"></a>ResourceTest yöntemi

Doğrudan çağıran **Test** DSC kaynağı yöntemi.

## <a name="syntax"></a>Sözdizimi

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a>Parametreler

*ResourceType* \[içinde\] çağırmak için kaynağın adı.

*ModuleName* \[içinde\] çağırmak için kaynak içeren modül adı.

*resourceProperty* \[içinde\] kaynak özellik adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir. Kullanım [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet'ini kaynak özelliklerini ve bunların türlerini keşfedin.

*InDesiredState* \[kullanıma\] getirisi, bu özellik kümesine **true** hedef düğüm istenen durumda ise.

## <a name="return-value"></a>Dönüş değeri

Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar

Statik bir yöntem budur.

## <a name="requirements"></a>Gereksinimler

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Ayrıca bkz.

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
