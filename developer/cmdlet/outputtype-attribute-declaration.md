---
title: OutputType özniteliğini bildirimi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067612"
---
# <a name="outputtype-attribute-declaration"></a>OutputType Özniteliği Bildirimi

`OutputType` Öznitelik, bir cmdlet, işlev veya komut dosyası tarafından döndürülen .NET Framework türleri tanımlar.

## <a name="syntax"></a>Sözdizimi

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>Parametreler

Türü (`string[]` veya `Type[]`) gereklidir. Cmdlet'i işlevi veya komut dosyası tarafından döndürülen türlerini belirtir.

ParameterSetName (string[]) isteğe bağlı. Dönüş türleri belirtilen parametre kümeleri belirtir `type` parametresi.

providerCmdlet isteğe bağlı. İçinde belirtilen türlerle döndüren sağlayıcısı cmdlet belirtir `type` parametresi.

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
