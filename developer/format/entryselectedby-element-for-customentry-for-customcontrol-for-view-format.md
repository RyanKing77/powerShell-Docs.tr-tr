---
title: EntrySelectedBy öğesi görünümü (biçimi) için özel denetim için CustomEntry için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849325"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="a27bc-102">Görünüm CustomControl için CustomEntry EntrySelectedBy Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="a27bc-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="a27bc-103">Bu özel giriş veya kullanılmak üzere bu giriş için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a27bc-103">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="a27bc-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomEntry öğesinin CustomEntries EntrySelectedBy görünümü (biçimi) için özel denetim için Öğe için CustomEntry görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="a27bc-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a27bc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a27bc-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a27bc-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a27bc-106">Attributes and Elements</span></span>

<span data-ttu-id="a27bc-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `EntrySelectedBy` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a27bc-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a27bc-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a27bc-108">Attributes</span></span>

<span data-ttu-id="a27bc-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="a27bc-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a27bc-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a27bc-110">Child Elements</span></span>

|<span data-ttu-id="a27bc-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="a27bc-111">Element</span></span>|<span data-ttu-id="a27bc-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a27bc-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a27bc-113">EntrySelectedBy CustomEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="a27bc-113">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="a27bc-114">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="a27bc-114">Optional element.</span></span><br /><br /> <span data-ttu-id="a27bc-115">Bu tanım için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a27bc-115">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="a27bc-116">EntrySelectedBy CustomEntry (biçimi) için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="a27bc-116">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="a27bc-117">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="a27bc-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a27bc-118">Denetim görünüm bu tanımı kullanan .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a27bc-118">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="a27bc-119">TypeName öğesi için EntrySelectedBy CustomEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="a27bc-119">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="a27bc-120">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="a27bc-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a27bc-121">Denetim görünüm bu tanımı kullanan bir .NET türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a27bc-121">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a27bc-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a27bc-122">Parent Elements</span></span>

|<span data-ttu-id="a27bc-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="a27bc-123">Element</span></span>|<span data-ttu-id="a27bc-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a27bc-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a27bc-125">İçin görünümün (biçimi) CustomEntries CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="a27bc-125">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="a27bc-126">Belirli bir .NET nesneleri tarafından kullanılan denetimlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a27bc-126">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a27bc-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a27bc-127">Remarks</span></span>

<span data-ttu-id="a27bc-128">En az bir türü, seçim kümesi veya bir giriş için seçim koşulu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a27bc-128">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="a27bc-129">Kullanabileceğiniz bir alt öğe sayısı maksimum sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="a27bc-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="a27bc-130">Seçimi koşullar bulunması gereken bir koşul için kullanılacak giriş, gibi bir nesne belirli bir özelliğine sahip olduğunda veya bir özel özellik değerini tanımlamak için kullanılan veya komut dosyası değerlendirilen `true`.</span><span class="sxs-lookup"><span data-stu-id="a27bc-130">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="a27bc-131">Seçimi koşullar hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a27bc-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a27bc-132">Bir özel denetim görünüm bileşenleri hakkında daha fazla bilgi için bkz. [özel denetim Görünüm](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a27bc-132">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a27bc-133">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a27bc-133">See Also</span></span>

[<span data-ttu-id="a27bc-134">EntrySelectedBy CustomEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="a27bc-134">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="a27bc-135">EntrySelectedBy CustomEntry (biçimi) için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="a27bc-135">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a27bc-136">TypeName öğesi için EntrySelectedBy CustomEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="a27bc-136">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a27bc-137">İçin görünümün (biçimi) CustomEntries CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="a27bc-137">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a27bc-138">Özel denetim görünümü</span><span class="sxs-lookup"><span data-stu-id="a27bc-138">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="a27bc-139">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="a27bc-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
