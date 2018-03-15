---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının ResourceSet yöntemi"
ms.openlocfilehash: 3486ef559102929f8d05994a4bf6e45d49a0c140
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager sınıfının ResourceSet yöntemi

Doğrudan çağıran **ayarlamak** DSC kaynağı yöntemi.

<a name="syntax"></a>Sözdizimi
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a>Parametreler
----------

*ResourceType* \[in\]  
Çağrılacak kaynağının adı.

*ModuleName* \[in\]  
Aranacak kaynak içeren modülü adı.

*resourceProperty* \[in\]  
Kaynak özelliği adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir. Kullanım [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) kaynak özelliklerini ve bunların türlerini bulmak için cmdlet.

*RebootRequired* \[çıkışı\]  
Getirisi, bu özelliği ayarlamak **true** hedef düğümün yeniden başlatılması gerekiyorsa.

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

 

 



