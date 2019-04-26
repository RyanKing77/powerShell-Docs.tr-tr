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
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="5913f-102">OutputType Özniteliği Bildirimi</span><span class="sxs-lookup"><span data-stu-id="5913f-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="5913f-103">`OutputType` Öznitelik, bir cmdlet, işlev veya komut dosyası tarafından döndürülen .NET Framework türleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5913f-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="5913f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5913f-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="5913f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5913f-105">Parameters</span></span>

<span data-ttu-id="5913f-106">Türü (`string[]` veya `Type[]`) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5913f-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="5913f-107">Cmdlet'i işlevi veya komut dosyası tarafından döndürülen türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5913f-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="5913f-108">ParameterSetName (string[]) isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5913f-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="5913f-109">Dönüş türleri belirtilen parametre kümeleri belirtir `type` parametresi.</span><span class="sxs-lookup"><span data-stu-id="5913f-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="5913f-110">providerCmdlet isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5913f-110">providerCmdlet Optional.</span></span> <span data-ttu-id="5913f-111">İçinde belirtilen türlerle döndüren sağlayıcısı cmdlet belirtir `type` parametresi.</span><span class="sxs-lookup"><span data-stu-id="5913f-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="5913f-112">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="5913f-112">See Also</span></span>

[<span data-ttu-id="5913f-113">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="5913f-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
