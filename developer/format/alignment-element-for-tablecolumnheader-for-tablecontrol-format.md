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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067017"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="b9ef2-102">TableControl TableColumnHeader için Hizalama Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="b9ef2-102">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="b9ef2-103">Sütun üst bilgisindeki verilerin nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b9ef2-103">Defines how the data in a column header is displayed.</span></span>

<span data-ttu-id="b9ef2-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableHeaders öğesi (biçimi) TableColumnHeader öğesi (biçimi) hizalama öğesi TableColumnHeader (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="b9ef2-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element (Format) TableColumnHeader Element (Format) Alignment Element for TableColumnHeader (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b9ef2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b9ef2-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b9ef2-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="b9ef2-106">Attributes and Elements</span></span>

<span data-ttu-id="b9ef2-107">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `Alignment` öğesi.</span><span class="sxs-lookup"><span data-stu-id="b9ef2-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b9ef2-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b9ef2-108">Attributes</span></span>

<span data-ttu-id="b9ef2-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="b9ef2-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b9ef2-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="b9ef2-110">Child Elements</span></span>

<span data-ttu-id="b9ef2-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="b9ef2-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b9ef2-112">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="b9ef2-112">Parent Elements</span></span>

|<span data-ttu-id="b9ef2-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="b9ef2-113">Element</span></span>|<span data-ttu-id="b9ef2-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9ef2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b9ef2-115">TableColumnHeader öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="b9ef2-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="b9ef2-116">Bir etiket, genişliğini ve hizalamasını tablosunun bir sütunu için veri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b9ef2-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b9ef2-117">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="b9ef2-117">Text Value</span></span>

<span data-ttu-id="b9ef2-118">Aşağıdaki değerlerden birini belirtin.</span><span class="sxs-lookup"><span data-stu-id="b9ef2-118">Specify one of the following values.</span></span> <span data-ttu-id="b9ef2-119">Bu değerler büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="b9ef2-119">These values are not case-sensitive.</span></span>

<span data-ttu-id="b9ef2-120">Bu öğe belirtilmemişse, sol sütundaki verilerin görüntülenme sola hizalanır. Bu varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="b9ef2-120">Left Aligns the data displayed in the column on the left This is the default if this element is not specified.</span></span>

<span data-ttu-id="b9ef2-121">Sağa hizalar, sağdaki sütundaki veriler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b9ef2-121">Right Aligns the data displayed in the column on the right.</span></span>

<span data-ttu-id="b9ef2-122">Merkezi merkezleri sütunda görüntülenen veri.</span><span class="sxs-lookup"><span data-stu-id="b9ef2-122">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9ef2-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9ef2-123">Remarks</span></span>

<span data-ttu-id="b9ef2-124">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="b9ef2-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b9ef2-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="b9ef2-125">Example</span></span>

<span data-ttu-id="b9ef2-126">Bu örnek gösterir bir `TableColumnHeader` öğesi verisini, sol taraftaki hizalanır.</span><span class="sxs-lookup"><span data-stu-id="b9ef2-126">This example shows a `TableColumnHeader` element whose data is aligned on the left.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="b9ef2-127">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="b9ef2-127">See Also</span></span>

[<span data-ttu-id="b9ef2-128">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="b9ef2-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b9ef2-129">TableColumnHeader öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="b9ef2-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="b9ef2-130">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="b9ef2-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
