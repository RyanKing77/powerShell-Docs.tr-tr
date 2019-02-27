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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848807"
---
# <a name="validating-parameter-input"></a>Parametre Girişini Doğrulama

Windows PowerShell cmdlet parametreleri, çeşitli şekillerde geçirilecek bağımsız değişkenler doğrulayabilirsiniz. Windows PowerShell, uzunluğu, aralığı ve bağımsız değişken karakter desenini doğrulayabilirsiniz. Bu bağımsız değişkenler kullanılabilir (sayı) sayısını doğrulayabilirsiniz. Bu doğrulama kuralları, cmdlet sınıfın genel özellikleri parametre özniteliği ile bildirilen doğrulama öznitelikleri tarafından tanımlanır.

Bir parametre bağımsız değişkenini doğrulamak için cmdlet çalıştırılmadan önce parametresinin değerini doğrulamak için doğrulama öznitelikleri tarafından sağlanan bilgileri Windows PowerShell çalışma zamanı kullanır. Parametre girişi geçerli değil, kullanıcı bir hata iletisi alır. Windows PowerShell tarafından zorlanan bir doğrulama kuralı her doğrulama parametresi tanımlar.

Windows PowerShell aşağıdaki özniteliklerine dayalı doğrulama kuralları zorlar.

ValidateCount bir parametre kabul edebilen bağımsız değişkenleri minimum ve maksimum sayısını belirtir. Bu öznitelik bildirmek için kullanılan sözdizimi hakkında daha fazla bilgi için bkz. [ValidateCount özniteliği bildirimi](./validatecount-attribute-declaration.md).

ValidateLength parametre bağımsız değişkendeki karakter minimum ve maksimum sayısını belirtir. Bu öznitelik bildirmek için kullanılan sözdizimi hakkında daha fazla bilgi için bkz. [ValidateLength özniteliği bildirimi](./validatelength-attribute-declaration.md).

ValidatePattern parametre bağımsız değişkenini onaylayan bir normal ifade belirtir. Bu öznitelik bildirmek için kullanılan sözdizimi hakkında daha fazla bilgi için bkz. [ValidatePattern özniteliği bildirimi](./validatepattern-attribute-declaration.md).

ValidateRange parametre bağımsız değişkenin minimum ve maksimum değerleri belirtir. Bu öznitelik bildirmek için kullanılan sözdizimi hakkında daha fazla bilgi için bkz. [ValidateRange özniteliği bildirimi](./validaterange-attribute-declaration.md).

ValidateSet parametre bağımsız değişkeni için geçerli değerleri belirtir. Bu öznitelik bildirmek için kullanılan sözdizimi hakkında daha fazla bilgi için bkz. [ValidateSet özniteliği bildirimi](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Ayrıca bkz:

[Parametre girişi doğrulama](./how-to-validate-parameter-input.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
