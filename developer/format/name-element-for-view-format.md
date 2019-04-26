---
title: Öğesi görünümü (biçimi) için ad | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065079"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="e3fdf-102">Görünüm için Ad Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="e3fdf-102">Name Element for View (Format)</span></span>

<span data-ttu-id="e3fdf-103">Görünümü tanımlamak için kullanılan adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="e3fdf-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) Name öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="e3fdf-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e3fdf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3fdf-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e3fdf-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="e3fdf-106">Attributes and Elements</span></span>

<span data-ttu-id="e3fdf-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `Name` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="e3fdf-108">Yalnızca bir `Name` öğesi her görünüm için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3fdf-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e3fdf-109">Attributes</span></span>

<span data-ttu-id="e3fdf-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e3fdf-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="e3fdf-111">Child Elements</span></span>

<span data-ttu-id="e3fdf-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e3fdf-113">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="e3fdf-113">Parent Elements</span></span>

|<span data-ttu-id="e3fdf-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="e3fdf-114">Element</span></span>|<span data-ttu-id="e3fdf-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3fdf-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3fdf-116">Görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="e3fdf-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="e3fdf-117">Bir veya daha fazla .NET nesneleri üyelerini görüntülemek için kullanılan bir görünüm tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e3fdf-118">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="e3fdf-118">Text Value</span></span>

<span data-ttu-id="e3fdf-119">Görünüm için benzersiz bir kolay ad belirtin.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="e3fdf-120">Bu ad, hangi nesnesini veya nesne kümesini kullanın hangi komut nesneleri ya da bunların bir kombinasyonunu döndürür görünümü görünümün (örneğin, bir tablo görünümü veya liste görünümü), türe başvuru içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3fdf-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3fdf-121">Remarks</span></span>

<span data-ttu-id="e3fdf-122">Farklı görünüm türleri hakkında daha fazla bilgi için aşağıdaki konulara bakın: [Tablo görünümü](./creating-a-table-view.md), [liste görünümü](./creating-a-list-view.md), [geniş Görünüm](./creating-a-wide-view.md), ve [Özel Görünüm](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e3fdf-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="e3fdf-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="e3fdf-123">Example</span></span>

<span data-ttu-id="e3fdf-124">Aşağıdaki örnekte gösterildiği bir `View` için bir tablo görünümü tanımlayan öğe [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) nesne.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="e3fdf-125">"Hizmet" görünümü adıdır.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="e3fdf-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e3fdf-126">See Also</span></span>

[<span data-ttu-id="e3fdf-127">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3fdf-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e3fdf-128">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3fdf-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e3fdf-129">Geniş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3fdf-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e3fdf-130">Özel denetimler oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3fdf-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="e3fdf-131">Görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="e3fdf-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="e3fdf-132">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="e3fdf-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
