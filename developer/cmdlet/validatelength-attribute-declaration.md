---
title: ValidateLength özniteliği bildirimi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: 3a4c5f279ce8587eeb5d583376ea3d2286210b83
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067170"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="880e4-102">ValidateLength Özniteliği Bildirimi</span><span class="sxs-lookup"><span data-stu-id="880e4-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="880e4-103">ValidateLength öznitelik karakter cmdlet parametresi olan bir bağımsız değişken için minimum ve maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="880e4-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="880e4-104">Bu öznitelik, Windows PowerShell işlevleri tarafından da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="880e4-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="880e4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="880e4-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="880e4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="880e4-106">Parameters</span></span>

<span data-ttu-id="880e4-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="880e4-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="880e4-108">En az bir izin verilen karakter sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="880e4-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="880e4-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="880e4-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="880e4-110">En fazla izin verilen karakter sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="880e4-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="880e4-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="880e4-111">Remarks</span></span>

- <span data-ttu-id="880e4-112">Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [bildirmek giriş doğrulama kuralları nasıl](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="880e4-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="880e4-113">Bu öznitelik kullanıldığında, karşılık gelen parametre bağımsız değişkenini herhangi bir uzunlukta olabilir.</span><span class="sxs-lookup"><span data-stu-id="880e4-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="880e4-114">Windows PowerShell çalışma zamanı, aşağıdaki koşullarda bir hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="880e4-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="880e4-115">Zaman değerini `MaxLength` öznitelik parametresi değerini azdır `MinLength` parametre özniteliği.</span><span class="sxs-lookup"><span data-stu-id="880e4-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="880e4-116">Zaman `MaxLength` öznitelik parametresi 0 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="880e4-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="880e4-117">Ne zaman bağımsız değişken bir dize değil.</span><span class="sxs-lookup"><span data-stu-id="880e4-117">When the argument is not a string.</span></span>

- <span data-ttu-id="880e4-118">ValidateLength özniteliği tarafından tanımlanan [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="880e4-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="880e4-119">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="880e4-119">See Also</span></span>

[<span data-ttu-id="880e4-120">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="880e4-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="880e4-121">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="880e4-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
