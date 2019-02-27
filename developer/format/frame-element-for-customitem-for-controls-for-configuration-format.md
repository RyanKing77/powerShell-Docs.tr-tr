---
title: Çerçeve öğesi için CustomItem denetimleri için yapılandırma (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851698"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="0daf5-102">Yapılandırma Denetimleri için CustomItem Çerçeve Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="0daf5-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0daf5-103">Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0daf5-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="0daf5-104">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0daf5-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="0daf5-105">Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Yapılandırma (biçimi) CustomItem öğesinin CustomEntry CustomItem denetimleri için yapılandırma (biçimi) için yapılandırma çerçeve öğesinin denetimleri için denetimler için özel denetim için biçimlendirme) CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="0daf5-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0daf5-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0daf5-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0daf5-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0daf5-107">Attributes and Elements</span></span>

<span data-ttu-id="0daf5-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `Frame` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0daf5-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0daf5-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0daf5-109">Attributes</span></span>

<span data-ttu-id="0daf5-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="0daf5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0daf5-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0daf5-111">Child Elements</span></span>

|<span data-ttu-id="0daf5-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="0daf5-112">Element</span></span>|<span data-ttu-id="0daf5-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0daf5-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="0daf5-114">Gerekli öğe</span><span class="sxs-lookup"><span data-stu-id="0daf5-114">Required Element</span></span>|
|[<span data-ttu-id="0daf5-115">Denetimler için yapılandırma (biçimi) için bir çerçeve için FirstLineHanging öğesi</span><span class="sxs-lookup"><span data-stu-id="0daf5-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="0daf5-116">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="0daf5-116">Optional element.</span></span><br /><br /> <span data-ttu-id="0daf5-117">Verilerin ilk satırı, sola kaydırılacak karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0daf5-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="0daf5-118">Denetimler için yapılandırma (biçimi) için bir çerçeve için FirstLineIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="0daf5-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="0daf5-119">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="0daf5-119">Optional element.</span></span><br /><br /> <span data-ttu-id="0daf5-120">İlk veri satırını sağa kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0daf5-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="0daf5-121">Denetimler için yapılandırma (biçimi) için bir çerçeve için LeftIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="0daf5-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="0daf5-122">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="0daf5-122">Optional element.</span></span><br /><br /> <span data-ttu-id="0daf5-123">Sol kenar boşluğu uzağa veri kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0daf5-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="0daf5-124">Denetimler için yapılandırma (biçimi) için bir çerçeve için RightIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="0daf5-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="0daf5-125">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="0daf5-125">Optional element.</span></span><br /><br /> <span data-ttu-id="0daf5-126">Sağ kenar boşluğu uzağa veri kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0daf5-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0daf5-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0daf5-127">Parent Elements</span></span>

|<span data-ttu-id="0daf5-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="0daf5-128">Element</span></span>|<span data-ttu-id="0daf5-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0daf5-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0daf5-130">Yapılandırma için denetimleri için CustomEntry için CustomItem öğesi</span><span class="sxs-lookup"><span data-stu-id="0daf5-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="0daf5-131">Hangi veri denetimi tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0daf5-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0daf5-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0daf5-132">Remarks</span></span>

<span data-ttu-id="0daf5-133">Belirtemezsiniz [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) ve [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) aynı öğeleri `Frame` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0daf5-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="0daf5-134">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="0daf5-134">See Also</span></span>

[<span data-ttu-id="0daf5-135">Denetimler için yapılandırma (biçimi) için bir çerçeve için FirstLineHanging öğesi</span><span class="sxs-lookup"><span data-stu-id="0daf5-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="0daf5-136">Denetimler için yapılandırma (biçimi) için bir çerçeve için FirstLineIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="0daf5-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="0daf5-137">Denetimler için yapılandırma (biçimi) için bir çerçeve için LeftIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="0daf5-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="0daf5-138">Denetimler için yapılandırma (biçimi) için bir çerçeve için RightIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="0daf5-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="0daf5-139">Yapılandırma için denetimleri için CustomEntry için CustomItem öğesi</span><span class="sxs-lookup"><span data-stu-id="0daf5-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="0daf5-140">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="0daf5-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
