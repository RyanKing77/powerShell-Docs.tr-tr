---
title: TableControl (biçimi) için TableColumnItem için PropertyName öğesi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849241"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="8fda1-102">TableControl TableColumnItem için PropertyName Öğesi (Biçim)</span><span class="sxs-lookup"><span data-stu-id="8fda1-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="8fda1-103">Değeri satır sütununda görüntülenen alan özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="8fda1-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="8fda1-104">Yapılandırma öğesi (biçimi) ViewDefinitions öğesi (biçimi) görünüm öğesi (biçimi) TableControl öğesi (biçimi) TableRowEntries öğesi (biçimi) TableRowEntry öğesi (biçimi) TableColumnItems öğesi (biçimi) TableColumnItem öğesi (biçimi) PropertyName öğesi TableColumnItem (biçimi) için</span><span class="sxs-lookup"><span data-stu-id="8fda1-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8fda1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8fda1-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8fda1-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8fda1-106">Attributes and Elements</span></span>

<span data-ttu-id="8fda1-107">Aşağıdaki öznitelikler, alt ve üst öğenin bölümlerde `PropertyName` öğesi.</span><span class="sxs-lookup"><span data-stu-id="8fda1-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8fda1-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8fda1-108">Attributes</span></span>

<span data-ttu-id="8fda1-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="8fda1-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8fda1-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8fda1-110">Child Elements</span></span>

<span data-ttu-id="8fda1-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="8fda1-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8fda1-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8fda1-112">Parent Elements</span></span>

|<span data-ttu-id="8fda1-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="8fda1-113">Element</span></span>|<span data-ttu-id="8fda1-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fda1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8fda1-115">TableColumnItem öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="8fda1-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="8fda1-116">Özellik veya betik değeri satırın sütunda görüntülenen tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8fda1-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8fda1-117">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="8fda1-117">Text Value</span></span>

<span data-ttu-id="8fda1-118">Özellik değeri görüntülenen adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="8fda1-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="8fda1-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fda1-119">Remarks</span></span>

<span data-ttu-id="8fda1-120">Tablo görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir tablo görünümü oluşturma](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="8fda1-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8fda1-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="8fda1-121">Example</span></span>

<span data-ttu-id="8fda1-122">Bu örnek gösterir bir `TableColumnItem` belirten öğesi `Status` özelliği [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesne.</span><span class="sxs-lookup"><span data-stu-id="8fda1-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="8fda1-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="8fda1-123">See Also</span></span>

[<span data-ttu-id="8fda1-124">Bir tablo görünümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="8fda1-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8fda1-125">TableColumnItem öğesi (biçimi)</span><span class="sxs-lookup"><span data-stu-id="8fda1-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="8fda1-126">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="8fda1-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
