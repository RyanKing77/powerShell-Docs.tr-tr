---
title: ExpressionBinding öğesi görünümü (biçimi) için denetimleri için CustomItem için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065963"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="98f28-102">Görünüm Denetimleri için CustomItem ExpressionBinding Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="98f28-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="98f28-103">Denetimi tarafından görüntülenen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="98f28-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="98f28-104">Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="98f28-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="98f28-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) denetimleri (biçimi) öğesi denetim öğesi denetimi için CustomEntries öğesi görünümü (biçimi) için denetimleri için özel denetim öğesi görünümü (biçimi) için denetimleri için Özel denetim CustomEntry öğesinin CustomEntries CustomEntry CustomItem Görünüm (biçimi) için denetimleri için görüntüleme (biçimi) ExpressionBinding öğesinin denetimleri için görüntüleme (biçimi) CustomItem öğesinin denetimleri için görüntüleme (biçimi)</span><span class="sxs-lookup"><span data-stu-id="98f28-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="98f28-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98f28-106">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="98f28-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="98f28-107">Attributes and Elements</span></span>

<span data-ttu-id="98f28-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ExpressionBinding` öğesi.</span><span class="sxs-lookup"><span data-stu-id="98f28-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="98f28-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="98f28-109">Attributes</span></span>

<span data-ttu-id="98f28-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="98f28-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="98f28-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="98f28-111">Child Elements</span></span>

|<span data-ttu-id="98f28-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="98f28-112">Element</span></span>|<span data-ttu-id="98f28-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98f28-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="98f28-114">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="98f28-114">Optional element.</span></span><br /><br /> <span data-ttu-id="98f28-115">Bu denetim tarafından kullanılan bir denetimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="98f28-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="98f28-116">CustomControlName öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="98f28-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="98f28-117">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="98f28-117">Optional element.</span></span><br /><br /> <span data-ttu-id="98f28-118">Bir ortak denetimi veya bir görünüm denetimi adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="98f28-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="98f28-119">EnumerateCollection öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="98f28-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="98f28-120">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="98f28-120">Optional element.</span></span><br /><br /> <span data-ttu-id="98f28-121">Koleksiyon öğelerini görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="98f28-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="98f28-122">Görünüm (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="98f28-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="98f28-123">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="98f28-123">Optional element.</span></span><br /><br /> <span data-ttu-id="98f28-124">Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="98f28-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="98f28-125">PropertyName öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="98f28-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="98f28-126">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="98f28-126">Optional element.</span></span><br /><br /> <span data-ttu-id="98f28-127">.NET özelliğinin denetimi tarafından görüntülenen değeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="98f28-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="98f28-128">ScriptBlock öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="98f28-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="98f28-129">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="98f28-129">Optional element.</span></span><br /><br /> <span data-ttu-id="98f28-130">Denetimi tarafından görüntülenen değeri betiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="98f28-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="98f28-131">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="98f28-131">Parent Elements</span></span>

|<span data-ttu-id="98f28-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="98f28-132">Element</span></span>|<span data-ttu-id="98f28-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98f28-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="98f28-134">CustomItem öğesi görünümü (biçimi) için denetimleri için CustomEntry için</span><span class="sxs-lookup"><span data-stu-id="98f28-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="98f28-135">Hangi veri denetimi tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="98f28-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="98f28-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98f28-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="98f28-137">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="98f28-137">See Also</span></span>

[<span data-ttu-id="98f28-138">CustomItem öğesi görünümü (biçimi) için denetimleri için CustomEntry için</span><span class="sxs-lookup"><span data-stu-id="98f28-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="98f28-139">CustomControlName öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="98f28-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="98f28-140">EnumerateCollection öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="98f28-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="98f28-141">Görünüm (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="98f28-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="98f28-142">PropertyName öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="98f28-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="98f28-143">ScriptBlock öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="98f28-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="98f28-144">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="98f28-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
