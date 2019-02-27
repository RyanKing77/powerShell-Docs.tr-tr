---
title: GroupBy (biçimi) için ExpressionBinding için ItemSelectionCondition öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844810"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="e4d59-102">GroupBy ExpressionBinding için ItemSelectionCondition Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="e4d59-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="e4d59-103">Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e4d59-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="e4d59-104">Bir denetim öğesi için belirtilip seçimi koşullar sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="e4d59-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="e4d59-105">Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e4d59-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e4d59-106">GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) CustomItem öğesinin CustomEntry GroupBy (biçimi) ExpressionBinding öğesinin CustomItem GroupBy (biçimi) ItemSelectionCondition öğesinin ExpressionBinding GroupBy (biçimi) için özel denetim</span><span class="sxs-lookup"><span data-stu-id="e4d59-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e4d59-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4d59-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e4d59-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4d59-108">Attributes and Elements</span></span>

<span data-ttu-id="e4d59-109">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ItemSelectionCondition` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e4d59-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e4d59-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e4d59-110">Attributes</span></span>

<span data-ttu-id="e4d59-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="e4d59-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e4d59-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4d59-112">Child Elements</span></span>

|<span data-ttu-id="e4d59-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="e4d59-113">Element</span></span>|<span data-ttu-id="e4d59-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4d59-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e4d59-115">GroupBy (biçimi) için ItemSelectionCondition için PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="e4d59-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="e4d59-116">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="e4d59-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e4d59-117">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4d59-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="e4d59-118">GroupBy (biçimi) için ItemSelectionCondition için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="e4d59-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="e4d59-119">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="e4d59-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e4d59-120">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4d59-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e4d59-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4d59-121">Parent Elements</span></span>

|<span data-ttu-id="e4d59-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="e4d59-122">Element</span></span>|<span data-ttu-id="e4d59-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4d59-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e4d59-124">GroupBy (biçimi) için CustomItem için ExpressionBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="e4d59-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e4d59-125">Denetimi tarafından görüntülenen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e4d59-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e4d59-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4d59-126">Remarks</span></span>

<span data-ttu-id="e4d59-127">Bir özellik adı veya bu koşul için bir betik belirtebilirsiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4d59-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4d59-128">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e4d59-128">See Also</span></span>

[<span data-ttu-id="e4d59-129">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="e4d59-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="e4d59-130">GroupBy (biçimi) için CustomItem için ExpressionBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="e4d59-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
