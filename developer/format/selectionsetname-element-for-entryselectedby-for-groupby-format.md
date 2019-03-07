---
title: GroupBy (biçimi) için EntrySelectedBy için SelectionSetName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848814"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="a2385-102">GroupBy EntrySelectedBy için SelectionSetName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="a2385-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="a2385-103">.NET nesnelerinin listesi girişi için bir dizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="a2385-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="a2385-104">Bir giriş için belirtilen seçim kümeleri sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="a2385-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="a2385-105">Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a2385-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="a2385-106">GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) EntrySelectedBy öğesinin CustomEntry GroupBy (biçimi) SelectionSetName öğesinin EntrySelectedBy GroupBy (biçimi) için özel denetim</span><span class="sxs-lookup"><span data-stu-id="a2385-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a2385-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2385-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a2385-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a2385-108">Attributes and Elements</span></span>

<span data-ttu-id="a2385-109">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionSetName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a2385-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a2385-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a2385-110">Attributes</span></span>

<span data-ttu-id="a2385-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="a2385-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a2385-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a2385-112">Child Elements</span></span>

<span data-ttu-id="a2385-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="a2385-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a2385-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a2385-114">Parent Elements</span></span>

|<span data-ttu-id="a2385-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="a2385-115">Element</span></span>|<span data-ttu-id="a2385-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2385-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a2385-117">GroupBy (biçimi) için CustomEntry için EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="a2385-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="a2385-118">Bu özel giriş veya kullanılmak üzere bu giriş için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a2385-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a2385-119">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="a2385-119">Text Value</span></span>

<span data-ttu-id="a2385-120">Seçimi kümesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="a2385-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="a2385-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2385-121">Remarks</span></span>

<span data-ttu-id="a2385-122">Her özel denetim tanımı en az bir tür adı, seçim kümesi veya seçim koşulu tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2385-122">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="a2385-123">Seçimi ayarlar, genellikle kullanılan nesnelerin bir grup içinde birden çok görünüm tanımlamak istediğinizde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a2385-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="a2385-124">Örneğin, bir tablo görünümü ve aynı nesne kümesini bir liste görünümü oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2385-124">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="a2385-125">Seçimi ayarlar tanımlama hakkında daha fazla bilgi için bkz. [tanımlama seçimi](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="a2385-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="a2385-126">Bir özel denetim görünüm bileşenleri hakkında daha fazla bilgi için bkz. [özel denetimler oluşturma](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a2385-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a2385-127">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a2385-127">See Also</span></span>

[<span data-ttu-id="a2385-128">GroupBy (biçimi) için CustomEntry için EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="a2385-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="a2385-129">Özel denetimler oluşturma</span><span class="sxs-lookup"><span data-stu-id="a2385-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="a2385-130">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="a2385-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)