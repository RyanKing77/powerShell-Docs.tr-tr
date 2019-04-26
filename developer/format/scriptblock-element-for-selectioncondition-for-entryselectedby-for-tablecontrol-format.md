---
title: TableControl (biçimi) için EntrySelectedBy için SelectionCondition için ScriptBlock öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076353"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="f8e49-102">TableControl EntrySelectedBy için SelectionCondition ScriptBlock Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="f8e49-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="f8e49-103">Koşul tetikler betik bloğu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8e49-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="f8e49-104">Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve tablo girişi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f8e49-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="f8e49-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi (biçimi) TableRowEntry öğesi (biçimi) EntrySelectedBy öğesi TableRowEntry (biçimi) için SelectionCondition öğesi EntrySelectedBy SelectionCondition EntrySelectedBy TableRowEntry (biçimi) için için ScriptBlock öğesinin TableRowEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="f8e49-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f8e49-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f8e49-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f8e49-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="f8e49-107">Attributes and Elements</span></span>

<span data-ttu-id="f8e49-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ScriptBlock` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f8e49-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f8e49-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f8e49-109">Attributes</span></span>

<span data-ttu-id="f8e49-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="f8e49-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f8e49-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="f8e49-111">Child Elements</span></span>

<span data-ttu-id="f8e49-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="f8e49-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f8e49-113">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="f8e49-113">Parent Elements</span></span>

|<span data-ttu-id="f8e49-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="f8e49-114">Element</span></span>|<span data-ttu-id="f8e49-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f8e49-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8e49-116">EntrySelectedBy TableRowEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="f8e49-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="f8e49-117">Bu tablo girişi kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f8e49-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f8e49-118">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="f8e49-118">Text Value</span></span>

<span data-ttu-id="f8e49-119">Yürütülecek betiği belirtin.</span><span class="sxs-lookup"><span data-stu-id="f8e49-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8e49-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f8e49-120">Remarks</span></span>

<span data-ttu-id="f8e49-121">Seçim koşulu en az bir betik bloğu ya da özellik adı belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8e49-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="f8e49-122">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [tanımlama koşulları için bir görünüm girişi olduğunda veya öğe kullanılan](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f8e49-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f8e49-123">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f8e49-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f8e49-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="f8e49-124">See Also</span></span>

[<span data-ttu-id="f8e49-125">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="f8e49-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f8e49-126">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="f8e49-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f8e49-127">PropertyName öğesi SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için</span><span class="sxs-lookup"><span data-stu-id="f8e49-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="f8e49-128">EntrySelectedBy TableRowEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="f8e49-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="f8e49-129">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="f8e49-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
