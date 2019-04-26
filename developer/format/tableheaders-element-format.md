---
title: TableHeaders öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075418"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="6df1a-102">TableHeaders Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="6df1a-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="6df1a-103">Üstbilgileri için bir tablonun sütunlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6df1a-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="6df1a-104">TableControl (biçimi) için ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableHeaders öğesi</span><span class="sxs-lookup"><span data-stu-id="6df1a-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6df1a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6df1a-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="6df1a-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="6df1a-106">Attributes and Elements</span></span>

<span data-ttu-id="6df1a-107">Aşağıdaki bölümlerde, öznitelikler, alt ve üst öğeleri açıklayan `TableHeaders` öğesi.</span><span class="sxs-lookup"><span data-stu-id="6df1a-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="6df1a-108">Görüntülenecek olan nesnenin her bir özellik için bir alt öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6df1a-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="6df1a-109">Sütun üst bilgisini, alt öğeler belirttiğiniz sırada görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6df1a-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="6df1a-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6df1a-110">Attributes</span></span>

<span data-ttu-id="6df1a-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="6df1a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6df1a-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="6df1a-112">Child Elements</span></span>

|<span data-ttu-id="6df1a-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="6df1a-113">Element</span></span>|<span data-ttu-id="6df1a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6df1a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6df1a-115">TableColumnHeader öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="6df1a-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="6df1a-116">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="6df1a-116">Optional element.</span></span><br /><br /> <span data-ttu-id="6df1a-117">Etiket, genişliğini ve Tablo görünümüne içeren bir sütun için verilerin hizalama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6df1a-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6df1a-118">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="6df1a-118">Parent Elements</span></span>

|<span data-ttu-id="6df1a-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="6df1a-119">Element</span></span>|<span data-ttu-id="6df1a-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6df1a-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6df1a-121">TableControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="6df1a-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="6df1a-122">Bir görünüm için bir tablo biçiminde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6df1a-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6df1a-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6df1a-123">Remarks</span></span>

<span data-ttu-id="6df1a-124">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="6df1a-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6df1a-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="6df1a-125">Example</span></span>

<span data-ttu-id="6df1a-126">Bu örnek gösterir bir `TableHeaders` tanımlayan iki sütun üst öğe.</span><span class="sxs-lookup"><span data-stu-id="6df1a-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
  <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a><span data-ttu-id="6df1a-127">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6df1a-127">See Also</span></span>

[<span data-ttu-id="6df1a-128">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="6df1a-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="6df1a-129">TableColumnHeader öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="6df1a-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="6df1a-130">TableControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="6df1a-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="6df1a-131">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="6df1a-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
