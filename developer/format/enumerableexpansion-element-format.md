---
title: EnumerableExpansion öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066150"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="6a8df-102">EnumerableExpansion Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="6a8df-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="6a8df-103">Bir görünümü'nde görüntülendiğinde nesneleri genişletilir belirli .NET koleksiyonu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6a8df-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="6a8df-104">Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi) EnumerableExpansions öğesi (biçimi) EnumerableExpansion öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="6a8df-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6a8df-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a8df-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a8df-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="6a8df-106">Attributes and Elements</span></span>

<span data-ttu-id="6a8df-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `EnumerableExpansion` öğesi.</span><span class="sxs-lookup"><span data-stu-id="6a8df-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6a8df-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6a8df-108">Attributes</span></span>

<span data-ttu-id="6a8df-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="6a8df-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6a8df-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="6a8df-110">Child Elements</span></span>

|<span data-ttu-id="6a8df-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="6a8df-111">Element</span></span>|<span data-ttu-id="6a8df-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a8df-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a8df-113">EntrySelectedBy öğesi EnumerableExpansion (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="6a8df-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="6a8df-114">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="6a8df-114">Optional element.</span></span><br /><br /> <span data-ttu-id="6a8df-115">Bu tanımı tarafından hangi .NET koleksiyon nesnelerini genişletilir tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6a8df-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="6a8df-116">Öğesi (biçimi) genişletin</span><span class="sxs-lookup"><span data-stu-id="6a8df-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="6a8df-117">Koleksiyon nesnesi bu tanım için nasıl genişletilmiş belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a8df-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6a8df-118">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="6a8df-118">Parent Elements</span></span>

|<span data-ttu-id="6a8df-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="6a8df-119">Element</span></span>|<span data-ttu-id="6a8df-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a8df-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a8df-121">EnumerableExpansions öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="6a8df-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="6a8df-122">Farklı şekilde Görünümü'nde görüntülendiğinde nesneleri genişletilir, .NET koleksiyonu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6a8df-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6a8df-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a8df-123">Remarks</span></span>

<span data-ttu-id="6a8df-124">Bu öğe, koleksiyon nesnelerini ve koleksiyondaki nesnelerin nasıl görüntüleneceğini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6a8df-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="6a8df-125">Bu durumda, destekleyen herhangi bir nesne için bir koleksiyon nesnesini ifade eder **System.Collections.ICollection** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6a8df-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="6a8df-126">Koleksiyonda yalnızca nesnelerin özelliklerini görüntülemek için varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="6a8df-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a8df-127">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6a8df-127">See Also</span></span>

[<span data-ttu-id="6a8df-128">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="6a8df-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
