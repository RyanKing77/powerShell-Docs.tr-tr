---
title: SelectionSetName öğesi EntrySelectedBy WideEntry (biçimi) için için SelectionCondition için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13a429c-a31b-4e29-828c-c0c0917b5415
caps.latest.revision: 11
ms.openlocfilehash: baea89e4b259611dfa45b6bcf94fa0bf2df6b9de
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075486"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="2d0ea-102">WideEntry EntrySelectedBy için SelectionCondition SelectionSetName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="2d0ea-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="2d0ea-103">Tetikleme koşulu .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d0ea-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="2d0ea-104">Bu türlerinden herhangi birini mevcut olduğunda, koşul karşılanır ve nesne bu geniş görünüm tanımını kullanarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2d0ea-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="2d0ea-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi (biçimi) EntrySelectedBy öğesi SelectionCondition öğesinin WideEntry (biçimi) EntrySelectedBy EntrySelectedBy WideEntry (biçimi) için için SelectionCondition SelectionSetName öğesinin WideEntry (biçimi)</span><span class="sxs-lookup"><span data-stu-id="2d0ea-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2d0ea-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d0ea-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2d0ea-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="2d0ea-107">Attributes and Elements</span></span>

<span data-ttu-id="2d0ea-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionSetName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="2d0ea-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2d0ea-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2d0ea-109">Attributes</span></span>

<span data-ttu-id="2d0ea-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="2d0ea-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2d0ea-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="2d0ea-111">Child Elements</span></span>

<span data-ttu-id="2d0ea-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="2d0ea-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2d0ea-113">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="2d0ea-113">Parent Elements</span></span>

|<span data-ttu-id="2d0ea-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="2d0ea-114">Element</span></span>|<span data-ttu-id="2d0ea-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d0ea-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2d0ea-116">EntrySelectedBy WideEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="2d0ea-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="2d0ea-117">Bu tanım için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2d0ea-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2d0ea-118">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="2d0ea-118">Text Value</span></span>

<span data-ttu-id="2d0ea-119">Seçimi kümesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="2d0ea-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="2d0ea-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d0ea-120">Remarks</span></span>

<span data-ttu-id="2d0ea-121">Seçim koşulu, bir seçim kümesi veya .NET türü belirtebilirsiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d0ea-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="2d0ea-122">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2d0ea-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2d0ea-123">Seçimi ayarlar biçimlendirme dosyayı tanımlayan herhangi bir görünüm tarafından kullanılan .NET nesneleri ortak gruplarıdır.</span><span class="sxs-lookup"><span data-stu-id="2d0ea-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="2d0ea-124">Oluşturma ve başvuran seçimi ayarlar hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="2d0ea-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="2d0ea-125">Geniş bir görünüm diğer bileşenler hakkında daha fazla bilgi için bkz. [geniş bir görünüm oluşturma](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="2d0ea-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2d0ea-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="2d0ea-126">See Also</span></span>

[<span data-ttu-id="2d0ea-127">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="2d0ea-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="2d0ea-128">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="2d0ea-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2d0ea-129">Seçimi ayarlar tanımlama</span><span class="sxs-lookup"><span data-stu-id="2d0ea-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="2d0ea-130">EntrySelectedBy WideEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="2d0ea-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="2d0ea-131">TypeName öğesi SelectionCondition WideEntry (biçimi) için EntrySelectedBy için için</span><span class="sxs-lookup"><span data-stu-id="2d0ea-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="2d0ea-132">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="2d0ea-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
