---
title: ItemSelectionCondition öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850907"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="2f5c8-102">Görünüm Denetimleri için ExpressionBinding ItemSelectionCondition Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="2f5c8-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="2f5c8-103">Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2f5c8-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="2f5c8-104">Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2f5c8-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="2f5c8-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) denetimleri (biçimi) öğesi denetim öğesi denetimi için CustomEntries öğesi görünümü (biçimi) için denetimleri için özel denetim öğesi görünümü (biçimi) için denetimleri için Özel denetim CustomEntry öğesinin CustomEntries CustomEntry CustomItem Görünüm (biçimi) için denetimleri için görüntüleme (biçimi) ExpressionBinding öğesinin denetimleri için görüntüleme (biçimi) CustomItem öğesinin denetimleri için görüntüleme (biçimi) Görünüm (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="2f5c8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2f5c8-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f5c8-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2f5c8-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2f5c8-107">Attributes and Elements</span></span>

<span data-ttu-id="2f5c8-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ItemSelectionCondition` öğesi.</span><span class="sxs-lookup"><span data-stu-id="2f5c8-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2f5c8-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2f5c8-109">Attributes</span></span>

<span data-ttu-id="2f5c8-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="2f5c8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2f5c8-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2f5c8-111">Child Elements</span></span>

|<span data-ttu-id="2f5c8-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="2f5c8-112">Element</span></span>|<span data-ttu-id="2f5c8-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f5c8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2f5c8-114">PropertyName öğesi görünümü (biçimi) için denetimleri için ItemSelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="2f5c8-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="2f5c8-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="2f5c8-115">Optional element.</span></span><br /><br /> <span data-ttu-id="2f5c8-116">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="2f5c8-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="2f5c8-117">ScriptBlock öğesi görünümü (biçimi) için denetimleri için ItemSelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="2f5c8-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="2f5c8-118">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="2f5c8-118">Optional element.</span></span><br /><br /> <span data-ttu-id="2f5c8-119">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="2f5c8-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2f5c8-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2f5c8-120">Parent Elements</span></span>

|<span data-ttu-id="2f5c8-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="2f5c8-121">Element</span></span>|<span data-ttu-id="2f5c8-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f5c8-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2f5c8-123">ExpressionBinding öğesi görünümü (biçimi) için denetimleri için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="2f5c8-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="2f5c8-124">Denetimi tarafından görüntülenen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2f5c8-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2f5c8-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f5c8-125">Remarks</span></span>

<span data-ttu-id="2f5c8-126">Bir özellik adı veya bu koşul için bir betik belirtebilirsiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f5c8-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f5c8-127">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="2f5c8-127">See Also</span></span>

[<span data-ttu-id="2f5c8-128">PropertyName öğesi görünümü (biçimi) için denetimleri için ItemSelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="2f5c8-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="2f5c8-129">ScriptBlock öğesi görünümü (biçimi) için denetimleri için ItemSelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="2f5c8-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="2f5c8-130">ExpressionBinding öğesi görünümü (biçimi) için denetimleri için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="2f5c8-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="2f5c8-131">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="2f5c8-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
