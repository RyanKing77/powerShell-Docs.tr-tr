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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848401"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="2e4e5-102">GroupBy ItemSelectionCondition için PropertyName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="2e4e5-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="2e4e5-103">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e4e5-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="2e4e5-104">Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve denetimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e4e5-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="2e4e5-105">Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e4e5-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="2e4e5-106">GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi Özel denetim CustomItem GroupBy (biçimi) PropertyName öğesinin ExpressionBinding GroupBy (biçimi) ItemSelectionCondition öğesinin GroupBy (biçimi) ExpressionBinding öğesinin CustomEntry CustomItem öğesinin GroupBy (biçimi) GroupBy (biçimi) için ItemSelectionCondition</span><span class="sxs-lookup"><span data-stu-id="2e4e5-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2e4e5-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e4e5-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2e4e5-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2e4e5-108">Attributes and Elements</span></span>

<span data-ttu-id="2e4e5-109">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `PropertyName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="2e4e5-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2e4e5-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2e4e5-110">Attributes</span></span>

<span data-ttu-id="2e4e5-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="2e4e5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2e4e5-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2e4e5-112">Child Elements</span></span>

<span data-ttu-id="2e4e5-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="2e4e5-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2e4e5-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2e4e5-114">Parent Elements</span></span>

|<span data-ttu-id="2e4e5-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="2e4e5-115">Element</span></span>|<span data-ttu-id="2e4e5-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e4e5-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e4e5-117">GroupBy (biçimi) için ExpressionBinding için ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="2e4e5-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="2e4e5-118">Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2e4e5-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2e4e5-119">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="2e4e5-119">Text Value</span></span>

<span data-ttu-id="2e4e5-120">Koşul tetikleyen .NET özelliğinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="2e4e5-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="2e4e5-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e4e5-121">Remarks</span></span>

<span data-ttu-id="2e4e5-122">Bu öğe kullanılıp kullanılmadığını belirtemezsiniz [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) seçim koşulu tanımlarken öğesi.</span><span class="sxs-lookup"><span data-stu-id="2e4e5-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e4e5-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="2e4e5-123">See Also</span></span>

[<span data-ttu-id="2e4e5-124">GroupBy (biçimi) için ItemSelectionCondition için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="2e4e5-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="2e4e5-125">GroupBy (biçimi) için ExpressionBinding için ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="2e4e5-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="2e4e5-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="2e4e5-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
