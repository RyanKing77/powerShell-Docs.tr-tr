---
title: TableControl (biçimi) için EntrySelectedBy için SelectionSetName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063930"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="ac898-102">TableControl EntrySelectedBy için SelectionSetName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="ac898-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="ac898-103">.NET bir dizi tablo görünümü, bu girdi kullanım türleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac898-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="ac898-104">Bir giriş için belirtilen seçim kümeleri sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="ac898-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="ac898-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi (biçimi) TableRowEntry öğesi (biçimi) EntrySelectedBy öğesi (biçimi) SelectionSetName öğesi EntrySelectedBy TableRowEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="ac898-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ac898-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac898-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ac898-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="ac898-107">Attributes and Elements</span></span>

<span data-ttu-id="ac898-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac898-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ac898-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ac898-109">Attributes</span></span>

<span data-ttu-id="ac898-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="ac898-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ac898-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="ac898-111">Child Elements</span></span>

<span data-ttu-id="ac898-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="ac898-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ac898-113">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="ac898-113">Parent Elements</span></span>

|<span data-ttu-id="ac898-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="ac898-114">Element</span></span>|<span data-ttu-id="ac898-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac898-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ac898-116">EntrySelectedBy öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="ac898-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="ac898-117">Bu girdi veya kullanılmak üzere bu giriş için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ac898-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ac898-118">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="ac898-118">Text Value</span></span>

<span data-ttu-id="ac898-119">Seçimi kümesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="ac898-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="ac898-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac898-120">Remarks</span></span>

<span data-ttu-id="ac898-121">Seçimi ayarlar, genellikle kullanılan nesnelerin bir grup içinde birden çok görünüm tanımlamak istediğinizde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ac898-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="ac898-122">Örneğin, bir tablo görünümü ve aynı nesne kümesini bir liste görünümü oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac898-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="ac898-123">Seçimi ayarlar tanımlama hakkında daha fazla bilgi için bkz. [bir görünüm için nesneleri tanımlayan ayarlar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="ac898-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="ac898-124">Bir seçim için bir giriş ayarlamak belirtirseniz, bir tür adı belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="ac898-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="ac898-125">Bir .NET türü belirtme hakkında daha fazla bilgi için bkz. [TypeName öğesi EntrySelectedBy TableRowEntry (biçimi) için için](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span><span class="sxs-lookup"><span data-stu-id="ac898-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="ac898-126">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="ac898-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ac898-127">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ac898-127">See Also</span></span>

[<span data-ttu-id="ac898-128">EntrySelectedBy öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="ac898-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="ac898-129">Görünüm için nesneleri kümesini tanımlama</span><span class="sxs-lookup"><span data-stu-id="ac898-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="ac898-130">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="ac898-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ac898-131">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="ac898-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
