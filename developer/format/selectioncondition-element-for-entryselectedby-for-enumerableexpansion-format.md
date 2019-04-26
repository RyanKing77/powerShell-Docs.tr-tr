---
title: SelectionCondition öğesi EntrySelectedBy EnumerableExpansion (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064144"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="3b4be-102">EnumerableExpansion EntrySelectedBy için SelectionCondition Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="3b4be-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="3b4be-103">Bu tanımın koleksiyon nesnelerini genişletmek için bulunması gereken koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3b4be-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="3b4be-104">Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi) EnumerableExpansions öğesi (biçimi) EnumerableExpansion öğesi (biçimi) EntrySelectedBy öğesi için EntrySelectedBy SelectionCondition öğesinin EnumerableExpansion (biçimi) EnumerableExpansion (biçimi)</span><span class="sxs-lookup"><span data-stu-id="3b4be-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3b4be-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b4be-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3b4be-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="3b4be-106">Attributes and Elements</span></span>

<span data-ttu-id="3b4be-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionCondition` öğesi.</span><span class="sxs-lookup"><span data-stu-id="3b4be-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="3b4be-108">Tek bir belirtmelisiniz `PropertyName` veya `ScriptBlock` öğesi.</span><span class="sxs-lookup"><span data-stu-id="3b4be-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="3b4be-109">`SelectionSetName` Ve `TypeName` öğeler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3b4be-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="3b4be-110">Her iki öğe birini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b4be-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3b4be-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3b4be-111">Attributes</span></span>

<span data-ttu-id="3b4be-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="3b4be-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3b4be-113">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="3b4be-113">Child Elements</span></span>

|<span data-ttu-id="3b4be-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="3b4be-114">Element</span></span>|<span data-ttu-id="3b4be-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b4be-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3b4be-116">PropertyName öğesi SelectionCondition EnumerableExpansion (biçimi) için EntrySelectedBy için için</span><span class="sxs-lookup"><span data-stu-id="3b4be-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="3b4be-117">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="3b4be-117">Optional element.</span></span><br /><br /> <span data-ttu-id="3b4be-118">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b4be-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="3b4be-119">SelectionCondition EnumerableExpansion (biçimi) için EntrySelectedBy için için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="3b4be-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="3b4be-120">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="3b4be-120">Optional element.</span></span><br /><br /> <span data-ttu-id="3b4be-121">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b4be-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="3b4be-122">SelectionCondition EnumerableExpansion (biçimi) için EntrySelectedBy için için SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="3b4be-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="3b4be-123">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="3b4be-123">Optional element.</span></span><br /><br /> <span data-ttu-id="3b4be-124">Koşul tetikleyen .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b4be-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="3b4be-125">TypeName öğesi SelectionCondition EnumerableExpansion (biçimi) için EntrySelectedBy için için</span><span class="sxs-lookup"><span data-stu-id="3b4be-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="3b4be-126">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="3b4be-126">Optional element.</span></span><br /><br /> <span data-ttu-id="3b4be-127">Koşul tetikleyen bir .NET türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b4be-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3b4be-128">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="3b4be-128">Parent Elements</span></span>

|<span data-ttu-id="3b4be-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="3b4be-129">Element</span></span>|<span data-ttu-id="3b4be-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b4be-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3b4be-131">EntrySelectedBy öğesi EnumerableExpansion (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="3b4be-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="3b4be-132">Bu tanımı tarafından hangi .NET koleksiyon nesnelerini genişletilir tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3b4be-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3b4be-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b4be-133">Remarks</span></span>

<span data-ttu-id="3b4be-134">Her tanımı en az bir tür adı, seçim kümesi veya seçim koşulu tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3b4be-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="3b4be-135">Bir seçim koşulu tanımlarken, aşağıdaki gereksinimler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="3b4be-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="3b4be-136">Seçim koşulu en az bir özellik adı veya bir betik bloğu belirtmelisiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b4be-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="3b4be-137">Seçim koşulu .NET türleri herhangi bir sayıda belirtebilirsiniz veya seçimi ayarlar, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b4be-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="3b4be-138">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [Diplaying veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3b4be-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="3b4be-139">Geniş bir görünüm diğer bileşenler hakkında daha fazla bilgi için bkz. [geniş Görünüm](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="3b4be-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3b4be-140">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="3b4be-140">See Also</span></span>

[<span data-ttu-id="3b4be-141">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="3b4be-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="3b4be-142">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="3b4be-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
