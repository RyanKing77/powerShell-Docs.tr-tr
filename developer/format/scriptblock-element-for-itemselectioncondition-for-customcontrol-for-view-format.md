---
title: ScriptBlock öğesi görünümü (biçimi) için özel denetim için ItemSelectionCondition için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064484"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="61621-102">Görünüm CustomControl için ItemSelectionCondition ScriptBlock Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="61621-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="61621-103">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="61621-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="61621-104">Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve denetimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="61621-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="61621-105">Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="61621-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="61621-106">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomItem öğesinin CustomEntries görünümü (biçimi) CustomEntry öğesinin özel denetim için CustomEntry ExpressionBinding öğesinin CustomItem görünümü (biçimi) ItemSelectionCondition öğesinin özel denetim için ifade bağlama için ItemSelectionCondition için ScriptBlock öğesi görünümü (biçimi) için özel denetim için View (biçimi) Görünüm (biçimi) için özel denetim</span><span class="sxs-lookup"><span data-stu-id="61621-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="61621-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61621-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="61621-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="61621-108">Attributes and Elements</span></span>

<span data-ttu-id="61621-109">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ScriptBlock` öğesi.</span><span class="sxs-lookup"><span data-stu-id="61621-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="61621-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="61621-110">Attributes</span></span>

<span data-ttu-id="61621-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="61621-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="61621-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="61621-112">Child Elements</span></span>

<span data-ttu-id="61621-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="61621-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="61621-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="61621-114">Parent Elements</span></span>

|<span data-ttu-id="61621-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="61621-115">Element</span></span>|<span data-ttu-id="61621-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61621-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="61621-117">ItemSelectionCondition öğesi görünümü (biçimi) için özel denetim için ifade bağlama</span><span class="sxs-lookup"><span data-stu-id="61621-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="61621-118">Bu denetim için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="61621-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="61621-119">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="61621-119">Text Value</span></span>

<span data-ttu-id="61621-120">Yürütülecek betiği belirtin.</span><span class="sxs-lookup"><span data-stu-id="61621-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="61621-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61621-121">Remarks</span></span>

<span data-ttu-id="61621-122">Bu öğe kullanılıp kullanılmadığını belirtemezsiniz [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) seçim koşulu tanımlarken öğesi.</span><span class="sxs-lookup"><span data-stu-id="61621-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="61621-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="61621-123">See Also</span></span>

[<span data-ttu-id="61621-124">PropertyName öğesi görünümü (biçimi) için özel denetim için ItemSelectionCondition için</span><span class="sxs-lookup"><span data-stu-id="61621-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="61621-125">ItemSelectionCondition öğesi görünümü (biçimi) için özel denetim için ifade bağlama</span><span class="sxs-lookup"><span data-stu-id="61621-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="61621-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="61621-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
