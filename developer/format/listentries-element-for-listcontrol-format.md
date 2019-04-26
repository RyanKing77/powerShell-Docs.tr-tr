---
title: ListEntries öğesi ListControl (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065402"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="c03ff-102">ListControl için ListEntries Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="c03ff-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="c03ff-103">Liste Görünümü tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c03ff-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="c03ff-104">Liste görünümünde bir veya daha fazla tanımları belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c03ff-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="c03ff-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c03ff-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c03ff-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c03ff-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c03ff-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="c03ff-107">Attributes and Elements</span></span>

<span data-ttu-id="c03ff-108">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `ListEntries` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c03ff-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="c03ff-109">En az bir alt öğesi belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c03ff-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="c03ff-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c03ff-110">Attributes</span></span>

<span data-ttu-id="c03ff-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="c03ff-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c03ff-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="c03ff-112">Child Elements</span></span>

|<span data-ttu-id="c03ff-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="c03ff-113">Element</span></span>|<span data-ttu-id="c03ff-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c03ff-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c03ff-115">ListEntry öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c03ff-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="c03ff-116">Liste Görünümü tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c03ff-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c03ff-117">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="c03ff-117">Parent Elements</span></span>

|<span data-ttu-id="c03ff-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="c03ff-118">Element</span></span>|<span data-ttu-id="c03ff-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c03ff-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c03ff-120">ListControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c03ff-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="c03ff-121">Görünüm için bir liste biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c03ff-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c03ff-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c03ff-122">Remarks</span></span>

<span data-ttu-id="c03ff-123">Liste görünümleri hakkında daha fazla bilgi için bkz: [liste görünümü](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="c03ff-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c03ff-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="c03ff-124">Example</span></span>

<span data-ttu-id="c03ff-125">Bu örnek için liste görünümüne tanımlayan XML öğeleri gösterir [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) nesne.</span><span class="sxs-lookup"><span data-stu-id="c03ff-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="c03ff-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="c03ff-126">See Also</span></span>

[<span data-ttu-id="c03ff-127">ListControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c03ff-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="c03ff-128">ListEntry öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c03ff-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="c03ff-129">Liste Görünümü</span><span class="sxs-lookup"><span data-stu-id="c03ff-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c03ff-130">Biçimlendirme bir Windows PowerShell yazma ve dosya türleri</span><span class="sxs-lookup"><span data-stu-id="c03ff-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
