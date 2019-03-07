---
title: SelectionSet öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850424"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="7c973-102">SelectionSet Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="7c973-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="7c973-103">Küme adı tarafından başvurulan bir .NET nesne tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7c973-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="7c973-104">Yapılandırma öğesi (biçimi) SelectionSets öğesi (biçimi) SelectionSet öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="7c973-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7c973-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c973-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7c973-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c973-106">Attributes and Elements</span></span>

<span data-ttu-id="7c973-107">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `SelectionSet` öğesi.</span><span class="sxs-lookup"><span data-stu-id="7c973-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="7c973-108">Her seçim kümesinin bir adı olması gerekir ve .NET nesneleri kümesinin belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7c973-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="7c973-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7c973-109">Attributes</span></span>

<span data-ttu-id="7c973-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="7c973-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7c973-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c973-111">Child Elements</span></span>

|<span data-ttu-id="7c973-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="7c973-112">Element</span></span>|<span data-ttu-id="7c973-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c973-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7c973-114">Name öğesi SelectionSet (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="7c973-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="7c973-115">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="7c973-115">Required element.</span></span><br /><br /> <span data-ttu-id="7c973-116">Seçimi kümesi başvurmak için kullanılan adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c973-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="7c973-117">Türleri öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="7c973-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="7c973-118">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="7c973-118">Required element.</span></span><br /><br /> <span data-ttu-id="7c973-119">Seçimdeki ayarlanan .NET nesneleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7c973-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7c973-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c973-120">Parent Elements</span></span>

|<span data-ttu-id="7c973-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="7c973-121">Element</span></span>|<span data-ttu-id="7c973-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c973-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7c973-123">SelectionSets öğesi biçimi</span><span class="sxs-lookup"><span data-stu-id="7c973-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="7c973-124">Biçimlendirme dosyanın tüm görünümler tarafından kullanılan .NET nesneleri ortak kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7c973-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7c973-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c973-125">Remarks</span></span>

<span data-ttu-id="7c973-126">Devralma yoluyla ilişkili bir nesne gibi tek bir adı kullanarak başvurmak istediğiniz bir ilgili nesne varsa, seçim kümeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c973-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="7c973-127">Kendi görünümlerinizi tanımlarken, her bir görünüm içindeki tüm nesneleri listelemek yerine ayarlamak seçimi adını kullanarak nesne kümesini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c973-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="7c973-128">Ortak seçimi ayarlar, biçimlendirme dosyası görünümlerini veya görünümlerinin tanımlarını tanımlarken adlarına göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="7c973-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="7c973-129">Bu gibi durumlarda, `SelectionSetName` alt öğesi `ViewSelectedBy` ve `EntrySelectedBy` öğeleri kullanılacak kümesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c973-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="7c973-130">Seçimi kümeleri hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="7c973-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="7c973-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="7c973-131">Example</span></span>

<span data-ttu-id="7c973-132">Aşağıdaki örnekte gösterildiği bir `SelectionSet` dört .NET türlerini tanımlayan öğe.</span><span class="sxs-lookup"><span data-stu-id="7c973-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7c973-133">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="7c973-133">See Also</span></span>

[<span data-ttu-id="7c973-134">Seçimi ayarlar tanımlama</span><span class="sxs-lookup"><span data-stu-id="7c973-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="7c973-135">SelectionSet (biçimi) öğesinin adı</span><span class="sxs-lookup"><span data-stu-id="7c973-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="7c973-136">SelectionSets öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="7c973-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="7c973-137">Türleri öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="7c973-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="7c973-138">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="7c973-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)