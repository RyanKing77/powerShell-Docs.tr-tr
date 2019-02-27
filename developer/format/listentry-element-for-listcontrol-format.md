---
title: ListEntry öğesi ListControl (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851187"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="74b4a-102">ListControl için ListEntry Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="74b4a-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="74b4a-103">Liste Görünümü tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="74b4a-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="74b4a-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="74b4a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="74b4a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74b4a-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="74b4a-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="74b4a-106">Attributes and Elements</span></span>

<span data-ttu-id="74b4a-107">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `ListEntry` öğesi.</span><span class="sxs-lookup"><span data-stu-id="74b4a-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="74b4a-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="74b4a-108">Attributes</span></span>

<span data-ttu-id="74b4a-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="74b4a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="74b4a-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="74b4a-110">Child Elements</span></span>

|<span data-ttu-id="74b4a-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="74b4a-111">Element</span></span>|<span data-ttu-id="74b4a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74b4a-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="74b4a-113">EntrySelectedBy öğesi ListEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="74b4a-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="74b4a-114">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="74b4a-114">Optional element.</span></span><br /><br /> <span data-ttu-id="74b4a-115">Bu liste görünümü tanımını veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET nesneleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="74b4a-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="74b4a-116">ListItems öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="74b4a-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="74b4a-117">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="74b4a-117">Required element.</span></span><br /><br /> <span data-ttu-id="74b4a-118">Betikleri değerleri tarafından liste görünümü görüntülenir ve özellikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="74b4a-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="74b4a-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="74b4a-119">Parent Elements</span></span>

|<span data-ttu-id="74b4a-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="74b4a-120">Element</span></span>|<span data-ttu-id="74b4a-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74b4a-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="74b4a-122">ListEntries öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="74b4a-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="74b4a-123">Liste Görünümü tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="74b4a-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="74b4a-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74b4a-124">Remarks</span></span>

<span data-ttu-id="74b4a-125">Bir liste görünümü özellik değerlerini ya da her nesne için betik değerlerini görüntüleyen bir liste biçimidir.</span><span class="sxs-lookup"><span data-stu-id="74b4a-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="74b4a-126">Liste görünümleri hakkında daha fazla bilgi için bkz: [bir liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="74b4a-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="74b4a-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="74b4a-127">Example</span></span>

<span data-ttu-id="74b4a-128">Bu örnek için liste görünümüne tanımlayan XML öğeleri gösterir [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) nesne.</span><span class="sxs-lookup"><span data-stu-id="74b4a-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="74b4a-129">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="74b4a-129">See Also</span></span>

[<span data-ttu-id="74b4a-130">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="74b4a-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="74b4a-131">EntrySelectedBy öğesi ListEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="74b4a-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="74b4a-132">ListEntries öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="74b4a-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="74b4a-133">ListItems öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="74b4a-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="74b4a-134">Biçimlendirme bir Windows PowerShell yazma ve dosya türleri</span><span class="sxs-lookup"><span data-stu-id="74b4a-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
