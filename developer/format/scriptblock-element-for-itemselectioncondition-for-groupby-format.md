---
title: GroupBy (biçimi) için ItemSelectionCondition için ScriptBlock öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064552"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="1ef4f-102">GroupBy ItemSelectionCondition için ScriptBlock Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="1ef4f-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="1ef4f-103">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ef4f-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="1ef4f-104">Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve denetimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1ef4f-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="1ef4f-105">Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1ef4f-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="1ef4f-106">GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi Özel denetim CustomItem ExpressionBinding GroupBy (biçimi) ScriptBlock öğesinin GroupBy (biçimi) ItemSelectionCondition öğesinin GroupBy (biçimi) ExpressionBinding öğesinin CustomEntry CustomItem öğesinin GroupBy (biçimi) GroupBy (biçimi) için ItemSelectionCondition</span><span class="sxs-lookup"><span data-stu-id="1ef4f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1ef4f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ef4f-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1ef4f-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="1ef4f-108">Attributes and Elements</span></span>

<span data-ttu-id="1ef4f-109">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ScriptBlock` öğesi.</span><span class="sxs-lookup"><span data-stu-id="1ef4f-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1ef4f-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1ef4f-110">Attributes</span></span>

<span data-ttu-id="1ef4f-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="1ef4f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1ef4f-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="1ef4f-112">Child Elements</span></span>

<span data-ttu-id="1ef4f-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="1ef4f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1ef4f-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="1ef4f-114">Parent Elements</span></span>

|<span data-ttu-id="1ef4f-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="1ef4f-115">Element</span></span>|<span data-ttu-id="1ef4f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ef4f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1ef4f-117">GroupBy (biçimi) için ExpressionBinding için ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="1ef4f-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="1ef4f-118">Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1ef4f-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1ef4f-119">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="1ef4f-119">Text Value</span></span>

<span data-ttu-id="1ef4f-120">Yürütülecek betiği belirtin.</span><span class="sxs-lookup"><span data-stu-id="1ef4f-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ef4f-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ef4f-121">Remarks</span></span>

<span data-ttu-id="1ef4f-122">Bu öğe kullanılıp kullanılmadığını belirtemezsiniz [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) seçim koşulu tanımlarken öğesi.</span><span class="sxs-lookup"><span data-stu-id="1ef4f-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ef4f-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="1ef4f-123">See Also</span></span>

[<span data-ttu-id="1ef4f-124">GroupBy (biçimi) için ExpressionBinding için ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="1ef4f-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="1ef4f-125">GroupBy (biçimi) için ItemSelectionCondition için PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="1ef4f-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="1ef4f-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="1ef4f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
