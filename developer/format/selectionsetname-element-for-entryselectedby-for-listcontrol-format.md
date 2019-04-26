---
title: SelectionSetName öğesi EntrySelectedBy ListControl (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075571"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="a7061-102">ListControl EntrySelectedBy için SelectionSetName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="a7061-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="a7061-103">.NET nesnelerinin listesi girişi için bir dizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7061-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="a7061-104">Bir giriş için belirtilen seçim kümeleri sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="a7061-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="a7061-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi) EntrySelectedBy öğesi SelectionSetName öğesinin ListEntry (biçimi) EntrySelectedBy ListEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="a7061-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a7061-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7061-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a7061-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="a7061-107">Attributes and Elements</span></span>

<span data-ttu-id="a7061-108">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `SelectionSetName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a7061-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a7061-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a7061-109">Attributes</span></span>

<span data-ttu-id="a7061-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="a7061-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a7061-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="a7061-111">Child Elements</span></span>

<span data-ttu-id="a7061-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="a7061-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a7061-113">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="a7061-113">Parent Elements</span></span>

|<span data-ttu-id="a7061-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="a7061-114">Element</span></span>|<span data-ttu-id="a7061-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7061-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a7061-116">EntrySelectedBy öğesi ListEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="a7061-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="a7061-117">Bu liste girişi kullanıp bu giriş için kullanılacak bulunmalıdır koşul .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7061-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a7061-118">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="a7061-118">Text Value</span></span>

<span data-ttu-id="a7061-119">Seçimi kümesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="a7061-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="a7061-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7061-120">Remarks</span></span>

<span data-ttu-id="a7061-121">Her liste girişi, en az bir tür adı, seçim kümesi veya seçim koşulu tanımlanmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a7061-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="a7061-122">Seçimi ayarlar, genellikle kullanılan nesnelerin bir grup içinde birden çok görünüm tanımlamak istediğinizde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a7061-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="a7061-123">Örneğin, bir tablo görünümü ve aynı nesne kümesini bir liste görünümü oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7061-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="a7061-124">Seçimi ayarlar tanımlama hakkında daha fazla bilgi için bkz. [bir görünüm için nesneleri tanımlayan ayarlar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="a7061-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="a7061-125">Bir liste görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="a7061-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a7061-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7061-126">Example</span></span>

<span data-ttu-id="a7061-127">Aşağıdaki örnek, bir liste görünümü için bir giriş ayarlamak seçim belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a7061-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="a7061-128">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a7061-128">See Also</span></span>

[<span data-ttu-id="a7061-129">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="a7061-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="a7061-130">EntrySelectedBy öğesi ListEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="a7061-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="a7061-131">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="a7061-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
