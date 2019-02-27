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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846147"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="97126-102">Diğer Ad Özniteliği Bildirimi</span><span class="sxs-lookup"><span data-stu-id="97126-102">Alias Attribute Declaration</span></span>

<span data-ttu-id="97126-103">Diğer ad özniteliği, bir cmdlet parametresi için farklı adlar belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="97126-103">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="97126-104">Farklı senaryolar için uygun olan farklı adlar sağlayabilirler veya diğer adları, parametre adı için kısayollar sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97126-104">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="97126-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97126-105">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="97126-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97126-106">Parameters</span></span>

<span data-ttu-id="97126-107">`aliasName` (String[]) Gerekli.</span><span class="sxs-lookup"><span data-stu-id="97126-107">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="97126-108">Virgülle ayrılmış takma adlar cmdlet parametresi için bir dizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="97126-108">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="97126-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="97126-109">Remarks</span></span>

- <span data-ttu-id="97126-110">Diğer öznitelik parametre özniteliği ile kullanıldığında bir cmdlet parametresi belirtin.</span><span class="sxs-lookup"><span data-stu-id="97126-110">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="97126-111">Bu öznitelikler bildirme hakkında daha fazla bilgi için bkz: [Cmdlet parametreleri bildirmek için nasıl](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="97126-111">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="97126-112">Her bir diğer ad, bir cmdlet'in içinde benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="97126-112">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="97126-113">Windows PowerShell için yinelenen diğer adlar denetlemez.</span><span class="sxs-lookup"><span data-stu-id="97126-113">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="97126-114">Diğer ad özniteliği, bir kez her bir cmdlet parametresi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97126-114">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="97126-115">Diğer ad özniteliği tarafından tanımlanan [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="97126-115">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="97126-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="97126-116">See Also</span></span>

[<span data-ttu-id="97126-117">Parametre diğer adları</span><span class="sxs-lookup"><span data-stu-id="97126-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="97126-118">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="97126-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
