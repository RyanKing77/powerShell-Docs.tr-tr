---
title: GroupBy (biçimi) için CustomItem için ExpressionBinding öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846063"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="80761-102">GroupBy CustomItem için ExpressionBinding Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="80761-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="80761-103">Denetimi tarafından görüntülenen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="80761-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="80761-104">Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="80761-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="80761-105">GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) CustomItem öğesinin CustomEntry GroupBy (biçimi) ExpressionBinding öğesinin CustomItem GroupBy (biçimi) için özel denetim</span><span class="sxs-lookup"><span data-stu-id="80761-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="80761-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80761-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="80761-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="80761-107">Attributes and Elements</span></span>

<span data-ttu-id="80761-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ExpressionBinding` öğesi.</span><span class="sxs-lookup"><span data-stu-id="80761-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="80761-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="80761-109">Attributes</span></span>

<span data-ttu-id="80761-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="80761-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="80761-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="80761-111">Child Elements</span></span>

|<span data-ttu-id="80761-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="80761-112">Element</span></span>|<span data-ttu-id="80761-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80761-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="80761-114">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="80761-114">Optional element.</span></span><br /><br /> <span data-ttu-id="80761-115">Bu denetim tarafından kullanılan bir denetimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="80761-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="80761-116">GroupBy (biçimi) için ExpressionBinding için CustomControlName öğesi</span><span class="sxs-lookup"><span data-stu-id="80761-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="80761-117">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="80761-117">Optional element.</span></span><br /><br /> <span data-ttu-id="80761-118">Bir ortak denetimi veya bir görünüm denetimi adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="80761-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="80761-119">[GroupBy (biçimi) için ExpressionBinding için EnumerateCollection öğesi](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)ExpressionBinding GroupBy (biçimi) için için EnumerateCollection öğesi</span><span class="sxs-lookup"><span data-stu-id="80761-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="80761-120">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="80761-120">Optional element.</span></span><br /><br /> <span data-ttu-id="80761-121">Belirtilen koleksiyonun öğeleri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="80761-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="80761-122">GroupBy (biçimi) için ExpressionBinding için ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="80761-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="80761-123">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="80761-123">Optional element.</span></span><br /><br /> <span data-ttu-id="80761-124">Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="80761-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="80761-125">GroupBy (biçimi) için ExpressionBinding için PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="80761-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="80761-126">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="80761-126">Optional element.</span></span><br /><br /> <span data-ttu-id="80761-127">.NET özelliğinin denetimi tarafından görüntülenen değeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="80761-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="80761-128">GroupBy (biçimi) için ExpressionBinding için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="80761-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="80761-129">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="80761-129">Optional element.</span></span><br /><br /> <span data-ttu-id="80761-130">Denetimi tarafından görüntülenen değeri betiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="80761-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="80761-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="80761-131">Parent Elements</span></span>

|<span data-ttu-id="80761-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="80761-132">Element</span></span>|<span data-ttu-id="80761-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80761-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80761-134">GroupBy (biçimi) için CustomEntry için CustomItem öğesi</span><span class="sxs-lookup"><span data-stu-id="80761-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="80761-135">Özel denetim görünüm tarafından hangi veriler görüntülenir ve nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="80761-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="80761-136">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="80761-136">See Also</span></span>

[<span data-ttu-id="80761-137">GroupBy (biçimi) için ExpressionBinding için CustomControlName öğesi</span><span class="sxs-lookup"><span data-stu-id="80761-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="80761-138">GroupBy (biçimi) için ExpressionBinding için EnumerateCollection öğesi</span><span class="sxs-lookup"><span data-stu-id="80761-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="80761-139">GroupBy (biçimi) için ExpressionBinding için ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="80761-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="80761-140">GroupBy (biçimi) için ExpressionBinding için PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="80761-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="80761-141">GroupBy (biçimi) için ExpressionBinding için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="80761-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="80761-142">GroupBy (biçimi) için CustomEntry için CustomItem öğesi</span><span class="sxs-lookup"><span data-stu-id="80761-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="80761-143">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="80761-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
