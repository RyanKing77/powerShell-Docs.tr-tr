---
title: PropertyName öğesi EntrySelectedBy TableRowEntry (biçimi) için için SelectionCondition için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064671"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="76953-102">TableRowEntry EntrySelectedBy için SelectionCondition PropertyName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="76953-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="76953-103">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="76953-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="76953-104">Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve tablo girişi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="76953-104">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="76953-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi (biçimi) TableRowEntry öğesi (biçimi) EntrySelectedBy öğesi TableRowEntry (biçimi) için SelectionCondition öğesi EntrySelectedBy EntrySelectedBy TableRowEntry (biçimi) için için SelectionCondition PropertyName öğesinin TableRowEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="76953-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="76953-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76953-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="76953-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="76953-107">Attributes and Elements</span></span>

<span data-ttu-id="76953-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `PropertyName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="76953-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="76953-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="76953-109">Attributes</span></span>

<span data-ttu-id="76953-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="76953-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="76953-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="76953-111">Child Elements</span></span>

<span data-ttu-id="76953-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="76953-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="76953-113">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="76953-113">Parent Elements</span></span>

|<span data-ttu-id="76953-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="76953-114">Element</span></span>|<span data-ttu-id="76953-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76953-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="76953-116">EntrySelectedBy TableRowEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="76953-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="76953-117">Bu tablo girişi kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="76953-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="76953-118">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="76953-118">Text Value</span></span>

<span data-ttu-id="76953-119">.NET özellik adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="76953-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="76953-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76953-120">Remarks</span></span>

<span data-ttu-id="76953-121">Seçim koşulu en az bir özellik adı veya bir betik bloğu belirtmelisiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="76953-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="76953-122">Seçimi koşulları nasıl kullanılabileceği hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="76953-122">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="76953-123">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="76953-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="76953-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="76953-124">See Also</span></span>

[<span data-ttu-id="76953-125">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="76953-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="76953-126">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="76953-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="76953-127">SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="76953-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="76953-128">EntrySelectedBy TableRowEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="76953-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="76953-129">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="76953-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
