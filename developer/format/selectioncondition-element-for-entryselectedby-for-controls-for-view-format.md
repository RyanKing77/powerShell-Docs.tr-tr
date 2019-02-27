---
title: SelectionCondition öğesi görünümü (biçimi) için denetimleri için EntrySelectedBy için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848226"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="8f826-102">Görünüm Denetimleri için EntrySelectedBy SelectionCondition Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="8f826-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="8f826-103">Kullanılacak denetimi tanımı bulunması gereken bir koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8f826-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="8f826-104">Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8f826-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="8f826-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) denetimleri (biçimi) öğesi denetim öğesi denetimi için CustomEntries öğesi görünümü (biçimi) için denetimleri için özel denetim öğesi görünümü (biçimi) için denetimleri için Görünümü (biçimi) CustomEntry öğesinin CustomEntries CustomEntry EntrySelectedBy denetimleri için View (Görünüm (biçimi) SelectionCondition öğesinin denetimleri için görüntüleme (biçimi) EntrySelectedBy öğesinin denetimleri için denetimler için özel denetim Biçimi)</span><span class="sxs-lookup"><span data-stu-id="8f826-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8f826-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f826-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8f826-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f826-107">Attributes and Elements</span></span>

<span data-ttu-id="8f826-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionCondition` öğesi.</span><span class="sxs-lookup"><span data-stu-id="8f826-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8f826-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8f826-109">Attributes</span></span>

<span data-ttu-id="8f826-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="8f826-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8f826-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f826-111">Child Elements</span></span>

|<span data-ttu-id="8f826-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="8f826-112">Element</span></span>|<span data-ttu-id="8f826-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f826-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f826-114">PropertyName öğesi görünümü (biçimi) için denetimleri için SelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="8f826-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8f826-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="8f826-115">Optional element.</span></span><br /><br /> <span data-ttu-id="8f826-116">Koşul tetikleyen .NET özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f826-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="8f826-117">ScriptBlock öğesi görünümü (biçimi) için denetimleri için SelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="8f826-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8f826-118">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="8f826-118">Optional element.</span></span><br /><br /> <span data-ttu-id="8f826-119">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f826-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="8f826-120">SelectionSetName öğesi görünümü (biçimi) için denetimleri için SelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="8f826-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8f826-121">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="8f826-121">Optional element.</span></span><br /><br /> <span data-ttu-id="8f826-122">Koşul tetikleyen .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f826-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="8f826-123">TypeName öğesi görünümü (biçimi) için denetimleri için SelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="8f826-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8f826-124">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="8f826-124">Optional element.</span></span><br /><br /> <span data-ttu-id="8f826-125">Koşul tetikleyen bir .NET türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f826-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8f826-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f826-126">Parent Elements</span></span>

|<span data-ttu-id="8f826-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="8f826-127">Element</span></span>|<span data-ttu-id="8f826-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f826-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f826-129">EntrySelectedBy öğesi görünümü (biçimi) için denetimleri için CustomEntry için</span><span class="sxs-lookup"><span data-stu-id="8f826-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="8f826-130">Bu denetim tanımı veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8f826-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8f826-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f826-131">Remarks</span></span>

<span data-ttu-id="8f826-132">Bir seçim koşulu tanımlarken, aşağıdaki gereksinimler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="8f826-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="8f826-133">Seçim koşulu en az bir özellik adı veya bir betik bloğu belirtmelisiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f826-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="8f826-134">Seçim koşulu .NET türleri herhangi bir sayıda belirtebilirsiniz veya seçimi ayarlar, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f826-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="8f826-135">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="8f826-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8f826-136">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="8f826-136">See Also</span></span>

[<span data-ttu-id="8f826-137">PropertyName öğesi görünümü (biçimi) için denetimleri için SelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="8f826-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8f826-138">ScriptBlock öğesi görünümü (biçimi) için denetimleri için SelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="8f826-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8f826-139">SelectionSetName öğesi görünümü (biçimi) için denetimleri için SelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="8f826-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8f826-140">TypeName öğesi görünümü (biçimi) için denetimleri için SelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="8f826-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8f826-141">EntrySelectedBy öğesi görünümü (biçimi) için denetimleri için CustomEntry için</span><span class="sxs-lookup"><span data-stu-id="8f826-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="8f826-142">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="8f826-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
