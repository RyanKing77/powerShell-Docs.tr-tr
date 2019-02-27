---
title: PropertyName öğesi ItemSelectionCondition ListControl (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846490"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="a1a24-102">ListControl ItemSelectionCondition için PropertyName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="a1a24-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="a1a24-103">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="a1a24-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="a1a24-104">Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve görünümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a1a24-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="a1a24-105">Bu öğe, bir liste görünümü tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a1a24-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="a1a24-106">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi ListControl (biçimi) ListItem için ListEntry ListItems öğesinin ListControl (biçimi) Öğe için ListItems ItemSelectionCondition ListControl (biçimi) için ListControls PropertyName öğesinin ListItem ItemSelectionCondition öğesinin ListControl (biçimi)</span><span class="sxs-lookup"><span data-stu-id="a1a24-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a1a24-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a1a24-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a1a24-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1a24-108">Attributes and Elements</span></span>

<span data-ttu-id="a1a24-109">Aşağıdaki öznitelikler, alt ve üst öğelerinin bölümlerde `PropertyName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a1a24-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a1a24-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a1a24-110">Attributes</span></span>

<span data-ttu-id="a1a24-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="a1a24-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a1a24-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1a24-112">Child Elements</span></span>

<span data-ttu-id="a1a24-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="a1a24-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a1a24-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1a24-114">Parent Elements</span></span>

|<span data-ttu-id="a1a24-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="a1a24-115">Element</span></span>|<span data-ttu-id="a1a24-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1a24-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a1a24-117">ListItem ListControl (biçimi) için için ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="a1a24-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="a1a24-118">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="a1a24-118">Text Value</span></span>

<span data-ttu-id="a1a24-119">Özellik değeri görüntülenen adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="a1a24-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="a1a24-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1a24-120">Remarks</span></span>

<span data-ttu-id="a1a24-121">Bu öğe kullanılıp kullanılmadığını belirtemezsiniz [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) seçim koşulu tanımlarken öğesi.</span><span class="sxs-lookup"><span data-stu-id="a1a24-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1a24-122">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a1a24-122">See Also</span></span>

[<span data-ttu-id="a1a24-123">ItemSelectionCondition ListIControl (biçimi) için için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="a1a24-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="a1a24-124">ListItem ListControl (biçimi) için için ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="a1a24-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="a1a24-125">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="a1a24-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
