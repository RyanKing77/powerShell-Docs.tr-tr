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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059023"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="f2fee-102">ListControl EntrySelectedBy için SelectionCondition PropertyName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="f2fee-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="f2fee-103">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2fee-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="f2fee-104">Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve liste girdisini kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f2fee-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="f2fee-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi) EntrySelectedBy öğesi SelectionCondition öğesinin ListEntry (biçimi) EntrySelectedBy EntrySelectedBy ListEntry (biçimi) için için SelectionCondition PropertyName öğesinin ListEntry (biçimi)</span><span class="sxs-lookup"><span data-stu-id="f2fee-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f2fee-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2fee-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f2fee-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2fee-107">Attributes and Elements</span></span>

<span data-ttu-id="f2fee-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `PropertyName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f2fee-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f2fee-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f2fee-109">Attributes</span></span>

<span data-ttu-id="f2fee-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="f2fee-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f2fee-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2fee-111">Child Elements</span></span>

<span data-ttu-id="f2fee-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="f2fee-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f2fee-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2fee-113">Parent Elements</span></span>

|<span data-ttu-id="f2fee-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2fee-114">Element</span></span>|<span data-ttu-id="f2fee-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2fee-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2fee-116">EntrySelectedBy ListEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="f2fee-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="f2fee-117">Bu liste girişi kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f2fee-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f2fee-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="f2fee-118">Text Value</span></span>

<span data-ttu-id="f2fee-119">.NET özellik adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="f2fee-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="f2fee-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2fee-120">Remarks</span></span>

<span data-ttu-id="f2fee-121">Seçim koşulu en az bir özellik adı veya bir betik bloğu belirtmelisiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2fee-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="f2fee-122">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f2fee-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f2fee-123">Bir liste görünümü diğer bileşenler hakkında daha fazla bilgi için bkz. [liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="f2fee-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f2fee-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="f2fee-124">See Also</span></span>

[<span data-ttu-id="f2fee-125">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2fee-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f2fee-126">Verilerinin koşulları tanımlama görüntülenir</span><span class="sxs-lookup"><span data-stu-id="f2fee-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f2fee-127">ListEntry öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="f2fee-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="f2fee-128">SelectionCondition ListEntry (biçimi) için EntrySelectedBy için için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="f2fee-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="f2fee-129">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="f2fee-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
