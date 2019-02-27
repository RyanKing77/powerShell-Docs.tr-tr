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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850914"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="ee964-102">Yapılandırma Denetimleri için ItemSelectionCondition ScriptBlock Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="ee964-102">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="ee964-103">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="ee964-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="ee964-104">Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve denetimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee964-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="ee964-105">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee964-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="ee964-106">Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) CustomItem öğesinin CustomEntry CustomItem denetimleri için yapılandırma (biçimi) için yapılandırma ExpressionBinding öğesinin denetimleri için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi ItemSelectionCondition öğesi ExpressionBinding ItemSelectionCondition denetimleri için yapılandırma (biçimi) için yapılandırma (biçimi) ScriptBlock öğesinin denetimleri için</span><span class="sxs-lookup"><span data-stu-id="ee964-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ee964-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee964-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ee964-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee964-108">Attributes and Elements</span></span>

<span data-ttu-id="ee964-109">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ScriptBlock` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ee964-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ee964-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ee964-110">Attributes</span></span>

<span data-ttu-id="ee964-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="ee964-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ee964-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee964-112">Child Elements</span></span>

<span data-ttu-id="ee964-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="ee964-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ee964-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee964-114">Parent Elements</span></span>

|<span data-ttu-id="ee964-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="ee964-115">Element</span></span>|<span data-ttu-id="ee964-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee964-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ee964-117">İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="ee964-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="ee964-118">Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ee964-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ee964-119">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="ee964-119">Text Value</span></span>

<span data-ttu-id="ee964-120">Yürütülecek betiği belirtin.</span><span class="sxs-lookup"><span data-stu-id="ee964-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="ee964-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee964-121">Remarks</span></span>

<span data-ttu-id="ee964-122">Bu öğe kullanılıp kullanılmadığını belirtemezsiniz [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) seçim koşulu tanımlarken öğesi.</span><span class="sxs-lookup"><span data-stu-id="ee964-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee964-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ee964-123">See Also</span></span>

[<span data-ttu-id="ee964-124">İçin yapılandırma (biçimi) için denetimleri için ItemSeclectionCondition PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="ee964-124">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="ee964-125">İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="ee964-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="ee964-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="ee964-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
