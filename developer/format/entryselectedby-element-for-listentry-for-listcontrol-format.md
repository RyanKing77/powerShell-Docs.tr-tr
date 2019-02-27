---
title: EntrySelectedBy öğesi ListEntry ListControl (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 723619e67612b859d0acbab37eecd82141adf923
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846077"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="79559-102">ListControl ListEntry için EntrySelectedBy Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="79559-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="79559-103">Bu liste görünüm tanımını kullanma .NET türleri veya bu tanım için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="79559-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="79559-104">Çoğu durumda, yalnızca bir tanımı bir liste görünümü için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="79559-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="79559-105">Ancak, farklı nesneler için farklı veri görüntülemek için aynı liste görünümü kullanmak istiyorsanız, liste görünümü için birden çok tanım sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79559-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="79559-106">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi ListControl (biçimi) EntrySelectedBy öğesinin ListEntry ListEntry öğesinin ListControl (biçimi) ListEntry ListControl (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="79559-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="79559-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79559-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="79559-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="79559-108">Attributes and Elements</span></span>

<span data-ttu-id="79559-109">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `EntrySelectedBy` öğesi.</span><span class="sxs-lookup"><span data-stu-id="79559-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="79559-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="79559-110">Attributes</span></span>

<span data-ttu-id="79559-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="79559-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="79559-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="79559-112">Child Elements</span></span>

|<span data-ttu-id="79559-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="79559-113">Element</span></span>|<span data-ttu-id="79559-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79559-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="79559-115">EntrySelectedBy ListControl (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="79559-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="79559-116">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="79559-116">Optional element.</span></span><br /><br /> <span data-ttu-id="79559-117">Bu liste görünümü tanımını kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="79559-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="79559-118">EnrtySelectedBy ListControl (biçimi) için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="79559-118">SelectionSetName Element for EnrtySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="79559-119">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="79559-119">Optional element.</span></span><br /><br /> <span data-ttu-id="79559-120">Bu liste görünüm tanımını kullanma .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="79559-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="79559-121">TypeName öğesi için EntrySelectedBy ListControl (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="79559-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="79559-122">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="79559-122">Optional element.</span></span><br /><br /> <span data-ttu-id="79559-123">Bu liste görünüm tanımı kullanan bir .NET türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="79559-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="79559-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="79559-124">Parent Elements</span></span>

|<span data-ttu-id="79559-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="79559-125">Element</span></span>|<span data-ttu-id="79559-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79559-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="79559-127">ListEntry öğesi ListControl (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="79559-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="79559-128">Satırları listesinin nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="79559-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="79559-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79559-129">Remarks</span></span>

<span data-ttu-id="79559-130">En az bir türü, seçim kümesi veya bir liste görünüm tanımı için seçim koşulu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="79559-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="79559-131">Kullanabileceğiniz bir alt öğe sayısı maksimum sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="79559-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="79559-132">Seçimi koşullar bir nesne belirli bir özelliğine sahip olduğunda gibi kullanılacak tanımı için bulunması gereken bir koşul tanımlamak için kullanılır veya bir özel özellik değerini veya betik değerlendiren `true`.</span><span class="sxs-lookup"><span data-stu-id="79559-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="79559-133">Seçimi koşullar hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="79559-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="79559-134">Bir liste görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="79559-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="79559-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="79559-135">Example</span></span>

<span data-ttu-id="79559-136">Aşağıdaki örnek, kendi .NET türü adını kullanarak bir liste görünümü nesneleri tanımlamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="79559-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="79559-137">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="79559-137">See Also</span></span>

[<span data-ttu-id="79559-138">ListEntry öğesi ListControl (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="79559-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="79559-139">EntrySelectedBy ListControl (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="79559-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="79559-140">EnrtySelectedBy ListControl (biçimi) için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="79559-140">SelectionSetName Element for EnrtySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="79559-141">TypeName öğesi için EntrySelectedBy ListControl (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="79559-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="79559-142">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="79559-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="79559-143">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="79559-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="79559-144">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="79559-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
