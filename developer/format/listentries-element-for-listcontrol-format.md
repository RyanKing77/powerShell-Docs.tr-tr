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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847365"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="291a1-102">ListControl için ListEntries Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="291a1-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="291a1-103">Liste Görünümü tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="291a1-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="291a1-104">Liste görünümünde bir veya daha fazla tanımları belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="291a1-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="291a1-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="291a1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="291a1-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="291a1-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="291a1-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="291a1-107">Attributes and Elements</span></span>

<span data-ttu-id="291a1-108">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `ListEntries` öğesi.</span><span class="sxs-lookup"><span data-stu-id="291a1-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="291a1-109">En az bir alt öğesi belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="291a1-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="291a1-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="291a1-110">Attributes</span></span>

<span data-ttu-id="291a1-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="291a1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="291a1-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="291a1-112">Child Elements</span></span>

|<span data-ttu-id="291a1-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="291a1-113">Element</span></span>|<span data-ttu-id="291a1-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="291a1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="291a1-115">ListEntry öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="291a1-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="291a1-116">Liste Görünümü tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="291a1-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="291a1-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="291a1-117">Parent Elements</span></span>

|<span data-ttu-id="291a1-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="291a1-118">Element</span></span>|<span data-ttu-id="291a1-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="291a1-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="291a1-120">ListControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="291a1-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="291a1-121">Görünüm için bir liste biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="291a1-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="291a1-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="291a1-122">Remarks</span></span>

<span data-ttu-id="291a1-123">Liste görünümleri hakkında daha fazla bilgi için bkz: [liste görünümü](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="291a1-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="291a1-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="291a1-124">Example</span></span>

<span data-ttu-id="291a1-125">Bu örnek için liste görünümüne tanımlayan XML öğeleri gösterir [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) nesne.</span><span class="sxs-lookup"><span data-stu-id="291a1-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="291a1-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="291a1-126">See Also</span></span>

[<span data-ttu-id="291a1-127">ListControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="291a1-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="291a1-128">ListEntry öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="291a1-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="291a1-129">Liste Görünümü</span><span class="sxs-lookup"><span data-stu-id="291a1-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="291a1-130">Biçimlendirme bir Windows PowerShell yazma ve dosya türleri</span><span class="sxs-lookup"><span data-stu-id="291a1-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
