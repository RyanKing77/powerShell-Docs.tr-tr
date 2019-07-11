---
title: ValidateLength özniteliği bildirimi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: a25fa2410fcc6803563573596af1bc99052c3ffa
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735097"
---
# <a name="validatelength-attribute-declaration"></a>ValidateLength Özniteliği Bildirimi

ValidateLength öznitelik karakter cmdlet parametresi olan bir bağımsız değişken için minimum ve maksimum sayısını belirtir. Bu öznitelik, Windows PowerShell işlevleri tarafından da kullanılabilir.

## <a name="syntax"></a>Sözdizimi

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parametreler

`MinLength` ([System.Int32](/dotnet/api/System.Int32)) gereklidir. En az bir izin verilen karakter sayısını belirtir.

`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) gereklidir. En fazla izin verilen karakter sayısını belirtir.

## <a name="remarks"></a>Açıklamalar

- Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [bildirmek giriş doğrulama kuralları nasıl](./how-to-validate-parameter-input.md).

- Bu öznitelik kullanıldığında, karşılık gelen parametre bağımsız değişkenini herhangi bir uzunlukta olabilir.

- Windows PowerShell çalışma zamanı, aşağıdaki koşullarda bir hata oluşturur:

    - Zaman değerini `MaxLength` öznitelik parametresi değerini azdır `MinLength` parametre özniteliği.

    - Zaman `MaxLength` öznitelik parametresi 0 olarak ayarlanır.

    - Ne zaman bağımsız değişken bir dize değil.

- ValidateLength özniteliği tarafından tanımlanan [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) sınıfı.

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
