---
title: TableControl (biçimi) için TableRowEntries öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075503"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="205aa-102">TableControl için TableRowEntries Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="205aa-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="205aa-103">Tablonun satırlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="205aa-103">Defines the rows of the table.</span></span>

<span data-ttu-id="205aa-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi TableControl (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="205aa-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="205aa-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="205aa-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="205aa-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="205aa-106">Attributes and Elements</span></span>

<span data-ttu-id="205aa-107">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `TableRowEntries` öğesi.</span><span class="sxs-lookup"><span data-stu-id="205aa-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="205aa-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="205aa-108">Attributes</span></span>

<span data-ttu-id="205aa-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="205aa-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="205aa-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="205aa-110">Child Elements</span></span>

|<span data-ttu-id="205aa-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="205aa-111">Element</span></span>|<span data-ttu-id="205aa-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="205aa-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="205aa-113">TableControl (biçimi) için TableRowEntries için TableRowEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="205aa-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="205aa-114">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="205aa-114">Required element.</span></span><br /><br /> <span data-ttu-id="205aa-115">Bir tablonun satırında görüntülenen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="205aa-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="205aa-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="205aa-116">Parent Elements</span></span>

|<span data-ttu-id="205aa-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="205aa-117">Element</span></span>|<span data-ttu-id="205aa-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="205aa-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="205aa-119">TableControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="205aa-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="205aa-120">Bir görünüm için bir tablo biçiminde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="205aa-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="205aa-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="205aa-121">Remarks</span></span>

<span data-ttu-id="205aa-122">Bir veya daha fazla belirtmelisiniz `TableRowEntry` Tablo görünümü için öğeleri.</span><span class="sxs-lookup"><span data-stu-id="205aa-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="205aa-123">En fazla sınırsız sayıda `TableRowEntry` eklenebilir öğeleri ve bunların sırası önemlidir.</span><span class="sxs-lookup"><span data-stu-id="205aa-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="205aa-124">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="205aa-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="205aa-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="205aa-125">Example</span></span>

<span data-ttu-id="205aa-126">Aşağıdaki örnekte gösterildiği bir `TableRowEntries` tanımlayan iki özelliklerinin değerlerini görüntüleyen bir satır öğesi [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesne.</span><span class="sxs-lookup"><span data-stu-id="205aa-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntries>
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
</TableRowEntries>

```

## <a name="see-also"></a><span data-ttu-id="205aa-127">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="205aa-127">See Also</span></span>

[<span data-ttu-id="205aa-128">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="205aa-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="205aa-129">TableControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="205aa-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="205aa-130">TableRowEntry öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="205aa-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="205aa-131">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="205aa-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
