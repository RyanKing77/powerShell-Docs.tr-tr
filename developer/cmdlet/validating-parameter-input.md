---
title: Parametre girişi doğrulama | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067153"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="36bbb-102">Parametre Girişini Doğrulama</span><span class="sxs-lookup"><span data-stu-id="36bbb-102">Validating Parameter Input</span></span>

<span data-ttu-id="36bbb-103">PowerShell cmdlet parametreleri, çeşitli şekillerde geçirilecek bağımsız değişkenler doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36bbb-103">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="36bbb-104">PowerShell, uzunluğu, aralığı ve bağımsız değişken karakter desenini doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36bbb-104">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="36bbb-105">Bu bağımsız değişkenler kullanılabilir (sayı) sayısını doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36bbb-105">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="36bbb-106">Bu doğrulama kuralları, cmdlet sınıfın genel özellikleri parametre özniteliği ile bildirilen doğrulama öznitelikleri tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="36bbb-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="36bbb-107">Bir parametre bağımsız değişkenini doğrulamak için cmdlet çalıştırılmadan önce parametresinin değerini doğrulamak için doğrulama öznitelikleri tarafından sağlanan bilgileri PowerShell çalışma zamanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="36bbb-107">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="36bbb-108">Parametre girişi geçerli değil, kullanıcı bir hata iletisi alır.</span><span class="sxs-lookup"><span data-stu-id="36bbb-108">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="36bbb-109">Her doğrulama parametre PowerShell tarafından zorlanan bir doğrulama kuralı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="36bbb-109">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="36bbb-110">PowerShell aşağıdaki özniteliklerine dayalı doğrulama kuralları zorlar.</span><span class="sxs-lookup"><span data-stu-id="36bbb-110">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="36bbb-111">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="36bbb-111">ValidateCount</span></span>

<span data-ttu-id="36bbb-112">Bir parametre kabul edebilen bağımsız değişkenleri minimum ve maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="36bbb-112">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="36bbb-113">Daha fazla bilgi için [ValidateCount özniteliği bildirimi](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="36bbb-113">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="36bbb-114">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="36bbb-114">ValidateLength</span></span>

<span data-ttu-id="36bbb-115">Parametre bağımsız değişkendeki karakter minimum ve maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="36bbb-115">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="36bbb-116">Daha fazla bilgi için [ValidateLength özniteliği bildirimi](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="36bbb-116">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="36bbb-117">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="36bbb-117">ValidatePattern</span></span>

<span data-ttu-id="36bbb-118">Parametre bağımsız değişkenini onaylayan bir normal ifade belirtir.</span><span class="sxs-lookup"><span data-stu-id="36bbb-118">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="36bbb-119">Daha fazla bilgi için [ValidatePattern özniteliği bildirimi](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="36bbb-119">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="36bbb-120">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="36bbb-120">ValidateRange</span></span>

<span data-ttu-id="36bbb-121">Parametre bağımsız değişkenin minimum ve maksimum değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="36bbb-121">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="36bbb-122">Daha fazla bilgi için [ValidateRange özniteliği bildirimi](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="36bbb-122">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="36bbb-123">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="36bbb-123">ValidateSet</span></span>

<span data-ttu-id="36bbb-124">Parametre bağımsız değişkeni için geçerli değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="36bbb-124">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="36bbb-125">Daha fazla bilgi için [ValidateSet özniteliği bildirimi](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="36bbb-125">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="36bbb-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="36bbb-126">See Also</span></span>

[<span data-ttu-id="36bbb-127">Parametre girişi doğrulama</span><span class="sxs-lookup"><span data-stu-id="36bbb-127">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="36bbb-128">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="36bbb-128">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
