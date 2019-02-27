---
title: CustomItem öğesi görünümü (biçimi) için özel denetim için CustomEntry için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846945"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="3da3d-102">Görünüm CustomControl için CustomEntry CustomItem Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="3da3d-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="3da3d-103">Özel denetim görünüm tarafından hangi veriler görüntülenir ve nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3da3d-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="3da3d-104">Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3da3d-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="3da3d-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomItem öğesinin CustomEntries görünümü (biçimi) CustomEntry öğesinin özel denetim için CustomEntry görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="3da3d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3da3d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3da3d-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3da3d-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3da3d-107">Attributes and Elements</span></span>

<span data-ttu-id="3da3d-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomItem` öğesi.</span><span class="sxs-lookup"><span data-stu-id="3da3d-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3da3d-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3da3d-109">Attributes</span></span>

<span data-ttu-id="3da3d-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="3da3d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3da3d-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3da3d-111">Child Elements</span></span>

|<span data-ttu-id="3da3d-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="3da3d-112">Element</span></span>|<span data-ttu-id="3da3d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3da3d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3da3d-114">ExpressionBinding öğesi görünümü (biçimi) için özel denetim için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="3da3d-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="3da3d-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="3da3d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3da3d-116">Denetimi tarafından görüntülenen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3da3d-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="3da3d-117">Çerçeve öğesi görünümü (biçimi) için özel denetim için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="3da3d-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="3da3d-118">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="3da3d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="3da3d-119">Özel denetim görünüm tarafından hangi veriler görüntülenir ve nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3da3d-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="3da3d-120">Yeni satır öğesi görünümü (biçimi) için özel denetim için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="3da3d-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="3da3d-121">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="3da3d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="3da3d-122">Boş bir satır denetimi görüntüye ekler.</span><span class="sxs-lookup"><span data-stu-id="3da3d-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="3da3d-123">Metin öğesi görünümü (biçimi) için özel denetim için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="3da3d-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="3da3d-124">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="3da3d-124">Optional element.</span></span><br /><br /> <span data-ttu-id="3da3d-125">Ek metin denetimi tarafından görüntülenen verilere belirtir.</span><span class="sxs-lookup"><span data-stu-id="3da3d-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3da3d-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3da3d-126">Parent Elements</span></span>

|<span data-ttu-id="3da3d-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="3da3d-127">Element</span></span>|<span data-ttu-id="3da3d-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3da3d-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3da3d-129">CustomEntry öğesi görünümü (biçimi) için özel denetim için CustomEntries için</span><span class="sxs-lookup"><span data-stu-id="3da3d-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="3da3d-130">Özel denetim görünüm tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3da3d-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3da3d-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3da3d-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="3da3d-132">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="3da3d-132">See Also</span></span>

[<span data-ttu-id="3da3d-133">İçin görünümün (biçimi) CustomEntries CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="3da3d-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3da3d-134">ExpressionBinding öğesi görünümü (biçimi) için özel denetim için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="3da3d-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3da3d-135">Çerçeve öğesi görünümü (biçimi) için özel denetim için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="3da3d-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3da3d-136">Yeni satır öğesi görünümü (biçimi) için özel denetim için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="3da3d-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3da3d-137">Metin öğesi görünümü (biçimi) için özel denetim için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="3da3d-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="3da3d-138">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="3da3d-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
