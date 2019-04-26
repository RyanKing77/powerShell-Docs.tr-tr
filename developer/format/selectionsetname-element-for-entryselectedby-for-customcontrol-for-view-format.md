---
title: SelectionSetName öğesi görünümü (biçimi) için özel denetim için EntrySelectedBy için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063992"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="988ee-102">Görünüm CustomControl için EntrySelectedBy SelectionSetName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="988ee-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="988ee-103">.NET nesnelerinin listesi girişi için bir dizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="988ee-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="988ee-104">Bir giriş için belirtilen seçim kümeleri sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="988ee-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="988ee-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomEntry öğesinin CustomEntries EntrySelectedBy görünümü (biçimi) için özel denetim için Öğe için CustomEntry SelectionSetName öğesinin EntrySelectedBy CustomEntry (biçimi) için View (biçimi)</span><span class="sxs-lookup"><span data-stu-id="988ee-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="988ee-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="988ee-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="988ee-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="988ee-107">Attributes and Elements</span></span>

<span data-ttu-id="988ee-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionSetName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="988ee-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="988ee-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="988ee-109">Attributes</span></span>

<span data-ttu-id="988ee-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="988ee-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="988ee-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="988ee-111">Child Elements</span></span>

<span data-ttu-id="988ee-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="988ee-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="988ee-113">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="988ee-113">Parent Elements</span></span>

|<span data-ttu-id="988ee-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="988ee-114">Element</span></span>|<span data-ttu-id="988ee-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="988ee-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="988ee-116">İçin görünümün (biçimi) CustomEntry EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="988ee-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="988ee-117">Bu özel giriş veya kullanılmak üzere bu giriş için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="988ee-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="988ee-118">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="988ee-118">Text Value</span></span>

<span data-ttu-id="988ee-119">Seçimi kümesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="988ee-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="988ee-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="988ee-120">Remarks</span></span>

<span data-ttu-id="988ee-121">Her özel denetim girişi, en az bir tür adı, seçim kümesi veya seçim koşulu tanımlanmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="988ee-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="988ee-122">Seçimi ayarlar, genellikle kullanılan nesnelerin bir grup içinde birden çok görünüm tanımlamak istediğinizde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="988ee-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="988ee-123">Örneğin, bir tablo görünümü ve aynı nesne kümesini bir liste görünümü oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="988ee-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="988ee-124">Seçimi ayarlar tanımlama hakkında daha fazla bilgi için bkz. [tanımlama seçimi](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="988ee-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="988ee-125">Bir özel denetim görünüm bileşenleri hakkında daha fazla bilgi için bkz. [özel denetimler oluşturma](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="988ee-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="988ee-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="988ee-126">See Also</span></span>

[<span data-ttu-id="988ee-127">İçin görünümün (biçimi) CustomEntry EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="988ee-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="988ee-128">Özel denetim görünümü</span><span class="sxs-lookup"><span data-stu-id="988ee-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="988ee-129">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="988ee-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
