---
title: SelectionCondition öğesi EntrySelectedBy WideControl (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064015"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="38221-102">WideControl EntrySelectedBy için SelectionCondition Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="38221-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="38221-103">Bu tanım için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="38221-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="38221-104">Geniş bir girdi tanımı için belirtilen seçim koşullar sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="38221-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="38221-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi (biçimi) EntrySelectedBy öğesi SelectionCondition öğesinin WideEntry (biçimi) EntrySelectedBy WideEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="38221-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="38221-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38221-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="38221-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="38221-107">Attributes and Elements</span></span>

<span data-ttu-id="38221-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionCondition` öğesi.</span><span class="sxs-lookup"><span data-stu-id="38221-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="38221-109">Tek bir belirtmelisiniz `PropertyName` veya `ScriptBlock` öğesi.</span><span class="sxs-lookup"><span data-stu-id="38221-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="38221-110">`SelectionSetName` Ve `TypeName` öğeler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="38221-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="38221-111">Her iki öğe birini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38221-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="38221-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="38221-112">Attributes</span></span>

<span data-ttu-id="38221-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="38221-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="38221-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="38221-114">Child Elements</span></span>

|<span data-ttu-id="38221-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="38221-115">Element</span></span>|<span data-ttu-id="38221-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38221-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38221-117">PropertyName öğesi SelectionCondition WideEntry (biçimi) için EntrySelectedBy için için</span><span class="sxs-lookup"><span data-stu-id="38221-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="38221-118">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="38221-118">Optional element.</span></span><br /><br /> <span data-ttu-id="38221-119">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="38221-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="38221-120">SelectionCondition WideEntry (biçimi) için EntrySelectedBy için için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="38221-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="38221-121">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="38221-121">Optional element.</span></span><br /><br /> <span data-ttu-id="38221-122">Koşul tetikler betik bloğu belirtir.</span><span class="sxs-lookup"><span data-stu-id="38221-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="38221-123">SelectionCondition WideEntry (biçimi) için EntrySelectedBy için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="38221-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="38221-124">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="38221-124">Optional element.</span></span><br /><br /> <span data-ttu-id="38221-125">Koşul tetikleyen .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="38221-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="38221-126">TypeName öğesi SelectionCondition WideEntry (biçimi) için EntrySelectedBy için için</span><span class="sxs-lookup"><span data-stu-id="38221-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="38221-127">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="38221-127">Optional element.</span></span><br /><br /> <span data-ttu-id="38221-128">Koşul tetikleyen bir .NET türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="38221-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="38221-129">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="38221-129">Parent Elements</span></span>

|<span data-ttu-id="38221-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="38221-130">Element</span></span>|<span data-ttu-id="38221-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38221-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38221-132">EntrySelectedBy öğesi WideEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="38221-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="38221-133">Bu geniş bir girdi veya kullanılmak üzere bu giriş için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="38221-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="38221-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38221-134">Remarks</span></span>

<span data-ttu-id="38221-135">En az bir tür adı, seçim kümesi veya tanımlanan seçim koşulu her geniş bir girdi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="38221-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="38221-136">Bir seçim koşulu tanımlarken, aşağıdaki gereksinimler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="38221-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="38221-137">Seçim koşulu en az bir özellik adı veya bir betik bloğu belirtmelisiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="38221-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="38221-138">Seçim koşulu .NET türleri herhangi bir sayıda belirtebilirsiniz veya seçimi ayarlar, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="38221-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="38221-139">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="38221-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="38221-140">Geniş bir görünüm diğer bileşenler hakkında daha fazla bilgi için bkz. [geniş bir görünüm oluşturma](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="38221-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="38221-141">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="38221-141">See Also</span></span>

[<span data-ttu-id="38221-142">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="38221-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="38221-143">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="38221-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="38221-144">EntrySelectedBy öğesi WideEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="38221-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="38221-145">PropertyName öğesi SelectionCondition WideEntry (biçimi) için EntrySelectedBy için için</span><span class="sxs-lookup"><span data-stu-id="38221-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="38221-146">SelectionCondition WideEntry (biçimi) için EntrySelectedBy için için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="38221-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="38221-147">SelectionCondition WideEntry (biçimi) için EntrySelectedBy için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="38221-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="38221-148">TypeName öğesi SelectionCondition WideEntry (biçimi) için EntrySelectedBy için için</span><span class="sxs-lookup"><span data-stu-id="38221-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="38221-149">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="38221-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
