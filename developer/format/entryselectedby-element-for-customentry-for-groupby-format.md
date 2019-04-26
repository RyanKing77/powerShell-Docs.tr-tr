---
title: GroupBy (biçimi) için CustomEntry için EntrySelectedBy öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066235"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="2b904-102">GroupBy CustomEntry için EntrySelectedBy Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="2b904-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="2b904-103">Bu denetim tanımı veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2b904-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="2b904-104">Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b904-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="2b904-105">GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) EntrySelectedBy öğesinin CustomEntry GroupBy (biçimi) için özel denetim</span><span class="sxs-lookup"><span data-stu-id="2b904-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2b904-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b904-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2b904-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="2b904-107">Attributes and Elements</span></span>

<span data-ttu-id="2b904-108">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `EntrySelectedBy` öğesi.</span><span class="sxs-lookup"><span data-stu-id="2b904-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="2b904-109">En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b904-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="2b904-110">Kullanabileceğiniz bir alt öğe sayısı maksimum sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="2b904-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="2b904-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2b904-111">Attributes</span></span>

<span data-ttu-id="2b904-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="2b904-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2b904-113">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="2b904-113">Child Elements</span></span>

|<span data-ttu-id="2b904-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b904-114">Element</span></span>|<span data-ttu-id="2b904-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b904-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b904-116">GroupBy (biçimi) için EntrySelectedBy için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="2b904-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="2b904-117">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="2b904-117">Optional element.</span></span><br /><br /> <span data-ttu-id="2b904-118">Bu tanım için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2b904-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="2b904-119">GroupBy (biçimi) için EntrySelectedBy için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="2b904-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="2b904-120">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="2b904-120">Optional element.</span></span><br /><br /> <span data-ttu-id="2b904-121">Denetimin bu tanımı kullanan .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b904-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="2b904-122">GroupBy (biçimi) için EntrySelectedBy için TypeName öğesi</span><span class="sxs-lookup"><span data-stu-id="2b904-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="2b904-123">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="2b904-123">Optional element.</span></span><br /><br /> <span data-ttu-id="2b904-124">Denetimin bu tanımı kullanan bir .NET türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b904-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2b904-125">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="2b904-125">Parent Elements</span></span>

|<span data-ttu-id="2b904-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b904-126">Element</span></span>|<span data-ttu-id="2b904-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b904-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b904-128">GroupBy (biçimi) için özel denetim için CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="2b904-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="2b904-129">Denetim tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b904-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2b904-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b904-130">Remarks</span></span>

<span data-ttu-id="2b904-131">Seçimi koşullar bulunması gereken bir koşul için kullanılacak tanım, bir nesne belirli bir özelliğine sahip olduğunda gibi veya özel özellik değerini tanımlamak için kullanılır veya komut dosyası değerlendirilen `true`.</span><span class="sxs-lookup"><span data-stu-id="2b904-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="2b904-132">Seçimi koşullar hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2b904-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2b904-133">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="2b904-133">See Also</span></span>

[<span data-ttu-id="2b904-134">GroupBy (biçimi) için EntrySelectedBy için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="2b904-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="2b904-135">GroupBy (biçimi) için EntrySelectedBy için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="2b904-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="2b904-136">GroupBy (biçimi) için EntrySelectedBy için TypeName öğesi</span><span class="sxs-lookup"><span data-stu-id="2b904-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="2b904-137">CustomEntry öğesi görünümü (biçimi) için denetimleri için CustomEntries için</span><span class="sxs-lookup"><span data-stu-id="2b904-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="2b904-138">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="2b904-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
