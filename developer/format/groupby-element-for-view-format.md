---
title: GroupBy öğesi görünümü (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849283"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="509ef-102">Görünüm için GroupBy Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="509ef-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="509ef-103">Yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="509ef-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="509ef-104">Bu öğe, bir tablo, liste, geniş veya özel denetimi görünüm tanımlarken, kullanılır.</span><span class="sxs-lookup"><span data-stu-id="509ef-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="509ef-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="509ef-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="509ef-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="509ef-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="509ef-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="509ef-107">Attributes and Elements</span></span>

<span data-ttu-id="509ef-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="509ef-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="509ef-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="509ef-109">Attributes</span></span>

<span data-ttu-id="509ef-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="509ef-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="509ef-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="509ef-111">Child Elements</span></span>

|<span data-ttu-id="509ef-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="509ef-112">Element</span></span>|<span data-ttu-id="509ef-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="509ef-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="509ef-114">GroupBy (biçimi) için özel denetim öğesi</span><span class="sxs-lookup"><span data-stu-id="509ef-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="509ef-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="509ef-115">Optional element.</span></span><br /><br /> <span data-ttu-id="509ef-116">Yeni gruplar görüntüleyen bir özel denetim tanımlar.</span><span class="sxs-lookup"><span data-stu-id="509ef-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="509ef-117">GroupBy (biçimi) için CustomControlName öğesi</span><span class="sxs-lookup"><span data-stu-id="509ef-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="509ef-118">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="509ef-118">Optional element.</span></span><br /><br /> <span data-ttu-id="509ef-119">Yeni grubunu görüntülemek için kullanılan bir denetimin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="509ef-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="509ef-120">GroupBy (biçimi) için etiket öğesi</span><span class="sxs-lookup"><span data-stu-id="509ef-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="509ef-121">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="509ef-121">Optional element.</span></span><br /><br /> <span data-ttu-id="509ef-122">Yeni bir grup ile karşılaşıldığında görüntülenen etiketi belirtir.</span><span class="sxs-lookup"><span data-stu-id="509ef-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="509ef-123">GroupBy (biçimi) için PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="509ef-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="509ef-124">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="509ef-124">Optional element.</span></span><br /><br /> <span data-ttu-id="509ef-125">.NET özelliğini başlatır belirtir, değeri değiştiğinde yeni bir grup.</span><span class="sxs-lookup"><span data-stu-id="509ef-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="509ef-126">GroupBy (biçimi) için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="509ef-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="509ef-127">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="509ef-127">Optional element.</span></span><br /><br /> <span data-ttu-id="509ef-128">Yeni bir grup değeri değiştiğinde başlatan betiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="509ef-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="509ef-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="509ef-129">Parent Elements</span></span>

|<span data-ttu-id="509ef-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="509ef-130">Element</span></span>|<span data-ttu-id="509ef-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="509ef-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="509ef-132">Görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="509ef-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="509ef-133">Bir veya daha fazla .NET nesnelerini görüntüleyen bir görünüm tanımlar.</span><span class="sxs-lookup"><span data-stu-id="509ef-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="509ef-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="509ef-134">Remarks</span></span>

<span data-ttu-id="509ef-135">Yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken, özellik veya yeni Grup başlatacak komut dosyasını belirtmeniz gerekir; Ancak, her ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="509ef-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="509ef-136">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="509ef-136">See Also</span></span>

[<span data-ttu-id="509ef-137">GroupBy (biçimi) için CustomControlName öğesi</span><span class="sxs-lookup"><span data-stu-id="509ef-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="509ef-138">GroupBy (biçimi) için etiket öğesi</span><span class="sxs-lookup"><span data-stu-id="509ef-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="509ef-139">GroupBy (biçimi) için PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="509ef-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="509ef-140">GroupBy (biçimi) için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="509ef-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="509ef-141">Görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="509ef-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="509ef-142">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="509ef-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
