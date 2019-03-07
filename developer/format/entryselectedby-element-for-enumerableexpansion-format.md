---
title: EntrySelectedBy öğesi EnumerableExpansion (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846525"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="2c1fe-102">EnumerableExpansion için EntrySelectedBy Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="2c1fe-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="2c1fe-103">Bu tanım veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2c1fe-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="2c1fe-104">Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi) EnumerableExpansions öğesi (biçimi) EnumerableExpansion öğesi (biçimi) EntrySelectedBy öğesi EnumerableExpansion (biçimi)</span><span class="sxs-lookup"><span data-stu-id="2c1fe-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2c1fe-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c1fe-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2c1fe-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c1fe-106">Attributes and Elements</span></span>

<span data-ttu-id="2c1fe-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `EntrySelectedBy` öğesi.</span><span class="sxs-lookup"><span data-stu-id="2c1fe-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2c1fe-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2c1fe-108">Attributes</span></span>

<span data-ttu-id="2c1fe-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="2c1fe-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2c1fe-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c1fe-110">Child Elements</span></span>

|<span data-ttu-id="2c1fe-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="2c1fe-111">Element</span></span>|<span data-ttu-id="2c1fe-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c1fe-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2c1fe-113">EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="2c1fe-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="2c1fe-114">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="2c1fe-114">Optional element.</span></span><br /><br /> <span data-ttu-id="2c1fe-115">Bu tanımın koleksiyon nesnelerini genişletmek için bulunması gereken koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2c1fe-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="2c1fe-116">EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="2c1fe-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="2c1fe-117">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="2c1fe-117">Optional element.</span></span><br /><br /> <span data-ttu-id="2c1fe-118">Koleksiyon nesnelerini nasıl genişletilir bu tanımı kullanan .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c1fe-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="2c1fe-119">TypeName öğesi için EntrySelectedBy EnumerableExpansion (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="2c1fe-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="2c1fe-120">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="2c1fe-120">Optional element.</span></span><br /><br /> <span data-ttu-id="2c1fe-121">Koleksiyon nesnelerini nasıl genişletilir bu tanımı kullanan bir .NET türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c1fe-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2c1fe-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c1fe-122">Parent Elements</span></span>

|<span data-ttu-id="2c1fe-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="2c1fe-123">Element</span></span>|<span data-ttu-id="2c1fe-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c1fe-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2c1fe-125">EnumerableExpansion öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="2c1fe-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="2c1fe-126">Bir görünümü'nde görüntülendiğinde nesneleri genişletilir belirli .NET koleksiyonu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2c1fe-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2c1fe-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c1fe-127">Remarks</span></span>

<span data-ttu-id="2c1fe-128">En az bir türü, seçim kümesi veya tanımı girişi için seçim koşulu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c1fe-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="2c1fe-129">Kullanabileceğiniz bir alt öğe sayısı maksimum sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="2c1fe-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="2c1fe-130">Seçimi koşullar bir nesne belirli bir özelliğine sahip olduğunda gibi kullanılacak tanımı için bulunması gereken bir koşul tanımlamak için kullanılır veya bir özel özellik değerini veya betik değerlendiren `true`.</span><span class="sxs-lookup"><span data-stu-id="2c1fe-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="2c1fe-131">Seçimi koşullar hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2c1fe-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2c1fe-132">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="2c1fe-132">See Also</span></span>

[<span data-ttu-id="2c1fe-133">Verileri görüntülemek için koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="2c1fe-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2c1fe-134">EnumerableExpansion öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="2c1fe-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="2c1fe-135">EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="2c1fe-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="2c1fe-136">EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="2c1fe-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="2c1fe-137">TypeName öğesi için EntrySelectedBy EnumerableExpansion (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="2c1fe-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="2c1fe-138">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="2c1fe-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)