---
title: ViewSelectedBy öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851845"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="307ff-102">ViewSelectedBy Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="307ff-102">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="307ff-103">Görünüm tarafından görüntülenen .NET nesneleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="307ff-103">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="307ff-104">Her görünüm en az bir .NET nesnesi belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="307ff-104">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="307ff-105">ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ViewSelectedBy öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="307ff-105">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="307ff-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="307ff-106">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="307ff-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="307ff-107">Attributes and Elements</span></span>

<span data-ttu-id="307ff-108">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `ViewSelectedBy` öğesi.</span><span class="sxs-lookup"><span data-stu-id="307ff-108">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="307ff-109">Bu öğe en az birini içermelidir `TypeName` veya `SelectionSetName` alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="307ff-109">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="307ff-110">Belirtilebilecek alt öğe sayısına bir sınır yoktur ve bunların sırası önemlidir.</span><span class="sxs-lookup"><span data-stu-id="307ff-110">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="307ff-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="307ff-111">Attributes</span></span>

<span data-ttu-id="307ff-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="307ff-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="307ff-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="307ff-113">Child Elements</span></span>

|<span data-ttu-id="307ff-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="307ff-114">Element</span></span>|<span data-ttu-id="307ff-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="307ff-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="307ff-116">TypeName öğesi ViewSelectedBy (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="307ff-116">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="307ff-117">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="307ff-117">Optional element.</span></span><br /><br /> <span data-ttu-id="307ff-118">Görünüm tarafından görüntülenen bir .NET nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="307ff-118">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="307ff-119">SelectionSetName öğesi ViewSelectedBy (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="307ff-119">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="307ff-120">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="307ff-120">Optional element.</span></span><br /><br /> <span data-ttu-id="307ff-121">Görünüm tarafından görüntülenen .NET nesneleri kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="307ff-121">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="307ff-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="307ff-122">Parent Elements</span></span>

|<span data-ttu-id="307ff-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="307ff-123">Element</span></span>|<span data-ttu-id="307ff-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="307ff-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="307ff-125">Görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="307ff-125">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="307ff-126">Bir veya daha fazla .NET nesnelerini görüntüleyen bir görünüm tanımlar.</span><span class="sxs-lookup"><span data-stu-id="307ff-126">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="307ff-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="307ff-127">Remarks</span></span>

<span data-ttu-id="307ff-128">Bu öğe farklı görünümleri nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [Tablo görünümü bileşenleri](./creating-a-table-view.md), [liste görünüm bileşenleri](./creating-a-list-view.md), [geniş görünüm bileşenleri](./creating-a-wide-view.md)ve [Özel denetim bileşenleri](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="307ff-128">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="307ff-129">`SelectionSetName` Öğesi, biçimlendirme dosyası birden çok görünüm tarafından görüntülenen bir nesne tanımlayan olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="307ff-129">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="307ff-130">Seçimi kümeleri nasıl tanımlandığı ve başvurulan hakkında daha fazla bilgi için bkz. [tanımlama ayarlar nesnelerin](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="307ff-130">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="307ff-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="307ff-131">Example</span></span>

<span data-ttu-id="307ff-132">Aşağıdaki örnek nasıl belirtileceğini gösterir [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) nesne için bir liste görünümü.</span><span class="sxs-lookup"><span data-stu-id="307ff-132">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="307ff-133">Aynı şemayı, tablo, geniş ve özel görünümleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="307ff-133">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="307ff-134">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="307ff-134">See Also</span></span>

[<span data-ttu-id="307ff-135">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="307ff-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="307ff-136">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="307ff-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="307ff-137">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="307ff-137">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="307ff-138">Özel denetimler oluşturma</span><span class="sxs-lookup"><span data-stu-id="307ff-138">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="307ff-139">Seçimi ayarlar tanımlama</span><span class="sxs-lookup"><span data-stu-id="307ff-139">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="307ff-140">SelectionSetName öğesi ViewSelectedBy (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="307ff-140">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="307ff-141">TypeName öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="307ff-141">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="307ff-142">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="307ff-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
