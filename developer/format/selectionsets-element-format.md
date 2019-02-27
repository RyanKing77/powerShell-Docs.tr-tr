---
title: SelectionSets öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845111"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="a175e-102">SelectionSets Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="a175e-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="a175e-103">Biçimlendirme dosyanın tüm görünümler tarafından kullanılan .NET nesneleri ortak kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a175e-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="a175e-104">Görünüm ve biçimlendirme dosyasının tam nesne kümesini yalnızca seçimi kümesinin adını kullanarak başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a175e-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="a175e-105">Yapılandırma öğesi SelectionSets öğesi biçimi</span><span class="sxs-lookup"><span data-stu-id="a175e-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="a175e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a175e-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a175e-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a175e-107">Attributes and Elements</span></span>

<span data-ttu-id="a175e-108">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `SelectionSets` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a175e-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="a175e-109">Her alt öğe kümesi adı tarafından başvurulan bir nesne tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a175e-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="a175e-110">Alt öğelerin sırası önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="a175e-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="a175e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a175e-111">Attributes</span></span>

<span data-ttu-id="a175e-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="a175e-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a175e-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a175e-113">Child Elements</span></span>

|<span data-ttu-id="a175e-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="a175e-114">Element</span></span>|<span data-ttu-id="a175e-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a175e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a175e-116">SelectionSet öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="a175e-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="a175e-117">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="a175e-117">Required element.</span></span><br /><br /> <span data-ttu-id="a175e-118">Tek bir küme adı tarafından başvurulan .NET nesneleri kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a175e-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a175e-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a175e-119">Parent Elements</span></span>

|<span data-ttu-id="a175e-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="a175e-120">Element</span></span>|<span data-ttu-id="a175e-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a175e-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a175e-122">Yapılandırma öğesi</span><span class="sxs-lookup"><span data-stu-id="a175e-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="a175e-123">Biçimlendirme bir dosyanın üst düzey öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a175e-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a175e-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a175e-124">Remarks</span></span>

<span data-ttu-id="a175e-125">Devralma yoluyla ilişkili bir nesne gibi tek bir adı kullanarak başvurmak istediğiniz bir ilgili nesne varsa, seçim kümeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a175e-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="a175e-126">Kendi görünümlerinizi tanımlarken, her bir görünüm içindeki tüm nesneleri listelemek yerine ayarlamak seçimi adını kullanarak nesne kümesini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a175e-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="a175e-127">Ortak seçimi ayarlar, biçimlendirme dosyası görünümlerini veya görünümlerinin tanımlarını tanımlarken adlarına göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a175e-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="a175e-128">Bu gibi durumlarda, `SelectionSetName` alt öğesi `ViewSelectedBy` ve `EntrySelectedBy` öğeleri kullanılacak kümesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="a175e-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="a175e-129">Seçimi kümeleri hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="a175e-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a175e-130">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a175e-130">See Also</span></span>

[<span data-ttu-id="a175e-131">Yapılandırma öğesi</span><span class="sxs-lookup"><span data-stu-id="a175e-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="a175e-132">Seçimi ayarlar tanımlama</span><span class="sxs-lookup"><span data-stu-id="a175e-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="a175e-133">SelectionSet öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="a175e-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="a175e-134">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="a175e-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
