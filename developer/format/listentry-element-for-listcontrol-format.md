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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065232"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="a9648-102">ListControl için ListEntry Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="a9648-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="a9648-103">Liste Görünümü tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9648-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="a9648-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) ListControl öğesi (biçimi) ListEntries öğesi (biçimi) ListEntry öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="a9648-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a9648-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9648-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a9648-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="a9648-106">Attributes and Elements</span></span>

<span data-ttu-id="a9648-107">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `ListEntry` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a9648-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a9648-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a9648-108">Attributes</span></span>

<span data-ttu-id="a9648-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="a9648-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a9648-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="a9648-110">Child Elements</span></span>

|<span data-ttu-id="a9648-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="a9648-111">Element</span></span>|<span data-ttu-id="a9648-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9648-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a9648-113">EntrySelectedBy öğesi ListEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="a9648-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="a9648-114">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="a9648-114">Optional element.</span></span><br /><br /> <span data-ttu-id="a9648-115">Bu liste görünümü tanımını veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET nesneleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a9648-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="a9648-116">ListItems öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="a9648-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="a9648-117">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="a9648-117">Required element.</span></span><br /><br /> <span data-ttu-id="a9648-118">Betikleri değerleri tarafından liste görünümü görüntülenir ve özellikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a9648-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a9648-119">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="a9648-119">Parent Elements</span></span>

|<span data-ttu-id="a9648-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="a9648-120">Element</span></span>|<span data-ttu-id="a9648-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9648-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a9648-122">ListEntries öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="a9648-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="a9648-123">Liste Görünümü tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9648-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a9648-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9648-124">Remarks</span></span>

<span data-ttu-id="a9648-125">Bir liste görünümü özellik değerlerini ya da her nesne için betik değerlerini görüntüleyen bir liste biçimidir.</span><span class="sxs-lookup"><span data-stu-id="a9648-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="a9648-126">Liste görünümleri hakkında daha fazla bilgi için bkz: [bir liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="a9648-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a9648-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9648-127">Example</span></span>

<span data-ttu-id="a9648-128">Bu örnek için liste görünümüne tanımlayan XML öğeleri gösterir [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) nesne.</span><span class="sxs-lookup"><span data-stu-id="a9648-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a9648-129">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a9648-129">See Also</span></span>

[<span data-ttu-id="a9648-130">Bir liste görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="a9648-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="a9648-131">EntrySelectedBy öğesi ListEntry (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="a9648-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="a9648-132">ListEntries öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="a9648-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="a9648-133">ListItems öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="a9648-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="a9648-134">Biçimlendirme bir Windows PowerShell yazma ve dosya türleri</span><span class="sxs-lookup"><span data-stu-id="a9648-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
