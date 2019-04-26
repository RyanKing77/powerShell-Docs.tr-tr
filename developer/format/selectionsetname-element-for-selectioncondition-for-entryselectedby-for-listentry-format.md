---
title: SelectionSetName öğesi EntrySelectedBy ListEntry (biçimi) için için SelectionCondition için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075520"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="e8ea4-102">ListEntry EntrySelectedBy için SelectionCondition SelectionSetName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="e8ea4-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="e8ea4-103">Tetikleme koşulu .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8ea4-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="e8ea4-104">Bu türlerinden herhangi birini mevcut olduğunda, koşul karşılanır ve nesne bu liste görünümü tanımını kullanarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e8ea4-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="e8ea4-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi) EntrySelectedBy öğesi SelectionCondition öğesinin ListEntry (biçimi) EntrySelectedBy EntrySelectedBy ListEntry (biçimi) için için SelectionCondition SelectionSetName öğesinin ListEntry (biçimi)</span><span class="sxs-lookup"><span data-stu-id="e8ea4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e8ea4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8ea4-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e8ea4-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="e8ea4-107">Attributes and Elements</span></span>

<span data-ttu-id="e8ea4-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionSetName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e8ea4-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e8ea4-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e8ea4-109">Attributes</span></span>

<span data-ttu-id="e8ea4-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="e8ea4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e8ea4-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="e8ea4-111">Child Elements</span></span>

<span data-ttu-id="e8ea4-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="e8ea4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e8ea4-113">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="e8ea4-113">Parent Elements</span></span>

|<span data-ttu-id="e8ea4-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="e8ea4-114">Element</span></span>|<span data-ttu-id="e8ea4-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8ea4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e8ea4-116">EntrySelectedBy ListEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="e8ea4-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="e8ea4-117">Bu liste görünümü tanımını kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e8ea4-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e8ea4-118">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="e8ea4-118">Text Value</span></span>

<span data-ttu-id="e8ea4-119">Seçimi kümesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="e8ea4-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="e8ea4-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8ea4-120">Remarks</span></span>

<span data-ttu-id="e8ea4-121">Seçim koşulu, bir seçim kümesi veya .NET türü belirtebilirsiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8ea4-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="e8ea4-122">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e8ea4-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e8ea4-123">Seçimi ayarlar biçimlendirme dosyayı tanımlayan herhangi bir görünüm tarafından kullanılan .NET nesneleri ortak gruplarıdır.</span><span class="sxs-lookup"><span data-stu-id="e8ea4-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="e8ea4-124">Oluşturma ve başvuran seçimi ayarlar hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e8ea4-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="e8ea4-125">Bir liste görünümü diğer bileşenler hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="e8ea4-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e8ea4-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e8ea4-126">See Also</span></span>

[<span data-ttu-id="e8ea4-127">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="e8ea4-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e8ea4-128">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="e8ea4-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e8ea4-129">EntrySelectedBy ListEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="e8ea4-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="e8ea4-130">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="e8ea4-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
