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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066439"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="b1ae7-102">Yapılandırma Denetimleri için CustomEntry CustomItem Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="b1ae7-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="b1ae7-103">Hangi veri denetimi tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b1ae7-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="b1ae7-104">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b1ae7-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="b1ae7-105">Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) CustomItem öğesinin CustomEntry yapılandırması için denetimleri için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="b1ae7-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="b1ae7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1ae7-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b1ae7-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="b1ae7-107">Attributes and Elements</span></span>

<span data-ttu-id="b1ae7-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomItem` öğesi.</span><span class="sxs-lookup"><span data-stu-id="b1ae7-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="b1ae7-109">Daha fazla bilgi için açıklamalara bakın.</span><span class="sxs-lookup"><span data-stu-id="b1ae7-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="b1ae7-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b1ae7-110">Attributes</span></span>

<span data-ttu-id="b1ae7-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="b1ae7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b1ae7-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="b1ae7-112">Child Elements</span></span>

|<span data-ttu-id="b1ae7-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="b1ae7-113">Element</span></span>|<span data-ttu-id="b1ae7-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1ae7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b1ae7-115">İçin yapılandırma (biçimi) için denetimleri için CustomItem ExpressionBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="b1ae7-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="b1ae7-116">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="b1ae7-116">Optional element.</span></span><br /><br /> <span data-ttu-id="b1ae7-117">Denetimi tarafından görüntülenen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b1ae7-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="b1ae7-118">Çerçeve öğesi CustomItem yapılandırması (biçimi) için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="b1ae7-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="b1ae7-119">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="b1ae7-119">Optional element.</span></span><br /><br /> <span data-ttu-id="b1ae7-120">Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b1ae7-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="b1ae7-121">Yeni satır öğesi CustomItem yapılandırması (biçimi) için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="b1ae7-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="b1ae7-122">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="b1ae7-122">Optional element.</span></span><br /><br /> <span data-ttu-id="b1ae7-123">Boş bir satır denetimi görüntüye ekler.</span><span class="sxs-lookup"><span data-stu-id="b1ae7-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="b1ae7-124">Denetimler için yapılandırma (biçimi) için CustomItem için metin öğesi</span><span class="sxs-lookup"><span data-stu-id="b1ae7-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="b1ae7-125">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="b1ae7-125">Optional element.</span></span><br /><br /> <span data-ttu-id="b1ae7-126">Parantez veya parantez gibi bir metin denetimi görüntüye ekler.</span><span class="sxs-lookup"><span data-stu-id="b1ae7-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b1ae7-127">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="b1ae7-127">Parent Elements</span></span>

|<span data-ttu-id="b1ae7-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="b1ae7-128">Element</span></span>|<span data-ttu-id="b1ae7-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1ae7-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b1ae7-130">Yapılandırma (biçimi) için denetimler için özel denetim için CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="b1ae7-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="b1ae7-131">Denetim tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1ae7-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b1ae7-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1ae7-132">Remarks</span></span>

<span data-ttu-id="b1ae7-133">Alt öğeleri belirtirken `CustomItem` öğesi, aşağıdakileri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b1ae7-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="b1ae7-134">Alt öğeleri aşağıdaki sırayla eklenmelidir: `ExpressionBinding`, `NewLine`, `Text`, ve `Frame`.</span><span class="sxs-lookup"><span data-stu-id="b1ae7-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="b1ae7-135">Belirtebileceğiniz dizileri sayısı maksimum sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="b1ae7-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="b1ae7-136">Her sırada sayısı maksimum sınırı yoktur `ExpressionBinding` öğeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1ae7-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1ae7-137">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="b1ae7-137">See Also</span></span>

[<span data-ttu-id="b1ae7-138">İçin yapılandırma (biçimi) için denetimleri için CustomItem ExpressionBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="b1ae7-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="b1ae7-139">Çerçeve öğesi CustomItem yapılandırması (biçimi) için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="b1ae7-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="b1ae7-140">Yeni satır öğesi CustomItem yapılandırması (biçimi) için denetimleri için</span><span class="sxs-lookup"><span data-stu-id="b1ae7-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="b1ae7-141">Denetimler için yapılandırma (biçimi) için CustomItem için metin öğesi</span><span class="sxs-lookup"><span data-stu-id="b1ae7-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="b1ae7-142">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="b1ae7-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
