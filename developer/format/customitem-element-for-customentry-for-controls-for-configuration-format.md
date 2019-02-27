---
title: İçin yapılandırma (biçimi) için denetimleri için CustomEntry CustomItem öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851670"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="e5da4-102">Yapılandırma Denetimleri için CustomEntry CustomItem Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="e5da4-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e5da4-103">Hangi veri denetimi tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e5da4-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="e5da4-104">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5da4-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e5da4-105">Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) CustomItem öğesinin CustomEntry yapılandırması için denetimleri için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="e5da4-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="e5da4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5da4-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5da4-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5da4-107">Attributes and Elements</span></span>

<span data-ttu-id="e5da4-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomItem` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e5da4-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="e5da4-109">Daha fazla bilgi için açıklamalara bakın.</span><span class="sxs-lookup"><span data-stu-id="e5da4-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5da4-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e5da4-110">Attributes</span></span>

<span data-ttu-id="e5da4-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="e5da4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5da4-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5da4-112">Child Elements</span></span>

|<span data-ttu-id="e5da4-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="e5da4-113">Element</span></span>|<span data-ttu-id="e5da4-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5da4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5da4-115">İçin yapılandırma (biçimi) için denetimleri için CustomItem ExpressionBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="e5da4-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="e5da4-116">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="e5da4-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e5da4-117">Denetimi tarafından görüntülenen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e5da4-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="e5da4-118">Çerçeve öğesi CustomItem yapılandırması (biçimi) için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="e5da4-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="e5da4-119">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="e5da4-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e5da4-120">Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e5da4-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="e5da4-121">Yeni satır öğesi CustomItem yapılandırması (biçimi) için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="e5da4-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="e5da4-122">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="e5da4-122">Optional element.</span></span><br /><br /> <span data-ttu-id="e5da4-123">Boş bir satır denetimi görüntüye ekler.</span><span class="sxs-lookup"><span data-stu-id="e5da4-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="e5da4-124">Denetimler için yapılandırma (biçimi) için CustomItem için metin öğesi</span><span class="sxs-lookup"><span data-stu-id="e5da4-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="e5da4-125">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="e5da4-125">Optional element.</span></span><br /><br /> <span data-ttu-id="e5da4-126">Parantez veya parantez gibi bir metin denetimi görüntüye ekler.</span><span class="sxs-lookup"><span data-stu-id="e5da4-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e5da4-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5da4-127">Parent Elements</span></span>

|<span data-ttu-id="e5da4-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="e5da4-128">Element</span></span>|<span data-ttu-id="e5da4-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5da4-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5da4-130">Yapılandırma (biçimi) için denetimler için özel denetim için CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="e5da4-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="e5da4-131">Denetim tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5da4-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5da4-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5da4-132">Remarks</span></span>

<span data-ttu-id="e5da4-133">Alt öğeleri belirtirken `CustomItem` öğesi, aşağıdakileri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e5da4-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="e5da4-134">Alt öğeleri aşağıdaki sırayla eklenmelidir: `ExpressionBinding`, `NewLine`, `Text`, ve `Frame`.</span><span class="sxs-lookup"><span data-stu-id="e5da4-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="e5da4-135">Belirtebileceğiniz dizileri sayısı maksimum sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="e5da4-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="e5da4-136">Her sırada sayısı maksimum sınırı yoktur `ExpressionBinding` öğeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5da4-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5da4-137">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e5da4-137">See Also</span></span>

[<span data-ttu-id="e5da4-138">İçin yapılandırma (biçimi) için denetimleri için CustomItem ExpressionBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="e5da4-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="e5da4-139">Çerçeve öğesi CustomItem yapılandırması (biçimi) için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="e5da4-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="e5da4-140">Yeni satır öğesi CustomItem yapılandırması (biçimi) için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="e5da4-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="e5da4-141">Denetimler için yapılandırma (biçimi) için CustomItem için metin öğesi</span><span class="sxs-lookup"><span data-stu-id="e5da4-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="e5da4-142">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="e5da4-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
