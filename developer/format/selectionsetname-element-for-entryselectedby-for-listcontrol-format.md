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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849724"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="9fd12-102">ListControl EntrySelectedBy için SelectionSetName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="9fd12-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="9fd12-103">.NET nesnelerinin listesi girişi için bir dizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="9fd12-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="9fd12-104">Bir giriş için belirtilen seçim kümeleri sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="9fd12-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="9fd12-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi) EntrySelectedBy öğesi SelectionSetName öğesinin ListEntry (biçimi) EntrySelectedBy ListEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="9fd12-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9fd12-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9fd12-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9fd12-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9fd12-107">Attributes and Elements</span></span>

<span data-ttu-id="9fd12-108">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `SelectionSetName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="9fd12-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9fd12-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9fd12-109">Attributes</span></span>

<span data-ttu-id="9fd12-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="9fd12-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9fd12-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9fd12-111">Child Elements</span></span>

<span data-ttu-id="9fd12-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="9fd12-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9fd12-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9fd12-113">Parent Elements</span></span>

|<span data-ttu-id="9fd12-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="9fd12-114">Element</span></span>|<span data-ttu-id="9fd12-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9fd12-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9fd12-116">EntrySelectedBy öğesi ListEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="9fd12-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="9fd12-117">Bu liste girişi kullanıp bu giriş için kullanılacak bulunmalıdır koşul .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9fd12-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9fd12-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="9fd12-118">Text Value</span></span>

<span data-ttu-id="9fd12-119">Seçimi kümesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="9fd12-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="9fd12-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9fd12-120">Remarks</span></span>

<span data-ttu-id="9fd12-121">Her liste girişi, en az bir tür adı, seçim kümesi veya seçim koşulu tanımlanmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9fd12-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="9fd12-122">Seçimi ayarlar, genellikle kullanılan nesnelerin bir grup içinde birden çok görünüm tanımlamak istediğinizde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9fd12-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="9fd12-123">Örneğin, bir tablo görünümü ve aynı nesne kümesini bir liste görünümü oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fd12-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="9fd12-124">Seçimi ayarlar tanımlama hakkında daha fazla bilgi için bkz. [bir görünüm için nesneleri tanımlayan ayarlar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="9fd12-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="9fd12-125">Bir liste görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="9fd12-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9fd12-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="9fd12-126">Example</span></span>

<span data-ttu-id="9fd12-127">Aşağıdaki örnek, bir liste görünümü için bir giriş ayarlamak seçim belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9fd12-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="9fd12-128">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="9fd12-128">See Also</span></span>

[<span data-ttu-id="9fd12-129">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="9fd12-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="9fd12-130">EntrySelectedBy öğesi ListEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="9fd12-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="9fd12-131">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="9fd12-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
