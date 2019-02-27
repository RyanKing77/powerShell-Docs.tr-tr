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
ms.openlocfilehash: fd708473d04a76bcf6cf3a8f8278e1d15fb9addf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848674"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="1d828-102">ListControl EntrySelectedBy için SelectionCondition ScriptBlock Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="1d828-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="1d828-103">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d828-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="1d828-104">Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve liste girdisini kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1d828-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="1d828-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi) EntrySelectedBy öğesi SelectionCondition öğesinin ListEntry (biçimi) EntrySelectedBy SelectionCondition EntrySelectedBy ListEntry (biçimi) için için ScriptBlock öğesinin ListEntry (biçimi)</span><span class="sxs-lookup"><span data-stu-id="1d828-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1d828-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d828-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1d828-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d828-107">Attributes and Elements</span></span>

<span data-ttu-id="1d828-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ScriptBlock` öğesi.</span><span class="sxs-lookup"><span data-stu-id="1d828-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1d828-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1d828-109">Attributes</span></span>

<span data-ttu-id="1d828-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="1d828-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1d828-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d828-111">Child Elements</span></span>

<span data-ttu-id="1d828-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="1d828-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1d828-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d828-113">Parent Elements</span></span>

|<span data-ttu-id="1d828-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="1d828-114">Element</span></span>|<span data-ttu-id="1d828-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d828-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1d828-116">EntrySelectedBy ListEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="1d828-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="1d828-117">Bu liste girişi kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1d828-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1d828-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="1d828-118">Text Value</span></span>

<span data-ttu-id="1d828-119">Yürütülecek betiği belirtin.</span><span class="sxs-lookup"><span data-stu-id="1d828-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="1d828-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d828-120">Remarks</span></span>

<span data-ttu-id="1d828-121">Seçim koşulu değerlendirmek için bir en az bir betik veya özellik adı belirtmeniz gerekir ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d828-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="1d828-122">(Seçimi koşulları nasıl kullanılabileceği hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).)</span><span class="sxs-lookup"><span data-stu-id="1d828-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="1d828-123">Bir liste görünümü diğer bileşenler hakkında daha fazla bilgi için bkz. [liste görünümü](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="1d828-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d828-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="1d828-124">See Also</span></span>

[<span data-ttu-id="1d828-125">ListEntry öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="1d828-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="1d828-126">PropertyName öğesi SelectionCondition ListEntry (biçimi) için EmtrySelectedBy için için</span><span class="sxs-lookup"><span data-stu-id="1d828-126">PropertyName Element for SelectionCondition for EmtrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="1d828-127">EntrySelectedBy ListEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="1d828-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="1d828-128">Liste Görünümü</span><span class="sxs-lookup"><span data-stu-id="1d828-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="1d828-129">Bir görünümü girişi veya öğeyi kullanıldığında koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="1d828-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1d828-130">Biçimlendirme bir Windows PowerShell yazma ve dosya türleri</span><span class="sxs-lookup"><span data-stu-id="1d828-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
