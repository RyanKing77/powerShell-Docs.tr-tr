---
title: ScriptBlock öğesi için yapılandırma (biçimi) için denetimleri için ItemSeclectionCondition | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064450"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="86906-102">Yapılandırma Denetimleri için ItemSelectionCondition ScriptBlock Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="86906-102">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="86906-103">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="86906-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="86906-104">Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve denetimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86906-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="86906-105">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86906-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="86906-106">Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) CustomItem öğesinin CustomEntry CustomItem denetimleri için yapılandırma (biçimi) için yapılandırma ExpressionBinding öğesinin denetimleri için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi ItemSelectionCondition öğesi ExpressionBinding ItemSelectionCondition denetimleri için yapılandırma (biçimi) için yapılandırma (biçimi) ScriptBlock öğesinin denetimleri için</span><span class="sxs-lookup"><span data-stu-id="86906-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="86906-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86906-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="86906-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="86906-108">Attributes and Elements</span></span>

<span data-ttu-id="86906-109">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ScriptBlock` öğesi.</span><span class="sxs-lookup"><span data-stu-id="86906-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="86906-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="86906-110">Attributes</span></span>

<span data-ttu-id="86906-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="86906-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="86906-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="86906-112">Child Elements</span></span>

<span data-ttu-id="86906-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="86906-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="86906-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="86906-114">Parent Elements</span></span>

|<span data-ttu-id="86906-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="86906-115">Element</span></span>|<span data-ttu-id="86906-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86906-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86906-117">İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="86906-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="86906-118">Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="86906-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="86906-119">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="86906-119">Text Value</span></span>

<span data-ttu-id="86906-120">Yürütülecek betiği belirtin.</span><span class="sxs-lookup"><span data-stu-id="86906-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="86906-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86906-121">Remarks</span></span>

<span data-ttu-id="86906-122">Bu öğe kullanılıp kullanılmadığını belirtemezsiniz [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) seçim koşulu tanımlarken öğesi.</span><span class="sxs-lookup"><span data-stu-id="86906-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="86906-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="86906-123">See Also</span></span>

[<span data-ttu-id="86906-124">İçin yapılandırma (biçimi) için denetimleri için ItemSeclectionCondition PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="86906-124">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="86906-125">İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="86906-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="86906-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="86906-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
