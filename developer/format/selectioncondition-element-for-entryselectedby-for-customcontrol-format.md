---
title: Özel denetim (biçimi) için EntrySelectedBy için SelectionCondition öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848793"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="db45a-102">CustomControl EntrySelectedBy için SelectionCondition Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="db45a-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="db45a-103">Bir denetim tanımı kullanılacak bulunması gereken bir koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="db45a-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="db45a-104">Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db45a-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="db45a-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi görünümü (biçimi) CustomEntries öğesinin CustomEntries için özel denetim için View (Görünüm (biçimi) CustomEntry öğesinin özel denetim Biçimi) CustomItem öğesi görünümü (biçimi) EntrySelectedBy öğesinin CustomEntry EntrySelectedBy Görünüm (biçimi) için özel denetim için View (biçimi) SelectionCondition öğesinin özel denetim için özel denetim için CustomEntry için</span><span class="sxs-lookup"><span data-stu-id="db45a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="db45a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db45a-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="db45a-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="db45a-107">Attributes and Elements</span></span>

<span data-ttu-id="db45a-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionCondition` öğesi.</span><span class="sxs-lookup"><span data-stu-id="db45a-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="db45a-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="db45a-109">Attributes</span></span>

<span data-ttu-id="db45a-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="db45a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="db45a-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="db45a-111">Child Elements</span></span>

|<span data-ttu-id="db45a-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="db45a-112">Element</span></span>|<span data-ttu-id="db45a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db45a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db45a-114">PropertyName öğesi görünümü (biçimi) için özel denetim için SelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="db45a-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="db45a-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="db45a-115">Optional element.</span></span><br /><br /> <span data-ttu-id="db45a-116">Koşul tetikleyen .NET özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="db45a-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="db45a-117">ScriptBlock öğesi görünümü (biçimi) için özel denetim için SelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="db45a-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="db45a-118">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="db45a-118">Optional element.</span></span><br /><br /> <span data-ttu-id="db45a-119">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="db45a-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="db45a-120">SelectionSetName öğesi görünümü (biçimi) için özel denetim için SelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="db45a-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="db45a-121">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="db45a-121">Optional element.</span></span><br /><br /> <span data-ttu-id="db45a-122">Koşul tetikleyen .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="db45a-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="db45a-123">TypeName öğesi görünümü (biçimi) için özel denetim için SelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="db45a-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="db45a-124">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="db45a-124">Optional element.</span></span><br /><br /> <span data-ttu-id="db45a-125">Koşul tetikleyen bir .NET türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="db45a-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="db45a-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="db45a-126">Parent Elements</span></span>

|<span data-ttu-id="db45a-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="db45a-127">Element</span></span>|<span data-ttu-id="db45a-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db45a-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db45a-129">EntrySelectedBy öğesi görünümü (biçimi) için özel denetim için CustomEntry için</span><span class="sxs-lookup"><span data-stu-id="db45a-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="db45a-130">Bu denetim tanımı veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="db45a-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="db45a-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db45a-131">Remarks</span></span>

<span data-ttu-id="db45a-132">Bir seçim koşulu tanımlarken, aşağıdaki gereksinimler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="db45a-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="db45a-133">Seçim koşulu en az bir özellik adı veya bir betik bloğu belirtmelisiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="db45a-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="db45a-134">Seçim koşulu .NET türleri herhangi bir sayıda belirtebilirsiniz veya seçimi ayarlar, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="db45a-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="db45a-135">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="db45a-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="db45a-136">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="db45a-136">See Also</span></span>

[<span data-ttu-id="db45a-137">PropertyName öğesi görünümü (biçimi) için özel denetim için SelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="db45a-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="db45a-138">ScriptBlock öğesi görünümü (biçimi) için özel denetim için SelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="db45a-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="db45a-139">SelectionSetName öğesi görünümü (biçimi) için özel denetim için SelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="db45a-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="db45a-140">TypeName öğesi görünümü (biçimi) için özel denetim için SelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="db45a-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="db45a-141">EntrySelectedBy öğesi görünümü (biçimi) için özel denetim için CustomEntry için</span><span class="sxs-lookup"><span data-stu-id="db45a-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="db45a-142">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="db45a-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
