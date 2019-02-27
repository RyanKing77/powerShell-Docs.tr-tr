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
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="6c8c5-102">ValidateSet Özniteliği Bildirimi</span><span class="sxs-lookup"><span data-stu-id="6c8c5-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="6c8c5-103">ValidateSetAttribute özniteliği bir cmdlet parametresi olan bir bağımsız değişken için olası değerler belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c8c5-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="6c8c5-104">Bu öznitelik, Windows PowerShell işlevleri tarafından da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c8c5-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="6c8c5-105">Bu öznitelik belirtildiğinde, çalışma zamanı Windows PowerShell cmdlet parametresi için sağlanan bağımsız değişken bir öğedeki belirtilen öğe kümesi eşleşip eşleşmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="6c8c5-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="6c8c5-106">Cmdlet'i, yalnızca küme içindeki bir öğeyi parametre bağımsız değişkenini eşleşmesi durumunda çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="6c8c5-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="6c8c5-107">Eşleşme bulunursa, Windows PowerShell çalışma zamanı tarafından bir hata oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6c8c5-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="6c8c5-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c8c5-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="6c8c5-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c8c5-109">Parameters</span></span>

<span data-ttu-id="6c8c5-110">`ValidValues` ([System.String](/dotnet/api/System.String)) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6c8c5-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="6c8c5-111">Geçerli parametre öğesi değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c8c5-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="6c8c5-112">Aşağıdaki örnek, bir öğe veya birden fazla öğe belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6c8c5-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="6c8c5-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) isteğe bağlı parametre adı.</span><span class="sxs-lookup"><span data-stu-id="6c8c5-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="6c8c5-114">Varsayılan değer olan `true` çalışması göz ardı edilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c8c5-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="6c8c5-115">Değerini `false` cmdlet büyük küçük harfe duyarlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="6c8c5-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="6c8c5-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c8c5-116">Remarks</span></span>

- <span data-ttu-id="6c8c5-117">Bu öznitelik, parametre yalnızca bir kez kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c8c5-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="6c8c5-118">Parametre değeri bir dizi ise, dizinin her öğesi bir öğe, öznitelik kümesinin eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c8c5-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="6c8c5-119">ValidateSetAttribute özniteliği tarafından tanımlanan [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6c8c5-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c8c5-120">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6c8c5-120">See Also</span></span>

[<span data-ttu-id="6c8c5-121">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="6c8c5-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="6c8c5-122">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="6c8c5-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
