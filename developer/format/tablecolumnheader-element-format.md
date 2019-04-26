---
title: TableColumnHeader öğesi (biçimi) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063818"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="c3d0b-102">TableColumnHeader Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="c3d0b-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="c3d0b-103">Etiketi, bir sütunun genişliğini ve hizalamasını tablosunun bir sütunu etiketi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="c3d0b-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableHeaders öğesi TableControl (biçimi) için TableHeaders TableColumnHeader öğesinin TableControl (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c3d0b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c3d0b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3d0b-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c3d0b-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="c3d0b-106">Attributes and Elements</span></span>

<span data-ttu-id="c3d0b-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `TableColumnHeader` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c3d0b-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c3d0b-108">Attributes</span></span>

<span data-ttu-id="c3d0b-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c3d0b-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="c3d0b-110">Child Elements</span></span>

|<span data-ttu-id="c3d0b-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="c3d0b-111">Element</span></span>|<span data-ttu-id="c3d0b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3d0b-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c3d0b-113">TableControl (biçimi) için TableColumnHeader için etiket öğesi</span><span class="sxs-lookup"><span data-stu-id="c3d0b-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="c3d0b-114">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-114">Optional element.</span></span><br /><br /> <span data-ttu-id="c3d0b-115">Sütun üst kısmında görüntülenen etiketi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="c3d0b-116">Hiçbir etiket belirtilirse, değeri satırlarda gösterilen özelliğin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="c3d0b-117">TableControl (biçimi) için TableColumnHeader için genişliği öğesi</span><span class="sxs-lookup"><span data-stu-id="c3d0b-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="c3d0b-118">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-118">Required element.</span></span><br /><br /> <span data-ttu-id="c3d0b-119">Sütun genişliğini (karakter cinsinden) belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="c3d0b-120">TableControl (biçimi) için TableColumnHeader için hizalama öğesi</span><span class="sxs-lookup"><span data-stu-id="c3d0b-120">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="c3d0b-121">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-121">Optional element.</span></span><br /><br /> <span data-ttu-id="c3d0b-122">Sütunun etiketi nasıl görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="c3d0b-123">Hizalama yok belirtilirse, etiket sol tarafta hizalanır.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c3d0b-124">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="c3d0b-124">Parent Elements</span></span>

|<span data-ttu-id="c3d0b-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="c3d0b-125">Element</span></span>|<span data-ttu-id="c3d0b-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3d0b-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c3d0b-127">TableHeaders öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="c3d0b-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="c3d0b-128">Tablo görünümü sütunlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c3d0b-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3d0b-129">Remarks</span></span>

<span data-ttu-id="c3d0b-130">Tablonun her sütunu için bir üstbilgi belirtin.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="c3d0b-131">Hangi sırayla görüntülenen sütunlar `TableColumnHeader` öğeleri tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="c3d0b-132">Bir tablo aynı sayıda olmalıdır `TableColumnHeader` öğeleri olarak `TableRowEntry` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="c3d0b-133">Sütun üst bilgisine Tablo üst kısmındaki metni nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="c3d0b-134">Satır girişleri tablonun satırlarını hangi verilerin gösterileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="c3d0b-135">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [Tablo görünümü](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="c3d0b-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c3d0b-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="c3d0b-136">Example</span></span>

<span data-ttu-id="c3d0b-137">Aşağıdaki örnek iki gösterir `TableColumnHeader` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="c3d0b-138">İlk öğe etiketini "sütun 1", 16 karakter genişliği sahiptir ve sol tarafta, etiketi hizalanacağını bir sütun tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="c3d0b-139">İkinci öğe etiketini "Sütun 2", 10 karakter genişliği sahiptir ve sütunu etiketini ortalanır bir sütun tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c3d0b-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c3d0b-140">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="c3d0b-140">See Also</span></span>

[<span data-ttu-id="c3d0b-141">TableControl (biçimi) için TableColumnHeader için hizalama öğesi</span><span class="sxs-lookup"><span data-stu-id="c3d0b-141">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="c3d0b-142">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="c3d0b-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c3d0b-143">TableControl (biçimi) için TableColumnHeader için etiket öğesi</span><span class="sxs-lookup"><span data-stu-id="c3d0b-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="c3d0b-144">TableControl (biçimi) için TableHeaders öğesi</span><span class="sxs-lookup"><span data-stu-id="c3d0b-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="c3d0b-145">TableControl öğe (biçimi) için TableColumnHeader genişliği</span><span class="sxs-lookup"><span data-stu-id="c3d0b-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="c3d0b-146">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="c3d0b-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
