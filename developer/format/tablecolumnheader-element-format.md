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
ms.openlocfilehash: 15f47c97ac5d55cb76e153af86672b3ffaf176c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848632"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="8e165-102">TableColumnHeader Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="8e165-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="8e165-103">Etiketi, bir sütunun genişliğini ve hizalamasını tablosunun bir sütunu etiketi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8e165-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="8e165-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableHeaders öğesi TableControl (biçimi) için TableHeaders TableColumnHeader öğesinin TableControl (biçimi)</span><span class="sxs-lookup"><span data-stu-id="8e165-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8e165-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e165-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8e165-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8e165-106">Attributes and Elements</span></span>

<span data-ttu-id="8e165-107">Aşağıdaki öznitelikler, alt ve üst öğesini bölümlerde `TableColumnHeader` öğesi.</span><span class="sxs-lookup"><span data-stu-id="8e165-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8e165-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8e165-108">Attributes</span></span>

<span data-ttu-id="8e165-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="8e165-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8e165-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8e165-110">Child Elements</span></span>

|<span data-ttu-id="8e165-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="8e165-111">Element</span></span>|<span data-ttu-id="8e165-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e165-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e165-113">TableControl (biçimi) için TableColumnHeader için etiket öğesi</span><span class="sxs-lookup"><span data-stu-id="8e165-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="8e165-114">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="8e165-114">Optional element.</span></span><br /><br /> <span data-ttu-id="8e165-115">Sütun üst kısmında görüntülenen etiketi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8e165-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="8e165-116">Hiçbir etiket belirtilirse, değeri satırlarda gösterilen özelliğin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8e165-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="8e165-117">TableControl (biçimi) için TableColumnHeader için genişliği öğesi</span><span class="sxs-lookup"><span data-stu-id="8e165-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="8e165-118">Gerekli öğe.</span><span class="sxs-lookup"><span data-stu-id="8e165-118">Required element.</span></span><br /><br /> <span data-ttu-id="8e165-119">Sütun genişliğini (karakter cinsinden) belirtir.</span><span class="sxs-lookup"><span data-stu-id="8e165-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="8e165-120">TableControl (biçimi) için TableColumbnHeader için hizalama öğesi</span><span class="sxs-lookup"><span data-stu-id="8e165-120">Alignment Element for TableColumbnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="8e165-121">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="8e165-121">Optional element.</span></span><br /><br /> <span data-ttu-id="8e165-122">Sütunun etiketi nasıl görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8e165-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="8e165-123">Hizalama yok belirtilirse, etiket sol tarafta hizalanır.</span><span class="sxs-lookup"><span data-stu-id="8e165-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8e165-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8e165-124">Parent Elements</span></span>

|<span data-ttu-id="8e165-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="8e165-125">Element</span></span>|<span data-ttu-id="8e165-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e165-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e165-127">TableHeaders öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="8e165-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="8e165-128">Tablo görünümü sütunlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8e165-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8e165-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e165-129">Remarks</span></span>

<span data-ttu-id="8e165-130">Tablonun her sütunu için bir üstbilgi belirtin.</span><span class="sxs-lookup"><span data-stu-id="8e165-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="8e165-131">Hangi sırayla görüntülenen sütunlar `TableColumnHeader` öğeleri tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8e165-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="8e165-132">Bir tablo aynı sayıda olmalıdır `TableColumnHeader` öğeleri olarak `TableRowEntry` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="8e165-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="8e165-133">Sütun üst bilgisine Tablo üst kısmındaki metni nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8e165-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="8e165-134">Satır girişleri tablonun satırlarını hangi verilerin gösterileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="8e165-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="8e165-135">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [Tablo görünümü](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="8e165-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8e165-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e165-136">Example</span></span>

<span data-ttu-id="8e165-137">Aşağıdaki örnek iki gösterir `TableColumnHeader` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="8e165-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="8e165-138">İlk öğe etiketini "sütun 1", 16 karakter genişliği sahiptir ve sol tarafta, etiketi hizalanacağını bir sütun tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8e165-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="8e165-139">İkinci öğe etiketini "Sütun 2", 10 karakter genişliği sahiptir ve sütunu etiketini ortalanır bir sütun tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8e165-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8e165-140">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="8e165-140">See Also</span></span>

[<span data-ttu-id="8e165-141">Hizalama öğesi için TableColumnHeader TableContrl (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="8e165-141">Alignment Element for TableColumnHeader for TableContrl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="8e165-142">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="8e165-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8e165-143">TableControl (biçimi) için TableColumnHeader için etiket öğesi</span><span class="sxs-lookup"><span data-stu-id="8e165-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="8e165-144">TableControl (biçimi) için TableHeaders öğesi</span><span class="sxs-lookup"><span data-stu-id="8e165-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="8e165-145">TableControl öğe (biçimi) için TableColumnHeader genişliği</span><span class="sxs-lookup"><span data-stu-id="8e165-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="8e165-146">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="8e165-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
