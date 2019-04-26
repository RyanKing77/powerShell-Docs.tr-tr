---
title: Çerçeve öğesi CustomItem için özel denetim için View (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065589"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="0ffd8-102">Görünüm CustomControl için CustomItem Çerçeve Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="0ffd8-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="0ffd8-103">Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0ffd8-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="0ffd8-104">Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0ffd8-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="0ffd8-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomItem öğesinin CustomEntries görünümü (biçimi) CustomEntry öğesinin özel denetim için CustomEntry CustomItem Görünüm (biçimi) için özel denetim için çerçeve öğesinin CustomControlView (biçimi)</span><span class="sxs-lookup"><span data-stu-id="0ffd8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0ffd8-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ffd8-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0ffd8-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="0ffd8-107">Attributes and Elements</span></span>

<span data-ttu-id="0ffd8-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `Frame` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0ffd8-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0ffd8-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0ffd8-109">Attributes</span></span>

<span data-ttu-id="0ffd8-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="0ffd8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0ffd8-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="0ffd8-111">Child Elements</span></span>

|<span data-ttu-id="0ffd8-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="0ffd8-112">Element</span></span>|<span data-ttu-id="0ffd8-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ffd8-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="0ffd8-114">Gerekli öğe</span><span class="sxs-lookup"><span data-stu-id="0ffd8-114">Required Element</span></span>|
|[<span data-ttu-id="0ffd8-115">FirstLineHanging öğesi</span><span class="sxs-lookup"><span data-stu-id="0ffd8-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="0ffd8-116">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="0ffd8-116">Optional element.</span></span><br /><br /> <span data-ttu-id="0ffd8-117">Verilerin ilk satırı, sola kaydırılacak karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ffd8-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="0ffd8-118">FirstLineIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="0ffd8-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="0ffd8-119">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="0ffd8-119">Optional element.</span></span><br /><br /> <span data-ttu-id="0ffd8-120">İlk veri satırını sağa kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ffd8-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="0ffd8-121">LeftIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="0ffd8-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="0ffd8-122">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="0ffd8-122">Optional element.</span></span><br /><br /> <span data-ttu-id="0ffd8-123">Sol kenar boşluğu uzağa veri kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ffd8-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="0ffd8-124">RightIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="0ffd8-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="0ffd8-125">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="0ffd8-125">Optional element.</span></span><br /><br /> <span data-ttu-id="0ffd8-126">Sağ kenar boşluğu uzağa veri kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ffd8-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0ffd8-127">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="0ffd8-127">Parent Elements</span></span>

|<span data-ttu-id="0ffd8-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="0ffd8-128">Element</span></span>|<span data-ttu-id="0ffd8-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ffd8-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0ffd8-130">İçin görünümün (biçimi) CustomEntry CustomItem öğesi</span><span class="sxs-lookup"><span data-stu-id="0ffd8-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="0ffd8-131">Hangi veri denetimi tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0ffd8-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0ffd8-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ffd8-132">Remarks</span></span>

<span data-ttu-id="0ffd8-133">Belirtemezsiniz [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) ve [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) aynı öğeleri `Frame` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0ffd8-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ffd8-134">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="0ffd8-134">See Also</span></span>

[<span data-ttu-id="0ffd8-135">FirstLineHanging öğesi</span><span class="sxs-lookup"><span data-stu-id="0ffd8-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0ffd8-136">FirstLineIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="0ffd8-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0ffd8-137">LeftIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="0ffd8-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0ffd8-138">RightIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="0ffd8-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0ffd8-139">İçin görünümün (biçimi) CustomEntry CustomItem öğesi</span><span class="sxs-lookup"><span data-stu-id="0ffd8-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0ffd8-140">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="0ffd8-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
