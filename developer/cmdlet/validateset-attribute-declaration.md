---
title: ValidateSet özniteliği bildirimi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850459"
---
# <a name="validateset-attribute-declaration"></a>ValidateSet Özniteliği Bildirimi

ValidateSetAttribute özniteliği bir cmdlet parametresi olan bir bağımsız değişken için olası değerler belirtir. Bu öznitelik, Windows PowerShell işlevleri tarafından da kullanılabilir.

Bu öznitelik belirtildiğinde, çalışma zamanı Windows PowerShell cmdlet parametresi için sağlanan bağımsız değişken bir öğedeki belirtilen öğe kümesi eşleşip eşleşmediğini belirler. Cmdlet'i, yalnızca küme içindeki bir öğeyi parametre bağımsız değişkenini eşleşmesi durumunda çalıştırılır. Eşleşme bulunursa, Windows PowerShell çalışma zamanı tarafından bir hata oluşturulur.

## <a name="syntax"></a>Sözdizimi

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>Parametreler

`ValidValues` ([System.String](/dotnet/api/System.String)) gereklidir. Geçerli parametre öğesi değerleri belirtir. Aşağıdaki örnek, bir öğe veya birden fazla öğe belirtmek gösterilmektedir.

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) isteğe bağlı parametre adı. Varsayılan değer olan `true` çalışması göz ardı edilir gösterir. Değerini `false` cmdlet büyük küçük harfe duyarlı hale getirir.

## <a name="remarks"></a>Açıklamalar

- Bu öznitelik, parametre yalnızca bir kez kullanılabilir.

- Parametre değeri bir dizi ise, dizinin her öğesi bir öğe, öznitelik kümesinin eşleşmesi gerekir.

- ValidateSetAttribute özniteliği tarafından tanımlanan [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) sınıfı.

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
