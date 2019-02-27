---
title: WideEntry öğesi WideControl (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847183"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="fed78-102">WideControl için WideEntry Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="fed78-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="fed78-103">Geniş bir görünüm tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fed78-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="fed78-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) WideControl öğesi (biçimi) WideEntries öğesi (biçimi) WideEntry öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="fed78-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fed78-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fed78-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fed78-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fed78-106">Attributes and Elements</span></span>

<span data-ttu-id="fed78-107">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `WideEntry` öğesi.</span><span class="sxs-lookup"><span data-stu-id="fed78-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="fed78-108">Tek bir belirtmelisiniz `WideItem` alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="fed78-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fed78-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fed78-109">Attributes</span></span>

<span data-ttu-id="fed78-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="fed78-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fed78-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fed78-111">Child Elements</span></span>

|<span data-ttu-id="fed78-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="fed78-112">Element</span></span>|<span data-ttu-id="fed78-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fed78-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fed78-114">EntrySelectedBy öğesi WideEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="fed78-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="fed78-115">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="fed78-115">Optional element.</span></span><br /><br /> <span data-ttu-id="fed78-116">Bu geniş bir girdi tanımı veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fed78-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="fed78-117">WideItem öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="fed78-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="fed78-118">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="fed78-118">Required element.</span></span><br /><br /> <span data-ttu-id="fed78-119">Betik değeri görüntülenir ve özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fed78-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fed78-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fed78-120">Parent Elements</span></span>

|<span data-ttu-id="fed78-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="fed78-121">Element</span></span>|<span data-ttu-id="fed78-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fed78-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fed78-123">WideEntries öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="fed78-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="fed78-124">Geniş bir görünüm tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fed78-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fed78-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fed78-125">Remarks</span></span>

<span data-ttu-id="fed78-126">Geniş bir görünüm tek özellik değeri ya da her nesne için betik değer görüntüleyen bir liste biçimidir.</span><span class="sxs-lookup"><span data-stu-id="fed78-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="fed78-127">Diğer görünüm türleri farklı olarak, her görünüm tanımı için yalnızca bir öğe öğeyi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fed78-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="fed78-128">Geniş bir görünüm diğer bileşenler hakkında daha fazla bilgi için bkz. [geniş bir görünüm oluşturma](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="fed78-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fed78-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="fed78-129">Example</span></span>

<span data-ttu-id="fed78-130">Aşağıdaki örnekte gösterildiği bir `WideEntry` tanımlayan tek bir öğe `WideItem` öğesi.</span><span class="sxs-lookup"><span data-stu-id="fed78-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="fed78-131">`WideItem` Öğe değeri görünümünde görüntülenen özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fed78-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="fed78-132">Geniş bir görünüm tam bir örnek için bkz: [geniş Görünüm (Temel)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="fed78-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fed78-133">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="fed78-133">See Also</span></span>

[<span data-ttu-id="fed78-134">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="fed78-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="fed78-135">SelectionCondition öğesi WideEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="fed78-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="fed78-136">SelectionSetName öğesi WideEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="fed78-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="fed78-137">TypeName öğesi WideEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="fed78-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="fed78-138">WideEntries öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="fed78-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="fed78-139">WideItem öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="fed78-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="fed78-140">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="fed78-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
