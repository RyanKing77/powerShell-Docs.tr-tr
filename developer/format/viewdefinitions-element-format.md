---
title: ViewDefinitions öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851075"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="889e4-102">ViewDefinitions Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="889e4-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="889e4-103">.NET nesneleri görüntülemek için kullanılan görünümleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="889e4-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="889e4-104">Bu görünümler, özelliklerini ve betik değerlerini bir nesnenin bir tablo biçiminde, liste biçimini, geniş bir biçim ve özel denetim biçimi görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="889e4-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="889e4-105">Yapılandırma öğesi (biçimi) ViewDefinitions (XML biçimi) öğesi</span><span class="sxs-lookup"><span data-stu-id="889e4-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="889e4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="889e4-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="889e4-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="889e4-107">Attributes and Elements</span></span>

<span data-ttu-id="889e4-108">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `ViewDefinitions` öğesi.</span><span class="sxs-lookup"><span data-stu-id="889e4-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="889e4-109">Bir biçimlendirme dosyasında tanımlanan görünümleri sayısına bir sınır yoktur ve herhangi bir sırada eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="889e4-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="889e4-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="889e4-110">Attributes</span></span>

<span data-ttu-id="889e4-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="889e4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="889e4-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="889e4-112">Child Elements</span></span>

|<span data-ttu-id="889e4-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="889e4-113">Element</span></span>|<span data-ttu-id="889e4-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="889e4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="889e4-115">Görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="889e4-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="889e4-116">Bir veya daha fazla .NET nesneleri görüntülemek için kullanılan bir görünüm tanımlar.</span><span class="sxs-lookup"><span data-stu-id="889e4-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="889e4-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="889e4-117">Parent Elements</span></span>

|<span data-ttu-id="889e4-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="889e4-118">Element</span></span>|<span data-ttu-id="889e4-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="889e4-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="889e4-120">Yapılandırma öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="889e4-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="889e4-121">Biçimlendirme bir dosyanın üst düzey öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="889e4-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="889e4-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="889e4-122">Remarks</span></span>

<span data-ttu-id="889e4-123">Görünüm türlerini farklı bileşenleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="889e4-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="889e4-124">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="889e4-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="889e4-125">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="889e4-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="889e4-126">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="889e4-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="889e4-127">Özel denetimler</span><span class="sxs-lookup"><span data-stu-id="889e4-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="889e4-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="889e4-128">Example</span></span>

<span data-ttu-id="889e4-129">Bu örnek gösterir bir `ViewDefinitions` Tablo görünümü ve liste görünümü üst öğe içeren öğe.</span><span class="sxs-lookup"><span data-stu-id="889e4-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a><span data-ttu-id="889e4-130">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="889e4-130">See Also</span></span>

[<span data-ttu-id="889e4-131">Yapılandırma öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="889e4-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="889e4-132">Görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="889e4-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="889e4-133">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="889e4-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="889e4-134">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="889e4-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="889e4-135">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="889e4-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="889e4-136">Özel denetimler</span><span class="sxs-lookup"><span data-stu-id="889e4-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="889e4-137">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="889e4-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)