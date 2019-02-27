---
title: SelectionSetName öğesi EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionCondition için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850466"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="a0e52-102">EnumerableExpansion EntrySelectedBy için SelectionCondition SelectionSetName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="a0e52-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="a0e52-103">Tetikleme koşulu .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0e52-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="a0e52-104">Bu türlerinden herhangi birini mevcut olduğunda, koşul karşılanır.</span><span class="sxs-lookup"><span data-stu-id="a0e52-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="a0e52-105">Yapılandırma öğesi DefaultSettings öğesi (biçimi) EnumerableExpansions öğesi (biçimi) EnumerableExpansions öğesi (biçimi) EntrySelectedBy öğesi için EntrySelectedBy SelectionCondition öğesinin EnumerableExpansion (biçimi) SelectionCondition EnumerableExpansion (biçimi) için EntrySelectedBy için için EnumerableExpansion (biçimi) SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="a0e52-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a0e52-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0e52-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a0e52-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0e52-107">Attributes and Elements</span></span>

<span data-ttu-id="a0e52-108">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `SelectionSetName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a0e52-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a0e52-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a0e52-109">Attributes</span></span>

<span data-ttu-id="a0e52-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="a0e52-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a0e52-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0e52-111">Child Elements</span></span>

<span data-ttu-id="a0e52-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="a0e52-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a0e52-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0e52-113">Parent Elements</span></span>

|<span data-ttu-id="a0e52-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="a0e52-114">Element</span></span>|<span data-ttu-id="a0e52-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0e52-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a0e52-116">EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="a0e52-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a0e52-117">Bu tanımın koleksiyon nesnelerini genişletmek için bulunması gereken koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a0e52-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a0e52-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="a0e52-118">Text Value</span></span>

<span data-ttu-id="a0e52-119">Seçimi kümesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="a0e52-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="a0e52-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0e52-120">Remarks</span></span>

<span data-ttu-id="a0e52-121">Seçim koşulu, bir seçim kümesi veya .NET türü belirtebilirsiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0e52-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="a0e52-122">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a0e52-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a0e52-123">Seçimi ayarlar biçimlendirme dosyayı tanımlayan herhangi bir görünüm tarafından kullanılan .NET nesneleri ortak gruplarıdır.</span><span class="sxs-lookup"><span data-stu-id="a0e52-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="a0e52-124">Oluşturma ve başvuran seçimi ayarlar hakkında daha fazla bilgi için bkz. [tanımlama seçimi](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="a0e52-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a0e52-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a0e52-125">See Also</span></span>

[<span data-ttu-id="a0e52-126">Seçimi ayarlar tanımlama</span><span class="sxs-lookup"><span data-stu-id="a0e52-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="a0e52-127">EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="a0e52-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="a0e52-128">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="a0e52-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
