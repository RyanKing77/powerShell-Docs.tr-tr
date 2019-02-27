---
title: ScriptBlock öğesi ItemSelectionCondition ListControl (biçimi) için için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846406"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="c1fa7-102">ListControl ItemSelectionCondition için ScriptBlock Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="c1fa7-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="c1fa7-103">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1fa7-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="c1fa7-104">Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve liste öğesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c1fa7-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="c1fa7-105">Bu öğe, bir liste görünümü tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c1fa7-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="c1fa7-106">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi ListEntry ListControl (biçimi) ListItems öğesinin ListEntries ListEntry öğesinin ListControl (biçimi) ListItem ItemSelectionCondition ListControl (biçimi) için ListControl (biçimi) ScriptBlock öğesinin listesi denetimi (biçimi) ItemSelectionCondition öğesinin ListItems için ListControl (biçimi) LISTITEM öğesinin</span><span class="sxs-lookup"><span data-stu-id="c1fa7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c1fa7-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1fa7-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c1fa7-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1fa7-108">Attributes and Elements</span></span>

<span data-ttu-id="c1fa7-109">Aşağıdaki öznitelikler, alt ve üst öğelerinin bölümlerde `ScriptBlock` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c1fa7-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c1fa7-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c1fa7-110">Attributes</span></span>

<span data-ttu-id="c1fa7-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="c1fa7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c1fa7-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1fa7-112">Child Elements</span></span>

<span data-ttu-id="c1fa7-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="c1fa7-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c1fa7-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1fa7-114">Parent Elements</span></span>

|<span data-ttu-id="c1fa7-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="c1fa7-115">Element</span></span>|<span data-ttu-id="c1fa7-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1fa7-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1fa7-117">ListItem ListControl (biçimi) için için ItemSelectionCondition öğesi</span><span class="sxs-lookup"><span data-stu-id="c1fa7-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="c1fa7-118">Bu liste öğesi için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c1fa7-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c1fa7-119">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="c1fa7-119">Text Value</span></span>

<span data-ttu-id="c1fa7-120">Yürütülecek betiği belirtin.</span><span class="sxs-lookup"><span data-stu-id="c1fa7-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="c1fa7-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1fa7-121">Remarks</span></span>

<span data-ttu-id="c1fa7-122">Bu öğe kullanılıp kullanılmadığını belirtemezsiniz `PropertyName` seçim koşulu tanımlarken öğesi.</span><span class="sxs-lookup"><span data-stu-id="c1fa7-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1fa7-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="c1fa7-123">See Also</span></span>

[<span data-ttu-id="c1fa7-124">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="c1fa7-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
