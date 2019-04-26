---
title: İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065521"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="33626-102">Yapılandırma Denetimleri için ExpressionBinding ItemSelectionCondition Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="33626-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="33626-103">Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="33626-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="33626-104">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33626-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="33626-105">Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) CustomItem öğesinin CustomEntry CustomItem denetimleri için yapılandırma (biçimi) için yapılandırma ExpressionBinding öğesinin denetimleri için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="33626-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="33626-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33626-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="33626-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="33626-107">Attributes and Elements</span></span>

<span data-ttu-id="33626-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ItemSelectionCondition` öğesi.</span><span class="sxs-lookup"><span data-stu-id="33626-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="33626-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="33626-109">Attributes</span></span>

<span data-ttu-id="33626-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="33626-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="33626-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="33626-111">Child Elements</span></span>

|<span data-ttu-id="33626-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="33626-112">Element</span></span>|<span data-ttu-id="33626-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33626-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33626-114">İçin yapılandırma (biçimi) için denetimleri için ItemSelectionCondition PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="33626-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="33626-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="33626-115">Optional element.</span></span><br /><br /> <span data-ttu-id="33626-116">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="33626-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="33626-117">Denetimler için yapılandırma (biçimi) için ItemSelectionCondition için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="33626-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="33626-118">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="33626-118">Optional element.</span></span><br /><br /> <span data-ttu-id="33626-119">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="33626-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="33626-120">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="33626-120">Parent Elements</span></span>

|<span data-ttu-id="33626-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="33626-121">Element</span></span>|<span data-ttu-id="33626-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33626-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33626-123">İçin yapılandırma (biçimi) için denetimleri için CustomItem ExpressionBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="33626-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="33626-124">Denetimi tarafından görüntülenen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="33626-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="33626-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33626-125">Remarks</span></span>

<span data-ttu-id="33626-126">Bir özellik adı veya bu koşul için bir betik belirtebilirsiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="33626-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="33626-127">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="33626-127">See Also</span></span>

[<span data-ttu-id="33626-128">İçin yapılandırma (biçimi) için denetimleri için ItemSelectionCondition PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="33626-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="33626-129">Denetimler için yapılandırma (biçimi) için ItemSelectionCondition için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="33626-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="33626-130">İçin yapılandırma (biçimi) için denetimleri için CustomItem ExpressionBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="33626-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="33626-131">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="33626-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
