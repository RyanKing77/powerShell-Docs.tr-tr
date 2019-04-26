---
title: TableControl (biçimi) için TableRowEntries için TableRowEntry öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075333"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a><span data-ttu-id="a5778-102">TableControl TableRowEntries için TableRowEntry Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="a5778-102">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

<span data-ttu-id="a5778-103">Bir tablonun satırında görüntülenen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a5778-103">Defines the data that is displayed in a row of the table.</span></span>

<span data-ttu-id="a5778-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi TableControl (biçimi) için TableRowEntries TableRowEntry öğesinin TableControl (biçimi)</span><span class="sxs-lookup"><span data-stu-id="a5778-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a5778-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5778-105">Syntax</span></span>

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a5778-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="a5778-106">Attributes and Elements</span></span>

<span data-ttu-id="a5778-107">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `TableRowEntry` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a5778-107">The following sections describe attributes, child elements, and parent element of the `TableRowEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a5778-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a5778-108">Attributes</span></span>

<span data-ttu-id="a5778-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="a5778-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a5778-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="a5778-110">Child Elements</span></span>

|<span data-ttu-id="a5778-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="a5778-111">Element</span></span>|<span data-ttu-id="a5778-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5778-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a5778-113">TableControl (biçimi) için TableRowEntry için EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="a5778-113">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="a5778-114">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="a5778-114">Required element.</span></span><br /><br /> <span data-ttu-id="a5778-115">Özellik değerleri satır içinde görüntülenen nesneleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a5778-115">Defines the objects whose property values are displayed in the row.</span></span>|
|[<span data-ttu-id="a5778-116">TableControl (biçimi) için TableRowEntry için TableColumnItems öğesi</span><span class="sxs-lookup"><span data-stu-id="a5778-116">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="a5778-117">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="a5778-117">Required element.</span></span><br /><br /> <span data-ttu-id="a5778-118">Betikleri değerleri görüntülenir ve özellikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a5778-118">Defines the properties or scripts whose values are displayed.</span></span>|
|[<span data-ttu-id="a5778-119">Öğe için TableRowEntry TableControl (biçimi) için kaydır.</span><span class="sxs-lookup"><span data-stu-id="a5778-119">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="a5778-120">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="a5778-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a5778-121">Sütun genişliğini aşıyor metin ve sonraki satırda görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a5778-121">Specifies that text that exceeds the column width is displayed on the next line.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a5778-122">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="a5778-122">Parent Elements</span></span>

|<span data-ttu-id="a5778-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="a5778-123">Element</span></span>|<span data-ttu-id="a5778-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5778-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a5778-125">TableControl (biçimi) için TableRowEntries öğesi</span><span class="sxs-lookup"><span data-stu-id="a5778-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="a5778-126">Tablonun satırlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a5778-126">Defines the rows of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a5778-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5778-127">Remarks</span></span>

<span data-ttu-id="a5778-128">Bir `TableColumnItems` öğesi ve bir `EntrySelectedBy` öğesi belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a5778-128">One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.</span></span>

<span data-ttu-id="a5778-129">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="a5778-129">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a5778-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="a5778-130">Example</span></span>

<span data-ttu-id="a5778-131">Aşağıdaki örnekte gösterildiği bir `TableRowEntry` tanımlayan iki özelliklerinin değerlerini görüntüleyen bir satır öğesi [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesne.</span><span class="sxs-lookup"><span data-stu-id="a5778-131">The following example shows a `TableRowEntry` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName> Property for first column</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName> Property for second column</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="a5778-132">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a5778-132">See Also</span></span>

[<span data-ttu-id="a5778-133">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="a5778-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a5778-134">TableControl (biçimi) için TableRowEntry için EntrySelectedBy öğesi</span><span class="sxs-lookup"><span data-stu-id="a5778-134">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="a5778-135">TableControl (biçimi) için TableRowEntry için TableColumnItems öğesi</span><span class="sxs-lookup"><span data-stu-id="a5778-135">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="a5778-136">TableControl (biçimi) için TableRowEntries öğesi</span><span class="sxs-lookup"><span data-stu-id="a5778-136">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="a5778-137">Öğe için TableRowEntry TableControl (biçimi) için kaydır.</span><span class="sxs-lookup"><span data-stu-id="a5778-137">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="a5778-138">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="a5778-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
