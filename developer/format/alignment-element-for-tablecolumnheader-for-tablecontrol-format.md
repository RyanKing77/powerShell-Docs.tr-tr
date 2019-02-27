---
title: TableControl (biçimi) için TableColumnHeader için hizalama öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845244"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="6364f-102">TableControl TableColumnHeader için Hizalama Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="6364f-102">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="6364f-103">Sütun üst bilgisindeki verilerin nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6364f-103">Defines how the data in a column header is displayed.</span></span>

<span data-ttu-id="6364f-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableHeaders öğesi (biçimi) TableColumnHeader öğesi (biçimi) hizalama öğesi TableColumnHeader (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="6364f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element (Format) TableColumnHeader Element (Format) Alignment Element for TableColumnHeader (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6364f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6364f-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6364f-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6364f-106">Attributes and Elements</span></span>

<span data-ttu-id="6364f-107">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `Alignment` öğesi.</span><span class="sxs-lookup"><span data-stu-id="6364f-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6364f-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6364f-108">Attributes</span></span>

<span data-ttu-id="6364f-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="6364f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6364f-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6364f-110">Child Elements</span></span>

<span data-ttu-id="6364f-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="6364f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6364f-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6364f-112">Parent Elements</span></span>

|<span data-ttu-id="6364f-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="6364f-113">Element</span></span>|<span data-ttu-id="6364f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6364f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6364f-115">TableColumnHeader öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="6364f-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="6364f-116">Bir etiket, genişliğini ve hizalamasını tablosunun bir sütunu için veri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6364f-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6364f-117">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="6364f-117">Text Value</span></span>

<span data-ttu-id="6364f-118">Aşağıdaki değerlerden birini belirtin.</span><span class="sxs-lookup"><span data-stu-id="6364f-118">Specify one of the following values.</span></span> <span data-ttu-id="6364f-119">Bu değerler büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="6364f-119">These values are not case-sensitive.</span></span>

<span data-ttu-id="6364f-120">Bu öğe belirtilmemişse, sol sütundaki verilerin görüntülenme sola hizalanır. Bu varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="6364f-120">Left Aligns the data displayed in the column on the left This is the default if this element is not specified.</span></span>

<span data-ttu-id="6364f-121">Sağa hizalar, sağdaki sütundaki veriler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6364f-121">Right Aligns the data displayed in the column on the right.</span></span>

<span data-ttu-id="6364f-122">Merkezi merkezleri sütunda görüntülenen veri.</span><span class="sxs-lookup"><span data-stu-id="6364f-122">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="6364f-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6364f-123">Remarks</span></span>

<span data-ttu-id="6364f-124">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="6364f-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6364f-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="6364f-125">Example</span></span>

<span data-ttu-id="6364f-126">Bu örnek gösterir bir `TableColumnHeader` öğesi verisini, sol taraftaki hizalanır.</span><span class="sxs-lookup"><span data-stu-id="6364f-126">This example shows a `TableColumnHeader` element whose data is aligned on the left.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="6364f-127">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6364f-127">See Also</span></span>

[<span data-ttu-id="6364f-128">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="6364f-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="6364f-129">TableColumnHeader öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="6364f-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="6364f-130">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="6364f-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
