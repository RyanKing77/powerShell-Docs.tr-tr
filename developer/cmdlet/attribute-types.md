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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068670"
---
# <a name="attribute-types"></a><span data-ttu-id="64994-102">Öznitelik Türleri</span><span class="sxs-lookup"><span data-stu-id="64994-102">Attribute Types</span></span>

<span data-ttu-id="64994-103">Cmdlet öznitelikleri işlevselliğe göre gruplanabilir.</span><span class="sxs-lookup"><span data-stu-id="64994-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="64994-104">Aşağıdaki bölümlerde, kullanılabilen öznitelikleri açıklar ve çalışma zamanı öznitelik çağrıldığında ne yaptığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="64994-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="64994-105">Cmdlet Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="64994-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="64994-106">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="64994-106">Cmdlet</span></span>

<span data-ttu-id="64994-107">.NET Framework sınıfı bir cmdlet tanımlar.</span><span class="sxs-lookup"><span data-stu-id="64994-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="64994-108">Gerekli base özniteliği budur.</span><span class="sxs-lookup"><span data-stu-id="64994-108">This is the required base attribute.</span></span>
<span data-ttu-id="64994-109">Daha fazla bilgi için [cmdlet'i özniteliği bildirimi](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="64994-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="64994-110">Parametre öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="64994-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="64994-111">Parametre</span><span class="sxs-lookup"><span data-stu-id="64994-111">Parameter</span></span>

<span data-ttu-id="64994-112">Cmdlet sınıftaki ortak özelliği, bir cmdlet parametresi olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="64994-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="64994-113">Daha fazla bilgi için [parametre özniteliği bildirimi](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="64994-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="64994-114">Diğer Ad</span><span class="sxs-lookup"><span data-stu-id="64994-114">Alias</span></span>

<span data-ttu-id="64994-115">Bir parametre için bir veya daha fazla diğer ad belirtir.</span><span class="sxs-lookup"><span data-stu-id="64994-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="64994-116">Daha fazla bilgi için [diğer ad özniteliği bildirimi](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="64994-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="64994-117">Bağımsız değişken doğrulama öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="64994-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="64994-118">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="64994-118">ValidateCount</span></span>

<span data-ttu-id="64994-119">Bağımsız bir cmdlet parametresi için izin verilen minimum ve maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="64994-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="64994-120">Daha fazla bilgi için [ValidateCount özniteliği bildirimi](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="64994-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="64994-121">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="64994-121">ValidateLength</span></span>

<span data-ttu-id="64994-122">Bir karakter cmdlet parametresi olan bir bağımsız değişken için minimum ve maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="64994-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="64994-123">Daha fazla bilgi için [ValidateLength özniteliği bildirimi](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="64994-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="64994-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="64994-124">ValidatePattern</span></span>

<span data-ttu-id="64994-125">Cmdlet'i parametre bağımsız değişkenini eşleşmelidir bir normal ifade desenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="64994-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="64994-126">Daha fazla bilgi için [ValidatePattern özniteliği bildirimi](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="64994-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="64994-127">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="64994-127">ValidateRange</span></span>

<span data-ttu-id="64994-128">Cmdlet parametresi olan bir bağımsız değişken için minimum ve maksimum değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="64994-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="64994-129">Daha fazla bilgi için [ValidateRange özniteliği bildirimi](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="64994-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="64994-130">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="64994-130">ValidateSet</span></span>

<span data-ttu-id="64994-131">Cmdlet parametresi bağımsız değişkeni için geçerli değerler kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="64994-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="64994-132">Daha fazla bilgi için [ValidateSet özniteliği bildirimi](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="64994-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="64994-133">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="64994-133">See Also</span></span>

[<span data-ttu-id="64994-134">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="64994-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
