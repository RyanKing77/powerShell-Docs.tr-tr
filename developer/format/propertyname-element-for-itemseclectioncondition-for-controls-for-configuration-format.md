---
title: PropertyName öğesi için yapılandırma (biçimi) için denetimleri için ItemSeclectionCondition | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850263"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="bbaac-102">Yapılandırma Denetimleri için ItemSelectionCondition PropertyName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="bbaac-102">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="bbaac-103">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="bbaac-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="bbaac-104">Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve denetimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbaac-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="bbaac-105">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbaac-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="bbaac-106">Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) CustomItem öğesinin CustomEntry CustomItem denetimleri için yapılandırma (biçimi) için yapılandırma ExpressionBinding öğesinin denetimleri için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi ItemSelectionCondition öğesi ExpressionBinding ItemSeclectionCondition denetimleri için yapılandırma (biçimi) için yapılandırma (biçimi) PropertyName öğesinin denetimleri için</span><span class="sxs-lookup"><span data-stu-id="bbaac-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bbaac-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbaac-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bbaac-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbaac-108">Attributes and Elements</span></span>

<span data-ttu-id="bbaac-109">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `PropertyName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="bbaac-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bbaac-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bbaac-110">Attributes</span></span>

<span data-ttu-id="bbaac-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="bbaac-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bbaac-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbaac-112">Child Elements</span></span>

<span data-ttu-id="bbaac-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="bbaac-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bbaac-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbaac-114">Parent Elements</span></span>

|<span data-ttu-id="bbaac-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="bbaac-115">Element</span></span>|<span data-ttu-id="bbaac-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbaac-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bbaac-117">İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="bbaac-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="bbaac-118">Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bbaac-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bbaac-119">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="bbaac-119">Text Value</span></span>

<span data-ttu-id="bbaac-120">Koşul tetikleyen .NET özelliğinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="bbaac-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="bbaac-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bbaac-121">Remarks</span></span>

<span data-ttu-id="bbaac-122">Bu öğe kullanılıp kullanılmadığını belirtemezsiniz [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) seçim koşulu tanımlarken öğesi.</span><span class="sxs-lookup"><span data-stu-id="bbaac-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="bbaac-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="bbaac-123">See Also</span></span>

[<span data-ttu-id="bbaac-124">Denetimler için yapılandırma (biçimi) için ItemSeclectionCondition için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="bbaac-124">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="bbaac-125">İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="bbaac-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="bbaac-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="bbaac-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
