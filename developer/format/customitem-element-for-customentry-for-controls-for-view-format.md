---
title: CustomItem öğesi görünümü (biçimi) için denetimleri için CustomEntry için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066391"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="1c845-102">Görünüm için Denetimler için CustomEntry için CustomItem Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="1c845-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="1c845-103">Hangi veri denetimi tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1c845-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="1c845-104">Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1c845-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="1c845-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) denetimleri (biçimi) öğesi denetim öğesi denetimi için CustomEntries öğesi görünümü (biçimi) için denetimleri için özel denetim öğesi görünümü (biçimi) için denetimleri için Özel denetim CustomEntry öğesinin CustomEntries CustomEntry Görünüm (biçimi) için denetimleri için görüntüleme (biçimi) CustomItem öğesinin denetimleri için görüntüleme (biçimi)</span><span class="sxs-lookup"><span data-stu-id="1c845-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1c845-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c845-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1c845-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="1c845-107">Attributes and Elements</span></span>

<span data-ttu-id="1c845-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomItem` öğesi.</span><span class="sxs-lookup"><span data-stu-id="1c845-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="1c845-109">Daha fazla bilgi için açıklamalara bakın.</span><span class="sxs-lookup"><span data-stu-id="1c845-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="1c845-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1c845-110">Attributes</span></span>

<span data-ttu-id="1c845-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="1c845-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1c845-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="1c845-112">Child Elements</span></span>

|<span data-ttu-id="1c845-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="1c845-113">Element</span></span>|<span data-ttu-id="1c845-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c845-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1c845-115">ExpressionBinding öğesi görünümü (biçimi) için denetimleri için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="1c845-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="1c845-116">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="1c845-116">Optional element.</span></span><br /><br /> <span data-ttu-id="1c845-117">Denetimi tarafından görüntülenen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1c845-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="1c845-118">Çerçeve öğesi görünümü (biçimi) için denetimleri için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="1c845-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="1c845-119">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="1c845-119">Optional element.</span></span><br /><br /> <span data-ttu-id="1c845-120">Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1c845-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="1c845-121">Yeni satır öğesi görünümü (biçimi) için denetimleri için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="1c845-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="1c845-122">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="1c845-122">Optional element.</span></span><br /><br /> <span data-ttu-id="1c845-123">Boş bir satır denetimi görüntüye ekler.</span><span class="sxs-lookup"><span data-stu-id="1c845-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="1c845-124">Metin öğesi görünümü (biçimi) için denetimleri için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="1c845-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="1c845-125">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="1c845-125">Optional element.</span></span><br /><br /> <span data-ttu-id="1c845-126">Parantez veya parantez gibi bir metin denetimi görüntüye ekler.</span><span class="sxs-lookup"><span data-stu-id="1c845-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1c845-127">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="1c845-127">Parent Elements</span></span>

|<span data-ttu-id="1c845-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="1c845-128">Element</span></span>|<span data-ttu-id="1c845-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c845-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1c845-130">CustomEntry öğesi görünümü (biçimi) için denetimleri için CustomEntries için</span><span class="sxs-lookup"><span data-stu-id="1c845-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="1c845-131">Denetim tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c845-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1c845-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c845-132">Remarks</span></span>

<span data-ttu-id="1c845-133">Alt öğeleri belirtirken `CustomItem` öğesi, aşağıdakileri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="1c845-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="1c845-134">Alt öğeleri aşağıdaki sırayla eklenmelidir: `ExpressionBinding`, `NewLine`, `Text`, ve `Frame`.</span><span class="sxs-lookup"><span data-stu-id="1c845-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="1c845-135">Belirtebileceğiniz dizileri sayısı maksimum sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="1c845-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="1c845-136">Her sırada sayısı maksimum sınırı yoktur `ExpressionBinding` öğeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c845-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c845-137">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="1c845-137">See Also</span></span>

[<span data-ttu-id="1c845-138">ExpressionBinding öğesi görünümü (biçimi) için denetimleri için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="1c845-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="1c845-139">Çerçeve öğesi görünümü (biçimi) için denetimleri için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="1c845-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="1c845-140">Yeni satır öğesi görünümü (biçimi) için denetimleri için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="1c845-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="1c845-141">Metin öğesi görünümü (biçimi) için denetimleri için CustomItem için</span><span class="sxs-lookup"><span data-stu-id="1c845-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="1c845-142">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="1c845-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
