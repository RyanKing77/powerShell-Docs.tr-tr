---
title: ValidateCount özniteliği bildirimi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 4e0be34b6f7a56dcf02a4381de4d2a5d08db14df
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794458"
---
# <a name="validatecount-attribute-declaration"></a>ValidateCount Özniteliği Bildirimi

ValidateCount öznitelik bağımsız değişkenleri bir cmdlet parametresi için izin verilen minimum ve maksimum sayısını belirtir.

## <a name="syntax"></a>Sözdizimi

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parametreler

`MinLength` ([System.Int32](/dotnet/api/System.Int32)) gereklidir. En az sayıda bağımsız değişken belirtir.

`MaxLength`([System.Int32](/dotnet/api/System.Int32)) gereklidir. En fazla sayıda bağımsız değişken belirtir.

## <a name="remarks"></a>Açıklamalar

- Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [bildirmek giriş doğrulama kuralları nasıl](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).

- Bu öznitelik değil çağrıldığında karşılık gelen bir cmdlet parametresi herhangi bir sayıda bağımsız değişken olabilir.

- Windows PowerShell çalışma zamanı, aşağıdaki koşullarda bir hata oluşturur:

    - `MinLength` Ve `MaxLength` öznitelik parametreleri türünde olmayan [System.Int32](/dotnet/api/System.Int32).

    - Değerini `MaxLength` öznitelik parametresi değerini azdır `MinLength` parametre özniteliği.

- ValidateCount özniteliği tarafından tanımlanan [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) sınıfı.

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount)

[Nasıl giriş doğrulama kuralları](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
