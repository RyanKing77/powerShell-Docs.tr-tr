---
title: SelectionSet (biçimi) için öğe türleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851278"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="6a1ba-102">SelectionSet için Türler Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="6a1ba-102">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="6a1ba-103">Seçimdeki ayarlanan .NET nesneleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6a1ba-103">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="6a1ba-104">Yapılandırma öğesi (biçimi) SelectionSets öğesi (biçimi) SelectionSet öğesi (biçimi) (biçimi) öğe türleri</span><span class="sxs-lookup"><span data-stu-id="6a1ba-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6a1ba-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a1ba-105">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a1ba-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a1ba-106">Attributes and Elements</span></span>

<span data-ttu-id="6a1ba-107">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `Types` öğesi.</span><span class="sxs-lookup"><span data-stu-id="6a1ba-107">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="6a1ba-108">En az bir alt öğesi olmalıdır, ancak eklenebilir alt öğe sayısı için en fazla bir sınır yoktur.</span><span class="sxs-lookup"><span data-stu-id="6a1ba-108">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="6a1ba-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6a1ba-109">Attributes</span></span>

<span data-ttu-id="6a1ba-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="6a1ba-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6a1ba-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a1ba-111">Child Elements</span></span>

|<span data-ttu-id="6a1ba-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="6a1ba-112">Element</span></span>|<span data-ttu-id="6a1ba-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a1ba-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a1ba-114">TypeName öğesi türleri (biçimi)</span><span class="sxs-lookup"><span data-stu-id="6a1ba-114">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="6a1ba-115">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="6a1ba-115">Required element.</span></span><br /><br /> <span data-ttu-id="6a1ba-116">Seçimi kümesine ait olan bir .NET nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a1ba-116">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6a1ba-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a1ba-117">Parent Elements</span></span>

|<span data-ttu-id="6a1ba-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="6a1ba-118">Element</span></span>|<span data-ttu-id="6a1ba-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a1ba-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a1ba-120">SelectionSet öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="6a1ba-120">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="6a1ba-121">Küme adı tarafından başvurulan bir .NET nesne tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6a1ba-121">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6a1ba-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a1ba-122">Remarks</span></span>

<span data-ttu-id="6a1ba-123">Bu öğe tarafından tanımlanan nesneler tarafından bir görünüm, görünüm tanımı tarafından kullanılabilecek seçim kümesi oluşturan (görünümler birden çok tanım olabilir) veya seçim koşulu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="6a1ba-123">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="6a1ba-124">Seçimi kümeleri hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="6a1ba-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="6a1ba-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a1ba-125">Example</span></span>

<span data-ttu-id="6a1ba-126">Bu örnek gösterir bir `SelectionSet` dört .NET türlerini tanımlayan öğe.</span><span class="sxs-lookup"><span data-stu-id="6a1ba-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a><span data-ttu-id="6a1ba-127">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6a1ba-127">See Also</span></span>

[<span data-ttu-id="6a1ba-128">Nesne kümesi tanımlama</span><span class="sxs-lookup"><span data-stu-id="6a1ba-128">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="6a1ba-129">SelectionSet öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="6a1ba-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="6a1ba-130">TypeName öğesi türleri (biçimi)</span><span class="sxs-lookup"><span data-stu-id="6a1ba-130">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="6a1ba-131">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="6a1ba-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
