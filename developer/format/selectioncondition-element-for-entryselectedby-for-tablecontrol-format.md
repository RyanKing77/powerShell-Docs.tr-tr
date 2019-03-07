---
title: TableControl (biçimi) için EntrySelectedBy için SelectionCondition öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850480"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="558cd-102">TableControl EntrySelectedBy için SelectionCondition Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="558cd-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="558cd-103">Bu tablo görünümü tanımı için kullanılmak üzere mevcut olmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="558cd-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="558cd-104">Tablo tanımı için belirtilen seçim koşullar sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="558cd-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="558cd-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi (biçimi) TableRowEntry öğesi (biçimi) EntrySelectedBy öğesi TableRowEntry (biçimi) için EntrySelectedBy TableRowEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="558cd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="558cd-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="558cd-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="558cd-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="558cd-107">Attributes and Elements</span></span>

<span data-ttu-id="558cd-108">Aşağıdaki bölümlerde, öznitelikleri ve alt öğeleri SelectionCondition öğesinin üst öğesi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="558cd-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="558cd-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="558cd-109">Attributes</span></span>

<span data-ttu-id="558cd-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="558cd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="558cd-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="558cd-111">Child Elements</span></span>

|<span data-ttu-id="558cd-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="558cd-112">Element</span></span>|<span data-ttu-id="558cd-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="558cd-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="558cd-114">PropertyName öğesi SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için</span><span class="sxs-lookup"><span data-stu-id="558cd-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="558cd-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="558cd-115">Optional element.</span></span><br /><br /> <span data-ttu-id="558cd-116">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="558cd-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="558cd-117">SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="558cd-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="558cd-118">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="558cd-118">Optional element.</span></span><br /><br /> <span data-ttu-id="558cd-119">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="558cd-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="558cd-120">SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="558cd-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="558cd-121">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="558cd-121">Optional element.</span></span><br /><br /> <span data-ttu-id="558cd-122">Tetikleme koşulu .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="558cd-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="558cd-123">TypeName öğesi SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için</span><span class="sxs-lookup"><span data-stu-id="558cd-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="558cd-124">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="558cd-124">Optional element.</span></span><br /><br /> <span data-ttu-id="558cd-125">Koşul tetikleyen bir .NET türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="558cd-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="558cd-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="558cd-126">Parent Elements</span></span>

|<span data-ttu-id="558cd-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="558cd-127">Element</span></span>|<span data-ttu-id="558cd-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="558cd-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="558cd-129">EntrySelectedBy öğesi TableRowEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="558cd-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="558cd-130">Bu tablo girişi kullanıp bu giriş için kullanılacak bulunmalıdır koşul .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="558cd-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="558cd-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="558cd-131">Remarks</span></span>

<span data-ttu-id="558cd-132">Her liste girişi, en az bir tür adı, seçim kümesi veya seçim koşulu tanımlanmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="558cd-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="558cd-133">Bir seçim koşulu tanımlarken, aşağıdaki gereksinimler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="558cd-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="558cd-134">Seçim koşulu en az bir özellik adı veya bir betik bloğu belirtmelisiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="558cd-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="558cd-135">Seçim koşulu .NET türleri herhangi bir sayıda belirtebilirsiniz veya seçimi ayarlar, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="558cd-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="558cd-136">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="558cd-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="558cd-137">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="558cd-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="558cd-138">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="558cd-138">See Also</span></span>

[<span data-ttu-id="558cd-139">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="558cd-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="558cd-140">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="558cd-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="558cd-141">EntrySelectedBy öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="558cd-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="558cd-142">PropertyName öğesi SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için</span><span class="sxs-lookup"><span data-stu-id="558cd-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="558cd-143">SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="558cd-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="558cd-144">SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="558cd-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="558cd-145">TypeName öğesi SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için</span><span class="sxs-lookup"><span data-stu-id="558cd-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="558cd-146">Biçimlendirme bir Windows PowerShell yazma ve dosya türleri</span><span class="sxs-lookup"><span data-stu-id="558cd-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)