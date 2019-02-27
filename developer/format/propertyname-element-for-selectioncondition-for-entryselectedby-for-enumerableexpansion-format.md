---
title: PropertyName öğesi EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionCondition için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849353"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="ad3e6-102">EnumerableExpansion EntrySelectedBy için SelectionCondition PropertyName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="ad3e6-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="ad3e6-103">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="ad3e6-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="ad3e6-104">Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve tanımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ad3e6-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="ad3e6-105">Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi) EnumerableExpansions öğesi (biçimi) EnumerableExpansion öğesi (biçimi) EntrySelectedBy öğesi için EntrySelectedBy SelectionCondition öğesinin EnumerableExpansion (biçimi) PropertyName öğesini SelectionCondition EntrySelectedBy EnumerableExpansion (biçimi) için için EnumerableExpansion (biçimi)</span><span class="sxs-lookup"><span data-stu-id="ad3e6-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ad3e6-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad3e6-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ad3e6-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad3e6-107">Attributes and Elements</span></span>

<span data-ttu-id="ad3e6-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `PropertyName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ad3e6-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ad3e6-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ad3e6-109">Attributes</span></span>

<span data-ttu-id="ad3e6-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="ad3e6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ad3e6-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad3e6-111">Child Elements</span></span>

<span data-ttu-id="ad3e6-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="ad3e6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ad3e6-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad3e6-113">Parent Elements</span></span>

|<span data-ttu-id="ad3e6-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="ad3e6-114">Element</span></span>|<span data-ttu-id="ad3e6-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad3e6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ad3e6-116">EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="ad3e6-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="ad3e6-117">Bu tanımın koleksiyon nesnelerini genişletmek için bulunması gereken koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ad3e6-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ad3e6-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="ad3e6-118">Text Value</span></span>

<span data-ttu-id="ad3e6-119">.NET özellik adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="ad3e6-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="ad3e6-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad3e6-120">Remarks</span></span>

<span data-ttu-id="ad3e6-121">Seçim koşulu değerlendirmek için bir betik ya da en az bir özellik adı belirtmeniz gerekir ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad3e6-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="ad3e6-122">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ad3e6-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ad3e6-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ad3e6-123">See Also</span></span>

[<span data-ttu-id="ad3e6-124">Verilerinin koşulları tanımlama görüntülenir</span><span class="sxs-lookup"><span data-stu-id="ad3e6-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ad3e6-125">SelectionCondition EnumerableExpansion (biçimi) için EntrySelectedBy için için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="ad3e6-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="ad3e6-126">EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="ad3e6-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="ad3e6-127">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="ad3e6-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
