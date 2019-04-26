---
title: ScriptBlock öğesi görünümü (biçimi) için özel denetim için SelectionCondition için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064569"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="6e335-102">Görünüm CustomControl için SelectionCondition ScriptBlock Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="6e335-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="6e335-103">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e335-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="6e335-104">Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve tanımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6e335-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="6e335-105">Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6e335-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="6e335-106">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi görünümü (biçimi) CustomEntries öğesinin CustomEntries için özel denetim için View (Görünüm (biçimi) CustomEntry öğesinin özel denetim Biçimi) CustomItem öğesi görünümü (biçimi) SelectionCondition öğesinin EntrySelectedBy SelectionCondition Görünüm (biçimi) için özel denetim için View (biçimi) ScriptBlock öğesinin özel denetim için özel denetim için CustomEntry için</span><span class="sxs-lookup"><span data-stu-id="6e335-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6e335-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e335-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6e335-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="6e335-108">Attributes and Elements</span></span>

<span data-ttu-id="6e335-109">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ScriptBlock` öğesi.</span><span class="sxs-lookup"><span data-stu-id="6e335-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6e335-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6e335-110">Attributes</span></span>

<span data-ttu-id="6e335-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="6e335-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6e335-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="6e335-112">Child Elements</span></span>

<span data-ttu-id="6e335-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="6e335-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6e335-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="6e335-114">Parent Elements</span></span>

|<span data-ttu-id="6e335-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e335-115">Element</span></span>|<span data-ttu-id="6e335-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e335-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6e335-117">SelectionCondition öğesi görünümü (biçimi) için özel denetim için EntrySelectedBy için</span><span class="sxs-lookup"><span data-stu-id="6e335-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="6e335-118">Kullanılacak denetimi tanımı bulunması gereken bir koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6e335-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6e335-119">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="6e335-119">Text Value</span></span>

<span data-ttu-id="6e335-120">Yürütülecek betiği belirtin.</span><span class="sxs-lookup"><span data-stu-id="6e335-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="6e335-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e335-121">Remarks</span></span>

<span data-ttu-id="6e335-122">Seçim koşulu değerlendirmek için bir en az bir betik veya özellik adı belirtmeniz gerekir ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e335-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="6e335-123">Seçimi koşulları nasıl kullanılabileceği hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6e335-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6e335-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6e335-124">See Also</span></span>

[<span data-ttu-id="6e335-125">SelectionCondition öğesi görünümü (biçimi) için özel denetim için EntrySelectedBy için</span><span class="sxs-lookup"><span data-stu-id="6e335-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="6e335-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="6e335-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
