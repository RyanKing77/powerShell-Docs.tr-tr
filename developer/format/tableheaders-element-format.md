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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847428"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="c86e3-102">TableHeaders Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="c86e3-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="c86e3-103">Üstbilgileri için bir tablonun sütunlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c86e3-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="c86e3-104">TableControl (biçimi) için ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableHeaders öğesi</span><span class="sxs-lookup"><span data-stu-id="c86e3-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c86e3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c86e3-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c86e3-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c86e3-106">Attributes and Elements</span></span>

<span data-ttu-id="c86e3-107">Aşağıdaki bölümlerde, öznitelikler, alt ve üst öğeleri açıklayan `TableHeaders` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c86e3-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="c86e3-108">Görüntülenecek olan nesnenin her bir özellik için bir alt öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c86e3-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="c86e3-109">Sütun üst bilgisini, alt öğeler belirttiğiniz sırada görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c86e3-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="c86e3-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c86e3-110">Attributes</span></span>

<span data-ttu-id="c86e3-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="c86e3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c86e3-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c86e3-112">Child Elements</span></span>

|<span data-ttu-id="c86e3-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="c86e3-113">Element</span></span>|<span data-ttu-id="c86e3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c86e3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c86e3-115">TableColumnHeader öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c86e3-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="c86e3-116">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="c86e3-116">Optional element.</span></span><br /><br /> <span data-ttu-id="c86e3-117">Etiket, genişliğini ve Tablo görünümüne içeren bir sütun için verilerin hizalama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c86e3-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c86e3-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c86e3-118">Parent Elements</span></span>

|<span data-ttu-id="c86e3-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="c86e3-119">Element</span></span>|<span data-ttu-id="c86e3-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c86e3-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c86e3-121">TableControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c86e3-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="c86e3-122">Bir görünüm için bir tablo biçiminde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c86e3-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c86e3-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c86e3-123">Remarks</span></span>

<span data-ttu-id="c86e3-124">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="c86e3-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c86e3-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="c86e3-125">Example</span></span>

<span data-ttu-id="c86e3-126">Bu örnek gösterir bir `TableHeaders` tanımlayan iki sütun üst öğe.</span><span class="sxs-lookup"><span data-stu-id="c86e3-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c86e3-127">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="c86e3-127">See Also</span></span>

[<span data-ttu-id="c86e3-128">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="c86e3-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c86e3-129">TableColumnHeader öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c86e3-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="c86e3-130">TableControl öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c86e3-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="c86e3-131">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="c86e3-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
