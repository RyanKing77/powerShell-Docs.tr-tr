---
title: ScriptBlock öğesi EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionCondition için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845972"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="27323-102">EnumerableExpansion EntrySelectedBy için SelectionCondition ScriptBlock Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="27323-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="27323-103">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="27323-103">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="27323-104">Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi) EnumerableExpansions öğesi (biçimi) EnumerableExpansion öğesi (biçimi) EntrySelectedBy öğesi için EntrySelectedBy SelectionCondition öğesinin EnumerableExpansion (biçimi) SelectionCondition EntrySelectedBy EnumerableExpansion (biçimi) için için ScriptBlock öğesini EnumerableExpansion (biçimi)</span><span class="sxs-lookup"><span data-stu-id="27323-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="27323-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27323-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="27323-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="27323-106">Attributes and Elements</span></span>

<span data-ttu-id="27323-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ScriptBlock` öğesi.</span><span class="sxs-lookup"><span data-stu-id="27323-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="27323-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="27323-108">Attributes</span></span>

<span data-ttu-id="27323-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="27323-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="27323-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="27323-110">Child Elements</span></span>

<span data-ttu-id="27323-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="27323-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="27323-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="27323-112">Parent Elements</span></span>

|<span data-ttu-id="27323-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="27323-113">Element</span></span>|<span data-ttu-id="27323-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27323-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="27323-115">EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="27323-115">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="27323-116">Bu tanımın koleksiyon nesnelerini genişletmek için bulunması gereken koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="27323-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="27323-117">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="27323-117">Text Value</span></span>

<span data-ttu-id="27323-118">Yürütülecek betiği belirtin.</span><span class="sxs-lookup"><span data-stu-id="27323-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="27323-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27323-119">Remarks</span></span>

<span data-ttu-id="27323-120">Seçim koşulu değerlendirmek için en az bir betik veya özellik adı belirtmeniz gerekir ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="27323-120">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="27323-121">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="27323-121">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="27323-122">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="27323-122">See Also</span></span>

[<span data-ttu-id="27323-123">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="27323-123">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="27323-124">PropertyName öğesi SelectionCondition EnumerableExpansion (biçimi) için EntrySelectedBy için için</span><span class="sxs-lookup"><span data-stu-id="27323-124">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="27323-125">EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="27323-125">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="27323-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="27323-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
