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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851152"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="585e7-102">ListEntry EntrySelectedBy için SelectionCondition SelectionSetName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="585e7-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="585e7-103">Tetikleme koşulu .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="585e7-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="585e7-104">Bu türlerinden herhangi birini mevcut olduğunda, koşul karşılanır ve nesne bu liste görünümü tanımını kullanarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="585e7-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="585e7-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi) EntrySelectedBy öğesi SelectionCondition öğesinin ListEntry (biçimi) EntrySelectedBy EntrySelectedBy ListEntry (biçimi) için için SelectionCondition SelectionSetName öğesinin ListEntry (biçimi)</span><span class="sxs-lookup"><span data-stu-id="585e7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="585e7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="585e7-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="585e7-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="585e7-107">Attributes and Elements</span></span>

<span data-ttu-id="585e7-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionSetName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="585e7-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="585e7-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="585e7-109">Attributes</span></span>

<span data-ttu-id="585e7-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="585e7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="585e7-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="585e7-111">Child Elements</span></span>

<span data-ttu-id="585e7-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="585e7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="585e7-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="585e7-113">Parent Elements</span></span>

|<span data-ttu-id="585e7-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="585e7-114">Element</span></span>|<span data-ttu-id="585e7-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="585e7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="585e7-116">EntrySelectedBy ListEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="585e7-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="585e7-117">Bu liste görünümü tanımını kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="585e7-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="585e7-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="585e7-118">Text Value</span></span>

<span data-ttu-id="585e7-119">Seçimi kümesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="585e7-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="585e7-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="585e7-120">Remarks</span></span>

<span data-ttu-id="585e7-121">Seçim koşulu, bir seçim kümesi veya .NET türü belirtebilirsiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="585e7-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="585e7-122">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="585e7-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="585e7-123">Seçimi ayarlar biçimlendirme dosyayı tanımlayan herhangi bir görünüm tarafından kullanılan .NET nesneleri ortak gruplarıdır.</span><span class="sxs-lookup"><span data-stu-id="585e7-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="585e7-124">Oluşturma ve başvuran seçimi ayarlar hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="585e7-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="585e7-125">Bir liste görünümü diğer bileşenler hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="585e7-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="585e7-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="585e7-126">See Also</span></span>

[<span data-ttu-id="585e7-127">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="585e7-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="585e7-128">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="585e7-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="585e7-129">EntrySelectedBy ListEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="585e7-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="585e7-130">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="585e7-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
