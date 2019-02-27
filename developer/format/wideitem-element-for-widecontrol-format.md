---
title: WideItem öğesi WideControl (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851453"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="0755e-102">WideControl için WideItem Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="0755e-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="0755e-103">Betik değeri görüntülenir ve özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0755e-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="0755e-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi (biçimi) WideItem öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="0755e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0755e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0755e-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0755e-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0755e-106">Attributes and Elements</span></span>

<span data-ttu-id="0755e-107">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `WideItem` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0755e-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="0755e-108">`FormatString` Öğesi, isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0755e-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="0755e-109">Ancak, belirtmeniz gereken bir `PropertyName` veya `ScriptBlock` öğesi, ancak belirtemez hem de.</span><span class="sxs-lookup"><span data-stu-id="0755e-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="0755e-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0755e-110">Attributes</span></span>

<span data-ttu-id="0755e-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="0755e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0755e-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0755e-112">Child Elements</span></span>

|<span data-ttu-id="0755e-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="0755e-113">Element</span></span>|<span data-ttu-id="0755e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0755e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0755e-115">WideItem WideControl (biçimi) için için FormatString öğesi</span><span class="sxs-lookup"><span data-stu-id="0755e-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="0755e-116">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="0755e-116">Optional element.</span></span><br /><br /> <span data-ttu-id="0755e-117">Özellik veya betik değeri Görünümü'nde nasıl görüntüleneceğini tanımlayan bir biçim deseni belirtir.</span><span class="sxs-lookup"><span data-stu-id="0755e-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="0755e-118">PropertyName öğesi WideItem (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="0755e-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="0755e-119">Özellik değeri geniş görünümünde görüntülenen nesne belirtir.</span><span class="sxs-lookup"><span data-stu-id="0755e-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="0755e-120">ScriptBlock öğesi WideItem (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="0755e-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="0755e-121">Değeri, geniş görünümde görüntülenir betiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0755e-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0755e-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0755e-122">Parent Elements</span></span>

|<span data-ttu-id="0755e-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="0755e-123">Element</span></span>|<span data-ttu-id="0755e-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0755e-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0755e-125">WideEntry öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="0755e-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="0755e-126">Geniş bir görünüm tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0755e-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0755e-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0755e-127">Remarks</span></span>

<span data-ttu-id="0755e-128">Geniş bir görünüm bileşenleri hakkında daha fazla bilgi için bkz. [geniş Görünüm](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="0755e-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0755e-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="0755e-129">Example</span></span>

<span data-ttu-id="0755e-130">Aşağıdaki örnekte gösterildiği bir `WideEntry` tanımlayan tek bir öğe `WideItem` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0755e-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="0755e-131">`WideItem` Öğe tanımlar özelliği veya betik değeri Görünümü'nde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0755e-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="0755e-132">Geniş bir görünüm tam bir örnek için bkz: [geniş Görünüm (Temel)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="0755e-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0755e-133">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="0755e-133">See Also</span></span>

[<span data-ttu-id="0755e-134">WideItem WideControl (biçimi) için için FormatString öğesi</span><span class="sxs-lookup"><span data-stu-id="0755e-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="0755e-135">PropertyName öğesi WideItem (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="0755e-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="0755e-136">ScriptBlock öğesi WideItem (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="0755e-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="0755e-137">WideEntry öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="0755e-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="0755e-138">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="0755e-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
