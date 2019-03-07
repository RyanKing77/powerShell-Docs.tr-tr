---
title: TableControl (biçimi) için TableRowEntry için TableColumnItems öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: faa9ba78397e713400f6072df9915f20d966bb37
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849227"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="046fb-102">TableControl TableRowEntry için TableColumnItems Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="046fb-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="046fb-103">Betikleri değerleri bir satır görüntülenir ve özellikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="046fb-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="046fb-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi TableControl (biçimi) için TableRowEntries TableRowEntry öğesinin TableControl (biçimi) TableControl (biçimi) için TableControlEntry için TableColumnItems öğesi</span><span class="sxs-lookup"><span data-stu-id="046fb-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="046fb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="046fb-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="046fb-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="046fb-106">Attributes and Elements</span></span>

<span data-ttu-id="046fb-107">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `TableColumnItems` öğesi.</span><span class="sxs-lookup"><span data-stu-id="046fb-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="046fb-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="046fb-108">Attributes</span></span>

<span data-ttu-id="046fb-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="046fb-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="046fb-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="046fb-110">Child Elements</span></span>

|<span data-ttu-id="046fb-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="046fb-111">Element</span></span>|<span data-ttu-id="046fb-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="046fb-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="046fb-113">TableControl (biçimi) için TableColumnItems için TableColumnItem öğesi</span><span class="sxs-lookup"><span data-stu-id="046fb-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="046fb-114">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="046fb-114">Required element.</span></span><br /><br /> <span data-ttu-id="046fb-115">Komut satırının sütundaki değeri görüntülenir ve özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="046fb-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="046fb-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="046fb-116">Parent Elements</span></span>

|<span data-ttu-id="046fb-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="046fb-117">Element</span></span>|<span data-ttu-id="046fb-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="046fb-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="046fb-119">TableControl (biçimi) için TableRowEntries için TableRowEntry öğesi</span><span class="sxs-lookup"><span data-stu-id="046fb-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|<span data-ttu-id="046fb-120">Bir tablonun satırında görüntülenen verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="046fb-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="046fb-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="046fb-121">Remarks</span></span>

<span data-ttu-id="046fb-122">A `TableColumnItem` öğesi satırın her sütun için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="046fb-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="046fb-123">İlk girişi, ilk sütunda, ikinci sütun ve benzeri ikinci girdi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="046fb-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="046fb-124">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="046fb-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="046fb-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="046fb-125">Example</span></span>

<span data-ttu-id="046fb-126">Aşağıdaki örnekte gösterildiği bir `TableColumnItems` üç özelliklerini tanımlayan öğe [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesne.</span><span class="sxs-lookup"><span data-stu-id="046fb-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a><span data-ttu-id="046fb-127">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="046fb-127">See Also</span></span>

[<span data-ttu-id="046fb-128">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="046fb-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="046fb-129">TableColumnItem öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="046fb-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="046fb-130">TableRowEntry öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="046fb-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[<span data-ttu-id="046fb-131">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="046fb-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)