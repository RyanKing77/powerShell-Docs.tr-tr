---
title: Etiket öğesi için TableColumnHeader TableControl (biçimi) için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 59dfd40b95d5088a711eb89cf101eb31a4b159f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846875"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="635ec-102">TableControl TableColumnHeader için Etiket Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="635ec-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="635ec-103">Bir sütunun en üstünde gösterilen etiketi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="635ec-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="635ec-104">Bu öğe, bir tablo görünümü tanımlarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="635ec-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="635ec-105">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableHeaders öğesi TableControl (biçimi) etiketi öğesinin TableHeaders TableColumnHeader öğesinin TableControl (biçimi) TableColumnHeader TablControl (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="635ec-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TablControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="635ec-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="635ec-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="635ec-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="635ec-107">Attributes and Elements</span></span>

<span data-ttu-id="635ec-108">Öznitelikler, alt ve üst öğesini aşağıdaki bölümlerde açıklanmaktadır `Label` öğesi.</span><span class="sxs-lookup"><span data-stu-id="635ec-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="635ec-109">Yalnızca bir etiket, her sütun için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="635ec-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="635ec-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="635ec-110">Attributes</span></span>

<span data-ttu-id="635ec-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="635ec-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="635ec-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="635ec-112">Child Elements</span></span>

<span data-ttu-id="635ec-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="635ec-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="635ec-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="635ec-114">Parent Elements</span></span>

|<span data-ttu-id="635ec-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="635ec-115">Element</span></span>|<span data-ttu-id="635ec-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="635ec-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="635ec-117">TableControl (biçimi) için TableHeaders için TableColumnHeader öğesi</span><span class="sxs-lookup"><span data-stu-id="635ec-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="635ec-118">Bir etiket, genişliğini ve hizalamasını tablosunun bir sütunu için veri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="635ec-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="635ec-119">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="635ec-119">Text Value</span></span>

<span data-ttu-id="635ec-120">Tablonun sütun üst kısmında görüntülenen metni belirtin.</span><span class="sxs-lookup"><span data-stu-id="635ec-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="635ec-121">Sütun etiket için kısıtlı hiçbir karakter vardır.</span><span class="sxs-lookup"><span data-stu-id="635ec-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="635ec-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="635ec-122">Remarks</span></span>

<span data-ttu-id="635ec-123">Hiçbir etiket belirtilirse, değeri satırlarda gösterilen özelliğin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="635ec-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="635ec-124">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="635ec-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="635ec-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="635ec-125">Example</span></span>

<span data-ttu-id="635ec-126">Bu örnek gösterir bir `TableColumnHeader` olan etiketi olan "Sütun 1" öğesi.</span><span class="sxs-lookup"><span data-stu-id="635ec-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="635ec-127">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="635ec-127">See Also</span></span>

[<span data-ttu-id="635ec-128">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="635ec-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="635ec-129">TableColumnHeader öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="635ec-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="635ec-130">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="635ec-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
