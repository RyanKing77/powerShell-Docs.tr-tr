---
title: CustomEntries öğesi görünümü (biçimi) için özel denetim için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850802"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="683a3-102">Görünüm CustomControl için CustomEntries Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="683a3-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="683a3-103">Özel denetim görünüm tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="683a3-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="683a3-104">Özel denetimin görünümü, bir veya daha fazla tanımları belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="683a3-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="683a3-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) özel denetim öğesi (biçimi) CustomEntries öğesi görünümü (biçimi) için özel denetim için</span><span class="sxs-lookup"><span data-stu-id="683a3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="683a3-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="683a3-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="683a3-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="683a3-107">Attributes and Elements</span></span>

<span data-ttu-id="683a3-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomControlEntries` öğesi.</span><span class="sxs-lookup"><span data-stu-id="683a3-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="683a3-109">Bir veya daha fazla alt öğeleri belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="683a3-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="683a3-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="683a3-110">Attributes</span></span>

<span data-ttu-id="683a3-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="683a3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="683a3-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="683a3-112">Child Elements</span></span>

|<span data-ttu-id="683a3-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="683a3-113">Element</span></span>|<span data-ttu-id="683a3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="683a3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="683a3-115">İçin görünümün (biçimi) CustomEntries CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="683a3-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="683a3-116">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="683a3-116">Required element.</span></span><br /><br /> <span data-ttu-id="683a3-117">Özel denetim görünüm tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="683a3-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="683a3-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="683a3-118">Parent Elements</span></span>

|<span data-ttu-id="683a3-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="683a3-119">Element</span></span>|<span data-ttu-id="683a3-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="683a3-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="683a3-121">Özel denetim öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="683a3-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="683a3-122">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="683a3-122">Required element.</span></span><br /><br /> <span data-ttu-id="683a3-123">Görünüm için bir özel denetim biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="683a3-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="683a3-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="683a3-124">Remarks</span></span>

<span data-ttu-id="683a3-125">Çoğu durumda, tek bir tanımlı yalnızca bir tanımı kontrolünde `CustomEntry` öğesi.</span><span class="sxs-lookup"><span data-stu-id="683a3-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="683a3-126">Ancak farklı .NET nesneleri görüntülemek için aynı denetimi kullanmak istiyorsanız birden çok tanım olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="683a3-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="683a3-127">Bu gibi durumlarda, tanımladığınız bir `CustomEntry` her nesne veya nesneler için öğesi.</span><span class="sxs-lookup"><span data-stu-id="683a3-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="683a3-128">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="683a3-128">See Also</span></span>

[<span data-ttu-id="683a3-129">Özel denetim öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="683a3-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="683a3-130">İçin görünümün (biçimi) CustomEntries CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="683a3-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="683a3-131">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="683a3-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
