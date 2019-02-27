---
title: SelectionSetName öğesi EntrySelectedBy EnumerableExpansion (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851537"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="f9ca3-102">EnumerableExpansion EntrySelectedBy için SelectionSetName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="f9ca3-102">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="f9ca3-103">Bu tanımı tarafından genişletilen .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9ca3-103">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="f9ca3-104">Yapılandırma öğesi (biçimi) DefaultSettings öğesi (biçimi) EnumerableExpansions öğesi (biçimi) EnumerableExpansion öğesi (biçimi) EntrySelectedBy öğesi için EntrySelectedBy SelectionSetName öğesinin EnumerableExpansion (biçimi) EnumerableExpansion (biçimi)</span><span class="sxs-lookup"><span data-stu-id="f9ca3-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f9ca3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9ca3-105">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="f9ca3-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9ca3-106">Attributes and Elements</span></span>

<span data-ttu-id="f9ca3-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionSetName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f9ca3-107">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f9ca3-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f9ca3-108">Attributes</span></span>

<span data-ttu-id="f9ca3-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="f9ca3-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f9ca3-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9ca3-110">Child Elements</span></span>

<span data-ttu-id="f9ca3-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="f9ca3-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f9ca3-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9ca3-112">Parent Elements</span></span>

|<span data-ttu-id="f9ca3-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="f9ca3-113">Element</span></span>|<span data-ttu-id="f9ca3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9ca3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f9ca3-115">EntrySelectedBy öğesi EnumerableExpansion (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="f9ca3-115">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="f9ca3-116">Bu tanımı tarafından genişletilen .NET koleksiyon nesnelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f9ca3-116">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f9ca3-117">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="f9ca3-117">Text Value</span></span>

<span data-ttu-id="f9ca3-118">Seçimi kümesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="f9ca3-118">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="f9ca3-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9ca3-119">Remarks</span></span>

<span data-ttu-id="f9ca3-120">Her tanım, bir veya daha fazla tür adları, seçim kümesi veya bir seçim koşulu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9ca3-120">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="f9ca3-121">Seçimi ayarlar, genellikle kullanılan nesnelerin bir grup içinde birden çok görünüm tanımlamak istediğinizde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f9ca3-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="f9ca3-122">Örneğin, bir tablo görünümü ve aynı nesne kümesini bir liste görünümü oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9ca3-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="f9ca3-123">Seçimi ayarlar tanımlama hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin bir görünüm için](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="f9ca3-123">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f9ca3-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="f9ca3-124">See Also</span></span>

[<span data-ttu-id="f9ca3-125">Seçimi ayarlar tanımlama</span><span class="sxs-lookup"><span data-stu-id="f9ca3-125">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="f9ca3-126">EntrySelectedBy öğesi EnumerableExpansion (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="f9ca3-126">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="f9ca3-127">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="f9ca3-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
