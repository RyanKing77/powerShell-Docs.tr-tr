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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846917"
---
# <a name="view-element-format"></a><span data-ttu-id="bfda8-102">Görünüm Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="bfda8-102">View Element (Format)</span></span>

<span data-ttu-id="bfda8-103">Bir veya daha fazla .NET nesnelerini görüntüleyen bir görünüm tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bfda8-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="bfda8-104">Bir biçimlendirme dosyasında tanımlanan görünümleri sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="bfda8-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="bfda8-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bfda8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bfda8-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bfda8-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="bfda8-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bfda8-107">Attributes and Elements</span></span>

<span data-ttu-id="bfda8-108">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `View` öğesi.</span><span class="sxs-lookup"><span data-stu-id="bfda8-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="bfda8-109">Bir ve yalnızca bir denetim alt öğeleri belirtmeniz gerekir ve görünümü ve görünüm kullanan nesneler adını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bfda8-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="bfda8-110">Özel denetimleri tanımlama, nesneleri nasıl gruplanacağını ve görünüm bant dışı olup olmadığını belirten isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bfda8-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="bfda8-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bfda8-111">Attributes</span></span>

<span data-ttu-id="bfda8-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="bfda8-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bfda8-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bfda8-113">Child Elements</span></span>

|<span data-ttu-id="bfda8-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="bfda8-114">Element</span></span>|<span data-ttu-id="bfda8-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bfda8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bfda8-116">Denetim öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bfda8-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="bfda8-117">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="bfda8-117">Optional element.</span></span><br /><br /> <span data-ttu-id="bfda8-118">Görünümü içinde adlarına başvurduğu denetimleri kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bfda8-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="bfda8-119">Özel denetim öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bfda8-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="bfda8-120">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="bfda8-120">Optional element.</span></span><br /><br /> <span data-ttu-id="bfda8-121">Görünüm için bir özel denetim biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bfda8-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="bfda8-122">GroupBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bfda8-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="bfda8-123">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="bfda8-123">Optional element.</span></span><br /><br /> <span data-ttu-id="bfda8-124">.NET nesneleri üyelerin gruplandırılma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bfda8-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="bfda8-125">ListControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bfda8-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="bfda8-126">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="bfda8-126">Optional element.</span></span><br /><br /> <span data-ttu-id="bfda8-127">Görünüm için bir liste biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bfda8-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="bfda8-128">Name öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bfda8-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="bfda8-129">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="bfda8-129">Required element.</span></span><br /><br /> <span data-ttu-id="bfda8-130">Görünüm başvurmak için kullanılan adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bfda8-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="bfda8-131">TableControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bfda8-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="bfda8-132">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="bfda8-132">Optional element.</span></span><br /><br /> <span data-ttu-id="bfda8-133">Görünüm için bir tablo biçiminde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bfda8-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="bfda8-134">ViewSelectedBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bfda8-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="bfda8-135">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="bfda8-135">Required element.</span></span><br /><br /> <span data-ttu-id="bfda8-136">Bu görünüm görüntüler .NET nesneleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bfda8-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="bfda8-137">WideControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bfda8-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="bfda8-138">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="bfda8-138">Optional element.</span></span><br /><br /> <span data-ttu-id="bfda8-139">Bir geniş (çoklu değer) tanımlar görünüm için liste biçimini.</span><span class="sxs-lookup"><span data-stu-id="bfda8-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bfda8-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bfda8-140">Parent Elements</span></span>

|<span data-ttu-id="bfda8-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="bfda8-141">Element</span></span>|<span data-ttu-id="bfda8-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bfda8-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bfda8-143">ViewDefinitions öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bfda8-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="bfda8-144">Nesneleri görüntülemek için kullanılan görünümleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bfda8-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bfda8-145">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bfda8-145">Remarks</span></span>

<span data-ttu-id="bfda8-146">Farklı görünümleri özel denetimleri ve bileşenleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="bfda8-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="bfda8-147">Tablo görünümü bileşenleri</span><span class="sxs-lookup"><span data-stu-id="bfda8-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="bfda8-148">Liste Görünümü bileşenleri</span><span class="sxs-lookup"><span data-stu-id="bfda8-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="bfda8-149">Geniş görünüm bileşenleri</span><span class="sxs-lookup"><span data-stu-id="bfda8-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="bfda8-150">Özel denetimler</span><span class="sxs-lookup"><span data-stu-id="bfda8-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="bfda8-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="bfda8-151">Example</span></span>

<span data-ttu-id="bfda8-152">Bu örnek gösterir bir `View` için bir tablo görünümü tanımlayan öğe [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) nesne.</span><span class="sxs-lookup"><span data-stu-id="bfda8-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bfda8-153">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="bfda8-153">See Also</span></span>

[<span data-ttu-id="bfda8-154">ViewDefinitions öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bfda8-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="bfda8-155">Name öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bfda8-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="bfda8-156">ViewSelectedBy öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bfda8-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="bfda8-157">Denetim öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bfda8-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="bfda8-158">GroupBy öğesi görünümü (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bfda8-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="bfda8-159">TableControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bfda8-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="bfda8-160">ListControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bfda8-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="bfda8-161">WideControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bfda8-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="bfda8-162">Özel denetim öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="bfda8-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="bfda8-163">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="bfda8-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
