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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848807"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="bc6be-102">Parametre Girişini Doğrulama</span><span class="sxs-lookup"><span data-stu-id="bc6be-102">Validating Parameter Input</span></span>

<span data-ttu-id="bc6be-103">Windows PowerShell cmdlet parametreleri, çeşitli şekillerde geçirilecek bağımsız değişkenler doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc6be-103">Windows PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span> <span data-ttu-id="bc6be-104">Windows PowerShell, uzunluğu, aralığı ve bağımsız değişken karakter desenini doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc6be-104">Windows PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span> <span data-ttu-id="bc6be-105">Bu bağımsız değişkenler kullanılabilir (sayı) sayısını doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc6be-105">It can validate the number of arguments available (the count).</span></span> <span data-ttu-id="bc6be-106">Bu doğrulama kuralları, cmdlet sınıfın genel özellikleri parametre özniteliği ile bildirilen doğrulama öznitelikleri tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="bc6be-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="bc6be-107">Bir parametre bağımsız değişkenini doğrulamak için cmdlet çalıştırılmadan önce parametresinin değerini doğrulamak için doğrulama öznitelikleri tarafından sağlanan bilgileri Windows PowerShell çalışma zamanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="bc6be-107">To validate a parameter argument, the Windows PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span> <span data-ttu-id="bc6be-108">Parametre girişi geçerli değil, kullanıcı bir hata iletisi alır.</span><span class="sxs-lookup"><span data-stu-id="bc6be-108">If the parameter input is not valid, the user receives an error message.</span></span> <span data-ttu-id="bc6be-109">Windows PowerShell tarafından zorlanan bir doğrulama kuralı her doğrulama parametresi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bc6be-109">Each validation parameter defines a validation rule that is enforced by Windows PowerShell.</span></span>

<span data-ttu-id="bc6be-110">Windows PowerShell aşağıdaki özniteliklerine dayalı doğrulama kuralları zorlar.</span><span class="sxs-lookup"><span data-stu-id="bc6be-110">Windows PowerShell enforces the validation rules based on the following attributes.</span></span>

<span data-ttu-id="bc6be-111">ValidateCount bir parametre kabul edebilen bağımsız değişkenleri minimum ve maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc6be-111">ValidateCount Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span> <span data-ttu-id="bc6be-112">Bu öznitelik bildirmek için kullanılan sözdizimi hakkında daha fazla bilgi için bkz. [ValidateCount özniteliği bildirimi](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="bc6be-112">For more information about the syntax used to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

<span data-ttu-id="bc6be-113">ValidateLength parametre bağımsız değişkendeki karakter minimum ve maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc6be-113">ValidateLength Specifies the minimum and maximum number of characters in the parameter argument.</span></span> <span data-ttu-id="bc6be-114">Bu öznitelik bildirmek için kullanılan sözdizimi hakkında daha fazla bilgi için bkz. [ValidateLength özniteliği bildirimi](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="bc6be-114">For more information about the syntax used to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

<span data-ttu-id="bc6be-115">ValidatePattern parametre bağımsız değişkenini onaylayan bir normal ifade belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc6be-115">ValidatePattern Specifies a regular expression that validates the parameter argument.</span></span> <span data-ttu-id="bc6be-116">Bu öznitelik bildirmek için kullanılan sözdizimi hakkında daha fazla bilgi için bkz. [ValidatePattern özniteliği bildirimi](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="bc6be-116">For more information about the syntax used to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

<span data-ttu-id="bc6be-117">ValidateRange parametre bağımsız değişkenin minimum ve maksimum değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc6be-117">ValidateRange Specifies the minimum and maximum values of the parameter argument.</span></span> <span data-ttu-id="bc6be-118">Bu öznitelik bildirmek için kullanılan sözdizimi hakkında daha fazla bilgi için bkz. [ValidateRange özniteliği bildirimi](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="bc6be-118">For more information about the syntax used to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

<span data-ttu-id="bc6be-119">ValidateSet parametre bağımsız değişkeni için geçerli değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc6be-119">ValidateSet Specifies the valid values for the parameter argument.</span></span> <span data-ttu-id="bc6be-120">Bu öznitelik bildirmek için kullanılan sözdizimi hakkında daha fazla bilgi için bkz. [ValidateSet özniteliği bildirimi](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="bc6be-120">For more information about the syntax used to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bc6be-121">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="bc6be-121">See Also</span></span>

[<span data-ttu-id="bc6be-122">Parametre girişi doğrulama</span><span class="sxs-lookup"><span data-stu-id="bc6be-122">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="bc6be-123">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="bc6be-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
