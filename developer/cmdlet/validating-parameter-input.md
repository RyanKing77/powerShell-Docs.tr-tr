---
title: Parametre girişi doğrulama | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429848"
---
# <a name="validating-parameter-input"></a>Parametre Girişini Doğrulama

PowerShell cmdlet parametreleri, çeşitli şekillerde geçirilecek bağımsız değişkenler doğrulayabilirsiniz.
PowerShell, uzunluğu, aralığı ve bağımsız değişken karakter desenini doğrulayabilirsiniz.
Bu bağımsız değişkenler kullanılabilir (sayı) sayısını doğrulayabilirsiniz.
Bu doğrulama kuralları, cmdlet sınıfın genel özellikleri parametre özniteliği ile bildirilen doğrulama öznitelikleri tarafından tanımlanır.

Bir parametre bağımsız değişkenini doğrulamak için cmdlet çalıştırılmadan önce parametresinin değerini doğrulamak için doğrulama öznitelikleri tarafından sağlanan bilgileri PowerShell çalışma zamanı kullanır.
Parametre girişi geçerli değil, kullanıcı bir hata iletisi alır.
Her doğrulama parametre PowerShell tarafından zorlanan bir doğrulama kuralı tanımlar.

PowerShell aşağıdaki özniteliklerine dayalı doğrulama kuralları zorlar.

### <a name="validatecount"></a>ValidateCount

Bir parametre kabul edebilen bağımsız değişkenleri minimum ve maksimum sayısını belirtir.
Daha fazla bilgi için [ValidateCount özniteliği bildirimi](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Parametre bağımsız değişkendeki karakter minimum ve maksimum sayısını belirtir.
Daha fazla bilgi için [ValidateLength özniteliği bildirimi](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Parametre bağımsız değişkenini onaylayan bir normal ifade belirtir.
Daha fazla bilgi için [ValidatePattern özniteliği bildirimi](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Parametre bağımsız değişkenin minimum ve maksimum değerleri belirtir.
Daha fazla bilgi için [ValidateRange özniteliği bildirimi](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Parametre bağımsız değişkeni için geçerli değerleri belirtir.
Daha fazla bilgi için [ValidateSet özniteliği bildirimi](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Ayrıca bkz:

[Parametre girişi doğrulama](./how-to-validate-parameter-input.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
