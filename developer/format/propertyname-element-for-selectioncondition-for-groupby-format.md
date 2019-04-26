---
title: GroupBy (biçimi) için SelectionCondition için PropertyName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1707317-6c26-4866-bcc1-8924103c9014
caps.latest.revision: 6
ms.openlocfilehash: 7241ea0ea364befa7ad4ab0af4c4209be72214a7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064824"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="5174e-102">GroupBy SelectionCondition için PropertyName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="5174e-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="5174e-103">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="5174e-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="5174e-104">Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve tanımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5174e-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="5174e-105">Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5174e-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="5174e-106">GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) EntrySelectedBy öğesinin CustomEntry GroupBy (biçimi) SelectionCondition öğesinin EntrySelectedBy GroupBy (biçimi) PropertyName öğesinin SelectionCondition GroupBy (biçimi) için özel denetim</span><span class="sxs-lookup"><span data-stu-id="5174e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5174e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5174e-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5174e-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="5174e-108">Attributes and Elements</span></span>

<span data-ttu-id="5174e-109">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `PropertyName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="5174e-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5174e-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5174e-110">Attributes</span></span>

<span data-ttu-id="5174e-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="5174e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5174e-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="5174e-112">Child Elements</span></span>

<span data-ttu-id="5174e-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="5174e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5174e-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="5174e-114">Parent Elements</span></span>

|<span data-ttu-id="5174e-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="5174e-115">Element</span></span>|<span data-ttu-id="5174e-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5174e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5174e-117">GroupBy (biçimi) için EntrySelectedBy için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="5174e-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="5174e-118">Kullanılacak denetimi tanımı bulunması gereken bir koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5174e-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5174e-119">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="5174e-119">Text Value</span></span>

<span data-ttu-id="5174e-120">.NET özellik adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="5174e-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="5174e-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5174e-121">Remarks</span></span>

<span data-ttu-id="5174e-122">Seçim koşulu en az bir özellik adı veya komut dosyasını belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="5174e-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="5174e-123">Seçimi koşulları nasıl kullanılabileceği hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5174e-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5174e-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="5174e-124">See Also</span></span>

[<span data-ttu-id="5174e-125">GroupBy (biçimi) için EntrySelectedBy için SelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="5174e-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="5174e-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="5174e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
