---
title: ValidatePattern özniteliği bildirimi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067136"
---
# <a name="validatepattern-attribute-declaration"></a>ValidatePattern Özniteliği Bildirimi

ValidatePattern öznitelik bağımsız değişkeni bir cmdlet parametresi onaylayan bir normal ifade desenini belirtir. Bu öznitelik, Windows PowerShell işlevleri tarafından da kullanılabilir.

İçinde bir cmdlet ValidatePattern çağrıldığında, Windows PowerShell çalışma zamanı cmdlet parametresi bağımsız değişkeni bir dizeye dönüştürür ve ardından o dizeyi ValidatePattern özniteliği tarafından sağlanan desenle karşılaştırır. Dönüştürülmüş dize gösterimini bağımsız değişkeni ve belirtilen desenle eşleşiyorsa cmdlet çalıştırılır. Bunlar eşleşmiyorsa Windows PowerShell çalışma zamanı tarafından bir hata oluşturulur.

## <a name="syntax"></a>Sözdizimi

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>Parametreler

`RegexString` ([System.String](/dotnet/api/System.String)) gereklidir. Parametre bağımsız değişkenini onaylayan bir normal ifade belirtir.

Seçenekler ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) isteğe bağlı parametre adı. Bitsel bir birleşimi belirler [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) normal ifade seçenekleri belirten bayrak.

## <a name="remarks"></a>Açıklamalar

- Bu öznitelik, parametre yalnızca bir kez kullanılabilir.

- Kullanabileceğiniz `Option` daha fazla düzeni tanımlamak için öznitelik parametresi. Örneğin, deseni büyük küçük harfe duyarlı yapabilirsiniz.

- Bu öznitelik bir derlemeye uygulanmışsa, koleksiyondaki her öğe belirtilen desenle eşleşmelidir.

- ValidatePattern özniteliği tarafından tanımlanan [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) sınıfı.

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
