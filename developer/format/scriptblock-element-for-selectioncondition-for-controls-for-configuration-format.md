---
title: ScriptBlock öğesi için yapılandırma (biçimi) için denetimleri için SelectionCondition | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064433"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="e9606-102">Yapılandırma Denetimleri için SelectionCondition ScriptBlock Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="e9606-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e9606-103">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9606-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="e9606-104">Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve tanımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9606-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="e9606-105">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9606-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e9606-106">Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) EntrySelectedBy öğesinin CustomEntry EntrySelectedBy denetimleri için yapılandırma (biçimi) için yapılandırma (biçimi) SelectionCondition öğesinin denetimleri için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi Denetimler için yapılandırma (biçimi) için SelectionCondition için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="e9606-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e9606-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9606-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e9606-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="e9606-108">Attributes and Elements</span></span>

<span data-ttu-id="e9606-109">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ScriptBlock` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e9606-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e9606-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e9606-110">Attributes</span></span>

<span data-ttu-id="e9606-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="e9606-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e9606-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="e9606-112">Child Elements</span></span>

<span data-ttu-id="e9606-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="e9606-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e9606-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="e9606-114">Parent Elements</span></span>

|<span data-ttu-id="e9606-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="e9606-115">Element</span></span>|<span data-ttu-id="e9606-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9606-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e9606-117">İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="e9606-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="e9606-118">Kullanılacak ortak denetim tanımı bulunması gereken bir koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e9606-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e9606-119">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="e9606-119">Text Value</span></span>

<span data-ttu-id="e9606-120">Yürütülecek betiği belirtin.</span><span class="sxs-lookup"><span data-stu-id="e9606-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="e9606-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9606-121">Remarks</span></span>

<span data-ttu-id="e9606-122">Seçim koşulu değerlendirmek için bir en az bir betik veya özellik adı belirtmeniz gerekir ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9606-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="e9606-123">Seçimi koşulları nasıl kullanılabileceği hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e9606-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e9606-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e9606-124">See Also</span></span>

[<span data-ttu-id="e9606-125">İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="e9606-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="e9606-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="e9606-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
