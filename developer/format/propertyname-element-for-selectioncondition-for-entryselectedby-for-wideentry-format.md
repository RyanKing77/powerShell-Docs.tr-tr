---
title: PropertyName öğesi EntrySelectedBy WideEntry (biçimi) için için SelectionCondition için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064688"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="d0c9d-102">WideEntry EntrySelectedBy için SelectionCondition PropertyName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="d0c9d-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="d0c9d-103">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="d0c9d-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="d0c9d-104">Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve tanımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0c9d-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="d0c9d-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi (biçimi) EntrySelectedBy öğesi SelectionCondition öğesinin WideEntry (biçimi) EntrySelectedBy EntrySelectedBy WideEntry (biçimi) için için SelectionCondition PropertyName öğesinin WideEntry (biçimi)</span><span class="sxs-lookup"><span data-stu-id="d0c9d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d0c9d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0c9d-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d0c9d-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="d0c9d-107">Attributes and Elements</span></span>

<span data-ttu-id="d0c9d-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `PropertyName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d0c9d-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d0c9d-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d0c9d-109">Attributes</span></span>

<span data-ttu-id="d0c9d-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="d0c9d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d0c9d-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="d0c9d-111">Child Elements</span></span>

<span data-ttu-id="d0c9d-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="d0c9d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d0c9d-113">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="d0c9d-113">Parent Elements</span></span>

|<span data-ttu-id="d0c9d-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0c9d-114">Element</span></span>|<span data-ttu-id="d0c9d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0c9d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0c9d-116">EntrySelectedBy WideEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="d0c9d-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="d0c9d-117">Bu tanım için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d0c9d-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d0c9d-118">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="d0c9d-118">Text Value</span></span>

<span data-ttu-id="d0c9d-119">.NET özellik adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="d0c9d-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0c9d-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0c9d-120">Remarks</span></span>

<span data-ttu-id="d0c9d-121">Seçim koşulu değerlendirmek için bir betik ya da en az bir özellik adı belirtmeniz gerekir ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c9d-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="d0c9d-122">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d0c9d-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d0c9d-123">Geniş bir görünüm diğer bileşenler hakkında daha fazla bilgi için bkz. [geniş Görünüm](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="d0c9d-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0c9d-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="d0c9d-124">See Also</span></span>

[<span data-ttu-id="d0c9d-125">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0c9d-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d0c9d-126">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="d0c9d-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d0c9d-127">SelectionCondition WideEntry (biçimi) için EntrySelectedBy için için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="d0c9d-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="d0c9d-128">EntrySelectedBy WideEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="d0c9d-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="d0c9d-129">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="d0c9d-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
