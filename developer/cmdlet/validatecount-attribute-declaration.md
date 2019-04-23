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
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59983907"
---
# <a name="validatecount-attribute-declaration"></a>ValidateCount Özniteliği Bildirimi

ValidateCount öznitelik bağımsız değişkenleri bir cmdlet parametresi için izin verilen minimum ve maksimum sayısını belirtir.

## <a name="syntax"></a>Sözdizimi

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parametreler

`MinLength` ([System.Int32][]) gereklidir. En az sayıda bağımsız değişken belirtir.

`MaxLength`([System.Int32][]) gereklidir. En fazla sayıda bağımsız değişken belirtir.

## <a name="remarks"></a>Açıklamalar

- Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [bir bağımsız değişken sayısı doğrulama][].

- Bu öznitelik değil çağrıldığında karşılık gelen bir cmdlet parametresi herhangi bir sayıda bağımsız değişken olabilir.

- Windows PowerShell çalışma zamanı, aşağıdaki koşullarda bir hata oluşturur:

    - `MinLength` Ve `MaxLength` öznitelik parametreleri türünde olmayan [System.Int32][].

    - Değerini `MaxLength` öznitelik parametresi değerini azdır `MinLength` parametre özniteliği.

- ValidateCount özniteliği tarafından tanımlanan [System.Management.Automation.ValidateCountAttribute][] sınıfı.

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.ValidateCountAttribute][]

[Bir bağımsız değişken sayısı doğrulama][]

[Bir Windows PowerShell cmdlet'i yazma][]

[Bir bağımsız değişken sayısı doğrulama]: how-to-validate-an-argument-count.md
[Bir Windows PowerShell cmdlet'i yazma]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
