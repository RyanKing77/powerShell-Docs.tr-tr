---
title: TableControl (biçimi) için TableColumnItems için TableColumnItem öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 159f943f6bfb33c5403b5714380631351523789f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057000"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="913b8-102">TableControl TableColumnItems için TableColumnItem Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="913b8-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="913b8-103">Özellik veya betik değeri satırın sütunda görüntülenen tanımlar.</span><span class="sxs-lookup"><span data-stu-id="913b8-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="913b8-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi TableControl (biçimi) için TableRowEntries TableRowEntry öğesinin TableControl (biçimi) TableControl (biçimi) için TableColumnItems TableControl (biçimi) TableColumnItem öğesinin TableControlEntry için TableColumnItems öğesi</span><span class="sxs-lookup"><span data-stu-id="913b8-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="913b8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="913b8-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="913b8-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="913b8-106">Attributes and Elements</span></span>

<span data-ttu-id="913b8-107">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `TableColumnItem` öğesi.</span><span class="sxs-lookup"><span data-stu-id="913b8-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="913b8-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="913b8-108">Attributes</span></span>

<span data-ttu-id="913b8-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="913b8-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="913b8-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="913b8-110">Child Elements</span></span>

|<span data-ttu-id="913b8-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="913b8-111">Element</span></span>|<span data-ttu-id="913b8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="913b8-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="913b8-113">TableControl (biçimi) için TableColumnItem için hizalama öğesi</span><span class="sxs-lookup"><span data-stu-id="913b8-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="913b8-114">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="913b8-114">Optional element.</span></span><br /><br /> <span data-ttu-id="913b8-115">Satır bir sütundaki verilerin nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="913b8-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="913b8-116">TableControl (biçimi) için TableColumnItem için FormatString öğesi</span><span class="sxs-lookup"><span data-stu-id="913b8-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="913b8-117">Satırın sütundaki verilerin biçimlendirilmesi için kullanılan biçimi desen belirtir.</span><span class="sxs-lookup"><span data-stu-id="913b8-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="913b8-118">TableControl (biçimi) için TableColumnItem için PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="913b8-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="913b8-119">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="913b8-119">Optional element.</span></span><br /><br /> <span data-ttu-id="913b8-120">Özellik değeri görüntülenen adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="913b8-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="913b8-121">TableControl (biçimi) için TableColumnItem için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="913b8-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="913b8-122">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="913b8-122">Optional element.</span></span><br /><br /> <span data-ttu-id="913b8-123">Değeri bir satır sütununda görüntülenen komut dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="913b8-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="913b8-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="913b8-124">Parent Elements</span></span>

|<span data-ttu-id="913b8-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="913b8-125">Element</span></span>|<span data-ttu-id="913b8-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="913b8-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="913b8-127">TableControl (biçimi) için TableControlEntry için TableColumnItems öğesi</span><span class="sxs-lookup"><span data-stu-id="913b8-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="913b8-128">Komut satırında değerleri görüntülenir ve özellikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="913b8-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="913b8-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="913b8-129">Remarks</span></span>

<span data-ttu-id="913b8-130">Satırın her sütun bir özelliği bir nesne veya bir betik belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="913b8-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="913b8-131">Alt öğe yok belirtilirse, öğeyi bir yer tutucudur ve veri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="913b8-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="913b8-132">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="913b8-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="913b8-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="913b8-133">Example</span></span>

<span data-ttu-id="913b8-134">Bu örnek gösterir bir `TableColumnItem` değerini görüntüler öğesi `Status` özelliği [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesne.</span><span class="sxs-lookup"><span data-stu-id="913b8-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="913b8-135">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="913b8-135">See Also</span></span>

[<span data-ttu-id="913b8-136">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="913b8-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="913b8-137">TableControl (biçimi) için TableColumnItem için hizalama öğesi</span><span class="sxs-lookup"><span data-stu-id="913b8-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="913b8-138">TableColumnItems öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="913b8-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="913b8-139">TableControl (biçimi) için TableColumnItem için FormatString öğesi</span><span class="sxs-lookup"><span data-stu-id="913b8-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="913b8-140">TableControl (biçimi) için TableColumnItem için PropertyName öğesi</span><span class="sxs-lookup"><span data-stu-id="913b8-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="913b8-141">TableControl (biçimi) için TableColumnItem için ScriptBlock öğesi</span><span class="sxs-lookup"><span data-stu-id="913b8-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="913b8-142">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="913b8-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
