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
ms.openlocfilehash: 3a4c5f279ce8587eeb5d583376ea3d2286210b83
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794340"
---
# <a name="validatelength-attribute-declaration"></a>ValidateLength Özniteliği Bildirimi

ValidateLength öznitelik karakter cmdlet parametresi olan bir bağımsız değişken için minimum ve maksimum sayısını belirtir. Bu öznitelik, Windows PowerShell işlevleri tarafından da kullanılabilir.

## <a name="syntax"></a>Sözdizimi

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parametreler

`MinLength` ([System.Integer](/dotnet/api/System.Integer)) gereklidir. En az bir izin verilen karakter sayısını belirtir.

`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) gereklidir. En fazla izin verilen karakter sayısını belirtir.

## <a name="remarks"></a>Açıklamalar

- Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [bildirmek giriş doğrulama kuralları nasıl](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).

- Bu öznitelik kullanıldığında, karşılık gelen parametre bağımsız değişkenini herhangi bir uzunlukta olabilir.

- Windows PowerShell çalışma zamanı, aşağıdaki koşullarda bir hata oluşturur:

    - Zaman değerini `MaxLength` öznitelik parametresi değerini azdır `MinLength` parametre özniteliği.

    - Zaman `MaxLength` öznitelik parametresi 0 olarak ayarlanır.

    - Ne zaman bağımsız değişken bir dize değil.

- ValidateLength özniteliği tarafından tanımlanan [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) sınıfı.

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
