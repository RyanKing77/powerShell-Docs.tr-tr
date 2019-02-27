---
title: GroupBy (biçimi) için özel denetim için CustomEntries öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845188"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="3bb4e-102">GroupBy CustomControl için CustomEntries Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="3bb4e-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="3bb4e-103">Denetim için tanımları sağlar.</span><span class="sxs-lookup"><span data-stu-id="3bb4e-103">Provides the definitions for the control.</span></span> <span data-ttu-id="3bb4e-104">Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3bb4e-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="3bb4e-105">GroupBy (biçimi) CustomEntries öğesinin GroupBy (biçimi) için özel denetim özel denetim öğesi görünümü (biçimi) için yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) GroupBy öğesi</span><span class="sxs-lookup"><span data-stu-id="3bb4e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3bb4e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3bb4e-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3bb4e-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3bb4e-107">Attributes and Elements</span></span>

<span data-ttu-id="3bb4e-108">Aşağıdaki bölümlerde, öznitelikler, alt ve üst öğeleri açıklayan `CustomEntries` öğesi.</span><span class="sxs-lookup"><span data-stu-id="3bb4e-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="3bb4e-109">Hiçbir belirtilebilir alt öğe sayısı üst sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="3bb4e-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="3bb4e-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3bb4e-110">Attributes</span></span>

<span data-ttu-id="3bb4e-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="3bb4e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3bb4e-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3bb4e-112">Child Elements</span></span>

|<span data-ttu-id="3bb4e-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="3bb4e-113">Element</span></span>|<span data-ttu-id="3bb4e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3bb4e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3bb4e-115">GroupBy (biçimi) için özel denetim için CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="3bb4e-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="3bb4e-116">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="3bb4e-116">Required element.</span></span><br /><br /> <span data-ttu-id="3bb4e-117">Denetim tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3bb4e-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3bb4e-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3bb4e-118">Parent Elements</span></span>

|<span data-ttu-id="3bb4e-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="3bb4e-119">Element</span></span>|<span data-ttu-id="3bb4e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3bb4e-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3bb4e-121">GroupBy (biçimi) için özel denetim öğesi</span><span class="sxs-lookup"><span data-stu-id="3bb4e-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="3bb4e-122">Yeni grubu gösteren özel bir denetimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3bb4e-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3bb4e-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3bb4e-123">Remarks</span></span>

<span data-ttu-id="3bb4e-124">Çoğu durumda, tek bir belirtilen sadece bir tanım kontrolünde `CustomEntry` öğesi.</span><span class="sxs-lookup"><span data-stu-id="3bb4e-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="3bb4e-125">Ancak, farklı gruplarını görüntülemek için aynı denetimi kullanmak istiyorsanız birden çok tanım sağlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="3bb4e-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="3bb4e-126">Bu gibi durumlarda, tanımladığınız bir `CustomEntry` bir grup için öğesi.</span><span class="sxs-lookup"><span data-stu-id="3bb4e-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="3bb4e-127">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="3bb4e-127">See Also</span></span>

[<span data-ttu-id="3bb4e-128">CustomEntry öğesi görünümü (biçimi) için denetimleri için CustomEntries için</span><span class="sxs-lookup"><span data-stu-id="3bb4e-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="3bb4e-129">GroupBy (biçimi) için özel denetim öğesi</span><span class="sxs-lookup"><span data-stu-id="3bb4e-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="3bb4e-130">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="3bb4e-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
