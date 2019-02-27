---
title: ListItem ListControl (biçimi) için için ItemSelectionCondition öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850921"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="5ad48-102">ListControl ListItem için ItemSelectionCondition Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="5ad48-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="5ad48-103">Bu liste öğesi için kullanılacak bulunmalıdır koşulu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5ad48-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="5ad48-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi ListEntry ListControl (biçimi) ListItems öğesinin ListEntries ListEntry öğesinin ListControl (biçimi) ListItem ListControl (biçimi) için ListControl (biçimi) ItemSelectionCondition öğesinin ListItems için ListControl (biçimi) LISTITEM öğesinin</span><span class="sxs-lookup"><span data-stu-id="5ad48-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5ad48-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ad48-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5ad48-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ad48-106">Attributes and Elements</span></span>

<span data-ttu-id="5ad48-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `ItemSelectionCondition` öğesi.</span><span class="sxs-lookup"><span data-stu-id="5ad48-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ad48-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5ad48-108">Attributes</span></span>

<span data-ttu-id="5ad48-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ad48-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5ad48-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ad48-110">Child Elements</span></span>

|<span data-ttu-id="5ad48-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ad48-111">Element</span></span>|<span data-ttu-id="5ad48-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ad48-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ad48-113">PropertyName öğesi için ItemSelectionCondition ListControl (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="5ad48-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="5ad48-114">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="5ad48-114">Optional element.</span></span><br /><br /> <span data-ttu-id="5ad48-115">Koşul tetikleyen .NET alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ad48-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="5ad48-116">ItemSelectionCondition ListControl (biçimi) için için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="5ad48-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="5ad48-117">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="5ad48-117">Optional element.</span></span><br /><br /> <span data-ttu-id="5ad48-118">Koşul tetikleyen betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ad48-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5ad48-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ad48-119">Parent Elements</span></span>

|<span data-ttu-id="5ad48-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ad48-120">Element</span></span>|<span data-ttu-id="5ad48-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ad48-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ad48-122">LISTITEM öğesinin ListControl (biçimi) için ListItems için</span><span class="sxs-lookup"><span data-stu-id="5ad48-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="5ad48-123">Betik değeri liste görünümünün bir satır görüntülenir ve özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5ad48-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5ad48-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ad48-124">Remarks</span></span>

<span data-ttu-id="5ad48-125">Bir özellik adı veya bu koşul için bir betik belirtebilirsiniz, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ad48-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ad48-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="5ad48-126">See Also</span></span>

[<span data-ttu-id="5ad48-127">LISTITEM öğesinin ListControl (biçimi) için ListItems için</span><span class="sxs-lookup"><span data-stu-id="5ad48-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="5ad48-128">PropertyName öğesi için ItemSelectionCondition ListControl (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="5ad48-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="5ad48-129">ItemSelectionCondition ListControl (biçimi) için için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="5ad48-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="5ad48-130">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="5ad48-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
