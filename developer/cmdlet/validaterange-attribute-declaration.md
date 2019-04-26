---
title: ValidateRange özniteliği bildirimi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067119"
---
# <a name="validaterange-attribute-declaration"></a>ValidateRange Özniteliği Bildirimi

ValidateRange öznitelik minimum ve maksimum değerleri (aralık) için cmdlet parametre bağımsız değişkenini belirtir. Bu öznitelik, Windows PowerShell işlevleri tarafından da kullanılabilir.

## <a name="syntax"></a>Sözdizimi

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>Parametreler

`MinRange` ([System.Object](/dotnet/api/system.object)) gereklidir. İzin verilen minimum değer belirtir.

`MaxRange` ([System.Object](/dotnet/api/system.object)) gereklidir. İzin verilen en büyük değerini belirtir.

## <a name="remarks"></a>Açıklamalar

- Windows PowerShell çalışma zamanı bir yapı hatası oluşturur, değerini `MinRange` parametresi değerinden büyükse `MaxRange` parametresi.

- Windows PowerShell çalışma zamanı aşağıdaki koşullar altında bir doğrulama hatası oluşturur:

    - Bağımsız değişkenin değeri olduğunda küçüktür `MinRange` sınırı veya bu değerden `MaxRange` sınırı.

    - Bağımsız değişken olmadığında aynı türde `MinRange` ve `MaxRange` parametreleri.

- ValidateRange özniteliği tarafından tanımlanan [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) sınıfı.

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
