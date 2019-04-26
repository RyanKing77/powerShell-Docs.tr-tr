---
title: Öğesi (biçimi) görüntüleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083731"
---
# <a name="view-element-format"></a><span data-ttu-id="c0322-102">Görünüm Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="c0322-102">View Element (Format)</span></span>

<span data-ttu-id="c0322-103">Bir veya daha fazla .NET nesnelerini görüntüleyen bir görünüm tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0322-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="c0322-104">Bir biçimlendirme dosyasında tanımlanan görünümleri sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="c0322-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="c0322-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c0322-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c0322-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0322-106">Syntax</span></span>

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c0322-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="c0322-107">Attributes and Elements</span></span>

<span data-ttu-id="c0322-108">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `View` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c0322-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="c0322-109">Bir ve yalnızca bir denetim alt öğeleri belirtmeniz gerekir ve görünümü ve görünüm kullanan nesneler adını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c0322-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="c0322-110">Özel denetimleri tanımlama, nesneleri nasıl gruplanacağını ve görünüm bant dışı olup olmadığını belirten isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c0322-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="c0322-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c0322-111">Attributes</span></span>

<span data-ttu-id="c0322-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="c0322-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c0322-113">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="c0322-113">Child Elements</span></span>

|<span data-ttu-id="c0322-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="c0322-114">Element</span></span>|<span data-ttu-id="c0322-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0322-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0322-116">Denetim öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c0322-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="c0322-117">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="c0322-117">Optional element.</span></span><br /><br /> <span data-ttu-id="c0322-118">Görünümü içinde adlarına başvurduğu denetimleri kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0322-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="c0322-119">Özel denetim öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c0322-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="c0322-120">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="c0322-120">Optional element.</span></span><br /><br /> <span data-ttu-id="c0322-121">Görünüm için bir özel denetim biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0322-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="c0322-122">GroupBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c0322-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="c0322-123">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="c0322-123">Optional element.</span></span><br /><br /> <span data-ttu-id="c0322-124">.NET nesneleri üyelerin gruplandırılma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0322-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="c0322-125">ListControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c0322-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="c0322-126">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="c0322-126">Optional element.</span></span><br /><br /> <span data-ttu-id="c0322-127">Görünüm için bir liste biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0322-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="c0322-128">Name öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c0322-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="c0322-129">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="c0322-129">Required element.</span></span><br /><br /> <span data-ttu-id="c0322-130">Görünüm başvurmak için kullanılan adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c0322-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="c0322-131">TableControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c0322-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="c0322-132">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="c0322-132">Optional element.</span></span><br /><br /> <span data-ttu-id="c0322-133">Görünüm için bir tablo biçiminde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0322-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="c0322-134">ViewSelectedBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c0322-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="c0322-135">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="c0322-135">Required element.</span></span><br /><br /> <span data-ttu-id="c0322-136">Bu görünüm görüntüler .NET nesneleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0322-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="c0322-137">WideControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c0322-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="c0322-138">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="c0322-138">Optional element.</span></span><br /><br /> <span data-ttu-id="c0322-139">Bir geniş (çoklu değer) tanımlar görünüm için liste biçimini.</span><span class="sxs-lookup"><span data-stu-id="c0322-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c0322-140">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="c0322-140">Parent Elements</span></span>

|<span data-ttu-id="c0322-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="c0322-141">Element</span></span>|<span data-ttu-id="c0322-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0322-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0322-143">ViewDefinitions öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c0322-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="c0322-144">Nesneleri görüntülemek için kullanılan görünümleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0322-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c0322-145">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0322-145">Remarks</span></span>

<span data-ttu-id="c0322-146">Farklı görünümleri özel denetimleri ve bileşenleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="c0322-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="c0322-147">Tablo görünümü bileşenleri</span><span class="sxs-lookup"><span data-stu-id="c0322-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="c0322-148">Liste Görünümü bileşenleri</span><span class="sxs-lookup"><span data-stu-id="c0322-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="c0322-149">Geniş görünüm bileşenleri</span><span class="sxs-lookup"><span data-stu-id="c0322-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="c0322-150">Özel denetimler</span><span class="sxs-lookup"><span data-stu-id="c0322-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="c0322-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0322-151">Example</span></span>

<span data-ttu-id="c0322-152">Bu örnek gösterir bir `View` için bir tablo görünümü tanımlayan öğe [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) nesne.</span><span class="sxs-lookup"><span data-stu-id="c0322-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="c0322-153">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="c0322-153">See Also</span></span>

[<span data-ttu-id="c0322-154">ViewDefinitions öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c0322-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="c0322-155">Name öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c0322-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="c0322-156">ViewSelectedBy öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c0322-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="c0322-157">Denetim öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c0322-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="c0322-158">GroupBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c0322-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="c0322-159">TableControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c0322-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="c0322-160">ListControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c0322-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="c0322-161">WideControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c0322-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="c0322-162">Özel denetim öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c0322-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="c0322-163">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="c0322-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
