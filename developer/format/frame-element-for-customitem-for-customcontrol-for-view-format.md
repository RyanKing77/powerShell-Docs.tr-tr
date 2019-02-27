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
ms.openlocfilehash: a7ee550527ec1cb00b4ed83478992c7ab54dbdb6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850809"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="143d1-102">Görünüm CustomControl için CustomItem Çerçeve Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="143d1-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="143d1-103">Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="143d1-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="143d1-104">Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="143d1-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="143d1-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) CustomItem öğesinin CustomEntries görünümü (biçimi) CustomEntry öğesinin özel denetim için CustomEntry CustomItem Görünüm (biçimi) için özel denetim için çerçeve öğesinin CutomControlView (biçimi)</span><span class="sxs-lookup"><span data-stu-id="143d1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CutomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="143d1-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="143d1-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="143d1-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="143d1-107">Attributes and Elements</span></span>

<span data-ttu-id="143d1-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `Frame` öğesi.</span><span class="sxs-lookup"><span data-stu-id="143d1-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="143d1-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="143d1-109">Attributes</span></span>

<span data-ttu-id="143d1-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="143d1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="143d1-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="143d1-111">Child Elements</span></span>

|<span data-ttu-id="143d1-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="143d1-112">Element</span></span>|<span data-ttu-id="143d1-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="143d1-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="143d1-114">Gerekli öğe</span><span class="sxs-lookup"><span data-stu-id="143d1-114">Required Element</span></span>|
|[<span data-ttu-id="143d1-115">FirstLineHanging öğesi</span><span class="sxs-lookup"><span data-stu-id="143d1-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="143d1-116">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="143d1-116">Optional element.</span></span><br /><br /> <span data-ttu-id="143d1-117">Verilerin ilk satırı, sola kaydırılacak karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="143d1-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="143d1-118">FirstLineIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="143d1-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="143d1-119">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="143d1-119">Optional element.</span></span><br /><br /> <span data-ttu-id="143d1-120">İlk veri satırını sağa kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="143d1-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="143d1-121">LeftIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="143d1-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="143d1-122">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="143d1-122">Optional element.</span></span><br /><br /> <span data-ttu-id="143d1-123">Sol kenar boşluğu uzağa veri kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="143d1-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="143d1-124">RightIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="143d1-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="143d1-125">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="143d1-125">Optional element.</span></span><br /><br /> <span data-ttu-id="143d1-126">Sağ kenar boşluğu uzağa veri kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="143d1-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="143d1-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="143d1-127">Parent Elements</span></span>

|<span data-ttu-id="143d1-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="143d1-128">Element</span></span>|<span data-ttu-id="143d1-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="143d1-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="143d1-130">İçin görünümün (biçimi) CustomEntry CustomItem öğesi</span><span class="sxs-lookup"><span data-stu-id="143d1-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="143d1-131">Hangi veri denetimi tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="143d1-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="143d1-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="143d1-132">Remarks</span></span>

<span data-ttu-id="143d1-133">Belirtemezsiniz [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) ve [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) aynı öğeleri `Frame` öğesi.</span><span class="sxs-lookup"><span data-stu-id="143d1-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="143d1-134">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="143d1-134">See Also</span></span>

[<span data-ttu-id="143d1-135">FirstLineHanging öğesi</span><span class="sxs-lookup"><span data-stu-id="143d1-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="143d1-136">FirstLineIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="143d1-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="143d1-137">LeftIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="143d1-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="143d1-138">RightIndent öğesi</span><span class="sxs-lookup"><span data-stu-id="143d1-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="143d1-139">İçin görünümün (biçimi) CustomEntry CustomItem öğesi</span><span class="sxs-lookup"><span data-stu-id="143d1-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="143d1-140">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="143d1-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
