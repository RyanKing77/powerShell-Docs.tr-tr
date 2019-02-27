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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851586"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="0d2fa-102">GroupBy CustomEntry için EntrySelectedBy Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="0d2fa-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="0d2fa-103">Bu denetim tanımı veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0d2fa-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="0d2fa-104">Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0d2fa-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="0d2fa-105">GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) EntrySelectedBy öğesinin CustomEntry GroupBy (biçimi) için özel denetim</span><span class="sxs-lookup"><span data-stu-id="0d2fa-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0d2fa-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d2fa-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0d2fa-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0d2fa-107">Attributes and Elements</span></span>

<span data-ttu-id="0d2fa-108">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `EntrySelectedBy` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0d2fa-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="0d2fa-109">En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d2fa-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="0d2fa-110">Kullanabileceğiniz bir alt öğe sayısı maksimum sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="0d2fa-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="0d2fa-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0d2fa-111">Attributes</span></span>

<span data-ttu-id="0d2fa-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="0d2fa-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0d2fa-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0d2fa-113">Child Elements</span></span>

|<span data-ttu-id="0d2fa-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="0d2fa-114">Element</span></span>|<span data-ttu-id="0d2fa-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d2fa-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d2fa-116">GroupBy (biçimi) için EntrySelectedBy için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="0d2fa-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="0d2fa-117">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="0d2fa-117">Optional element.</span></span><br /><br /> <span data-ttu-id="0d2fa-118">Bu tanım için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0d2fa-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="0d2fa-119">GroupBy (biçimi) için EntrySelectedBy için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="0d2fa-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="0d2fa-120">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="0d2fa-120">Optional element.</span></span><br /><br /> <span data-ttu-id="0d2fa-121">Denetimin bu tanımı kullanan .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d2fa-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="0d2fa-122">GroupBy (biçimi) için EntrySelectedBy için TypeName öğesi</span><span class="sxs-lookup"><span data-stu-id="0d2fa-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="0d2fa-123">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="0d2fa-123">Optional element.</span></span><br /><br /> <span data-ttu-id="0d2fa-124">Denetimin bu tanımı kullanan bir .NET türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d2fa-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0d2fa-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0d2fa-125">Parent Elements</span></span>

|<span data-ttu-id="0d2fa-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="0d2fa-126">Element</span></span>|<span data-ttu-id="0d2fa-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d2fa-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d2fa-128">GroupBy (biçimi) için özel denetim için CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="0d2fa-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="0d2fa-129">Denetim tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d2fa-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0d2fa-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d2fa-130">Remarks</span></span>

<span data-ttu-id="0d2fa-131">Seçimi koşullar bulunması gereken bir koşul için kullanılacak tanım, bir nesne belirli bir özelliğine sahip olduğunda gibi veya özel özellik değerini tanımlamak için kullanılır veya komut dosyası değerlendirilen `true`.</span><span class="sxs-lookup"><span data-stu-id="0d2fa-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="0d2fa-132">Seçimi koşullar hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0d2fa-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d2fa-133">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="0d2fa-133">See Also</span></span>

[<span data-ttu-id="0d2fa-134">GroupBy (biçimi) için EntrySelectedBy için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="0d2fa-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="0d2fa-135">GroupBy (biçimi) için EntrySelectedBy için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="0d2fa-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="0d2fa-136">GroupBy (biçimi) için EntrySelectedBy için TypeName öğesi</span><span class="sxs-lookup"><span data-stu-id="0d2fa-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="0d2fa-137">CustomEntry öğesi görünümü (biçimi) için denetimleri için CustomEntries için</span><span class="sxs-lookup"><span data-stu-id="0d2fa-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="0d2fa-138">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="0d2fa-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
