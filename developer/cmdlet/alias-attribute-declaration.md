---
title: Diğer ad özniteliği bildirimi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068731"
---
# <a name="alias-attribute-declaration"></a>Diğer Ad Özniteliği Bildirimi

Diğer ad özniteliği, bir cmdlet parametresi için farklı adlar belirtmesini sağlar. Farklı senaryolar için uygun olan farklı adlar sağlayabilirler veya diğer adları, parametre adı için kısayollar sağlamak için kullanılabilir.

## <a name="syntax"></a>Sözdizimi

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>Parametreler

`aliasName` (String[]) Gerekli. Virgülle ayrılmış takma adlar cmdlet parametresi için bir dizi belirtir.

## <a name="remarks"></a>Açıklamalar

- Diğer öznitelik parametre özniteliği ile kullanıldığında bir cmdlet parametresi belirtin. Bu öznitelikler bildirme hakkında daha fazla bilgi için bkz: [Cmdlet parametreleri bildirmek için nasıl](./how-to-declare-cmdlet-parameters.md).

- Her bir diğer ad, bir cmdlet'in içinde benzersiz olmalıdır. Windows PowerShell için yinelenen diğer adlar denetlemez.

- Diğer ad özniteliği, bir kez her bir cmdlet parametresi için kullanılır.

- Diğer ad özniteliği tarafından tanımlanan [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) sınıfı.

## <a name="see-also"></a>Ayrıca bkz:

[Parametre diğer adları](./parameter-aliases.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
