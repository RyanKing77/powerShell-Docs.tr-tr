---
title: ValidateCount özniteliği bildirimi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 1a7b5ea340fe5212d003c97a9017278d6c631355
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849024"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="39ac2-102">ValidateCount Özniteliği Bildirimi</span><span class="sxs-lookup"><span data-stu-id="39ac2-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="39ac2-103">ValidateCount öznitelik bağımsız değişkenleri bir cmdlet parametresi için izin verilen minimum ve maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="39ac2-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="39ac2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39ac2-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="39ac2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="39ac2-105">Parameters</span></span>

<span data-ttu-id="39ac2-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="39ac2-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="39ac2-107">En az sayıda bağımsız değişken belirtir.</span><span class="sxs-lookup"><span data-stu-id="39ac2-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="39ac2-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="39ac2-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="39ac2-109">En fazla sayıda bağımsız değişken belirtir.</span><span class="sxs-lookup"><span data-stu-id="39ac2-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="39ac2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39ac2-110">Remarks</span></span>

- <span data-ttu-id="39ac2-111">Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [bildirmek giriş doğrulama kuralları nasıl](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="39ac2-111">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="39ac2-112">Bu öznitelik değil çağrıldığında karşılık gelen bir cmdlet parametresi herhangi bir sayıda bağımsız değişken olabilir.</span><span class="sxs-lookup"><span data-stu-id="39ac2-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="39ac2-113">Windows PowerShell çalışma zamanı, aşağıdaki koşullarda bir hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="39ac2-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="39ac2-114">`MinLength` Ve `MaxLength` öznitelik parametreleri türünde olmayan [System.Int32](/dotnet/api/System.Int32).</span><span class="sxs-lookup"><span data-stu-id="39ac2-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32](/dotnet/api/System.Int32).</span></span>

    - <span data-ttu-id="39ac2-115">Değerini `MaxLength` öznitelik parametresi değerini azdır `MinLength` parametre özniteliği.</span><span class="sxs-lookup"><span data-stu-id="39ac2-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="39ac2-116">ValidateCount özniteliği tarafından tanımlanan [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="39ac2-116">The ValidateCount attribute is defined by the [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="39ac2-117">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="39ac2-117">See Also</span></span>

[<span data-ttu-id="39ac2-118">System.Management.Automation.Validatecount</span><span class="sxs-lookup"><span data-stu-id="39ac2-118">System.Management.Automation.Validatecount</span></span>](/dotnet/api/System.Management.Automation.ValidateCount)

[<span data-ttu-id="39ac2-119">Nasıl giriş doğrulama kuralları</span><span class="sxs-lookup"><span data-stu-id="39ac2-119">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="39ac2-120">Nasıl giriş doğrulama kuralları</span><span class="sxs-lookup"><span data-stu-id="39ac2-120">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="39ac2-121">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="39ac2-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
