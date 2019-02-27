---
title: Özel denetim (biçimi) için ExpressionBinding için ItemSelectionCondition öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848345"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="f0606-102">CustomControl ExpressionBinding için ItemSelectionCondition Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="f0606-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="f0606-103">Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f0606-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="f0606-104">Bir denetim öğesi için belirtilip seçimi koşullar sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="f0606-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="f0606-105">Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f0606-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="f0606-106">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomItem öğesinin CustomEntries görünümü (biçimi) CustomEntry öğesinin özel denetim için CustomEntry ExpressionBinding öğesinin CustomItem görüntüleme (biçimi) ItemSelectionCondition öğesi görünümü (biçimi) için özel denetim için ifade bağlama için özel denetim için View (biçimi)</span><span class="sxs-lookup"><span data-stu-id="f0606-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f0606-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0606-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f0606-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0606-108">Attributes and Elements</span></span>

<span data-ttu-id="f0606-109">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ItemSelectionCondition` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f0606-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f0606-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f0606-110">Attributes</span></span>

<span data-ttu-id="f0606-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="f0606-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f0606-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0606-112">Child Elements</span></span>

|<span data-ttu-id="f0606-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="f0606-113">Element</span></span>|<span data-ttu-id="f0606-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0606-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f0606-115">PropertyName öğesi görünümü (biçimi için özel denetim için ItemSelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="f0606-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="f0606-116">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="f0606-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f0606-117">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0606-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f0606-118">ScriptBlock öğesi görünümü (biçimi) için özel denetim için ItemSelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="f0606-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="f0606-119">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="f0606-119">Optional element.</span></span><br /><br /> <span data-ttu-id="f0606-120">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0606-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f0606-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0606-121">Parent Elements</span></span>

|<span data-ttu-id="f0606-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="f0606-122">Element</span></span>|<span data-ttu-id="f0606-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0606-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f0606-124">ExpressionBinding öğesi görünümü (biçimi) için özel denetim için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="f0606-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="f0606-125">Denetimi tarafından görüntülenen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f0606-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f0606-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0606-126">Remarks</span></span>

<span data-ttu-id="f0606-127">Bir özellik adı veya bu koşul için bir betik belirtebilirsiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0606-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0606-128">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="f0606-128">See Also</span></span>

[<span data-ttu-id="f0606-129">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="f0606-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="f0606-130">ExpressionBinding öğesi görünümü (biçimi) için özel denetim için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="f0606-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
