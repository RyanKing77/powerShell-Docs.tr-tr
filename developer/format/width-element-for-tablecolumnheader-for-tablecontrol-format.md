---
title: TableControl (biçimi) için TableColumnHeader için genişliği öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083629"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="fe6c0-102">TableControl TableColumnHeader için Genişlik Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="fe6c0-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="fe6c0-103">Bir sütunun genişliğini (karakter cinsinden) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fe6c0-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="fe6c0-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableHeaders öğesi TableControl (biçimi) genişliği öğesinin TableColumnHeader öğesi TableHeaders TableControl (biçimi) için TableControl (biçimi) için TableColumnHeader</span><span class="sxs-lookup"><span data-stu-id="fe6c0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fe6c0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe6c0-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fe6c0-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="fe6c0-106">Attributes and Elements</span></span>

<span data-ttu-id="fe6c0-107">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `Width` sütun üst bilgilerini tanımlarken kullanılan öğe.</span><span class="sxs-lookup"><span data-stu-id="fe6c0-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="fe6c0-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fe6c0-108">Attributes</span></span>

<span data-ttu-id="fe6c0-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe6c0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fe6c0-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="fe6c0-110">Child Elements</span></span>

<span data-ttu-id="fe6c0-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe6c0-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fe6c0-112">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="fe6c0-112">Parent Elements</span></span>

|<span data-ttu-id="fe6c0-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="fe6c0-113">Element</span></span>|<span data-ttu-id="fe6c0-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe6c0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fe6c0-115">TableControl (biçimi) için TableHeaders için TableColumnHeader öğesi</span><span class="sxs-lookup"><span data-stu-id="fe6c0-115">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="fe6c0-116">Bir etiket, genişliği ve hizalamasını tablosunda bir sütun için verilerin tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fe6c0-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fe6c0-117">Metin değeri</span><span class="sxs-lookup"><span data-stu-id="fe6c0-117">Text Value</span></span>

<span data-ttu-id="fe6c0-118">Tüm mümkün olduğunda sırasında görüntülenen özellik değerlerini uzunluğundan daha büyük bir genişlik (karakter cinsinden) belirtin.</span><span class="sxs-lookup"><span data-stu-id="fe6c0-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="fe6c0-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe6c0-119">Remarks</span></span>

<span data-ttu-id="fe6c0-120">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="fe6c0-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fe6c0-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe6c0-121">Example</span></span>

<span data-ttu-id="fe6c0-122">Aşağıdaki örnekte gösterildiği bir `TableColumnHeader` genişliğini 16 karakter olan öğe.</span><span class="sxs-lookup"><span data-stu-id="fe6c0-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="fe6c0-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="fe6c0-123">See Also</span></span>

[<span data-ttu-id="fe6c0-124">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe6c0-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="fe6c0-125">TableControl (biçimi) için TableHeader için TableColumnHeader öğesi</span><span class="sxs-lookup"><span data-stu-id="fe6c0-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="fe6c0-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="fe6c0-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
