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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850333"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="1b13f-102">Yapılandırma Denetimleri için SelectionCondition PropertyName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="1b13f-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="1b13f-103">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b13f-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="1b13f-104">Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve giriş kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b13f-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="1b13f-105">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b13f-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="1b13f-106">Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) EntrySelectedBy öğesinin CustomEntry EntrySelectedBy için yapılandırma (CustomEntry için yapılandırma (biçimi) SelectionCondition öğesinin denetimleri için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi EntrySelectedBy ListEntry (biçimi) için için SelectionCondition için PropertyName öğesi biçimi)</span><span class="sxs-lookup"><span data-stu-id="1b13f-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1b13f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b13f-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1b13f-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b13f-108">Attributes and Elements</span></span>

<span data-ttu-id="1b13f-109">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `PropertyName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="1b13f-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1b13f-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1b13f-110">Attributes</span></span>

<span data-ttu-id="1b13f-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="1b13f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1b13f-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b13f-112">Child Elements</span></span>

<span data-ttu-id="1b13f-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="1b13f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1b13f-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b13f-114">Parent Elements</span></span>

|<span data-ttu-id="1b13f-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="1b13f-115">Element</span></span>|<span data-ttu-id="1b13f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b13f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1b13f-117">İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="1b13f-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="1b13f-118">Kullanılacak ortak bir denetim tanımı için bulunması gereken bir koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1b13f-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1b13f-119">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="1b13f-119">Text Value</span></span>

<span data-ttu-id="1b13f-120">.NET özellik adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="1b13f-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="1b13f-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b13f-121">Remarks</span></span>

<span data-ttu-id="1b13f-122">Seçim koşulu en az bir özellik adı veya komut dosyasını belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b13f-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="1b13f-123">Seçimi koşulları nasıl kullanılabileceği hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1b13f-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1b13f-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="1b13f-124">See Also</span></span>

[<span data-ttu-id="1b13f-125">İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="1b13f-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="1b13f-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="1b13f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
