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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847540"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="ff1ab-102">ValidateRange Özniteliği Bildirimi</span><span class="sxs-lookup"><span data-stu-id="ff1ab-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="ff1ab-103">ValidateRange öznitelik minimum ve maksimum değerleri (aralık) için cmdlet parametre bağımsız değişkenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff1ab-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="ff1ab-104">Bu öznitelik, Windows PowerShell işlevleri tarafından da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ff1ab-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="ff1ab-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff1ab-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="ff1ab-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff1ab-106">Parameters</span></span>

<span data-ttu-id="ff1ab-107">`MinRange` ([System.Object](/dotnet/api/system.object)) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ff1ab-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="ff1ab-108">İzin verilen minimum değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff1ab-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="ff1ab-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ff1ab-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="ff1ab-110">İzin verilen en büyük değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff1ab-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="ff1ab-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff1ab-111">Remarks</span></span>

- <span data-ttu-id="ff1ab-112">Windows PowerShell çalışma zamanı bir yapı hatası oluşturur, değerini `MinRange` parametresi değerinden büyükse `MaxRange` parametresi.</span><span class="sxs-lookup"><span data-stu-id="ff1ab-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="ff1ab-113">Windows PowerShell çalışma zamanı aşağıdaki koşullar altında bir doğrulama hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="ff1ab-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

    - <span data-ttu-id="ff1ab-114">Bağımsız değişkenin değeri olduğunda küçüktür `MinRange` sınırı veya bu değerden `MaxRange` sınırı.</span><span class="sxs-lookup"><span data-stu-id="ff1ab-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

    - <span data-ttu-id="ff1ab-115">Bağımsız değişken olmadığında aynı türde `MinRange` ve `MaxRange` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="ff1ab-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="ff1ab-116">ValidateRange özniteliği tarafından tanımlanan [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ff1ab-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff1ab-117">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ff1ab-117">See Also</span></span>

[<span data-ttu-id="ff1ab-118">System.Management.Automation.Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="ff1ab-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="ff1ab-119">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="ff1ab-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
