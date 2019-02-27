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
ms.openlocfilehash: 1e8364c78abba5272007019550ffcb2cedaf9fd0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848821"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="5c33c-102">ValidateLength Özniteliği Bildirimi</span><span class="sxs-lookup"><span data-stu-id="5c33c-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="5c33c-103">ValidateLength öznitelik karakter cmdlet parametresi olan bir bağımsız değişken için minimum ve maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c33c-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="5c33c-104">Bu öznitelik, Windows PowerShell işlevleri tarafından da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5c33c-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="5c33c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c33c-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="5c33c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c33c-106">Parameters</span></span>

<span data-ttu-id="5c33c-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5c33c-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="5c33c-108">En az bir izin verilen karakter sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c33c-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="5c33c-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5c33c-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="5c33c-110">En fazla izin verilen karakter sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c33c-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="5c33c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c33c-111">Remarks</span></span>

- <span data-ttu-id="5c33c-112">Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [bildirmek giriş doğrulama kuralları nasıl](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="5c33c-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>
- <span data-ttu-id="5c33c-113">Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [bildirmek giriş doğrulama kuralları nasıl](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="5c33c-113">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="5c33c-114">Bu öznitelik kullanıldığında, karşılık gelen parametre bağımsız değişkenini herhangi bir uzunlukta olabilir.</span><span class="sxs-lookup"><span data-stu-id="5c33c-114">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="5c33c-115">Windows PowerShell çalışma zamanı, aşağıdaki koşullarda bir hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="5c33c-115">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="5c33c-116">Zaman değerini `MaxLength` öznitelik parametresi değerini azdır `MinLength` parametre özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5c33c-116">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="5c33c-117">Zaman `MaxLength` öznitelik parametresi 0 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5c33c-117">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="5c33c-118">Ne zaman bağımsız değişken bir dize değil.</span><span class="sxs-lookup"><span data-stu-id="5c33c-118">When the argument is not a string.</span></span>

- <span data-ttu-id="5c33c-119">ValidateLength özniteliği tarafından tanımlanan [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5c33c-119">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c33c-120">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="5c33c-120">See Also</span></span>

[<span data-ttu-id="5c33c-121">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="5c33c-121">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="5c33c-122">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="5c33c-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
