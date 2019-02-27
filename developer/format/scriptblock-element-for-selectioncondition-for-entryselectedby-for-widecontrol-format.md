---
title: ScriptBlock öğesi EntrySelectedBy WideControl (biçimi) için için SelectionCondition için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851677"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="150f1-102">WideControl EntrySelectedBy için SelectionCondition ScriptBlock Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="150f1-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="150f1-103">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="150f1-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="150f1-104">Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve geniş bir girdi tanımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="150f1-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="150f1-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünümü öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi (biçimi) EntrySelectedBy öğesi SelectionCondition öğesinin WideEntry (biçimi) EntrySelectedBy SelectionCondition EntrySelectedBy WideEntry (biçimi) için için ScriptBlock öğesinin WideEntry (biçimi)</span><span class="sxs-lookup"><span data-stu-id="150f1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="150f1-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="150f1-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="150f1-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="150f1-107">Attributes and Elements</span></span>

<span data-ttu-id="150f1-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ScriptBlock` öğesi.</span><span class="sxs-lookup"><span data-stu-id="150f1-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="150f1-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="150f1-109">Attributes</span></span>

<span data-ttu-id="150f1-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="150f1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="150f1-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="150f1-111">Child Elements</span></span>

<span data-ttu-id="150f1-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="150f1-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="150f1-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="150f1-113">Parent Elements</span></span>

|<span data-ttu-id="150f1-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="150f1-114">Element</span></span>|<span data-ttu-id="150f1-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="150f1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="150f1-116">EntrySelectedBy WideEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="150f1-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="150f1-117">Bu tanım için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="150f1-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="150f1-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="150f1-118">Text Value</span></span>

<span data-ttu-id="150f1-119">Yürütülecek betiği belirtin.</span><span class="sxs-lookup"><span data-stu-id="150f1-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="150f1-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="150f1-120">Remarks</span></span>

<span data-ttu-id="150f1-121">Seçim koşulu değerlendirmek için en az bir betik veya özellik adı belirtmeniz gerekir ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="150f1-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="150f1-122">Seçimi koşulları kullanma hakkında daha fazla bilgi için bkz. [veri görüntülendiğinde için koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="150f1-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="150f1-123">Geniş bir görünüm diğer bileşenler hakkında daha fazla bilgi için bkz. [geniş Görünüm](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="150f1-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="150f1-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="150f1-124">See Also</span></span>

[<span data-ttu-id="150f1-125">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="150f1-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="150f1-126">Veri görüntülendiğinde koşulları tanımlama</span><span class="sxs-lookup"><span data-stu-id="150f1-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="150f1-127">PropertyName öğesi SelectionCondition WideEntry (biçimi) için EntrySelectedBy için için</span><span class="sxs-lookup"><span data-stu-id="150f1-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="150f1-128">EntrySelectedBy WideEntry (biçimi) için için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="150f1-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="150f1-129">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="150f1-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
