---
title: İçin yapılandırma (biçimi) için denetimleri için CustomItem ExpressionBinding öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065960"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="a90e5-102">Yapılandırma Denetimleri için CustomItem ExpressionBinding Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="a90e5-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="a90e5-103">Denetimi tarafından görüntülenen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a90e5-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="a90e5-104">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a90e5-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="a90e5-105">Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) CustomItem öğesinin CustomEntry CustomItem denetimleri için yapılandırma (biçimi) için yapılandırma ExpressionBinding öğesinin denetimleri için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="a90e5-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a90e5-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a90e5-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="a90e5-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="a90e5-107">Attributes and Elements</span></span>

<span data-ttu-id="a90e5-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ExpressionBinding` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a90e5-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a90e5-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a90e5-109">Attributes</span></span>

<span data-ttu-id="a90e5-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="a90e5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a90e5-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="a90e5-111">Child Elements</span></span>

|<span data-ttu-id="a90e5-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="a90e5-112">Element</span></span>|<span data-ttu-id="a90e5-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a90e5-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="a90e5-114">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="a90e5-114">Optional element.</span></span><br /><br /> <span data-ttu-id="a90e5-115">Bu denetim tarafından kullanılan bir denetimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a90e5-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="a90e5-116">İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding CustomControlName öğesi</span><span class="sxs-lookup"><span data-stu-id="a90e5-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="a90e5-117">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="a90e5-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a90e5-118">Bir ortak denetimi veya bir görünüm denetimi adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a90e5-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="a90e5-119">İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding EnumerateCollection öğesi</span><span class="sxs-lookup"><span data-stu-id="a90e5-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="a90e5-120">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="a90e5-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a90e5-121">Koleksiyon öğelerini denetimi tarafından görüntülenen belirtildi.</span><span class="sxs-lookup"><span data-stu-id="a90e5-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="a90e5-122">İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="a90e5-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="a90e5-123">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="a90e5-123">Optional element.</span></span><br /><br /> <span data-ttu-id="a90e5-124">Bu yaygın bir denetim kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a90e5-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="a90e5-125">İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="a90e5-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="a90e5-126">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="a90e5-126">Optional element.</span></span><br /><br /> <span data-ttu-id="a90e5-127">Ortak denetimi tarafından görüntülenen değeri .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="a90e5-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="a90e5-128">Denetimler için yapılandırma (biçimi) için ExpressionBinding için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="a90e5-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="a90e5-129">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="a90e5-129">Optional element.</span></span><br /><br /> <span data-ttu-id="a90e5-130">Ortak denetimi tarafından görüntülenen değeri betiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a90e5-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a90e5-131">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="a90e5-131">Parent Elements</span></span>

|<span data-ttu-id="a90e5-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="a90e5-132">Element</span></span>|<span data-ttu-id="a90e5-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a90e5-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a90e5-134">Yapılandırma için denetimleri için CustomEntry için CustomItem öğesi</span><span class="sxs-lookup"><span data-stu-id="a90e5-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="a90e5-135">Özel denetim görünüm tarafından hangi veriler görüntülenir ve nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a90e5-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a90e5-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a90e5-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="a90e5-137">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a90e5-137">See Also</span></span>

[<span data-ttu-id="a90e5-138">Yapılandırma için denetimleri için CustomEntry için CustomItem öğesi</span><span class="sxs-lookup"><span data-stu-id="a90e5-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="a90e5-139">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="a90e5-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
