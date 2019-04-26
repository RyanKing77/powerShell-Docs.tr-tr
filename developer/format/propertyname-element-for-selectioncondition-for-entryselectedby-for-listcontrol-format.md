---
title: PropertyName öğesi SelectionCondition EntrySelectedBy ListControl (biçimi) için için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064911"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="74af4-102">ListControl EntrySelectedBy için SelectionCondition PropertyName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="74af4-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="74af4-103">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="74af4-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="74af4-104">Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve liste girdisini kullanılır.</span><span class="sxs-lookup"><span data-stu-id="74af4-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="74af4-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi) EntrySelectedBy öğesi SelectionCondition öğesinin ListEntry (biçimi) EntrySelectedBy EntrySelectedBy ListEntry (biçimi) için için SelectionCondition PropertyName öğesinin ListEntry (biçimi)</span><span class="sxs-lookup"><span data-stu-id="74af4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="74af4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74af4-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="74af4-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="74af4-107">Attributes and Elements</span></span>

<span data-ttu-id="74af4-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `PropertyName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="74af4-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="74af4-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="74af4-109">Attributes</span></span>

<span data-ttu-id="74af4-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="74af4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="74af4-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="74af4-111">Child Elements</span></span>

<span data-ttu-id="74af4-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="74af4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="74af4-113">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="74af4-113">Parent Elements</span></span>

|<span data-ttu-id="74af4-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="74af4-114">Element</span></span>|<span data-ttu-id="74af4-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74af4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="74af4-116">EntrySelectedBy ListEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="74af4-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="74af4-117">Bu liste girişi kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="74af4-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="74af4-118">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="74af4-118">Text Value</span></span>

<span data-ttu-id="74af4-119">.NET özellik adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="74af4-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="74af4-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74af4-120">Remarks</span></span>

<span data-ttu-id="74af4-121">Seçim koşulu en az bir özellik adı veya bir betik bloğu belirtmelisiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="74af4-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="74af4-122">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="74af4-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="74af4-123">Bir liste görünümü diğer bileşenler hakkında daha fazla bilgi için bkz. [liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="74af4-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="74af4-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="74af4-124">See Also</span></span>

[<span data-ttu-id="74af4-125">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="74af4-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="74af4-126">Verilerinin koşulları tanımlama görüntülenir</span><span class="sxs-lookup"><span data-stu-id="74af4-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="74af4-127">ListEntry öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="74af4-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="74af4-128">SelectionCondition ListEntry (biçimi) için EntrySelectedBy için için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="74af4-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="74af4-129">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="74af4-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
