---
title: PropertyName öğesi için yapılandırma (biçimi) için denetimleri için SelectionCondition | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064736"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="e11f4-102">Yapılandırma Denetimleri için SelectionCondition PropertyName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="e11f4-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e11f4-103">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="e11f4-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="e11f4-104">Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve giriş kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e11f4-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="e11f4-105">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e11f4-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e11f4-106">Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) EntrySelectedBy öğesinin CustomEntry EntrySelectedBy için yapılandırma (CustomEntry için yapılandırma (biçimi) SelectionCondition öğesinin denetimleri için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi EntrySelectedBy ListEntry (biçimi) için için SelectionCondition için PropertyName öğesi biçimi)</span><span class="sxs-lookup"><span data-stu-id="e11f4-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e11f4-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e11f4-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e11f4-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="e11f4-108">Attributes and Elements</span></span>

<span data-ttu-id="e11f4-109">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `PropertyName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e11f4-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e11f4-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e11f4-110">Attributes</span></span>

<span data-ttu-id="e11f4-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="e11f4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e11f4-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="e11f4-112">Child Elements</span></span>

<span data-ttu-id="e11f4-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="e11f4-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e11f4-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="e11f4-114">Parent Elements</span></span>

|<span data-ttu-id="e11f4-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="e11f4-115">Element</span></span>|<span data-ttu-id="e11f4-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e11f4-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e11f4-117">İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="e11f4-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="e11f4-118">Kullanılacak ortak bir denetim tanımı için bulunması gereken bir koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e11f4-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e11f4-119">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="e11f4-119">Text Value</span></span>

<span data-ttu-id="e11f4-120">.NET özellik adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="e11f4-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="e11f4-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e11f4-121">Remarks</span></span>

<span data-ttu-id="e11f4-122">Seçim koşulu en az bir özellik adı veya komut dosyasını belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e11f4-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="e11f4-123">Seçimi koşulları nasıl kullanılabileceği hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e11f4-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e11f4-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e11f4-124">See Also</span></span>

[<span data-ttu-id="e11f4-125">İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="e11f4-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="e11f4-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="e11f4-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
