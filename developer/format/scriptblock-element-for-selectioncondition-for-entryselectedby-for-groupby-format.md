---
title: GroupBy (biçimi) için EntrySelectedBy için SelectionCondition için ScriptBlock öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01344bd-ad69-4789-8e9f-2e79880c3a33
caps.latest.revision: 6
ms.openlocfilehash: cb79fb942111cee89c6b2abba75de4c494082b7e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844768"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="25aba-102">GroupBy EntrySelectedBy için SelectionCondition ScriptBlock Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="25aba-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="25aba-103">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="25aba-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="25aba-104">Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve tanımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="25aba-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="25aba-105">Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="25aba-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="25aba-106">GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) EntrySelectedBy öğesinin CustomEntry GroupBy (biçimi) SelectionCondition öğesinin EntrySelectedBy GroupBy (biçimi) ScriptBlock öğesinin SelectionCondition GroupBy (biçimi) için özel denetim</span><span class="sxs-lookup"><span data-stu-id="25aba-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="25aba-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25aba-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="25aba-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="25aba-108">Attributes and Elements</span></span>

<span data-ttu-id="25aba-109">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ScriptBlock` öğesi.</span><span class="sxs-lookup"><span data-stu-id="25aba-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="25aba-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="25aba-110">Attributes</span></span>

<span data-ttu-id="25aba-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="25aba-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="25aba-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="25aba-112">Child Elements</span></span>

<span data-ttu-id="25aba-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="25aba-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="25aba-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="25aba-114">Parent Elements</span></span>

|<span data-ttu-id="25aba-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="25aba-115">Element</span></span>|<span data-ttu-id="25aba-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25aba-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="25aba-117">GroupBy (biçimi) için EntrySelectedBy için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="25aba-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="25aba-118">Kullanılacak denetimi tanımı bulunması gereken bir koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="25aba-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="25aba-119">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="25aba-119">Text Value</span></span>

<span data-ttu-id="25aba-120">Yürütülecek betiği belirtin.</span><span class="sxs-lookup"><span data-stu-id="25aba-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="25aba-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25aba-121">Remarks</span></span>

<span data-ttu-id="25aba-122">Seçim koşulu değerlendirmek için bir en az bir betik veya özellik adı belirtmeniz gerekir ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="25aba-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="25aba-123">Seçimi koşulları nasıl kullanılabileceği hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="25aba-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="25aba-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="25aba-124">See Also</span></span>

[<span data-ttu-id="25aba-125">GroupBy (biçimi) için EntrySelectedBy için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="25aba-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="25aba-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="25aba-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
