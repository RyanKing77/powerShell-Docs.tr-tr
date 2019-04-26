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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066014"
---
# <a name="expand-element-format"></a><span data-ttu-id="3ed0c-102">Genişletme Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="3ed0c-102">Expand Element (Format)</span></span>

<span data-ttu-id="3ed0c-103">Koleksiyon nesnesi bu tanım için nasıl genişletilmiş belirtir.</span><span class="sxs-lookup"><span data-stu-id="3ed0c-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="3ed0c-104">Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi) EnumerableExpansions öğesi (biçimi) EnumerableExpansion öğesi (biçimi) öğesi (biçimi) genişletin</span><span class="sxs-lookup"><span data-stu-id="3ed0c-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3ed0c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ed0c-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3ed0c-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="3ed0c-106">Attributes and Elements</span></span>

<span data-ttu-id="3ed0c-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `Expand` öğesi.</span><span class="sxs-lookup"><span data-stu-id="3ed0c-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3ed0c-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3ed0c-108">Attributes</span></span>

<span data-ttu-id="3ed0c-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="3ed0c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3ed0c-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="3ed0c-110">Child Elements</span></span>

<span data-ttu-id="3ed0c-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="3ed0c-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3ed0c-112">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="3ed0c-112">Parent Elements</span></span>

|<span data-ttu-id="3ed0c-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="3ed0c-113">Element</span></span>|<span data-ttu-id="3ed0c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ed0c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ed0c-115">EnumerableExpansion öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="3ed0c-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="3ed0c-116">Bir görünümü'nde görüntülendiğinde nesneleri genişletilir belirli .NET koleksiyonu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3ed0c-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3ed0c-117">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="3ed0c-117">Text Value</span></span>

<span data-ttu-id="3ed0c-118">Aşağıdaki değerlerden birini belirtin:</span><span class="sxs-lookup"><span data-stu-id="3ed0c-118">Specify one of the following values:</span></span>

- <span data-ttu-id="3ed0c-119">EnumOnly: Koleksiyonda yalnızca nesnelerin özelliklerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3ed0c-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="3ed0c-120">CoreOnly: Yalnızca koleksiyon nesnesinin özelliklerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3ed0c-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="3ed0c-121">Her ikisi: Nesnelerin özelliklerini, koleksiyon ve koleksiyon nesnesinin özelliklerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3ed0c-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ed0c-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ed0c-122">Remarks</span></span>

<span data-ttu-id="3ed0c-123">Bu öğe, koleksiyon nesnelerini ve koleksiyondaki nesnelerin nasıl görüntüleneceğini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ed0c-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="3ed0c-124">Bu durumda, destekleyen herhangi bir nesne için bir koleksiyon nesnesini ifade eder **System.Collections.ICollection** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3ed0c-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="3ed0c-125">Koleksiyonda yalnızca nesnelerin özelliklerini görüntülemek için varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="3ed0c-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ed0c-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="3ed0c-126">See Also</span></span>

[<span data-ttu-id="3ed0c-127">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="3ed0c-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
