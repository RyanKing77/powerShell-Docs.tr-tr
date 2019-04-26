---
title: ListControl öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065266"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="7e312-102">ListControl Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="7e312-102">ListControl Element (Format)</span></span>

<span data-ttu-id="7e312-103">Görünüm için bir liste biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7e312-103">Defines a list format for the view.</span></span>

<span data-ttu-id="7e312-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="7e312-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7e312-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e312-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="7e312-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="7e312-106">Attributes and Elements</span></span>

<span data-ttu-id="7e312-107">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `ListControl` öğesi.</span><span class="sxs-lookup"><span data-stu-id="7e312-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="7e312-108">Bu öğe yalnızca tek bir alt öğe içermelidir.</span><span class="sxs-lookup"><span data-stu-id="7e312-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7e312-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7e312-109">Attributes</span></span>

<span data-ttu-id="7e312-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="7e312-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7e312-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="7e312-111">Child Elements</span></span>

|<span data-ttu-id="7e312-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="7e312-112">Element</span></span>|<span data-ttu-id="7e312-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e312-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7e312-114">ListEntries öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="7e312-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="7e312-115">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="7e312-115">Required element.</span></span><br /><br /> <span data-ttu-id="7e312-116">Liste Görünümü tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e312-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7e312-117">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="7e312-117">Parent Elements</span></span>

|<span data-ttu-id="7e312-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="7e312-118">Element</span></span>|<span data-ttu-id="7e312-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e312-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7e312-120">Görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="7e312-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="7e312-121">Bir veya daha fazla nesne üyeleri görüntülemek için kullanılan bir görünüm tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7e312-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7e312-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e312-122">Remarks</span></span>

<span data-ttu-id="7e312-123">Bir liste görünümü oluşturma hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="7e312-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7e312-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e312-124">Example</span></span>

<span data-ttu-id="7e312-125">Bu örnek için bir liste görünümü gösterir [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) nesne.</span><span class="sxs-lookup"><span data-stu-id="7e312-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="7e312-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="7e312-126">See Also</span></span>

[<span data-ttu-id="7e312-127">Görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="7e312-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="7e312-128">ListEntries öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="7e312-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="7e312-129">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e312-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="7e312-130">Biçimlendirme bir Windows PowerShell yazma ve dosya türleri</span><span class="sxs-lookup"><span data-stu-id="7e312-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
