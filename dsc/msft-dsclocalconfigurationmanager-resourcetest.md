---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının ResourceTest yöntemi"
ms.openlocfilehash: 73d7d543505a3768a0660084345d3858e055514f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager sınıfının ResourceTest yöntemi

Doğrudan çağıran **Test** DSC kaynağı yöntemi.

<a name="syntax"></a>Sözdizimi
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a>Parametreler
----------

*ResourceType* \[içinde\]  
Çağrılacak kaynağının adı.

*ModuleName* \[içinde\]  
Aranacak kaynak içeren modülü adı.

*resourceProperty* \[içinde\]  
Kaynak özelliği adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir. Kullanım [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) kaynak özelliklerini ve bunların türlerini bulmak için cmdlet.

*InDesiredState* \[çıkışı\]  
Getirisi, bu özelliği ayarlamak **true** hedef düğüm istenen durumdaysa.

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


 

 



