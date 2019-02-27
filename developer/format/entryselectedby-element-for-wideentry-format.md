---
title: EntrySelectedBy öğesi WideEntry (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846098"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="70929-102">WideEntry için EntrySelectedBy Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="70929-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="70929-103">Geniş bir görünüm veya bu tanım için kullanılacak bulunmalıdır koşul bu tanımı kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="70929-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="70929-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi (biçimi) EntrySelectedBy öğesi WideEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="70929-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="70929-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70929-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="70929-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="70929-106">Attributes and Elements</span></span>

<span data-ttu-id="70929-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `EntrySelectedBy` öğesi.</span><span class="sxs-lookup"><span data-stu-id="70929-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="70929-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="70929-108">Attributes</span></span>

<span data-ttu-id="70929-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="70929-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="70929-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="70929-110">Child Elements</span></span>

|<span data-ttu-id="70929-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="70929-111">Element</span></span>|<span data-ttu-id="70929-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70929-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70929-113">EntrySelectedBy WideEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="70929-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="70929-114">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="70929-114">Optional element.</span></span><br /><br /> <span data-ttu-id="70929-115">Bu geniş görünüm tanımı kullanılmak üzere mevcut olmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="70929-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="70929-116">EntrySelectedBy WideEntry (biçimi) için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="70929-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="70929-117">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="70929-117">Optional element.</span></span><br /><br /> <span data-ttu-id="70929-118">Bu geniş görünüm tanımını kullanma .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="70929-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="70929-119">TypeName öğesi için EntrySelectedBy WideEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="70929-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="70929-120">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="70929-120">Optional element.</span></span><br /><br /> <span data-ttu-id="70929-121">Bu geniş görünüm tanımı kullanan bir .NET türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="70929-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="70929-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="70929-122">Parent Elements</span></span>

|<span data-ttu-id="70929-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="70929-123">Element</span></span>|<span data-ttu-id="70929-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70929-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70929-125">WideEntry öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="70929-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="70929-126">Geniş bir görünüm tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="70929-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="70929-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70929-127">Remarks</span></span>

<span data-ttu-id="70929-128">En az bir türü, seçim kümesi veya geniş görünüm tanımı için seçim koşulu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="70929-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="70929-129">Kullanabileceğiniz bir alt öğe sayısı maksimum sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="70929-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="70929-130">Seçimi koşullar bir nesne belirli bir özelliğine sahip olduğunda gibi kullanılacak tanımı için bulunması gereken bir koşul tanımlamak için kullanılır veya bir özel özellik değerini veya komut dosyası değerini değerlendiren `true`.</span><span class="sxs-lookup"><span data-stu-id="70929-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="70929-131">Seçimi koşullar hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="70929-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="70929-132">Geniş bir görünüm diğer bileşenler hakkında daha fazla bilgi için bkz. [geniş bir görünüm oluşturma](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="70929-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="70929-133">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="70929-133">See Also</span></span>

[<span data-ttu-id="70929-134">WideEntry öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="70929-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="70929-135">EntrySelectedBy WideEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="70929-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="70929-136">EntrySelectedBy WideEntry (biçimi) için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="70929-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="70929-137">TypeName öğesi için EntrySelectedBy WideEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="70929-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="70929-138">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="70929-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="70929-139">Verileri görüntülemek için koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="70929-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="70929-140">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="70929-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
