---
title: ScriptBlock öğesi SelectionCondition EntrySelectedBy ListControl (biçimi) için için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064365"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="56333-102">ListControl EntrySelectedBy için SelectionCondition ScriptBlock Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="56333-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="56333-103">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="56333-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="56333-104">Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve liste girdisini kullanılır.</span><span class="sxs-lookup"><span data-stu-id="56333-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="56333-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi) EntrySelectedBy öğesi SelectionCondition öğesinin ListEntry (biçimi) EntrySelectedBy SelectionCondition EntrySelectedBy ListEntry (biçimi) için için ScriptBlock öğesinin ListEntry (biçimi)</span><span class="sxs-lookup"><span data-stu-id="56333-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="56333-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56333-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="56333-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="56333-107">Attributes and Elements</span></span>

<span data-ttu-id="56333-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ScriptBlock` öğesi.</span><span class="sxs-lookup"><span data-stu-id="56333-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="56333-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="56333-109">Attributes</span></span>

<span data-ttu-id="56333-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="56333-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="56333-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="56333-111">Child Elements</span></span>

<span data-ttu-id="56333-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="56333-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="56333-113">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="56333-113">Parent Elements</span></span>

|<span data-ttu-id="56333-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="56333-114">Element</span></span>|<span data-ttu-id="56333-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56333-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="56333-116">EntrySelectedBy ListEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="56333-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="56333-117">Bu liste girişi kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="56333-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="56333-118">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="56333-118">Text Value</span></span>

<span data-ttu-id="56333-119">Yürütülecek betiği belirtin.</span><span class="sxs-lookup"><span data-stu-id="56333-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="56333-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56333-120">Remarks</span></span>

<span data-ttu-id="56333-121">Seçim koşulu değerlendirmek için bir en az bir betik veya özellik adı belirtmeniz gerekir ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="56333-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="56333-122">(Seçimi koşulları nasıl kullanılabileceği hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).)</span><span class="sxs-lookup"><span data-stu-id="56333-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="56333-123">Bir liste görünümü diğer bileşenler hakkında daha fazla bilgi için bkz. [liste görünümü](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="56333-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="56333-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="56333-124">See Also</span></span>

[<span data-ttu-id="56333-125">ListEntry öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="56333-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="56333-126">PropertyName öğesi SelectionCondition ListEntry (biçimi) için EntrySelectedBy için için</span><span class="sxs-lookup"><span data-stu-id="56333-126">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="56333-127">EntrySelectedBy ListEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="56333-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="56333-128">Liste Görünümü</span><span class="sxs-lookup"><span data-stu-id="56333-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="56333-129">Bir görünümü girişi veya öğeyi kullanıldığında koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="56333-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="56333-130">Biçimlendirme bir Windows PowerShell yazma ve dosya türleri</span><span class="sxs-lookup"><span data-stu-id="56333-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
