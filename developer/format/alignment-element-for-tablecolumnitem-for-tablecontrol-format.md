---
title: TableControl (biçimi) için TableColumnItem için hizalama öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b07a53df-64f1-49b0-8cea-c993b3f1f76b
caps.latest.revision: 10
ms.openlocfilehash: 1bc936b94ee6fd6239e9e3c4afcdb8f14fbe36eb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066949"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="60404-102">TableControl TableColumnItem için Hizalama Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="60404-102">Alignment Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="60404-103">Satır bir sütundaki verilerin nasıl görüntüleneceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="60404-103">Defines how the data in a column of the row is displayed.</span></span>

<span data-ttu-id="60404-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi (biçimi) TableRowEntry öğesi (biçimi) TableColumnItems öğesi (biçimi) TableColumnItem öğesi (biçimi) Hizalama öğesi TableColumnItem (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="60404-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) Alignment Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="60404-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60404-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="60404-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="60404-106">Attributes and Elements</span></span>

<span data-ttu-id="60404-107">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `Alignment` öğesi.</span><span class="sxs-lookup"><span data-stu-id="60404-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="60404-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="60404-108">Attributes</span></span>

<span data-ttu-id="60404-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="60404-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="60404-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="60404-110">Child Elements</span></span>

<span data-ttu-id="60404-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="60404-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="60404-112">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="60404-112">Parent Elements</span></span>

|<span data-ttu-id="60404-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="60404-113">Element</span></span>|<span data-ttu-id="60404-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60404-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="60404-115">TableColumnItem öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="60404-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="60404-116">Bir etiket, genişliğini ve hizalamasını tablosunun bir sütunu için veri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="60404-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="60404-117">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="60404-117">Text Value</span></span>

<span data-ttu-id="60404-118">Aşağıdaki değerlerden birini belirtin.</span><span class="sxs-lookup"><span data-stu-id="60404-118">Specify one of the following values.</span></span> <span data-ttu-id="60404-119">(Bu değerler büyük küçük harfe duyarlı değildir.)</span><span class="sxs-lookup"><span data-stu-id="60404-119">(These values are not case-sensitive.)</span></span>

<span data-ttu-id="60404-120">Sola kaydırmalar sol sütunda görüntülenen veriler.</span><span class="sxs-lookup"><span data-stu-id="60404-120">Left Shifts the data displayed in the column to the left.</span></span> <span data-ttu-id="60404-121">(Bu öğe belirtilmemişse, varsayılan değer budur.)</span><span class="sxs-lookup"><span data-stu-id="60404-121">(This is the default if this element is not specified.)</span></span>

<span data-ttu-id="60404-122">Sağa kaydırmalar sağ sütunda görüntülenen veriler.</span><span class="sxs-lookup"><span data-stu-id="60404-122">Right Shifts the data displayed in the column to the right.</span></span>

<span data-ttu-id="60404-123">Merkezi merkezleri sütunda görüntülenen veri.</span><span class="sxs-lookup"><span data-stu-id="60404-123">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="60404-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60404-124">Remarks</span></span>

<span data-ttu-id="60404-125">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [Tablo görünümü](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="60404-125">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="60404-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="60404-126">See Also</span></span>

[<span data-ttu-id="60404-127">Tablo görünümü</span><span class="sxs-lookup"><span data-stu-id="60404-127">Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="60404-128">TableColumnItem öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="60404-128">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
