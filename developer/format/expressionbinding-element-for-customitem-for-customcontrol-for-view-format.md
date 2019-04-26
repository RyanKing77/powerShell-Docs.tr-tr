---
title: ExpressionBinding öğesi görünümü (biçimi) için özel denetim için CustomItem için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065929"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="33c31-102">Görünüm CustomControl için CustomItem ExpressionBinding Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="33c31-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="33c31-103">Denetimi tarafından görüntülenen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="33c31-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="33c31-104">Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33c31-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="33c31-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi görünümü (biçimi) CustomEntries öğesinin CustomEntries için özel denetim için View (Görünüm (biçimi) CustomEntry öğesinin özel denetim Biçimi) CustomItem öğesi görünümü (biçimi) ExpressionBinding öğesinin CustomItem Görünüm (biçimi) için özel denetim için özel denetim için CustomEntry için</span><span class="sxs-lookup"><span data-stu-id="33c31-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="33c31-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33c31-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="33c31-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="33c31-107">Attributes and Elements</span></span>

<span data-ttu-id="33c31-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ExpressionBinding` öğesi.</span><span class="sxs-lookup"><span data-stu-id="33c31-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="33c31-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="33c31-109">Attributes</span></span>

<span data-ttu-id="33c31-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="33c31-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="33c31-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="33c31-111">Child Elements</span></span>

|<span data-ttu-id="33c31-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="33c31-112">Element</span></span>|<span data-ttu-id="33c31-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33c31-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="33c31-114">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="33c31-114">Optional element.</span></span><br /><br /> <span data-ttu-id="33c31-115">Bu denetim tarafından kullanılan bir denetimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="33c31-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="33c31-116">CustomControlName öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="33c31-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="33c31-117">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="33c31-117">Optional element.</span></span><br /><br /> <span data-ttu-id="33c31-118">Bir ortak denetimi veya bir görünüm denetimi adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="33c31-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="33c31-119">EnumerateCollection öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="33c31-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="33c31-120">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="33c31-120">Optional element.</span></span><br /><br /> <span data-ttu-id="33c31-121">Belirtilen koleksiyonun öğeleri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="33c31-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="33c31-122">ItemSelectionCondition öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="33c31-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="33c31-123">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="33c31-123">Optional element.</span></span><br /><br /> <span data-ttu-id="33c31-124">Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="33c31-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="33c31-125">PropertyName öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="33c31-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="33c31-126">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="33c31-126">Optional element.</span></span><br /><br /> <span data-ttu-id="33c31-127">.NET özelliğinin denetimi tarafından görüntülenen değeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="33c31-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="33c31-128">İçin görünümün (biçimi) CustomCustomControl ExpressionBinding için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="33c31-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="33c31-129">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="33c31-129">Optional element.</span></span><br /><br /> <span data-ttu-id="33c31-130">Denetimi tarafından görüntülenen değeri betiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="33c31-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="33c31-131">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="33c31-131">Parent Elements</span></span>

|<span data-ttu-id="33c31-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="33c31-132">Element</span></span>|<span data-ttu-id="33c31-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33c31-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33c31-134">CustomItem öğesi görünümü (biçimi) için özel denetim için CustomEntry için</span><span class="sxs-lookup"><span data-stu-id="33c31-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="33c31-135">Özel denetim görünüm tarafından hangi veriler görüntülenir ve nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="33c31-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="33c31-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33c31-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="33c31-137">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="33c31-137">See Also</span></span>

[<span data-ttu-id="33c31-138">CustomControlName öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="33c31-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="33c31-139">EnumerateCollection öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="33c31-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="33c31-140">ItemSelectionCondition öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="33c31-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="33c31-141">PropertyName öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="33c31-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="33c31-142">ScriptBlock öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için</span><span class="sxs-lookup"><span data-stu-id="33c31-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="33c31-143">CustomItem öğesi görünümü (biçimi) için özel denetim için CustomEntry için</span><span class="sxs-lookup"><span data-stu-id="33c31-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="33c31-144">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="33c31-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
