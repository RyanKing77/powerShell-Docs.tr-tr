---
title: Öğesi (biçimi) genişletin | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848618"
---
# <a name="expand-element-format"></a><span data-ttu-id="c5c20-102">Genişletme Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="c5c20-102">Expand Element (Format)</span></span>

<span data-ttu-id="c5c20-103">Koleksiyon nesnesi bu tanım için nasıl genişletilmiş belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5c20-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="c5c20-104">Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi) EnumerableExpansions öğesi (biçimi) EnumerableExpansion öğesi (biçimi) öğesi (biçimi) genişletin</span><span class="sxs-lookup"><span data-stu-id="c5c20-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c5c20-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5c20-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c5c20-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5c20-106">Attributes and Elements</span></span>

<span data-ttu-id="c5c20-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `Expand` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c5c20-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c5c20-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c5c20-108">Attributes</span></span>

<span data-ttu-id="c5c20-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="c5c20-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c5c20-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5c20-110">Child Elements</span></span>

<span data-ttu-id="c5c20-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="c5c20-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c5c20-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5c20-112">Parent Elements</span></span>

|<span data-ttu-id="c5c20-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="c5c20-113">Element</span></span>|<span data-ttu-id="c5c20-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5c20-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c5c20-115">EnumerableExpansion öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c5c20-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="c5c20-116">Bir görünümü'nde görüntülendiğinde nesneleri genişletilir belirli .NET koleksiyonu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c5c20-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c5c20-117">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="c5c20-117">Text Value</span></span>

<span data-ttu-id="c5c20-118">Aşağıdaki değerlerden birini belirtin:</span><span class="sxs-lookup"><span data-stu-id="c5c20-118">Specify one of the following values:</span></span>

- <span data-ttu-id="c5c20-119">EnumOnly: Koleksiyonda yalnızca nesnelerin özelliklerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c5c20-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="c5c20-120">CoreOnly: Yalnızca koleksiyon nesnesinin özelliklerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c5c20-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="c5c20-121">Her ikisi: Nesnelerin özelliklerini, koleksiyon ve koleksiyon nesnesinin özelliklerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c5c20-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="c5c20-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5c20-122">Remarks</span></span>

<span data-ttu-id="c5c20-123">Bu öğe, koleksiyon nesnelerini ve koleksiyondaki nesnelerin nasıl görüntüleneceğini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c5c20-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="c5c20-124">Bu durumda, destekleyen herhangi bir nesne için bir koleksiyon nesnesini ifade eder **System.Collections.ICollection** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c5c20-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="c5c20-125">Koleksiyonda yalnızca nesnelerin özelliklerini görüntülemek için varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="c5c20-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5c20-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="c5c20-126">See Also</span></span>

[<span data-ttu-id="c5c20-127">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="c5c20-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
