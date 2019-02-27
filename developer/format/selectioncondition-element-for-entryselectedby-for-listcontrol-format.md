---
title: SelectionCondition öğesi EntrySelectedBy ListControl (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: ec75945c5517c02fa001f0a38573c045ffcdbfd3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847855"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="4b918-102">ListControl EntrySelectedBy için SelectionCondition Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="4b918-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="4b918-103">Bu liste görünümü tanımını kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4b918-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="4b918-104">Bir liste tanımı için belirtilen seçim koşullar sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="4b918-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="4b918-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi) EntrySelectedBy öğesi SelectionCondition öğesinin ListEntry (biçimi) EntrySelectedBy ListEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="4b918-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4b918-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b918-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4b918-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b918-107">Attributes and Elements</span></span>

<span data-ttu-id="4b918-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionCondition` öğesi.</span><span class="sxs-lookup"><span data-stu-id="4b918-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4b918-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4b918-109">Attributes</span></span>

<span data-ttu-id="4b918-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="4b918-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4b918-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b918-111">Child Elements</span></span>

|<span data-ttu-id="4b918-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="4b918-112">Element</span></span>|<span data-ttu-id="4b918-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b918-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4b918-114">PropertyName öğesi SelectionCondition ListEntry (biçimi) için EmtrySelectedBy için için</span><span class="sxs-lookup"><span data-stu-id="4b918-114">PropertyName Element for SelectionCondition for EmtrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="4b918-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="4b918-115">Optional element.</span></span><br /><br /> <span data-ttu-id="4b918-116">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b918-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="4b918-117">SelectionCondition ListEntry (biçimi) için EntrySelectedBy için için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="4b918-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="4b918-118">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="4b918-118">Optional element.</span></span><br /><br /> <span data-ttu-id="4b918-119">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b918-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="4b918-120">SelectionCondition ListEntry (biçimi) için EntrySelectedBy için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="4b918-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="4b918-121">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="4b918-121">Optional element.</span></span><br /><br /> <span data-ttu-id="4b918-122">Tetikleme koşulu .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b918-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="4b918-123">TypeName öğesi SelectionCondition ListEntry (biçimi) için EntrySelectedBy için için</span><span class="sxs-lookup"><span data-stu-id="4b918-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="4b918-124">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="4b918-124">Optional element.</span></span><br /><br /> <span data-ttu-id="4b918-125">Koşul tetikleyen bir .NET türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b918-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4b918-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b918-126">Parent Elements</span></span>

|<span data-ttu-id="4b918-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="4b918-127">Element</span></span>|<span data-ttu-id="4b918-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b918-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4b918-129">EntrySelectedBy öğesi TableRowEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="4b918-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="4b918-130">Bu tablo girişi kullanıp bu giriş için kullanılacak bulunmalıdır koşul .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4b918-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4b918-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b918-131">Remarks</span></span>

<span data-ttu-id="4b918-132">lWhen seçim koşulu tanımlıyorsanız, aşağıdaki gereksinimler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="4b918-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="4b918-133">Seçim koşulu en az bir özellik adı veya bir betik bloğu belirtmelisiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b918-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="4b918-134">Seçim koşulu .NET türleri herhangi bir sayıda belirtebilirsiniz veya seçimi ayarlar, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b918-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="4b918-135">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="4b918-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="4b918-136">Bir liste görünümü diğer bileşenler hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="4b918-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4b918-137">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="4b918-137">See Also</span></span>

[<span data-ttu-id="4b918-138">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="4b918-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="4b918-139">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="4b918-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="4b918-140">ListEntry öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="4b918-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="4b918-141">EnrtySelectedBy ListEntry (biçimi) için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="4b918-141">SelectionSetName Element for EnrtySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="4b918-142">TypeName öğesi için EntrySelectedBy ListEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="4b918-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](http://msdn.microsoft.com/en-us/fcd4daa6-f3fd-43f7-a468-03c582d34533)

[<span data-ttu-id="4b918-143">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="4b918-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
