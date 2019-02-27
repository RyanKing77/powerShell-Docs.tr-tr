---
title: Öznitelik türleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2019
ms.locfileid: "56852279"
---
# <a name="attribute-types"></a><span data-ttu-id="5226f-102">Öznitelik Türleri</span><span class="sxs-lookup"><span data-stu-id="5226f-102">Attribute Types</span></span>

<span data-ttu-id="5226f-103">Cmdlet öznitelikleri işlevselliğe göre gruplanabilir.</span><span class="sxs-lookup"><span data-stu-id="5226f-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="5226f-104">Aşağıdaki bölümlerde, kullanılabilen öznitelikleri açıklar ve çalışma zamanı öznitelik çağrıldığında ne yaptığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="5226f-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="5226f-105">Cmdlet Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="5226f-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="5226f-106">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5226f-106">Cmdlet</span></span>

<span data-ttu-id="5226f-107">.NET Framework sınıfı bir cmdlet tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5226f-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="5226f-108">Gerekli base özniteliği budur.</span><span class="sxs-lookup"><span data-stu-id="5226f-108">This is the required base attribute.</span></span>
<span data-ttu-id="5226f-109">Daha fazla bilgi için [cmdlet'i özniteliği bildirimi](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5226f-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="5226f-110">Parametre öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="5226f-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="5226f-111">Parametre</span><span class="sxs-lookup"><span data-stu-id="5226f-111">Parameter</span></span>

<span data-ttu-id="5226f-112">Cmdlet sınıftaki ortak özelliği, bir cmdlet parametresi olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5226f-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="5226f-113">Daha fazla bilgi için [parametre özniteliği bildirimi](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5226f-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="5226f-114">Diğer Ad</span><span class="sxs-lookup"><span data-stu-id="5226f-114">Alias</span></span>

<span data-ttu-id="5226f-115">Bir parametre için bir veya daha fazla diğer ad belirtir.</span><span class="sxs-lookup"><span data-stu-id="5226f-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="5226f-116">Daha fazla bilgi için [diğer ad özniteliği bildirimi](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5226f-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="5226f-117">Bağımsız değişken doğrulama öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="5226f-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="5226f-118">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="5226f-118">ValidateCount</span></span>

<span data-ttu-id="5226f-119">Bağımsız bir cmdlet parametresi için izin verilen minimum ve maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5226f-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="5226f-120">Daha fazla bilgi için [ValidateCount özniteliği bildirimi](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5226f-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="5226f-121">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="5226f-121">ValidateLength</span></span>

<span data-ttu-id="5226f-122">Bir karakter cmdlet parametresi olan bir bağımsız değişken için minimum ve maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5226f-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="5226f-123">Daha fazla bilgi için [ValidateLength özniteliği bildirimi](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5226f-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="5226f-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="5226f-124">ValidatePattern</span></span>

<span data-ttu-id="5226f-125">Cmdlet'i parametre bağımsız değişkenini eşleşmelidir bir normal ifade desenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5226f-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="5226f-126">Daha fazla bilgi için [ValidatePattern özniteliği bildirimi](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5226f-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="5226f-127">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="5226f-127">ValidateRange</span></span>

<span data-ttu-id="5226f-128">Cmdlet parametresi olan bir bağımsız değişken için minimum ve maksimum değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="5226f-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="5226f-129">Daha fazla bilgi için [ValidateRange özniteliği bildirimi](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5226f-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="5226f-130">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="5226f-130">ValidateSet</span></span>

<span data-ttu-id="5226f-131">Cmdlet parametresi bağımsız değişkeni için geçerli değerler kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5226f-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="5226f-132">Daha fazla bilgi için [ValidateSet özniteliği bildirimi](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5226f-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5226f-133">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="5226f-133">See Also</span></span>

[<span data-ttu-id="5226f-134">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="5226f-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
