---
title: Çerçeve öğesi için CustomItem GroupBy (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846007"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="e83d6-102">GroupBy CustomItem için Çerçeve Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="e83d6-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="e83d6-103">Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e83d6-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="e83d6-104">Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e83d6-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e83d6-105">GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) CustomEntry öğesinin özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi GroupBy (biçimi) CustomItem öğesinin CustomEntry GroupBy (biçimi) çerçeve öğesinin CustomItem GroupBy (biçimi) için özel denetim</span><span class="sxs-lookup"><span data-stu-id="e83d6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e83d6-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e83d6-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e83d6-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e83d6-107">Attributes and Elements</span></span>

<span data-ttu-id="e83d6-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `Frame` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e83d6-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e83d6-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e83d6-109">Attributes</span></span>

<span data-ttu-id="e83d6-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="e83d6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e83d6-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e83d6-111">Child Elements</span></span>

|<span data-ttu-id="e83d6-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="e83d6-112">Element</span></span>|<span data-ttu-id="e83d6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e83d6-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="e83d6-114">Gerekli öğe</span><span class="sxs-lookup"><span data-stu-id="e83d6-114">Required Element</span></span>|
|[<span data-ttu-id="e83d6-115">GroupBy (biçimi) için bir çerçeve için FirstLineHanging öğesi</span><span class="sxs-lookup"><span data-stu-id="e83d6-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="e83d6-116">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="e83d6-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e83d6-117">Verilerin ilk satırı, sola kaydırılacak karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e83d6-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="e83d6-118">GroupBy (biçimi) için bir çerçeve için FirstLineIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="e83d6-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="e83d6-119">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="e83d6-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e83d6-120">İlk veri satırını sağa kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e83d6-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="e83d6-121">GroupBy (biçimi) için bir çerçeve için LeftIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="e83d6-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="e83d6-122">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="e83d6-122">Optional element.</span></span><br /><br /> <span data-ttu-id="e83d6-123">Sol kenar boşluğu uzağa veri kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e83d6-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="e83d6-124">[GroupBy (biçimi) için bir çerçeve için RightIndent öğesi](./rightindent-element-for-frame-for-groupby-format.md)RightIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="e83d6-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="e83d6-125">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="e83d6-125">Optional element.</span></span><br /><br /> <span data-ttu-id="e83d6-126">Sağ kenar boşluğu uzağa veri kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e83d6-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e83d6-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e83d6-127">Parent Elements</span></span>

|<span data-ttu-id="e83d6-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="e83d6-128">Element</span></span>|<span data-ttu-id="e83d6-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e83d6-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e83d6-130">GroupBy (biçimi) için CustomEntry için CustomItem öğesi</span><span class="sxs-lookup"><span data-stu-id="e83d6-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="e83d6-131">Hangi veri denetimi tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e83d6-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e83d6-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e83d6-132">Remarks</span></span>

<span data-ttu-id="e83d6-133">Belirtemezsiniz [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) ve [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) aynı öğeleri `Frame` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e83d6-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="e83d6-134">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e83d6-134">See Also</span></span>

[<span data-ttu-id="e83d6-135">GroupBy (biçimi) için bir çerçeve için FirstLineHanging öğesi</span><span class="sxs-lookup"><span data-stu-id="e83d6-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="e83d6-136">GroupBy (biçimi) için bir çerçeve için FirstLineIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="e83d6-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="e83d6-137">GroupBy (biçimi) için bir çerçeve için LeftIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="e83d6-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="e83d6-138">GroupBy (biçimi) için bir çerçeve için RightIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="e83d6-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="e83d6-139">GroupBy (biçimi) için CustomEntry için CustomItem öğesi</span><span class="sxs-lookup"><span data-stu-id="e83d6-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="e83d6-140">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="e83d6-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
