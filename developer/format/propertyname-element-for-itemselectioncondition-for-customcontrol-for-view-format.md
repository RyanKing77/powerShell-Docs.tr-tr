---
title: PropertyName öğesi görünümü (biçimi) için özel denetim için ItemSelectionCondition için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064875"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="aa425-102">Görünüm CustomControl için ItemSelectionCondition PropertyName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="aa425-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="aa425-103">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="aa425-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="aa425-104">Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve denetimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aa425-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="aa425-105">Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aa425-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="aa425-106">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomItem öğesinin CustomEntries görünümü (biçimi) CustomEntry öğesinin özel denetim için CustomEntry ExpressionBinding öğesinin CustomItem görünümü (biçimi) ItemSelectionCondition öğesi görünümü (biçimi) PropertyName öğesinin ItemSelectionCondition için özel denetim için ifade bağlama için için özel denetim için View (biçimi) Görünüm (biçimi için özel denetim</span><span class="sxs-lookup"><span data-stu-id="aa425-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="aa425-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa425-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aa425-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="aa425-108">Attributes and Elements</span></span>

<span data-ttu-id="aa425-109">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `PropertyName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="aa425-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aa425-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aa425-110">Attributes</span></span>

<span data-ttu-id="aa425-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="aa425-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aa425-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="aa425-112">Child Elements</span></span>

<span data-ttu-id="aa425-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="aa425-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="aa425-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="aa425-114">Parent Elements</span></span>

|<span data-ttu-id="aa425-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="aa425-115">Element</span></span>|<span data-ttu-id="aa425-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa425-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aa425-117">ItemSelectionCondition öğesi görünümü (biçimi) için özel denetim için ifade bağlama</span><span class="sxs-lookup"><span data-stu-id="aa425-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="aa425-118">Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aa425-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="aa425-119">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="aa425-119">Text Value</span></span>

<span data-ttu-id="aa425-120">Koşul tetikleyen .NET özelliğinin adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="aa425-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="aa425-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa425-121">Remarks</span></span>

<span data-ttu-id="aa425-122">Bu öğe kullanılıp kullanılmadığını belirtemezsiniz [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) seçim koşulu tanımlarken öğesi.</span><span class="sxs-lookup"><span data-stu-id="aa425-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa425-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="aa425-123">See Also</span></span>

[<span data-ttu-id="aa425-124">ScriptBlock öğesi görünümü (biçimi) için özel denetim için ItemSelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="aa425-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="aa425-125">ItemSelectionCondition öğesi görünümü (biçimi) için özel denetim için ifade bağlama</span><span class="sxs-lookup"><span data-stu-id="aa425-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="aa425-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="aa425-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
