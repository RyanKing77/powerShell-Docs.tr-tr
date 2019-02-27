---
title: GroupBy (biçimi) için CustomEntry için CustomItem öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847463"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="ca7eb-102">GroupBy CustomEntry için CustomItem Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="ca7eb-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="ca7eb-103">Özel denetim görünüm tarafından hangi veriler görüntülenir ve nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ca7eb-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="ca7eb-104">Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ca7eb-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="ca7eb-105">GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomItem öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) için CustomEntry</span><span class="sxs-lookup"><span data-stu-id="ca7eb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ca7eb-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca7eb-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ca7eb-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca7eb-107">Attributes and Elements</span></span>

<span data-ttu-id="ca7eb-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomItem` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ca7eb-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ca7eb-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ca7eb-109">Attributes</span></span>

<span data-ttu-id="ca7eb-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="ca7eb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ca7eb-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca7eb-111">Child Elements</span></span>

|<span data-ttu-id="ca7eb-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="ca7eb-112">Element</span></span>|<span data-ttu-id="ca7eb-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca7eb-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ca7eb-114">GroupBy (biçimi) için CustomItem için ExpressionBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="ca7eb-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="ca7eb-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="ca7eb-115">Optional element.</span></span><br /><br /> <span data-ttu-id="ca7eb-116">Denetimi tarafından görüntülenen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ca7eb-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="ca7eb-117">GroupBy (biçimi) için CustomItem için çerçeve öğesi</span><span class="sxs-lookup"><span data-stu-id="ca7eb-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="ca7eb-118">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="ca7eb-118">Optional element.</span></span><br /><br /> <span data-ttu-id="ca7eb-119">Özel denetim görünüm tarafından hangi veriler görüntülenir ve nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ca7eb-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="ca7eb-120">GroupBy (biçimi) için CustomItem için yeni satır öğesi</span><span class="sxs-lookup"><span data-stu-id="ca7eb-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="ca7eb-121">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="ca7eb-121">Optional element.</span></span><br /><br /> <span data-ttu-id="ca7eb-122">Boş bir satır denetimi görüntüye ekler.</span><span class="sxs-lookup"><span data-stu-id="ca7eb-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="ca7eb-123">GroupBy (biçimi) için CustomItem için metin öğesi</span><span class="sxs-lookup"><span data-stu-id="ca7eb-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="ca7eb-124">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="ca7eb-124">Optional element.</span></span><br /><br /> <span data-ttu-id="ca7eb-125">Ek metin denetimi tarafından görüntülenen verilere belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca7eb-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ca7eb-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca7eb-126">Parent Elements</span></span>

|<span data-ttu-id="ca7eb-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="ca7eb-127">Element</span></span>|<span data-ttu-id="ca7eb-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca7eb-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ca7eb-129">GroupBy (biçimi) için özel denetim için CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="ca7eb-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="ca7eb-130">Özel denetim görünüm tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca7eb-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ca7eb-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca7eb-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="ca7eb-132">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ca7eb-132">See Also</span></span>

[<span data-ttu-id="ca7eb-133">GroupBy (biçimi) için özel denetim için CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="ca7eb-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="ca7eb-134">GroupBy (biçimi) için CustomItem için ExpressionBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="ca7eb-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="ca7eb-135">GroupBy (biçimi) için CustomItem için çerçeve öğesi</span><span class="sxs-lookup"><span data-stu-id="ca7eb-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="ca7eb-136">GroupBy (biçimi) için CustomItem için yeni satır öğesi</span><span class="sxs-lookup"><span data-stu-id="ca7eb-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="ca7eb-137">GroupBy (biçimi) için CustomItem için metin öğesi</span><span class="sxs-lookup"><span data-stu-id="ca7eb-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="ca7eb-138">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="ca7eb-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
