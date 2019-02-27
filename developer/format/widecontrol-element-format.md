---
title: WideControl öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849493"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="5f327-102">WideControl Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="5f327-102">WideControl Element (Format)</span></span>

<span data-ttu-id="5f327-103">Bir geniş (çoklu değer) tanımlar görünüm için liste biçimini.</span><span class="sxs-lookup"><span data-stu-id="5f327-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="5f327-104">Bu görünüm, tek bir özellik değeri ya da her nesne için betik değeri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5f327-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="5f327-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) WideControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="5f327-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5f327-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f327-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5f327-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f327-107">Attributes and Elements</span></span>

<span data-ttu-id="5f327-108">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `WideControl` öğesi.</span><span class="sxs-lookup"><span data-stu-id="5f327-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="5f327-109">Belirtemezsiniz `AutoSize` ve `ColumnNumber` aynı anda öğeleri.</span><span class="sxs-lookup"><span data-stu-id="5f327-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="5f327-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5f327-110">Attributes</span></span>

<span data-ttu-id="5f327-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="5f327-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5f327-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f327-112">Child Elements</span></span>

|<span data-ttu-id="5f327-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="5f327-113">Element</span></span>|<span data-ttu-id="5f327-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f327-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5f327-115">AutoSize öğesi WideControl (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="5f327-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="5f327-116">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="5f327-116">Optional element.</span></span><br /><br /> <span data-ttu-id="5f327-117">Sütun boyutu ve sütun sayısı verilerin boyutuna bağlı olarak ayarlanır olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f327-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="5f327-118">ColumnNumber öğesi WideControl (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="5f327-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="5f327-119">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="5f327-119">Optional element.</span></span><br /><br /> <span data-ttu-id="5f327-120">Geniş görüntülenmesini sütun sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f327-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="5f327-121">WideEntries öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="5f327-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="5f327-122">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="5f327-122">Required element.</span></span><br /><br /> <span data-ttu-id="5f327-123">Geniş bir görünüm tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f327-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5f327-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f327-124">Parent Elements</span></span>

|<span data-ttu-id="5f327-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="5f327-125">Element</span></span>|<span data-ttu-id="5f327-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f327-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5f327-127">Görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="5f327-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="5f327-128">Bir veya daha fazla .NET nesneleri görüntülemek için kullanılan bir görünüm tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5f327-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5f327-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f327-129">Remarks</span></span>

<span data-ttu-id="5f327-130">Geniş bir görünüm tanımlarken, ekleyebileceğiniz `AutoSize` öğesi veya `ColumnNumber` ancak her ikisini de ekleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f327-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="5f327-131">Çoğu durumda, sadece bir tanım her geniş bir görünüm için gereklidir, ancak farklı .NET nesneleri görüntülemek için aynı görünümde kullanmak istiyorsanız birden çok tanım olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="5f327-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="5f327-132">Bu gibi durumlarda, her bir nesne veya nesne için ayrı bir tanımı sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="5f327-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="5f327-133">Geniş bir görünüm bileşenleri hakkında daha fazla bilgi için bkz. [geniş görünüm bileşenleri](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="5f327-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="5f327-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="5f327-134">Example</span></span>

<span data-ttu-id="5f327-135">Aşağıdaki örnekte gösterildiği bir `WideControl` özelliği görüntülemek için kullanılan öğe [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesne.</span><span class="sxs-lookup"><span data-stu-id="5f327-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

<span data-ttu-id="5f327-136">Geniş bir görünüm tam bir örnek için bkz: [geniş Görünüm (Temel)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="5f327-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5f327-137">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="5f327-137">See Also</span></span>

[<span data-ttu-id="5f327-138">AutoSize öğesi WideControl (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="5f327-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="5f327-139">ColumnNumber öğesi WideControl (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="5f327-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="5f327-140">Görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="5f327-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="5f327-141">WideEntries öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="5f327-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="5f327-142">Geniş Görünüm (Temel)</span><span class="sxs-lookup"><span data-stu-id="5f327-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="5f327-143">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="5f327-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="5f327-144">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="5f327-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
