---
title: EntrySelectedBy öğesi görünümü (biçimi) için denetimleri için CustomEntry için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066252"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="06590-102">Görünüm Denetimleri için CustomEntry EntrySelectedBy Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="06590-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="06590-103">Bu denetim tanımı veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="06590-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="06590-104">Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="06590-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="06590-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) denetimleri (biçimi) öğesi denetim öğesi denetimi için CustomEntries öğesi görünümü (biçimi) için denetimleri için özel denetim öğesi görünümü (biçimi) için denetimleri için Görünümü (biçimi) CustomEntry öğesinin CustomEntries CustomEntry Görünüm (biçimi) için denetimleri için görüntüleme (biçimi) EntrySelectedBy öğesinin denetimleri için denetimler için özel denetim</span><span class="sxs-lookup"><span data-stu-id="06590-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="06590-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06590-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="06590-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="06590-107">Attributes and Elements</span></span>

<span data-ttu-id="06590-108">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `EntrySelectedBy` öğesi.</span><span class="sxs-lookup"><span data-stu-id="06590-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="06590-109">En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="06590-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="06590-110">Kullanabileceğiniz bir alt öğe sayısı maksimum sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="06590-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="06590-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="06590-111">Attributes</span></span>

<span data-ttu-id="06590-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="06590-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="06590-113">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="06590-113">Child Elements</span></span>

|<span data-ttu-id="06590-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="06590-114">Element</span></span>|<span data-ttu-id="06590-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06590-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06590-116">SelectionCondition öğesi görünümü (biçimi) için denetimleri için EntrySelectedBy için</span><span class="sxs-lookup"><span data-stu-id="06590-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="06590-117">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="06590-117">Optional element.</span></span><br /><br /> <span data-ttu-id="06590-118">Bu tanım için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="06590-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="06590-119">SelectionSetName öğesi görünümü (biçimi) için denetimleri için EntrySelectedBy için</span><span class="sxs-lookup"><span data-stu-id="06590-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="06590-120">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="06590-120">Optional element.</span></span><br /><br /> <span data-ttu-id="06590-121">Denetimin bu tanımı kullanan .NET türleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="06590-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="06590-122">TypeName öğesi görünümü (biçimi) için denetimleri için EntrySelectedBy için</span><span class="sxs-lookup"><span data-stu-id="06590-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="06590-123">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="06590-123">Optional element.</span></span><br /><br /> <span data-ttu-id="06590-124">Denetimin bu tanımı kullanan bir .NET türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="06590-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="06590-125">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="06590-125">Parent Elements</span></span>

|<span data-ttu-id="06590-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="06590-126">Element</span></span>|<span data-ttu-id="06590-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06590-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06590-128">CustomEntry öğesi görünümü (biçimi) için denetimleri için CustomEntries için</span><span class="sxs-lookup"><span data-stu-id="06590-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="06590-129">Denetim tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="06590-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="06590-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06590-130">Remarks</span></span>

<span data-ttu-id="06590-131">Seçimi koşullar bulunması gereken bir koşul için kullanılacak tanım, bir nesne belirli bir özelliğine sahip olduğunda gibi veya özel özellik değerini tanımlamak için kullanılır veya komut dosyası değerlendirilen `true`.</span><span class="sxs-lookup"><span data-stu-id="06590-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="06590-132">Seçimi koşullar hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="06590-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="06590-133">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="06590-133">See Also</span></span>

[<span data-ttu-id="06590-134">CustomEntry öğesi görünümü (biçimi) için denetimleri için CustomEntries için</span><span class="sxs-lookup"><span data-stu-id="06590-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="06590-135">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="06590-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
