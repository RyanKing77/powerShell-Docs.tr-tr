---
title: Yapılandırma (biçimi) için denetimler için özel denetim için CustomEntries öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066609"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="aff4e-102">Yapılandırma Denetimleri için CustomControl CustomEntries Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="aff4e-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="aff4e-103">Tanımlarını bir ortak denetimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="aff4e-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="aff4e-104">Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aff4e-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="aff4e-105">Yapılandırma öğesi (biçimi) denetimleri öğesinin (biçimi) yapılandırma denetimi için yapılandırma (biçimi) özel denetim öğesi denetimi için yapılandırma (biçimi) CustomEntries öğesi özel denetim için yapılandırma (denetimleri için Biçimi)</span><span class="sxs-lookup"><span data-stu-id="aff4e-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aff4e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aff4e-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="aff4e-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="aff4e-107">Attributes and Elements</span></span>

<span data-ttu-id="aff4e-108">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `CustomEntries` öğesi.</span><span class="sxs-lookup"><span data-stu-id="aff4e-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="aff4e-109">Bir veya daha fazla alt öğeleri belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="aff4e-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="aff4e-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aff4e-110">Attributes</span></span>

<span data-ttu-id="aff4e-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="aff4e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aff4e-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="aff4e-112">Child Elements</span></span>

|<span data-ttu-id="aff4e-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="aff4e-113">Element</span></span>|<span data-ttu-id="aff4e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aff4e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aff4e-115">Yapılandırma (biçimi) için denetimler için özel denetim için CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="aff4e-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="aff4e-116">Bir ortak denetimi tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="aff4e-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="aff4e-117">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="aff4e-117">Parent Elements</span></span>

|<span data-ttu-id="aff4e-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="aff4e-118">Element</span></span>|<span data-ttu-id="aff4e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aff4e-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aff4e-120">Özel denetim öğesi denetimi için yapılandırma (biçimi)</span><span class="sxs-lookup"><span data-stu-id="aff4e-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="aff4e-121">Bir ortak denetimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aff4e-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="aff4e-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aff4e-122">Remarks</span></span>

<span data-ttu-id="aff4e-123">Çoğu durumda, tek bir tanımlı yalnızca bir tanımı kontrolünde `CustomEntry` öğesi.</span><span class="sxs-lookup"><span data-stu-id="aff4e-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="aff4e-124">Ancak farklı .NET nesneleri görüntülemek için aynı denetimi kullanmak istiyorsanız birden çok tanım olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="aff4e-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="aff4e-125">Bu gibi durumlarda, tanımladığınız bir `CustomEntry` her nesne veya nesneler için öğesi.</span><span class="sxs-lookup"><span data-stu-id="aff4e-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="aff4e-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="aff4e-126">See Also</span></span>

[<span data-ttu-id="aff4e-127">Özel denetim öğesi denetimi için yapılandırma (biçimi)</span><span class="sxs-lookup"><span data-stu-id="aff4e-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="aff4e-128">Yapılandırma (biçimi) için denetimler için özel denetim için CustomEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="aff4e-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="aff4e-129">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="aff4e-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
