---
title: Çerçeve öğesi için CustomItem denetimleri için görüntüleme (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849486"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="f9d35-102">Görünüm Denetimleri için CustomItem Çerçeve Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="f9d35-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="f9d35-103">Verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f9d35-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="f9d35-104">Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f9d35-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="f9d35-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) denetimleri (biçimi) öğesi denetim öğesi denetimi için CustomEntries öğesi görünümü (biçimi) için denetimleri için özel denetim öğesi görünümü (biçimi) için denetimleri için Özel denetim CustomEntry öğesinin CustomEntries CustomEntry CustomItem Görünüm (biçimi) için denetimleri için görüntüleme (biçimi) çerçeve öğesinin denetimleri için görüntüleme (biçimi) CustomItem öğesinin denetimleri için görüntüleme (biçimi)</span><span class="sxs-lookup"><span data-stu-id="f9d35-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f9d35-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9d35-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f9d35-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9d35-107">Attributes and Elements</span></span>

<span data-ttu-id="f9d35-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `Frame` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f9d35-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f9d35-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f9d35-109">Attributes</span></span>

<span data-ttu-id="f9d35-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="f9d35-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f9d35-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9d35-111">Child Elements</span></span>

|<span data-ttu-id="f9d35-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="f9d35-112">Element</span></span>|<span data-ttu-id="f9d35-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9d35-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="f9d35-114">Gerekli öğe</span><span class="sxs-lookup"><span data-stu-id="f9d35-114">Required Element</span></span>|
|[<span data-ttu-id="f9d35-115">FirstLineHanging öğesi çerçevesinin denetimlerinin görünümün (biçimi)</span><span class="sxs-lookup"><span data-stu-id="f9d35-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="f9d35-116">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="f9d35-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f9d35-117">İlk satır, sola kaydırılacak karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9d35-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="f9d35-118">FirstLineIndent öğesi çerçevesinin denetimlerinin görünümün (biçimi)</span><span class="sxs-lookup"><span data-stu-id="f9d35-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="f9d35-119">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="f9d35-119">Optional element.</span></span><br /><br /> <span data-ttu-id="f9d35-120">İlk satır, sağa kaydırılacak karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9d35-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="f9d35-121">LeftIndent öğesi çerçevesinin denetimlerinin görünümün (biçimi)</span><span class="sxs-lookup"><span data-stu-id="f9d35-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="f9d35-122">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="f9d35-122">Optional element.</span></span><br /><br /> <span data-ttu-id="f9d35-123">Sol kenar boşluğu uzağa veri kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9d35-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="f9d35-124">RightIndent öğesi çerçevesinin denetimlerinin görünümün (biçimi)</span><span class="sxs-lookup"><span data-stu-id="f9d35-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="f9d35-125">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="f9d35-125">Optional element.</span></span><br /><br /> <span data-ttu-id="f9d35-126">Sağ kenar boşluğu uzağa veri kaydırılacağı uzaklık karakterlerinin kaçının tutulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9d35-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f9d35-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9d35-127">Parent Elements</span></span>

|<span data-ttu-id="f9d35-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="f9d35-128">Element</span></span>|<span data-ttu-id="f9d35-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9d35-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f9d35-130">CustomItem öğesi görünümü (biçimi) için denetimleri için CustomEntry için</span><span class="sxs-lookup"><span data-stu-id="f9d35-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="f9d35-131">Hangi veri denetimi tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f9d35-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f9d35-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9d35-132">Remarks</span></span>

<span data-ttu-id="f9d35-133">Belirtemezsiniz [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) ve [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) aynı öğeleri `Frame` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f9d35-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9d35-134">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="f9d35-134">See Also</span></span>

[<span data-ttu-id="f9d35-135">FirstLineHanging öğesi çerçevesinin denetimlerinin görünümün (biçimi)</span><span class="sxs-lookup"><span data-stu-id="f9d35-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="f9d35-136">FirstLineIndent öğesi çerçevesinin denetimlerinin görünümün (biçimi)</span><span class="sxs-lookup"><span data-stu-id="f9d35-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="f9d35-137">LeftIndent öğesi çerçevesinin denetimlerinin görünümün (biçimi)</span><span class="sxs-lookup"><span data-stu-id="f9d35-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="f9d35-138">RightIndent öğesi çerçevesinin denetimlerinin görünümün (biçimi)</span><span class="sxs-lookup"><span data-stu-id="f9d35-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="f9d35-139">CustomItem öğesi görünümü (biçimi) için denetimleri için CustomEntry için</span><span class="sxs-lookup"><span data-stu-id="f9d35-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="f9d35-140">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="f9d35-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
