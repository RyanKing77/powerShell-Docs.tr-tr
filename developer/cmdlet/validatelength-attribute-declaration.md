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
ms.openlocfilehash: 4d3cdccc0fe3e24b1221e41beef4821b613aab93
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855154"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="42991-102">ValidateLength Özniteliği Bildirimi</span><span class="sxs-lookup"><span data-stu-id="42991-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="42991-103">ValidateLength öznitelik karakter cmdlet parametresi olan bir bağımsız değişken için minimum ve maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="42991-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="42991-104">Bu öznitelik, Windows PowerShell işlevleri tarafından da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="42991-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="42991-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="42991-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="42991-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="42991-106">Parameters</span></span>

<span data-ttu-id="42991-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="42991-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="42991-108">En az bir izin verilen karakter sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="42991-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="42991-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="42991-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="42991-110">En fazla izin verilen karakter sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="42991-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="42991-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42991-111">Remarks</span></span>

- <span data-ttu-id="42991-112">Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [bildirmek giriş doğrulama kuralları nasıl](./how-to-validate-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="42991-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="42991-113">Bu öznitelik kullanıldığında, karşılık gelen parametre bağımsız değişkenini herhangi bir uzunlukta olabilir.</span><span class="sxs-lookup"><span data-stu-id="42991-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="42991-114">Windows PowerShell çalışma zamanı, aşağıdaki koşullarda bir hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="42991-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="42991-115">Zaman değerini `MaxLength` öznitelik parametresi değerini azdır `MinLength` parametre özniteliği.</span><span class="sxs-lookup"><span data-stu-id="42991-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="42991-116">Zaman `MaxLength` öznitelik parametresi 0 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="42991-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="42991-117">Ne zaman bağımsız değişken bir dize değil.</span><span class="sxs-lookup"><span data-stu-id="42991-117">When the argument is not a string.</span></span>

- <span data-ttu-id="42991-118">ValidateLength özniteliği tarafından tanımlanan [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="42991-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="42991-119">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="42991-119">See Also</span></span>

[<span data-ttu-id="42991-120">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="42991-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="42991-121">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="42991-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
