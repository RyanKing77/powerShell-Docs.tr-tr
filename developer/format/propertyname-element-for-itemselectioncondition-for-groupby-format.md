---
title: GroupBy (biçimi) için ItemSelectionCondition için PropertyName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064773"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="b2c7a-102">GroupBy ItemSelectionCondition için PropertyName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="b2c7a-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="b2c7a-103">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2c7a-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="b2c7a-104">Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve denetimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b2c7a-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="b2c7a-105">Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b2c7a-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b2c7a-106">GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi Özel denetim CustomItem GroupBy (biçimi) PropertyName öğesinin ExpressionBinding GroupBy (biçimi) ItemSelectionCondition öğesinin GroupBy (biçimi) ExpressionBinding öğesinin CustomEntry CustomItem öğesinin GroupBy (biçimi) GroupBy (biçimi) için ItemSelectionCondition</span><span class="sxs-lookup"><span data-stu-id="b2c7a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b2c7a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2c7a-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b2c7a-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="b2c7a-108">Attributes and Elements</span></span>

<span data-ttu-id="b2c7a-109">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `PropertyName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="b2c7a-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b2c7a-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b2c7a-110">Attributes</span></span>

<span data-ttu-id="b2c7a-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="b2c7a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b2c7a-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="b2c7a-112">Child Elements</span></span>

<span data-ttu-id="b2c7a-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="b2c7a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b2c7a-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="b2c7a-114">Parent Elements</span></span>

|<span data-ttu-id="b2c7a-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="b2c7a-115">Element</span></span>|<span data-ttu-id="b2c7a-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2c7a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b2c7a-117">GroupBy (biçimi) için ExpressionBinding için ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="b2c7a-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="b2c7a-118">Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b2c7a-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b2c7a-119">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="b2c7a-119">Text Value</span></span>

<span data-ttu-id="b2c7a-120">Koşul tetikleyen .NET özelliğinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="b2c7a-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2c7a-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2c7a-121">Remarks</span></span>

<span data-ttu-id="b2c7a-122">Bu öğe kullanılıp kullanılmadığını belirtemezsiniz [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) seçim koşulu tanımlarken öğesi.</span><span class="sxs-lookup"><span data-stu-id="b2c7a-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2c7a-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="b2c7a-123">See Also</span></span>

[<span data-ttu-id="b2c7a-124">GroupBy (biçimi) için ItemSelectionCondition için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="b2c7a-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="b2c7a-125">GroupBy (biçimi) için ExpressionBinding için ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="b2c7a-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b2c7a-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="b2c7a-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
