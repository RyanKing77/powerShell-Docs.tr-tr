---
title: ValidatePattern özniteliği bildirimi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067136"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="baf4f-102">ValidatePattern Özniteliği Bildirimi</span><span class="sxs-lookup"><span data-stu-id="baf4f-102">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="baf4f-103">ValidatePattern öznitelik bağımsız değişkeni bir cmdlet parametresi onaylayan bir normal ifade desenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="baf4f-103">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="baf4f-104">Bu öznitelik, Windows PowerShell işlevleri tarafından da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="baf4f-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="baf4f-105">İçinde bir cmdlet ValidatePattern çağrıldığında, Windows PowerShell çalışma zamanı cmdlet parametresi bağımsız değişkeni bir dizeye dönüştürür ve ardından o dizeyi ValidatePattern özniteliği tarafından sağlanan desenle karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="baf4f-105">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="baf4f-106">Dönüştürülmüş dize gösterimini bağımsız değişkeni ve belirtilen desenle eşleşiyorsa cmdlet çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="baf4f-106">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="baf4f-107">Bunlar eşleşmiyorsa Windows PowerShell çalışma zamanı tarafından bir hata oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="baf4f-107">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="baf4f-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="baf4f-108">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="baf4f-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="baf4f-109">Parameters</span></span>

<span data-ttu-id="baf4f-110">`RegexString` ([System.String](/dotnet/api/System.String)) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="baf4f-110">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="baf4f-111">Parametre bağımsız değişkenini onaylayan bir normal ifade belirtir.</span><span class="sxs-lookup"><span data-stu-id="baf4f-111">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="baf4f-112">Seçenekler ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) isteğe bağlı parametre adı.</span><span class="sxs-lookup"><span data-stu-id="baf4f-112">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="baf4f-113">Bitsel bir birleşimi belirler [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) normal ifade seçenekleri belirten bayrak.</span><span class="sxs-lookup"><span data-stu-id="baf4f-113">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="baf4f-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="baf4f-114">Remarks</span></span>

- <span data-ttu-id="baf4f-115">Bu öznitelik, parametre yalnızca bir kez kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="baf4f-115">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="baf4f-116">Kullanabileceğiniz `Option` daha fazla düzeni tanımlamak için öznitelik parametresi.</span><span class="sxs-lookup"><span data-stu-id="baf4f-116">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="baf4f-117">Örneğin, deseni büyük küçük harfe duyarlı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baf4f-117">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="baf4f-118">Bu öznitelik bir derlemeye uygulanmışsa, koleksiyondaki her öğe belirtilen desenle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="baf4f-118">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="baf4f-119">ValidatePattern özniteliği tarafından tanımlanan [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="baf4f-119">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="baf4f-120">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="baf4f-120">See Also</span></span>

[<span data-ttu-id="baf4f-121">System.Management.Automation.Validatepatternattribute</span><span class="sxs-lookup"><span data-stu-id="baf4f-121">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="baf4f-122">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="baf4f-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
