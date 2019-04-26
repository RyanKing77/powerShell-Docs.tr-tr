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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063869"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="de7b5-102">EnumerableExpansion EntrySelectedBy için SelectionCondition SelectionSetName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="de7b5-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="de7b5-103">Tetikleme koşulu .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="de7b5-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="de7b5-104">Bu türlerinden herhangi birini mevcut olduğunda, koşul karşılanır.</span><span class="sxs-lookup"><span data-stu-id="de7b5-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="de7b5-105">Yapılandırma öğesi DefaultSettings öğesi (biçimi) EnumerableExpansions öğesi (biçimi) EnumerableExpansions öğesi (biçimi) EntrySelectedBy öğesi için EntrySelectedBy SelectionCondition öğesinin EnumerableExpansion (biçimi) SelectionCondition EnumerableExpansion (biçimi) için EntrySelectedBy için için EnumerableExpansion (biçimi) SelectionSetName öğesi</span><span class="sxs-lookup"><span data-stu-id="de7b5-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="de7b5-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de7b5-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="de7b5-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="de7b5-107">Attributes and Elements</span></span>

<span data-ttu-id="de7b5-108">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `SelectionSetName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="de7b5-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="de7b5-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="de7b5-109">Attributes</span></span>

<span data-ttu-id="de7b5-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="de7b5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="de7b5-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="de7b5-111">Child Elements</span></span>

<span data-ttu-id="de7b5-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="de7b5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="de7b5-113">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="de7b5-113">Parent Elements</span></span>

|<span data-ttu-id="de7b5-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="de7b5-114">Element</span></span>|<span data-ttu-id="de7b5-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de7b5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="de7b5-116">EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="de7b5-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="de7b5-117">Bu tanımın koleksiyon nesnelerini genişletmek için bulunması gereken koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="de7b5-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="de7b5-118">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="de7b5-118">Text Value</span></span>

<span data-ttu-id="de7b5-119">Seçimi kümesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="de7b5-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="de7b5-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="de7b5-120">Remarks</span></span>

<span data-ttu-id="de7b5-121">Seçim koşulu, bir seçim kümesi veya .NET türü belirtebilirsiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="de7b5-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="de7b5-122">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="de7b5-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="de7b5-123">Seçimi ayarlar biçimlendirme dosyayı tanımlayan herhangi bir görünüm tarafından kullanılan .NET nesneleri ortak gruplarıdır.</span><span class="sxs-lookup"><span data-stu-id="de7b5-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="de7b5-124">Oluşturma ve başvuran seçimi ayarlar hakkında daha fazla bilgi için bkz. [tanımlama seçimi](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="de7b5-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="de7b5-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="de7b5-125">See Also</span></span>

[<span data-ttu-id="de7b5-126">Seçimi ayarlar tanımlama</span><span class="sxs-lookup"><span data-stu-id="de7b5-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="de7b5-127">EntrySelectedBy EnumerableExpansion (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="de7b5-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="de7b5-128">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="de7b5-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
