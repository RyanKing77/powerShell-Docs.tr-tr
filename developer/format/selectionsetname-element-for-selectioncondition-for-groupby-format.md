---
title: GroupBy (biçimi) için SelectionCondition için SelectionSetName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063787"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="cac78-102">GroupBy SelectionCondition için SelectionSetName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="cac78-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="cac78-103">Tetikleme koşulu .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cac78-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="cac78-104">Bu türlerinden herhangi birini mevcut olduğunda, koşul karşılanır ve nesne bu denetimi kullanarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cac78-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="cac78-105">Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cac78-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="cac78-106">GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) EntrySelectedBy öğesinin CustomEntry GroupBy (biçimi) SelectionCondition öğesinin EntrySelectedBy GroupBy (biçimi) SelectionSetName öğesinin SelectionCondition GroupBy (biçimi) için özel denetim</span><span class="sxs-lookup"><span data-stu-id="cac78-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cac78-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cac78-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cac78-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="cac78-108">Attributes and Elements</span></span>

<span data-ttu-id="cac78-109">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `SelectionSetName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="cac78-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cac78-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cac78-110">Attributes</span></span>

<span data-ttu-id="cac78-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="cac78-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cac78-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="cac78-112">Child Elements</span></span>

<span data-ttu-id="cac78-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="cac78-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cac78-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="cac78-114">Parent Elements</span></span>

|<span data-ttu-id="cac78-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="cac78-115">Element</span></span>|<span data-ttu-id="cac78-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cac78-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cac78-117">GroupBy (biçimi) için EntrySelectedBy için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="cac78-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="cac78-118">Kullanılacak denetimi tanımı bulunması gereken bir koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cac78-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cac78-119">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="cac78-119">Text Value</span></span>

<span data-ttu-id="cac78-120">Seçimi kümesinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="cac78-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="cac78-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cac78-121">Remarks</span></span>

<span data-ttu-id="cac78-122">Seçimi ayarlar biçimlendirme dosyayı tanımlayan herhangi bir görünüm tarafından kullanılan .NET nesneleri ortak gruplarıdır.</span><span class="sxs-lookup"><span data-stu-id="cac78-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="cac78-123">Oluşturma ve başvuran seçimi ayarlar hakkında daha fazla bilgi için bkz. [tanımlama seçimi](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="cac78-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="cac78-124">Bu öğe belirtildiğinde, belirtemezsiniz [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="cac78-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="cac78-125">Seçimi koşulları tanımlama hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="cac78-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cac78-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="cac78-126">See Also</span></span>

[<span data-ttu-id="cac78-127">GroupBy (biçimi) için SelectionCondition için TypeName öğesi</span><span class="sxs-lookup"><span data-stu-id="cac78-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="cac78-128">GroupBy (biçimi) için EntrySelectedBy için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="cac78-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="cac78-129">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="cac78-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="cac78-130">Seçimi ayarlar tanımlama</span><span class="sxs-lookup"><span data-stu-id="cac78-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="cac78-131">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="cac78-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
