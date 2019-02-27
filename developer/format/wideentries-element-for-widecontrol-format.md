---
title: WideEntries öğesi WideControl (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844908"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="14597-102">WideControl için WideEntries Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="14597-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="14597-103">Geniş bir görünüm tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="14597-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="14597-104">Geniş bir görünüm, bir veya daha fazla tanımları belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="14597-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="14597-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="14597-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="14597-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14597-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="14597-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="14597-107">Attributes and Elements</span></span>

<span data-ttu-id="14597-108">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `WideEntries` öğesi.</span><span class="sxs-lookup"><span data-stu-id="14597-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="14597-109">En az bir alt öğesi belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="14597-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="14597-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="14597-110">Attributes</span></span>

<span data-ttu-id="14597-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="14597-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="14597-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="14597-112">Child Elements</span></span>

|<span data-ttu-id="14597-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="14597-113">Element</span></span>|<span data-ttu-id="14597-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14597-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="14597-115">WideEntry öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="14597-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="14597-116">Geniş bir görünüm tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="14597-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="14597-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="14597-117">Parent Elements</span></span>

|<span data-ttu-id="14597-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="14597-118">Element</span></span>|<span data-ttu-id="14597-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14597-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="14597-120">WideControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="14597-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="14597-121">Bir geniş (çoklu değer) tanımlar görünüm için liste biçimini.</span><span class="sxs-lookup"><span data-stu-id="14597-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="14597-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14597-122">Remarks</span></span>

<span data-ttu-id="14597-123">Geniş bir görünüm tek özellik değeri ya da her nesne için betik değer görüntüleyen bir liste biçimidir.</span><span class="sxs-lookup"><span data-stu-id="14597-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="14597-124">Geniş bir görünüm bileşenleri hakkında daha fazla bilgi için bkz. [geniş görünüm bileşenleri](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="14597-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="14597-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="14597-125">Example</span></span>

<span data-ttu-id="14597-126">Aşağıdaki örnekte gösterildiği bir `WideEntries` tanımlayan tek bir öğe `WideEntry` öğesi.</span><span class="sxs-lookup"><span data-stu-id="14597-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="14597-127">`WideEntry` Tek bir öğe içeriyorsa `WideItem` tanımlayan hangi özelliğinin veya betik değeri görünümünde görüntülenen öğe.</span><span class="sxs-lookup"><span data-stu-id="14597-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="14597-128">Geniş bir görünüm tam bir örnek için bkz: [geniş Görünüm (Temel)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="14597-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="14597-129">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="14597-129">See Also</span></span>

[<span data-ttu-id="14597-130">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="14597-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="14597-131">WideControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="14597-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="14597-132">WideEntry öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="14597-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="14597-133">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="14597-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
